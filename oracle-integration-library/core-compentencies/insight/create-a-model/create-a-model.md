# Learning Objective 1: Create a Model

## Introduction
The Lab will cover how to build a simple model by reading the learning objectives, participating in an excercise and reviewing the solution tab.

Estimated Lab Time: 15 minutes


## Learning Objectives
In this lab, you will learn how to create the following:
- Draft Model
- Initial and Terminal Milestones
- Identifier mapped to one of the Milestones through a data type

The Model has Milestone(s), and an Identifier which is mapped to one, or more, of the milestone(s). The Initial creation of a Model is called a Draft; which is not activated and can be modified, but not visable in the Console.
### Sample Creation of a Model

    A. Open Oracle Insight
        1. Click on <Models>
        2. Click on <Create>
            a. In Name field type "Model Name"
            b. In Description field type "Model Description" 
            c. Click on "Create"
        3. This will open the Draft Model page, at the Milestones Process.

A Milestone is a key component of a Model. Milestone(s) define point(s) in a business process that represent progress. Your Model requires an Initial Milestone and a Terminal Milestone. <br />
### Sample Milestones

    A. Intial Milestone (Rocket symbol) 
        1. Enter the milestone name "Initial Milestone name"
        2. Enter the milestone description "Initial Milestone Description"
    B. Terminal Milestone (Finish Flag Symbol)
        1. Enter the milestone name "Terminal Milestone Name"
        2. Enter the milestone description "Terminal Milestone Description"

Every Model must have a unique instance Identifier defined. This identifier describes a value that is extracted at runtime for every instance (business transaction) of the business process defined by the model. <br />
### Sample Indentifier

    A.  Click tab named <Indentifier>
        1. Enter the inentifier name "Indentier Name"
        2. Click on the Option Enter the Identifier Description. This will open the Milestone mapping area.
            a. From the Milestone dropdown select <It will show your current Milestones available to map>
            b. Select a Data Type of <String>
                i. Note: The selected data type must match the data type of the value that will be extracted at runtime, as defined by the associated identifier extraction criteria that you will specify later. Otherwise, the identifier will show an empty value in Insight dashboards.
            c. Click <Save>
        3. Click <Save> on the upper right corner

When a business process implementation spans more than one integration or process, or both, you must assign the model's unique instance identifier to mapped milestones to establish the correlation between the actions in the same instance of the business process and extract the unique instance identifier value when the specified milestone is passed. <br />

## Excercise
 You will create a Model with 2 Milestones, an Initial and a Terminal, and an identifier. The order process starts with an initial milestone, named Order Received, which provides metrics for an order, such as number of items, type ordered, shipping address, and shipping type. You will include a terminal milestone name Order Completed. The Identifier will be mapped to the milestone named Order Recieved via a String value. Your model will be kept in Draft form thru several iterations. 

### Task 1: Create Model
Open Insight and create your Draft Model. Name the Draft Model "Order Management" and provide the description of "My First Model". You will need to click Create to finish. When your completed it will open the Milestone Process for you; continue to Task 2 to add your Milestones
     
### Task 2: Create A Milestone
As taught, each Model needs an Initial and Terminal Milestone. For your Initial Milestone (Rocket Symbol), enter milestone name "Order Recieved" and for the Description enter "My first Orders received". For you Terminal Milestone (Finish Line Flag Symbol), Enter milestone name "Order Completed" and enter milestone description "Orders Completed via System"; continue to Task 3 to add your Indentifer.
    
### Task 3: Create an Identfier


## Solution



## Summary
Great job adding creating you Draft Model.<br />

You may now [proceed to the next lab](#next).
