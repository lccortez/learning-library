# Learning Objective 3: Process Integration Test

## Introduction
The Lab will cover how to test the process integration mapped milestones/indentiers and view the test in the Insight Console

Estimated Lab Time: 10 minutes

More info on Insight Models can be found [here](https://docs.oracle.com/en/cloud/paas/integration-cloud/user-int-insight-oci/work-models-integration-insight.html).

## Learning Objectives
In this lab, you will learn how to create the following:
- Test Order Process Lab integration
- Review Console 
- Review Standard Dashboards

Testing your mappings is vital. Ensuring that the mapped item function correctly and provide needed information in the console.  
### Map Testing
    A.  Access Integrations  
        1. Hover over the Status and the Run icon (forward arrow) will appear
        2. Click on the icon and message box will appear, click on the word "Test"
        3. Now you need to configure your request properties.
            a. Under the Request area, click on Tab named "Body" 
            b. Click "File" and choose your saved file 
                OR 
            c. Click text and copy the json file information
        4. Click "Test", located far center right of screen
        5. You will receive a message box and then see the Activity stream 
            a. Activity stream will showcase in Ascending order and will show green if succesful
            b. Activity stream will showcase yellow or red if unsuccesful

### Map an Indentifier
    A. Click your Indentifier, this will expand the view area.   
        1. Under mappings you will click on "Open mapped integration to define extraction criteria" 
        2. This will open the Integrations, that was previously used, for you to map 
        3. You will see your Identifier on the right
            a. Under Milstone you will see Extraction Criteria
                1. Click on Define extraction Criteria
                2. This will open the expression page
                    a. Under Source click on $OrderNumber and drag and drop to the Expression box, located on the right side 
            c. you may click "Validate" to confirm its readiness to use or click "Close" to returne to the integration mapping page.
        4.  Repeat for each Identifier you wish to map.
        5. Click Save, this will return you to the model
        
Once Integration has been mapped to the Milestone and Indentifier , it's time to change the Draft Model into a Configured State <br />

### Configured State

    A. Click "Save" and you will receive a confirmation box stating "Succesfully saved the changes"
    B. Exit and return to your Models listing. You will now see your Status as "Configured"

Activating a Model allows it to be tested or used. Active models showcase status of a green dot that says "Activated". <br />
### Activate Model

    A.  At the Model's list page locate your Model
        1. Hover your mouse over the Last Updated Date and 3 buttons will appear
        2. Click on the center button named "Activate"
        3. Display window will appear click "Activate"
        4. This may take a few minutes to generate or you may click the refresh symbol
        5. Status will now display a green dot and word "Activated"

When a business process implementation spans more than one integration or process, or both, you must assign the model's unique instance identifier to mapped milestones to establish the correlation between the actions in the same instance of the business process and extract the unique instance identifier value when the specified milestone is passed. <br />

Now your turn to try!

## Excercise 2
 You will map your Milestones and Indentifier to an existing integration. The Integration you will use is called Order Processing Lab. You will move your draft model into a configured model state and then active model state. 

### Task 1: Map Milestone
Accessing your draft model, go to Milestones. You will map 2 Milestones and 2 Indentiers.
Let's start with the Milestones. Map your Order Received Milestone "On Exit" event to the "PrepareOrderReceived" activity. Map your Order Completed Milestone "On Exit" event to the "PrepareOrderCompleted" activity. Now onto the Identifiers. Set your Order Number Identifier Extraction Criteria for the Order Received Milestone to $OrderNumber.
Set your Order Number Identifier Extraction Criteria for the Order Completed Milestone to $OrderNumber. Go to Task 2 in order to save your work.
     
### Task 2: Draft to Configured State
You may now click "Save" and ensure you receive the message box ""Succesfully saved the changes" and close your model. You should now see it as Configured. To activate the model, go to Task 3.
    
### Task 3: Configured State to Active State
Access your Insight Models, locate your model and ensure it says Configured. Now Activate your model. You will recieed an Activation Confirmation, click Activate.

Congratulation on completing the Process Mapping. The next excercise will test the mapping and showcase the Console/Dashboards. 

## Solution
>>>>>


## Summary
Great job mapping and activating your Model.<br />

You may now [proceed to the next lab](#next).