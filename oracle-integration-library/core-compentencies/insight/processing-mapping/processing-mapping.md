# Learning Objective 2: Process Integration

## Introduction
The Lab will cover how to map an integrations to a Milesone

Estimated Lab Time: 10 minutes

More info on Insight Models can be found [here](https://docs.oracle.com/en/cloud/paas/integration-cloud/user-int-insight-oci/work-models-integration-insight.html).

## Learning Objectives
In this lab, you will learn how to create the following:
- Map an Intergration to a Milestone
- Modify your Draft into a Configured state
- Acivate your Insight Model

Mapping milestones involves identifying execution points that best represent when a milestone has been passed. 
As part of the mapping process, you must also define extraction criteria for the unique instance identifier. Extraction criteria define the rules to extract information from runtime messages, and is expressed using XPath expressions. Before you can activate a model, the extraction criteria must be defined. 
### Map a Milestone
    A. Click your Milestone name, this will expand the view area.   
        1. Under mappings you will click on "Map Milestones" 
        2. This will open the Integrations, either search or scroll to find your integration
        3. At the far right (actions), and click on Insight Designer
            a. You will see your Milestones on the right
            b. Drag and drop the related criteria from the left to your Milestone
                1. Select from dropdown "On Entry" or "On Exit"
            c. Repeat for each Milestone you wish to map.
### Map a Indentifier
    A. Click your Indentifier, this will expand the view area.   
        1. Under mappings you will click on "Open mapped integration to define extraction criteria" 
        2. This will open the Integrations, that was previously used, for you to map 
        3. You will see your Identifier on the right
            a. Under Milstone you will see Extraction Criteria
                1. Click on Define extraction Criteria
                2. This will open the expression page
                    a. Under Source click on $OrderNumber and drag and drop to the Expression box, located on the right side 
            c. Repeat for each Identifier you wish to map.
Once Integration has been mapped to the Milestone and Indentifier , it's time to change the Draft Model into a Configured State <br />
### Configured State

    A. 
    B. 

Activating a Model allows it to be tested or used. Active models showcase status of a green dot that says "Activated". <br />
### Activate Model

    A.  C
        1. 
        2. 
        3. Click <Save> on the upper right corner

When a business process implementation spans more than one integration or process, or both, you must assign the model's unique instance identifier to mapped milestones to establish the correlation between the actions in the same instance of the business process and extract the unique instance identifier value when the specified milestone is passed. <br />

Now your turn to try!

## Excercise 2
 You will map several Milestones to an existing integration, you will move your draft into a configured state and then active state. 

### Task 1: Map Milestone


     
### Task 2: Draft to Configured State

    
### Task 3: Configured State to Active State


## Solution



## Summary
Great job creating your Draft Model.<br />

You may now [proceed to the next lab](#next).
