# Learning Objective 2

## About this Lab

The Lab will cover how to add and map indicators to the existing draft model.

 Estimated Lab Time: 15 minutes

## Learning Objectives

Indicators represent metrics that are unique to a business process, and are extracted when milestones are passed in a business process implementation. 

An indicator can be mapped to one or more milestones. Mapping an indicator to multiple milestones allows the value of the indicator to change during the execution of a business process if necessary. 

There are two types of indicators, Measures and Dimensions, that can be used. 
Measures are numerical values that can be used by mathematical functions. They identify values that allow the state of a business process to be quantified. For example, a business process might define measures for Total Order Value or Item Count. A single measure can change over the lifecycle of a model. 

In the prior excercise we created a draft model for a business process that tracks an order. However, what occurs if the value of an indicator changes if discounts are applied? In our draft model When the "Order Received" milestone is passed, the value extracted for an associated "Price" indicator may be $100. As the order progresses, a discount may be applied. The model can be modified to account for this or any other changes in the order process thru adding and mapping Indicators.

In excersice 2, you will add a new milestone named "Discount Applied". When "Discount Applied"  milestone is passed, the value extracted for the "Price" indicator may be reduced to $80.
In this excersice we will map a Measures Indicator to the Discount Applied Milestone to capture the business process. 

When a business process implementation spans more than one integration or process, or both, you must assign the model's unique instance identifier to mapped milestones to establish the correlation between the actions in the same instance of the business process and extract the unique instance identifier value when the specified milestone is passed.

## Excercise 2










## Solution 
