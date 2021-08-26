# Introduction to Oracle Insight Navigation

## About this Workshop

The workshop will cover how to navigate to Insight and the command fields you will experience while working with a model.

Estimated Workshop Time: 5 Minutes

### Oracle Insight Navigation
The Integration Insight feature (commonly referred to as Insight) is located in home page of Oracle Integration.


### Workshop Objectives

In this workshop, you will:
* Navigate Insight
* Understand Terminology

### Navigate
#### Main Page
Click the hamburger at the top left hand site of the home screen. Click on the Insight and you will see Consoles and Models.
#### Models
Click on Models to commence creating or modify models. In Models, starting left to right, you will see the search tool, filter tool, refresh, list horizontal, or list by block.
Above that you will see the Import button or Create button.
#### Consoles
Click Consoles to view consoles. Consoles are  created once you activate a model. You will see the Name of the console, its Status and the Status Last Updated date/timestamp.
#### Dashboards
Open Dashboards via clicking on a Console name to open its related Dashboard. In the Dashboards, starting left to right, you will see the search tool, filter tool, All dropdown (where you can locate preconfigured or create a custom Dashboard), Rearrange Dashboard, Embed Dashboard, Search Order Number, View All, Purge Console Data, and Refresh. Top right side, you will see the Console Manifest, Import, Create and the three dots is for the Details information. Lastly, you will see blocks with the dashboards displays as built within the model.   
### Lab Agenda
* Access Insight

Lab 1.

Using the hamburger ![hamburger](images/hamburgericon.png), located on top left hand side of the screen, this will open the Oracle Integration dropdown menu.

Click **Insight** ![insighticon](images/insighticon.png) to access the Oracle Integration Insight commands of Consoles or Models.


### Terminology
* Model: a business process, which passes through several states during its lifecycle. There are 8 states, which are Draft, Configured, Activation in Progress, Timeout, Activated, Deactivated, Failed,  and Unknown.
* Draft: A newly created model is in this state until the model is activated. In this state, changes can be made to the model and no metrics are collected. A draft model can be exported to later be imported into another Insight instance.
* Configured: A model moves into this state when its milestones, indicators, and unique instance identifier have been defined and milestones have been mapped to a business process. A model in this state is ready to activate.
* Activation In Progress: A model is in this state when activation has been initiated.
* Timeout: A model falls into this state when it times out after attempting to activate for five minutes.
* Activated: When a model is in this state, metrics are being collected, and changes are not possible. An activated model can be exported to later be imported into another Insight instance.
* Deactivated: A model moves into this state when you specifically deactivate it.
* Failed: A model falls into this state when it encounters issues during activation.
* Unknown: A model may move into this state when the state of the model cannot be determined as activated or deactivated. You can perform all lifecycle actions on a model in an unknown state.
* Milestones: Key components of an Insight model. They define points in a business process that represent progress and map to at least one activity in the business process implementation. There are 5 types of Milestones, which are Initial, Standard, Error, Terminal and Terminal/Error. Every milestone requires an initial and a terminal
* Instance: a business transaction. Every instance of the model must pass through at least an Initial and a Terminal milestone
* Unique Instance Identifier:  a business transaction Identifier
* Indictors: represent metrics that are unique to a business process, and are extracted when milestones are passed in a business process implementation. There are 2 types of indicators, measures and dimensions, that may be used.
* Measures: numerical values that can be used by mathematical functions. They identify values that allow the state of a business process to be quantified. For example, a business process might define measures for Total Order Value or Item Count. A single measure can change over the lifecycle of a model. For example, the Discount amount may change during a business process because the Quote Modified milestone can be passed more than once.
* Dimensions: provide a type of grouping and categorization of business transactions (instances), allowing for slicing and dicing of aggregate integration measures. For example, a typical order in a business process might define dimensions for Geographic Region, Sales Channel, or Product Category.
* Alerts: define conditions for milestones or indicators to notify users when those conditions are met or not.



This concludes this lab named Oracle Insight Navigation. You may now [proceed to the next lab](#next). Create Model

*Note: If you have a **Free Trial** account, when your Free Trial expires your account will be converted to an **Always Free** account. You will not be able to conduct Free Tier workshops unless the Always Free environment is available. **[Click here for the Free Tier FAQ page.](https://www.oracle.com/cloud/free/faq.html)***

*This is the "fold" - below items are collapsed by default*


*At the conclusion of the lab add this statement: Note how you can link to whatever lab follows by using #next as the target*
You may now [proceed to the next lab](#next).

## Want to Learn More

* [https://docs.oracle.com/en/cloud/paas/integration-cloud/index.html](http://docs.oracle.com)
* https://docs.oracle.com/en/cloud/paas/integration-cloud/integration-insight.html](http://docs.oracle.com)

## Acknowledgements
* **Author** - <Lucy Cortez, Product Enablement Manager, OIC>
* **Contributors** -  Nathan Angstadt, Senior Director, Oracle Integration Product Management
* **Last Updated By/Date** - <Lucy Cortez, July 2021>
