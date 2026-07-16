# 🚀 Automated CI/CD Pipeline for Beginners

Welcome! This project will teach you how to build a fully automated "CI/CD Pipeline" using Microsoft Azure. 

If you are new to cloud computing or DevOps, don't worry! This guide is written specifically for beginners.

## 🤔 What is a CI/CD Pipeline?

Imagine you are baking a cake. Instead of mixing everything by hand, putting it in the oven, and watching it bake every single time, you build a robot kitchen. 
As soon as you put the ingredients on the counter, the robot automatically mixes them, bakes the cake, and serves it on a plate.

In software, **CI/CD** is that robot kitchen for your code:
*   **Continuous Integration (CI)**: Every time you save and upload (commit) new code, a robot automatically checks it and packages it up. In our project, this package is called a **Docker Container**.
*   **Continuous Deployment (CD)**: After the package is ready, the robot automatically delivers it to the live server so users on the internet can see your changes immediately.

## 🏗️ What We Are Building

1.  **The App**: A very simple website built with Node.js.
2.  **The Box (Docker)**: We put the app inside a virtual box called a "Container" so it works perfectly everywhere.
3.  **The Storage (ACR)**: We save our finished box in the cloud using **Azure Container Registry**.
4.  **The Server (App Service)**: We run our box on a web server called **Azure App Service**.
5.  **The Robot (Azure Pipelines)**: The automated worker that takes our code, puts it in the box, saves it, and sends it to the server.

---

## 🛠️ Step-by-Step Setup Guide

Follow these steps exactly to get your automated pipeline working!

### Step 1: Prepare Your Code
1.  Make sure you have an account on [Azure DevOps](https://dev.azure.com/).
2.  Create a new "Project" in Azure DevOps.
3.  Upload (push) all the files in this folder to your Azure DevOps project's "Repos" (repository).

### Step 2: Create Your Cloud Resources
Go to the [Azure Portal](https://portal.azure.com/) and create two things:
1.  **Azure Container Registry (ACR)**: Think of this as a private locker for your app. Search for it, click Create, and give it a name.
2.  **Azure App Service (Web App)**: This is the server that will host your website to the public. 
    *   *Important*: When creating it, choose **Docker Container** under "Publish" and **Linux** under "Operating System".

### Step 3: Give Permission to Your Robot
Your robot (Azure Pipelines) needs permission to access your locker (ACR) and your server (App Service).
1.  Go to your Azure DevOps project.
2.  Click on **Project settings** (bottom left corner).
3.  Click on **Service connections**.
4.  Create a new connection for **Azure Resource Manager** (this lets the robot talk to your Azure account).
5.  Create a new connection for **Docker Registry** -> **Azure Container Registry** (this lets the robot put the box in your locker).

### Step 4: Update the Pipeline Instructions
We need to tell the robot the exact names of your locker and server.
Open the `azure-pipelines.yml` file in your code editor and change these specific lines at the top:
*   `dockerRegistryServiceConnection`: Put the name of the Docker connection you made in Step 3.
*   `containerRegistry`: Put the login server name of your ACR locker (e.g., `mycoolerlocker.azurecr.io`).
*   `webAppName`: Put the exact name of the App Service server you made in Step 2.
*   `azureSubscription`: Put the name of the Azure Resource connection you made in Step 3.

### Step 5: Start the Robot!
1.  In Azure DevOps, go to the **Pipelines** menu on the left.
2.  Click **Create Pipeline** (or New Pipeline).
3.  Choose **Azure Repos Git** (where your code is stored).
4.  Select your repository.
5.  Choose **Existing Azure Pipelines YAML file** and select the `/azure-pipelines.yml` file.
6.  Click **Run**!

Watch the screen! You will see the robot building your app, packaging it, and sending it to the live server automatically. 

🎉 **Congratulations! You have built your first CI/CD Pipeline!**
