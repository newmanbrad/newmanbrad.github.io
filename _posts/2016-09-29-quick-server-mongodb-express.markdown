---
layout: post
title:  "A quick REST API up and running in minutes"
date:   2016-09-29 2:35:05 -0400
categories: REST, NODE, Javascript, API, Mongodb
---

![Brad Newman]({{ site.url }}/assets/mongodb.png){: .center-image }

Often I find myself without bandwidth and in need of interaction with an API for a front-end project I may be working on.
Initially, I thought that I would be able to browse around Github and locate a repo that contained a quick and easy REST API I 
could spin up with node. It is true that I found many potential candidates. However, the projects I found were bloated with extra stuff that
I really did not need or care about. When I am putting a schema together for a backend, the last thing that I am worried about is
testing. On that note, is it really that hard to add testing packages later on in the process? Well, I think that is enough ranting
from me. On to it.

A simple REST API with Mongodb interaction can be found [here](https://github.com/newmanbrad/quick-mongo-rest-server). Instructions on getting up and 
running are located below. Enjoy!

### Installing Mongodb

If you have not already installed Mongo. You can find installs here: 

[Mongodb Site](https://www.mongodb.com/download-center#community)

#### Windows - After Install
If you are running Windows assure that you have the following environment variable:
 ```PATH=%PATH%;C:/Program Files/MongoDB/Server/3.2/bin/```
 
 **Note:** The path may vary depending on the current Mongo version.
 
#### Mac - After Install
You will need to set a Path variable in you .bash_profile in order to start Mongo from the command line.

1. From the command line it is easier to locate your Mongo path for copy paste. Type: ```find / -name 'mongod'```.
2. Look for the path that ends with ```bin/mongod```.
3. Replace the path here with the path you just copied: 
```
echo "PATH=/your/path/here/bin/:$PATH" >> ~/.bash_profile
. ~/.bash_profile
```

### Up and Running

I have created an example schema called users. Feel free to skip to step 3 if you are not looking to add anything else.

### Step 1

Create a mongoose model and schema in the ```server/models``` folder to represent the JSON structure you want to interact with.

Example Usage ```users.js```:

```
import mongoose from 'mongoose';

const userModel = mongoose.model('user', new mongoose.Schema({
  email: { type: String, index: true },
  username: { type: String, required: true },
  firstName: { type: String },
  lastName: { type: String },
  permissions: {
    admin: { type: Boolean }
  }
}));

export default userModel
```

#### Step 2 

Import your model into ```server/server.js``` and onto step 3.
 
 
#### Step 3

Serve the model in the ```server/server.js``` file.

```
restify.serve(router, userModel);
```

#### Step 4

Modify the config file here: ```server/config.js```

```
const config = {
    'database': 'test', // Whatever you would like to name your database.
    'port': 3000,
    'host': 'mongodb://localhost:27017/'
};
```

#### Step 5

Starting Mongodb: 

```
Mac: npm run mongo-mac
Windows: npm run mongo-win
```

Run the server:

In a new terminal window.

```
npm run start-server 
```

### Available API Endpoint

```
 GET http://localhost/api/v1/user/count
 GET http://localhost/api/v1/user
 POST http://localhost/api/v1/user
 DELETE http://localhost/api/v1/user

 GET http://localhost/api/v1/user/:id
 GET http://localhost/api/v1/user/:id/shallow
 PUT http://localhost/api/v1/user/:id
 POST http://localhost/api/v1/user/:id
 PATCH http://localhost/api/v1/user/:id
 DELETE http://localhost/api/v1/user/:id
```


### Interaction

Need help building or interacting with your API? I highly suggest looking at [Postman](https://www.getpostman.com/) 

