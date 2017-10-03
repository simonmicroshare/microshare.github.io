---
layout: docs
title: Tutorial
description: Getting Set-up in Microshare
group: getting-started
toc: true
---


This tutorial will provide an indepth review of Microshare. In this tutorial we will:

1. Create an account  
2. Get an access token  
3. Post data to Microshare  
4. Make a rule to govern this data  
5. Create a robot to moniter this data  
6. Make a dashboard to view this data  

This process will require Postman. It is avaliable to download and install [here](https://www.getpostman.com/)

## Create an Account

1. Navigate to the [Microshare platform](https://dapp.microshare.io)
2. Click on the "Sign up" link
2. Input your email address, first name, and last name
3. A link will be sent to your email, open this link 
4. Create your password
5. Login to the platform with your newly created account!
    * Note: You do not need an organization code to sign in


## Get an Access Token

You will need an access token to push data into the Microshare platform. Follow the steps listed below to get an access token.

Note: you will need an account to get an access token


*  Navigate to the [Microshare platform](https://dapp.microshare.io) and sign in using your credentials
*  Click the "Manage" button in the top toolbar

[insert screen shot of this page]

*  Click the "Keys" button in the left toolbar

[insert screen shot of this page]

* Click on the "Create New App" button at the top right of the screen
* Type the app name and any appropriate notes relating to the app, then click "Create App"
* This will create an app alongside an API Key to auth into our platform
* Click on the API Key to copy it 
* Open Postman
* Make a Post call to [insert where they make postcall][../file]
    * See below for an example of the parameters for the Post Call:


{% highlight JSON%}
{
    "key": "grant_type",
    "value": "password",
    "equals": true,
    "description": ""
},
{
    "key": "client_id",
    "value": "12345678-ABCD-9123-EFGH-456789IJKLMN",
    "equals": true,
    "description": ""
},
{
    "key": "scope",
    "value": "ALL:ALL",
    "equals": true,
    "description": ""
},
{
    "key": "username",
    "value": "example@microhare.io",
    "equals": true,
    "description": ""
},
{
    "key": "password",
    "value": "samplePassword",
    "equals": true,
    "description": ""
},
{% endhighlight %}

* The parameters of the Post call explained:
    * The key "grant_type" should have a value of "password"
    * The key "client_id" should have the API Key as it's value
    * The key "scope" should have a value of "ALL:ALL"
    * The key "username" should have your email as it's value
    * The key "password" should have your accounts password as it's value

* This will return a JSON with an access token. The access token will be a series of letters and numbers that is associated with the "access_token" Key. You can post data to Microshare with this access token
    

## Post Data to Microshare

Make a post call using the same parameters as before, but with two notable additions. 

1. Include the data you wish to upload into the body of the call
2. Include a header with a key of "recType" 
    * This key can have any value you want to attribute to your data
    * This will create a space for the data and attribute the above value as the recType's name  
        * It is recommended that your first recType follow a simple naming convention I.E. "yourFirstName.yourLastName"

See below for a sample Post call

[insert sample post call to upload data]

## Make a Rule 

A rule governs the data you have uploaded in a specific recType. You can adjust who can see the data and what they can do with it. In this section we will allow a user of your choosing to read and write to the data you have posted to microshare.

1. Navigate to [our platform](../file)(https://dapp.microshare.io)
2. Click the "Manage" button in the top toolbar
3. Click the "Rules" button in the left toolbar
4. Click the the "Create" button
5. You will be directed to the screen depicted below

[insert screenshot]

* Input the Rule name in the top most text field
* Type a description of the Rule in the text field labeled "Description"
* Input the recType your Rule will govern in the text field labeled "Record Type"
    * Note: the Rule can only govern an exisiting recType
* Determine what actions will be avaible to others in the "Operations" section
    * For this tutorial we will make a Rule allowing another user to "Read" and "Write"
* Determine who can see your data in the section labeled "Requestor". There are five sub-sections within the Requestor section:
    * User
    * Organization
    * APiKey/Appid
    * Role
    * Location
* All of these can be used to create a nuanced distribution of your data. For this tutorial we will cover the "user" dropdown. There are three options in this dropdown: 
    * "All(*)" will allow all Microshare users to access the data
    * "Exact Match to Owner (=)" will allow access to only the owner of the data
    * "Specific Value" will allow access to the email address that is input as this section's value
        * Enter the email of the user whom will be allowed to access the data
        * An example of a valid input would be "example@microshare.io"
        * Note: this new user's email must associated with an account on our platform in order to access the data

[insert screen shot of the "requestor" table with it filled in with Specific Value selected and example@microshare.io as it's value]

* You can simulate the Rules effect on sharing within the section labeled "Rule Simulation" - but this isn't a nessary step to create a Rule
* Once all nessary fields have been filled out click the "Create" button at the top of the page 

You have now made a Rule to govern access to your data!     

## Create a Robot 

1. Navigate to [our platform][../file](https://dapp.microshare.io)
2. Click the "Manage" button in the top toolbar
3. Click the "Robots" button in the left toolbar
4. Click the "Create" button 
5. The following page will open: 

[insert screen shot of Robot page]

* Input the Robot name in the top most text field
* Type a description of the Robot in the text field labeled "Description"
* Set the Robot to active by checking off the box labled "Active"
* Input which recType the robot should monitor in the "recType" section
    * The Robot should monitor the same recType which your data was previously posted to
* Determine what the robot will be allowed to do with the data within the section labeled "Permission Scopes"
    * Please leave this section as is for this tutorial
* Use Javascript within the "Script" section to control the robot
    * Let's drop in a webhook to make the robot send an email when the recType is updated. Copy and paste the code depicted below into the "Script" section of the robot 

  Note: You will need to change the variables X, Y, and Z to match the proper values. (This section needs to be filled out more)

[insert sample code with proper webhook for gmail]

Your Robot script should look like this:

[insert picture of robot script]

You should now receive an email whenever the recType is accessed! Test it out by uploading data to your recType!




## Make a Dashboard 


[Coming soon!] 
