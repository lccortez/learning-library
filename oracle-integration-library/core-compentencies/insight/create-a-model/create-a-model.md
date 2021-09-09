# Learning Objective 1

## About this Lab

The Lab will cover how to build a simple model by reading the learning objectives, participating in an excercise and reviewing the solution tab.

 Estimated labs Time: 15 minutes

## Learning Objectives
A Model is a web-besed interface which allow users to collect and monitor metrics for the business processes. 
The Model has Milestone(s), and an Indentifier which is mapped to one, or more, of the milestone(s). The Initial creation of a Model is called a Draft; which is not activated and can be modified, but not visable in the Console. 
A Milestone is a key component of a Model. Milestone(s) define point(s) in a business process that represent progress. Your Model requires an Initial Milestone and a Terminal Milestone. 
Every Model must have a unique instance Identifier defined. This identifier describes a value that is extracted at runtime for every instance (business transaction) of the business process defined by the model. 
When a business process implementation spans more than one integration or process, or both, you must assign the model's unique instance identifier to mapped milestones to establish the correlation between the actions in the same instance of the business process and extract the unique instance identifier value when the specified milestone is passed.
## Excercise 1
This initial excercise will have you create your draft model, initial and terminal milestones, and an identifier mapped to one of the milestones thru a data type.

### Create Model
    A. Open Oracle Insight
        1. Click on <Models>
        2. Click on <Create>
            a. In Name field type "Order Management"
            b. In Description field type "My first model"
            c. Click on "Create"
        3. This will open the Draft Model page, at the Milestones Process.
 
### Create A Milestone
    A. Intial Milestone (Rocket symbol) 
        1. Enter the milestone name "Order Received"
        2. Enter the milestone description "my orders received"
    B. Terminal Milestone (Finish Flag Symbol)
        1. Enter the milestone name "Order Complete"
        2. Enter the milestone description "Orders Completed via system"

### Create an Identfier
    A. Click tab named <Indentier>
        1. Enter the indentifer name "Order ID"
        2. Click on the Option Enter the Indefier Description. This will opne the Milestone mapping area.
            a. From the Milestone dropdown select <Order Recieved>
            b. Select a Data Type of <String>
                i.Note:The selected data type must match the data type of the value that will be extracted at runtime, as defined by the associated identifier extraction criteria that you will specify later. Otherwise, the identifier will show an empty value in Insight dashboards.
            c. Click <Save>
        3. Click <Save> on the upper right corner


## Solution



At this point you have completed your Draft Model with required Milestones (Initial and Terminal) and mapped Indentifier. 

On the next Lab you will modify the existing Draft Model.
You may now [proceed to the next lab](#next).
            


