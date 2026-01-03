# ***Backend***
The following documentation is mostly based on the [The ULTIMATE MERN Stack Complete Guide (MongoDB, Express, React, Node.js)](https://www.youtube.com/watch?v=4nKWREmCvsE). Please view for any further questions, and/or references.

## **_Table of Contents_**
- [Set Up](#set-up)
  - [Server](#server)
  - [MongoDB](#mongodb)
  - [Server Pt2](#server-pt2)

## ***Set Up***
### **Server**
  1. Verify/Install node.js and npm(node package manager)
     ```bash
       node -v                      #check for node installation
       npm -v                       #check for npm installation

       #Use ONLY if not installed!!
       #Go to https://nodejs.org/en/download and follow the install instructions. NOTE: installing node.js also installs npm
     ```
  2. To Set up a node.js server for your backend you must first have all of the necessary dependencies and packages installed
     ```bash
       #beginning in the root of the project "Tasky"
       mkdir backend && cd backend  #create backend folder and change into that directory
       mkdir server && cd server    #create server folder and change into that directory
       npm init -y                  #create your package.json file for your project's backend
       npm install express mongodb cors
       #Express is the server framework that handles HTTP requests and routing.
       #MongoDB is the database used to store application data.
       #CORS is a security middleware that allows the frontend to communicate with the backend across different domains.
     ```
  3. CRITICAL step, within your package.json file you must include the line: ***"type": "module",*** under the version attribute
  4. Within the server/ folder create a new file named server.js. We will come back to this file later. Within the server/ folder we will also create a new folder named db. Within db/ we will create connection.js. Within server/ we will also create a routes folder. Within routes/ we will create record.js.
     ```bash
       touch server.js
       mkdir db && cd db
       touch connection.js          #for handling the connection between our project and MongoDB
       cd ..
       mkdir routes && cd routes
       touch record.js              #for querying our data to and from our mongoDB database
     ```
  5. Project Structure
     ```text  
       ├── server/                 
       │   ├── db/
       │       └── connecetion.js
       │   ├── node_modules/   
       │   └── routes/
       │       └── record.js
       ├── .env              
       ├── package-lock.json                
       ├── package.json               
       └── server.js              
     ```
    
  ### **MongoDB**
  1. Now it is time to create our MongoDB Atlas Cluster
     1. View [MongoDB Atlas Free Cluster Set Up video](https://www.youtube.com/watch?v=SFkXQZ3x6zM)
     2. After creating the account, we can connect our project to our Atlas Cluster
     3. Click "Connect" button
     4. Input a User and Password that can be remembered and store it in a secure place (password will be used later for connection)
     5. Select "Drivers" as connection method
     6. Default settings should be fine, but if the Driver is not "Node.js" change it to Node.js for the latest version
     7. We can skip step 2 since we already installed mongodb
     8. Under step 3, select the "View full code sample" and copy the whole code into the 'server/db/connection.js' file. 
       1. Be sure to change the "<db_password>" with your actual password that was copied in OUR step 4(Input a User and Password)
     9. If not done already, create a .env file within the server folder. Then, copy the connection string, assign it to a variable "ATLAS_URI"(variable can be named whatever you want) in the .env file and save the file.
         ```text
           ATLAS_URI=<connection_string>
         ```
     10. Remove the first two lines from the connection.js file and replace them with the following
         ```javascript
           import { MongoClient, ServerApiVersion } from "mongodb";
           const uri = process.env.ATLAS_URI || "";
         ```
  
  ### **Server Pt2**

