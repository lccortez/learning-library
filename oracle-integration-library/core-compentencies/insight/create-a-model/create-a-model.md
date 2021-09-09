# Learning Objective 1

## About this Lab

The Lab will cover how to build a simple usable Model with milestones and an Identifier. 

 Estimated labs Time: 15 minutes

## Learning Objective
A Model is the 
A Milestone is a key component of an Insight Model. Milestone(s) define point(s) in a business process that represent progress. Your Model requires An Initial Milestone and a Terminal Milestone. 
Every Insight model must have a unique instance identifier defined. This identifier describes a value that is extracted at runtime for every instance (business transaction) of the business process defined by the model. When a business process implementation spans more than one integration or process, or both, you must assign the model's unique instance identifier to mapped milestones to establish the correlation between the actions in the same instance of the business process and extract the unique instance identifier value when the specified milestone is passed.
## Excercise 1
A model that is not activated is known as a Draft Model. In draft mode, you may modify the model.
### Create Model
    A. Open Oracle Insight
        1. Click on <Models>
        2. Click on <Create>
            a. In Name field type "Order Management"
            b. In Description field type "My first model"
            c. Click on "Create"
        3. This will open the Draft Model page, at the Milestones Process.
A Milestone is a key component of an Insight Model. Milestone(s) define point(s) in a business process that represent progress. Your Model requires An Initial Milestone and a Terminal Milestone. 
### Create A Milestone
    A. Intial Milestone (Rocket symbol) 
        1. Enter the milestone name "Order Received"
        2. Enter the milestone description "my orders received"
    B. Terminal Milestone (Finish Flag Symbol)
        1. Enter the milestone name "Order Complete"
        2. Enter the milestone description "Orders Completed via system"
Every Insight model must have a unique instance identifier defined. This identifier describes a value that is extracted at runtime for every instance (business transaction) of the business process defined by the model. When a business process implementation spans more than one integration or process, or both, you must assign the model's unique instance identifier to mapped milestones to establish the correlation between the actions in the same instance of the business process and extract the unique instance identifier value when the specified milestone is passed.
### Create an Identfier
    A. Click tab named <Indentier>
        1. Enter the indentifer name "Order ID"
        2. Click on the Option Enter the Indefier Description. This will opne the Milestone mapping area.
            a. From the Milestone dropdown select <Order Recieved>
            b. Do not select a Data Type
            b. Click <Save>
        3.  You will notice Message(s) will have a number one in a red circle. This is the system advising you of a missing part to your Identifier. Here is how to clear the error.
            a. Click on the number
            b. A drop down will have the Select a Data Type
            c. Click on "Order ID"
            d  Under Data Type, click the dropdown menu and select "String"
        4. Click save on the upper right corner

At this point you have completed your Draft Model with required Milestone and Indentifier. Your Draft Model is not visiable in the Console.





On the next Lab you will modify the existing Draft Model.
You may now [proceed to the next lab](#next).
            


