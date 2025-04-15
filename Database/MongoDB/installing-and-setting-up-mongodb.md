# Installing & Setting Up MongoDB

MongoDB can be installed and used in two main ways:
- Locally on your machine
- In the cloud using MongoDB Atlas

This guide will walk you through both setups.

---

## 1. Installing MongoDB Locally

### Step 1: Download MongoDB
- Visit: [https://www.mongodb.com/try/download/community](https://www.mongodb.com/try/download/community)
- Choose your OS and install the **MongoDB Community Server**.

### Step 2: Install MongoDB Compass (Optional GUI)
- Compass is a graphical interface to interact with your MongoDB databases.
- Download from: [https://www.mongodb.com/products/compass](https://www.mongodb.com/products/compass)

### Step 3: Start MongoDB Server
- On Windows, MongoDB runs as a service after installation.
- On Mac/Linux, run:
```bash
mongod
```
### Step 4: Open Mongo Shell (Optional)
```
mongo
```
Use this shell to run basic MongoDB commands.

## 2. Setting Up MongoDB Atlas (Cloud Database)
MongoDB Atlas is a free cloud-based service that lets you run MongoDB online.

### Step 1: Sign Up
- Go to: https://www.mongodb.com/cloud/atlas
- Create an account and login.

### Step 2: Create a Cluster
- Choose the free tier (Shared Cluster).
- Select a region near you.

Name your cluster and click “Create Cluster”.

### Step 3: Add Database User
- Set a username and password.
- Store them safely (you’ll need them to connect).

### Step 4: Allow IP Access
Whitelist your IP address or allow access from anywhere (0.0.0.0/0) for development.

### Step 5: Connect to Your Cluster
- Choose “Connect your application”
- Copy the connection string (e.g.):

php-template
```
mongodb+srv://<username>:<password>@cluster0.mongodb.net/<dbname>?retryWrites=true&w=majority
```
Replace <username>, <password>, and <dbname> with your credentials.

### Test the Connection in Node.js
Install mongoose:
```
npm install mongoose
```

Example:
```
const mongoose = require('mongoose');

mongoose.connect('your_mongodb_connection_string', {
  useNewUrlParser: true,
  useUnifiedTopology: true
})
.then(() => console.log("MongoDB connected 🚀"))
.catch((err) => console.log("MongoDB connection error: ", err));
```

## Summary
- Use MongoDB locally for offline development and practice.
- Use MongoDB Atlas for cloud-based projects and deployment.
- You’ll use Mongoose to interact with MongoDB in your Node.js apps.
