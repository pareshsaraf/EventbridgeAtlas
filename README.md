# EventbridgeAtlas

It demonstrates how Realm Webhooks can be invoked to perform CRUD operations on collections residing in MongoDB Atlas from Eventbridge API Endpoints option. 

## Architectural overview
![Architecture](/images/Architecture.png)


## Prerequisites & setup
- clone this repo!
- sign a trial MongoDB atlas account https://www.mongodb.com/cloud/atlas/register

## Create cluster on MongoDB Atlas
* Follow the steps [here](https://docs.atlas.mongodb.com/tutorial/create-new-cluster)  to create a new database cluster
* Configure database user, IP Whitelist and copy the connection string. Follow the steps [here](https://docs.atlas.mongodb.com/driver-connection)

## Create Realm webhook
Before we can write the code for our WebHook, we first need to configure it. The "Configure Service WebHooks guide in the Realm documentation goes into more detail, but you will need to configure the following options:

*Authentication type must be set to system
*The HTTP method is POST
*Keep rest of the parameters deafult.
![ConfigureWebhook](/images/RealmWebhook.png)

## Create Realm Function
For our WebHook we need to write a function which:

* Receives a POST request from Eventbridge
* Parses the JSON body from the request
* Iterates over the array
* Writes the object to MongoDB Atlas as a new document
* Returns the correct status code and JSON body to eventbridge in the response

![CreateFunction](/images/RealmFunction.png)




