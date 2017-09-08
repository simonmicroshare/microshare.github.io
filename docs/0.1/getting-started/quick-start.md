---
layout: docs
title: Quick Start
description: Quickly get started with Microshare
group: getting-started
redirect_from: "/getting-started/"
toc: true
---

## Management Console
The management console is available [here](https://app.microshare.io).
It is a great tool to share and manipulate your data.

In this _Getting Started_ section we will go through each of the different things you can create on that console. For more detailed information you can access the detailed documentation via the menu on the left.

## Hackathon Recipe

Follow those steps after your first login to build your first Application. 

1. Create an App key for your new project  
Used when creating new elements, to make sure they are yours.
2. Create your first Robot, that will be ready to process your data  
Really you just need to specify the recType properly.
Use the App key to confirm the creation.
3. Push an example record in your shares  
Use the [auth](../../../assets/html/api-ms.html#folder-authentication) to get an APIKEY from your App key and POST [Share APIs](../../../assets/html/api-ms.html#folder-shares).
4. Edit that Robot so test your data processing  
Build your data transformation script, and see live if it works.
You are saving the transformed data under another record type.
5. but just before? Create a fact called by the App?  
5. Create a Form, the front-end for your App, displaying your modified data  
It gets the data from your record
6. Create an App that uses the Form  
7. Run it  
8. To go further, extend your pipeline workflow with Facts and Robots  

## Uploading Data
Our `/share` API allows you to upload your data to our data lake.
Example of a POST /share call to upload one piece of data:
{% highlight http %}
POST /share/:recType HTTP/1.1
Host: api.microshare.io
Content-Type: application/json
Authorization: Bearer {{token}}
{
  "hello": "world"
}
{% endhighlight %}

To each piece of data is associated a `recType` field, which is a record type. `recType` are for example `io.microshare.sensortype.temperature`, and are usually associated with an organization.

A full documentation of the API is available [here](https://microshare.github.io/docs/0.1/advanced/api-reference/)

## Sharing Data
Once you have some data in the data lake, you may want to share it with specific users or members of an organization.

Creating **Rules** is what you need. When creating a rule, from the management console, you specify to which `recType` the rule will be associated with, and a set of operations to which the rule will apply.
These operations include:
- Read
- Query
- Write
- Delete
- Execute
- Policy


## Robots
