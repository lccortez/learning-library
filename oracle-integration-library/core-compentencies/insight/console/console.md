# Learning Objective 7: Custom Console Dashboards

## Introduction
While the Console page is display inforamtion about performance. Preconfigured Dashboards show nominal inforamtion, however, you can create a custom Dashboard to help identify bottlenecks or shortages in the process and track key metrics immediately and in real time.
![Dashboard](./images/feb2021-opp=order-console.jpb " ") <br />

Estimated Lab Time: 15 minutes

More info on Insight Dashboards can be found [here](https://docs.oracle.com/en/cloud/paas/integration-cloud/user-int-insight-oci/work-console-and-dashboards-business-process.html).

## Learning Objectives
In this lab, you will learn how to create the following:
- Indicator Map Testing
- Console Views
- Standard Dashboards

Insight automatically creates and associated Console when a model, with difined business processes, has been activated.

The Consoles page shows the status of all business processes and includes a high-level visualization of the metrics collected over the past day for all activated business processes. 

Conoles can be accessed either fromm the Oracle Integration navigational pane or from the Insight tile on the Oracle Integration home page. Consoles names are the same as the Model name or Business Process that was mapped.

Double-click on a dashboard to open the Business Transaction Details dashboard for that dashboard. The following dashboards support drilling down into the transaction details:
* Passed Milestones: Double-click any milestone bar to show the business transactions (instances) that have passed that milestone.
* Milestones Summary: Double-click any milestone bubble to show the business transactions (instances) associated with the milestone.
* Active Transactions: Double-click any business transaction bar to show the active business transactions. Because a business transaction state may change between the time the dashboard displayed and the time you clicked a bar, you may not see the same business transactions on the Business Transaction Details dashboard.
* Transaction Errors: Double-click any slice on the pie chart to show the business transactions in Error state.
* Avg. Transaction Completion Time: Double-click any bubble on the bubble chart to show the business transactions in Successful or Failed state, depending on the bubble you clicked.