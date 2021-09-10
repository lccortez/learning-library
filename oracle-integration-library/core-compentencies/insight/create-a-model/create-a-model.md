# Learning Objective 1: Create a Model

## Introduction

The Lab will cover how to build a simple model by reading the learning objectives, participating in an excercise and reviewing the solution tab.

Estimated Lab Time: 15 minutes

## About Insight Models
The Model has Milestone(s), and an Identifier which is mapped to one, or more, of the milestone(s). The Initial creation of a Model is called a Draft; which is not activated and can be modified, but not visable in the Console. <br />

A Milestone is a key component of a Model. Milestone(s) define point(s) in a business process that represent progress. Your Model requires an Initial Milestone and a Terminal Milestone. <br />

Every Model must have a unique instance Identifier defined. This identifier describes a value that is extracted at runtime for every instance (business transaction) of the business process defined by the model. <br />

When a business process implementation spans more than one integration or process, or both, you must assign the model's unique instance identifier to mapped milestones to establish the correlation between the actions in the same instance of the business process and extract the unique instance identifier value when the specified milestone is passed. <br />

## Learning Objectives
In this lab, you will learn how to create the following:
- Draft Model
- Initial and Terminal Milestones
- Identifier mapped to one of the Milestones through a data type


## Excercise
 You will create a Model named Order Management with 2 Milestone and an identifier. The order process starts with an initial milestone, named Order Received, which provides metrics for an order, such as number of items, type ordered, shipping address, and shipping type. You will include a terminal milestone name Order Completed. The Identifier will be mapped to the milestone named Order Recieved via a String value. Your model will be kept in Draft form thru several iterations. 

### Task 1: Create Model
    A. Open Oracle Insight
        1. Click on <Models>
        2. Click on <Create>
            a. In Name field type "Order Management"
            b. In Description field type "My first model"
            c. Click on "Create"
        3. This will open the Draft Model page, at the Milestones Process.
 
### Task 2: Create A Milestone
    A. Intial Milestone (Rocket symbol) 
        1. Enter the milestone name "Order Received"
        2. Enter the milestone description "my orders received"
    B. Terminal Milestone (Finish Flag Symbol)
        1. Enter the milestone name "Order Complete"
        2. Enter the milestone description "Orders Completed via system"

### Task 3: Create an Identfier
    A. Click tab named <Indentifier>
        1. Enter the inentifier name "Order ID"
        2. Click on the Option Enter the Identifier Description. This will opne the Milestone mapping area.
            a. From the Milestone dropdown select <Order Recieved>
            b. Select a Data Type of <String>
                i. Note: The selected data type must match the data type of the value that will be extracted at runtime, as defined by the associated identifier extraction criteria that you will specify later. Otherwise, the identifier will show an empty value in Insight dashboards.
            c. Click <Save>
        3. Click <Save> on the upper right corner


## Solution



## Summary
Great job adding your Indicator.<br />

On the next Lab you will modify your Draft Model. <br />

You may now [proceed to the next lab](#next).
