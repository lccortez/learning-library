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

### Access the Console
    A. Go to Integration Insight    
        1. Click Insight
        2. Click Console
        3. You will see your Identifier on the right
            
        


Now your turn to try!

## Excercise 2
 You will map your Milestones and Indentifier to an existing integration. The Integration you will use is called Order Processing Lab. You will move your draft model into a configured model state and then active model state. 

### Task 1: Test Mapping
Open the "Order Processing Lab" in Test. Either use the file named exercise-first-instance.json or copy the following informaiton:
 {
"orderId": "1000",
"product": "Laptop",
"quantity": 5,
"unitPrice": 1500,
"discount": 0,
"country": "US"
}

You will need to open the Console page to verify.     
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