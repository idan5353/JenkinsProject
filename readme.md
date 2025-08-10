# Jenkins CI/CD Pipeline for Node.js App

This project demonstrates a simple Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins to deploy a Node.js Express app to an Ubuntu EC2 instance.

---

## Project Structure

- `Jenkinsfile`: Defines the Jenkins pipeline that automates build, test, and deployment stages.
- `index.js`: Simple Express server that responds with a greeting message.
- `package.json`: Node.js dependencies and scripts.

---

## Jenkins Pipeline Overview

The pipeline is triggered by any push to the GitHub repository and consists of the following stages:

1. **Clone**: Pulls the latest code from the GitHub repository.
2. **Build**: Installs Node.js dependencies using `npm install`.
3. **Test**: Runs tests (currently a placeholder).
4. **Deploy**: SSH into the Ubuntu EC2 instance and:
   - Clones or updates the app repository.
   - Installs dependencies on the server.
   - Restarts the app using `pm2`.

---

## Prerequisites

- Jenkins server set up with:
  - Node.js and npm installed.
  - SSH Credentials configured for deployment server.
  - `pm2` installed on the deployment Ubuntu EC2 instance.
- Ubuntu EC2 instance configured with:
  - Node.js, npm, and pm2 installed.
  - Open port 3000 allowed in the security group.
  - SSH access enabled using the private key Jenkins uses.

---

## How to Use

1. Clone this repository and push to your GitHub account.
2. In Jenkins, create a pipeline job linked to this repo.
3. Add your SSH private key as a Jenkins credential and note its ID.
4. Update the `Jenkinsfile`:
   - Replace `<app-server-public-ip>` with your Ubuntu EC2 public IP.
   - Replace `'your-credential-id'` with your Jenkins SSH credential ID.
5. Commit and push changes to GitHub.
6. Jenkins will automatically trigger the pipeline on each push.

---

## Node.js App (index.js)

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello World!! idan king from Jenkins CI/CD pipeline!');
});

const port = process.env.PORT || 3000;
app.listen(port, '0.0.0.0', () => {
  console.log(`App running on port ${port}`);
});
