# Learning Objective 5: Define an Alert

## Introduction

The Lab will cover how to add an alert to your Model. 

Estimated Lab Time: 5 minutes

## Learning Objectives
In this lab, you will learn how to create the following:
- Add an Alert
- Test the Alert

### How to Add an Alert
    A. On the Models page, click the name or Edit icon icon of the model for which you want to create alerts. 
        1. If the model is not a draft, click Create Draft.
        2. Click <Alerts>
            a. If no alerts exist for the model, the Alerts page looks like this:
            ![noalert](./images/noalert.jpg " ")
            b. If alerts have been defined for the model, the Alerts page looks like this:
            ![existingalert](./images/existingalert.jpg " ")
        3. Click <Add Alert>, then enter an alert name and optional description.
        4. Define the required alert <Condition>:
            a. To define an alert based on whether or not a milestone is reached:
                i. <Based On>: <Select Milestone>.
               ii. <Select Milestone>: Select the milestone for which you want to define an alert.
              iii. Select whether the alert should be issued when the specified milestone is <Passed> or <Not Passed Within> a selected time.
            b. To define an alert based on the value of an indicator (dimension or measure):
                i. <Based On>: <Select Indicator>.
               ii. <Select Indicator>: Select the indicator for which you want to define an alert.
              iii. <Operator> and <Value>: Select the operator and enter a value to define the condition for issuing the alert.
        5. Define the alert <Action>:
            a. Click <Configure> to open the Configure Alert dialog:
            b. Configure the email for the alert notification:
                i. <To>: Enter one or more individual or group email addresses, separated by commas.
               ii. <From>: Select a sender from the dropdown list, which is populated by the configuration on the Notifications page in Oracle Integration. See **[Send Service Failure Alerts, System Status Reports, and Integration Error Reports by Notification Emails] (https://docs.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/integration-cloud/user-int-insight-oci&id=ICSUG-GUID-4A8952AD-00AB-423A-ABE5-94C01ABF4AC3)** in Using Integrations in Oracle Integration.
              iii. <Subject and Body>: Enter text you want to provide for the notification. The body text supports HTML markup tags. Type $ to select and insert the unique instance identifier, indicators, or a link to the Business Transaction Details dashboard.
             * Note: To be successfully extracted, the identifier and indicator values must be mapped to the same milestone for which the alert is configured. See Define a Unique Instance Identifier.
             In the notification email that the recipient receives, the indicator placeholders in subject and body are replaced with the actual values. The link placeholder is replaced with a clickable link to the Business Transaction Details dashboard. For those indicators whose values are not available, their placeholders will be replaced with the text [Not Available].
        6. Click <Done> and <Save>




## Excercise
 
### Task 1: Create An Alert
Open your existing Model and add an alert. Decide if your alert will be based on a Milestone or an Indicator. Define the Alert by configuring your personal email as both the <To> and <From>. Ensure the indentifier and Indicator values are mappend to same milestone that your alert is configured to. 

### Task 2: Test Alert

Run another Test using you model and see if you receive your email.


## Solution



## Summary