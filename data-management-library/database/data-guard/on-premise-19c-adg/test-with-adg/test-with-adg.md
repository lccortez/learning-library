# Test with ADG

## Introduction
In this lab, You can run some testing with the ADG.

Estimated Lab Time: 40 minutes.

### Objectives

- Test transaction replication
- Check lag between the primary and standby
- Test DML Redirection
- Switchover to the standby

### Prerequisites

This lab assumes you have already completed the following labs:

- Deploy Active Data Guard

## **STEP 1:** Test transaction replication

1. Connect the primary side with **oracle** user, create a test user in orclpdb, and grant privileges to the user. You need open the pdb if it is closed.

    ```
    [oracle@primary ~]$ sqlplus / as sysdba
    
    SQL*Plus: Release 19.0.0.0.0 - Production on Sat Feb 1 06:52:50 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2019, Oracle.  All rights reserved.
    
    
    Connected to:
    Oracle Database 19c Enterprise Edition Release 19.0.0.0.0 - Production
    Version 19.10.0.0.0
    
    SQL> show pdbs
    
        CON_ID CON_NAME			  OPEN MODE  RESTRICTED
    ---------- ------------------------------ ---------- ----------
    	 2 PDB$SEED			  READ ONLY  NO
    	 3 ORCLPDB			  MOUNTED
    
    SQL> alter pluggable database all open;
    
    Pluggable database altered.
    
    SQL> alter session set container=orclpdb;
    
    Session altered.
    
    SQL> create user testuser identified by testuser;
    
    User created.
    
    SQL> grant connect,resource to testuser;
    
    Grant succeeded.
    
    SQL> alter user testuser quota unlimited on users;
    
    User altered.
    
    SQL> exit;
    ```

2. Connect with **testuser**, create a test table and insert a test record.

    ```
    [oracle@primary ~]$ sqlplus testuser/testuser@localhost:1521/orclpdb
    
    SQL*Plus: Release 19.0.0.0.0 - Production on Sat Feb 1 06:59:56 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2019, Oracle.  All rights reserved.
    
    
    Connected to:
    Oracle Database 19c Enterprise Edition Release 19.0.0.0.0 - Production
    Version 19.10.0.0.0
    
    SQL> create table test(a number,b varchar2(20));
    
    Table created.
    SQL> insert into test values(1,'line1');
    
    1 row created.
    
    SQL> commit;
    
    Commit complete.
    
    SQL>  
    ```

3. From the standby side, open the standby database as read only.

    ```
    [oracle@standby ~]$ sqlplus / as sysdba
    
    SQL*Plus: Release 19.0.0.0.0 - Production on Sat Feb 1 07:04:39 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2019, Oracle.  All rights reserved.
    
    
    Connected to:
    Oracle Database 19c EE Extreme Perf Release 19.0.0.0.0 - Production
    Version 19.10.0.0.0
    
    SQL> select open_mode,database_role from v$database;
    
    OPEN_MODE	     DATABASE_ROLE
    -------------------- ----------------
    MOUNTED 	     PHYSICAL STANDBY
    
    SQL> alter database open;
    
    Database altered.
    
    SQL> alter pluggable database orclpdb open;
    
    Pluggable database altered.
    
    SQL> show pdbs
    
        CON_ID CON_NAME			  OPEN MODE  RESTRICTED
    ---------- ------------------------------ ---------- ----------
    	 2 PDB$SEED			  READ ONLY  NO
    	 3 ORCLPDB			  READ ONLY  NO
    	 
    SQL> select open_mode,database_role from v$database;
    
    OPEN_MODE	     DATABASE_ROLE
    -------------------- ----------------
    READ ONLY WITH APPLY PHYSICAL STANDBY
    
    SQL> exit
    Disconnected from Oracle Database 19c EE Extreme Perf Release 19.0.0.0.0 - Production
    Version 19.10.0.0.0
    [oracle@dbstby ~]$ 
    ```
If the `OPEN_MODE` is **READ ONLY**, you can run the following command in sqlplus as sysdba, then check the `open_mode` again, you can see the `OPEN_MODE` is **READ ONLY WITH APPLY** now.
    ```
    SQL> alter database recover managed standby database cancel;
    
    Database altered.
    
    SQL> alter database recover managed standby database using current logfile disconnect;
    
    Database altered.
    
    SQL> select open_mode,database_role from v$database;
    
    OPEN_MODE	     DATABASE_ROLE
    -------------------- ----------------
    READ ONLY WITH APPLY PHYSICAL STANDBY
    ```

4. From the standby side, connect as **testuser** to orclpdb. Check if the test table and record has replicated to the standby.

    ```
    [oracle@standby ~]$ sqlplus testuser/testuser@localhost:1521/orclpdb
    
    SQL*Plus: Release 19.0.0.0.0 - Production on Sat Feb 1 07:09:27 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2019, Oracle.  All rights reserved.
    
    Last Successful login time: Sat Feb 01 2020 06:59:56 +00:00
    
    Connected to:
    Oracle Database 19c EE Extreme Perf Release 19.0.0.0.0 - Production
    Version 19.10.0.0.0
    
    SQL> select * from test;
    
    	 A B
    ---------- --------------------
    	 1 line1
    
    SQL> 
    ```

## **STEP 2:** Check lag between the primary and standby

There are several ways to check the lag between the primary and standby.

1. First let's prepare a sample workload in the primary side. Copy the following command:

    ```
    <copy>
    wget https://objectstorage.us-ashburn-1.oraclecloud.com/p/Bq05Vhib-p_vraOu-wFpTEmyydA4d8qekXWXcb6W6M3pL43LVSAS2eFwKpYvAVxQ/n/c4u04/b/data-management-library-files/o/workload.sh
    wget https://objectstorage.us-ashburn-1.oraclecloud.com/p/KNpGKB2VdoBWC5VWOHvD5vHg9P1OO5mqBJUxNonwY9LzaMaZ8Kcu7w3wBq9xgebW/n/c4u04/b/data-management-library-files/o/scn.sql
    </copy>
    ```

   

2. From primary side, run as **oracle** user, download scripts using the command you copied.

    ```
    [oracle@primary ~]$ wget https://objectstorage.us-ashburn-1.oraclecloud.com/p/Bq05Vhib-p_vraOu-wFpTEmyydA4d8qekXWXcb6W6M3pL43LVSAS2eFwKpYvAVxQ/n/c4u04/b/data-management-library-files/o/workload.sh
    --2020-10-31 02:48:08--  https://objectstorage.us-ashburn-1.oraclecloud.com/p/Bq05Vhib-p_vraOu-wFpTEmyydA4d8qekXWXcb6W6M3pL43LVSAS2eFwKpYvAVxQ/n/c4u04/b/data-management-library-files/o/workload.sh
    Resolving objectstorage.us-ashburn-1.oraclecloud.com (objectstorage.us-ashburn-1. oraclecloud.com)... 134.70.31.247, 134.70.27.247, 134.70.35.189
    Connecting to objectstorage.us-ashburn-1.oraclecloud.com (objectstorage.us-ashburn-1. oraclecloud.com)|134.70.31.247|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1442 (1.4K) [text/x-sh]
    Saving to: ‘workload.sh’
    
    100%[==============================================>] 1,442       --.-K/s   in 0s      
    
    2020-10-31 02:48:09 (10.5 MB/s) - ‘workload.sh’ saved [1442/1442]
    
    [oracle@primary ~]$ wget https://objectstorage.us-ashburn-1.oraclecloud.com/p/KNpGKB2VdoBWC5VWOHvD5vHg9P1OO5mqBJUxNonwY9LzaMaZ8Kcu7w3wBq9xgebW/n/c4u04/b/data-management-library-files/o/scn.sql
    --2020-10-31 02:48:29--  https://objectstorage.us-ashburn-1.oraclecloud.com/p/KNpGKB2VdoBWC5VWOHvD5vHg9P1OO5mqBJUxNonwY9LzaMaZ8Kcu7w3wBq9xgebW/n/c4u04/b/data-management-library-files/o/scn.sql
    Resolving objectstorage.us-ashburn-1.oraclecloud.com (objectstorage.us-ashburn-1. oraclecloud.com)... 134.70.35.189, 134.70.31.247, 134.70.27.247
    Connecting to objectstorage.us-ashburn-1.oraclecloud.com (objectstorage.us-ashburn-1. oraclecloud.com)|134.70.35.189|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 108 [application/octet-stream]
    Saving to: ‘scn.sql’
    
    100%[==============================================>] 108         --.-K/s   in 0s      
    
    2020-10-31 02:48:30 (8.08 MB/s) - ‘scn.sql’ saved [108/108]
    
    [oracle@primary ~]$  
    ```

   

3. Change mode of the `workload.sh` file and run the workload. Ignore the error message of drop table. Keep this window open and running for the next few STEP s in this lab.

    ```
    [oracle@primary ~]$ chmod a+x workload.sh 
    [oracle@primary ~]$ . ./workload.sh 
    
      NOTE:
      To break out of this batch
      job, please issue CTL-C 
    
    ...sleeping 5 seconds
    
      drop table sale_orders
                 *
    ERROR at line 1:
    ORA-00942: table or view does not exist
    
    
    
    Table created.
    
    
    10 rows created.
    
    
    Commit complete.
    
    
      COUNT(*)
    ----------
    	10
    
    
    CURRENT_SCN TIME
    ----------- ---------------
        2814533 20200905-092831
    
    
    10 rows created.
    
    
    Commit complete.
    
    
      COUNT(*)
    ----------
    	20
    
    
    CURRENT_SCN TIME
    ----------- ---------------
        2814548 20200905-092833
        
    ```

   

4. From the standby side, connect as **testuser** to orclpdb, count the records in the sample table several times. Compare the record number with the primary side.

    ```
    [oracle@standby ~]$ sqlplus testuser/testuser@standby:1521/orclpdb
    
    SQL*Plus: Release 19.0.0.0.0 - Production on Sat Sep 5 09:41:29 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2020, Oracle.  All rights reserved.
    
    Last Successful login time: Sat Sep 05 2020 02:09:45 +00:00
    
    Connected to:
    Oracle Database 19c EE Extreme Perf Release 19.0.0.0.0 - Production
    Version 19.10.0.0.0
    
    SQL> select count(*) from sale_orders;
    
      COUNT(*)
    ----------
    	390
    
    SQL> 
    ```

    

5. From standby site, connect as sysdba. Check the Oracle System Change Number (SCN). Compare it with the primary side.

    ```
    SQL> connect / as sysdba
    Connected.
    SQL> SELECT current_scn FROM v$database;
    
    CURRENT_SCN
    -----------
        2784330
    ```

   

6. From standby site, query the `v$dataguard_stats` view to check the lag.

    ```
    SQL> set linesize 120;
    SQL> column name format a25;
    SQL> column value format a20;
    SQL> column time_computed format a20;
    SQL> column datum_time format a20;
    SQL> select name, value, time_computed, datum_time from v$dataguard_stats;
    
    NAME			                VALUE 	             TIME_COMPUTED	      DATUM_TIME
    ------------------------- -------------------- -------------------- --------------------
    transport lag		          +00 00:00:00	       09/05/2020 07:17:33  09/05/2020 07:17:30
    apply lag		              +00 00:00:00	       09/05/2020 07:17:33  09/05/2020 07:17:30
    apply finish time	        +00 00:00:00.000     09/05/2020 07:17:33
    estimated startup time	  9		                 09/05/2020 07:17:33
    
    SQL> 
    ```

   

7. Check lag using Data Guard Broker.

    ```
    [oracle@standby ~]$ dgmgrl sys/Ora_DB4U@orcl
    DGMGRL for Linux: Release 19.0.0.0.0 - Production on Sat Sep 5 07:25:52 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2019, Oracle and/or its affiliates.  All rights reserved.
    
    Welcome to DGMGRL, type "help" for information.
    Connected to "ORCL"
    Connected as SYSDBA.
    DGMGRL> show database ORCLSTBY
    
    Database - orclstby
    
      Role:               PHYSICAL STANDBY
      Intended State:     APPLY-ON
      Transport Lag:      0 seconds (computed 3 seconds ago)
      Apply Lag:          0 seconds (computed 3 seconds ago)
      Average Apply Rate: 6.00 KByte/s
      Real Time Query:    ON
      Instance(s):
        ORCL
    
    Database Status:
    SUCCESS
    
    DGMGRL> 
    ```
   
8. From the on-premise side, press `Ctrl-C` to terminate the running workload.




## **STEP 3:** Switchover to the standby 

At any time, you can manually execute a Data Guard switchover (planned event) or failover (unplanned event). Customers may also choose to automate Data Guard failover by configuring Fast-Start failover. Switchover and failover reverse the roles of the databases in a Data Guard configuration – the standby database becomes primary and the original primary becomes the standby database. Refer to Oracle MAA Best Practices for additional information on Data Guard role transitions. 

Switchovers are always a planned event that guarantees no data is lost. To execute a switchover, perform the following in Data Guard Broker 

1. Connect DGMGRL from the primary side, validate the standby database to see if Ready For Switchover is Yes. 

    ```
    [oracle@primary ~]$ dgmgrl sys/Ora_DB4U@orcl
    DGMGRL for Linux: Release 19.0.0.0.0 - Production on Sat Feb 1 07:21:55 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2019, Oracle and/or its affiliates.  All rights reserved.
    
    Welcome to DGMGRL, type "help" for information.
    Connected to "ORCL"
    Connected as SYSDBA.
    DGMGRL> validate database ORCLSTBY
    
      Database Role:     Physical standby database
      Primary Database:  orcl
    
      Ready for Switchover:  Yes
      Ready for Failover:    Yes (Primary Running)
    
      Flashback Database Status:
        orcl    :  On
        orclstby:  Off
    
      Managed by Clusterware:
        orcl    :  NO             
        orclstby:  NO             
        Validating static connect identifier for the primary database orcl...
        The static connect identifier allows for a connection to database "orcl".
    
    DGMGRL> 
    ```

2. Switch over to the standby database.

    ```
    DGMGRL> switchover to orclstby
    Performing switchover NOW, please wait...
    Operation requires a connection to database "orclstby"
    Connecting ...
    Connected to "ORCLSTBY"
    Connected as SYSDBA.
    New primary database "orclstby" is opening...
    Operation requires start up of instance "ORCL" on database "orcl"
    Starting instance "ORCL"...
    Connected to an idle instance.
    ORACLE instance started.
    Connected to "ORCL"
    Database mounted.
    Database opened.
    Connected to "ORCL"
    Switchover succeeded, new primary is "orclstby"
    DGMGRL> show configuration
    
    Configuration - adgconfig
    
      Protection Mode: MaxPerformance
      Members:
      orclstby - Primary database
        orcl     - Physical standby database 
    
    Fast-Start Failover:  Disabled
    
    Configuration Status:
    SUCCESS   (status updated 65 seconds ago)
    
    DGMGRL> exit
    ```

3. Check from the original primary side. You can see the previous primary side becomes the new standby side.

    ```
    [oracle@primary ~]$ sqlplus / as sysdba
    
    SQL*Plus: Release 19.0.0.0.0 - Production on Sat Feb 1 10:16:54 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2019, Oracle.  All rights reserved.
    
    
    Connected to:
    Oracle Database 19c Enterprise Edition Release 19.0.0.0.0 - Production
    Version 19.10.0.0.0
    
    SQL> show pdbs
    
        CON_ID CON_NAME			  OPEN MODE  RESTRICTED
    ---------- ------------------------------ ---------- ----------
    	 2 PDB$SEED			  READ ONLY  NO
    	 3 ORCLPDB			  READ ONLY  NO
    SQL> select open_mode,database_role from v$database;
    
    OPEN_MODE	     DATABASE_ROLE
    -------------------- ----------------
    READ ONLY WITH APPLY PHYSICAL STANDBY
    
    SQL> 
    ```

4. Check from the original standby side. You can see it's becomes the new primary side.

    ```
    [oracle@standby ~]$ sqlplus / as sysdba
    
    SQL*Plus: Release 19.0.0.0.0 - Production on Sat Feb 1 10:20:06 2020
    Version 19.10.0.0.0
    
    Copyright (c) 1982, 2019, Oracle.  All rights reserved.
    
    
    Connected to:
    Oracle Database 19c EE Extreme Perf Release 19.0.0.0.0 - Production
    Version 19.10.0.0.0
    
    SQL> show pdbs
    
        CON_ID CON_NAME			  OPEN MODE  RESTRICTED
    ---------- ------------------------------ ---------- ----------
    	 2 PDB$SEED			  READ ONLY  NO
    	 3 ORCLPDB			  READ WRITE NO
    SQL> select open_mode,database_role from v$database;
    
    OPEN_MODE	     DATABASE_ROLE
    -------------------- ----------------
    READ WRITE	     PRIMARY
    
    SQL> 
    ```

You may proceed to the next lab.

## Acknowledgements
* **Author** - Minqiao Wang, Oct 2020 
* **Last Updated By/Date** - Minqiao Wang, Aug 2021
* **Workshop Expiry Date** - Nov 30, 2021

