# Exercise 7


## Learnings

1. Basics about ARM Templates
1. Exporting ARM Templates
1. Downloading ARM Templates
1. Editing and deploying ARM Templates in the Azure Portal
1. Deploying a VM using an Azure ARM Quickstart

## Introduction

The infrastructure for your application is typically made up of **many components** – maybe a *virtual machine*, *storage account*, and *virtual network*, or a *web app*, *database*, *database server*, and 3rd party services. You do not see these components as separate entities, instead you see them as related and interdependent parts of a single entity. You want to **deploy, manage, and monitor them as a group**. Azure Resource Manager (ARM) enables you to work with the resources in your solution as a group. You can deploy, update or delete all of the resources for your solution in a single, coordinated operation. You use a template for deployment and that template can work for different environments such as testing, staging and production. Resource Manager provides security, auditing, and tagging features to help you manage your resources after deployment.

## Export ARM Template

1. Open [Azure Portal](https://portal.azure.com) and sign in.

1. Trigger *Template Export* for Resource Group `PracticalDevOps-Dev`:<br/>
   ![Export Template](img/azure-export-template.png)

1. Download exported template and make yourself familiar with the code.<br/>
   ![Download Template](img/azure-template-download.png)


## Edit and Deploy Using PowerShell

If you are very familiar with PowerShell, you can do the following steps using the downloaded code instead of editing and deploying it in the Azure Portal.


## Edit and Deploy Using Azure Portal

1. Save the exported template using the name `PracticalDevOps`.<br/>
   ![Save Template](img/azure-save-template.png)

1. Edit the ARM template in Azure Portal.<br/>
   ![Edit Template](img/azure-edit-template.png)
   
1. Replace all `-dev` by `-test` and save the changed template.

1. Deploy changed template with the following parameters. This step might take a while.<br/>
   ![Deploy Template](img/azure-deploy-template.png)
   

## Use ARM Quickstart Template from GitHub

1. Open [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates/tree/master/) on GitHub.

1. Take a look at Quickstart Templates on GitHub. In particular, look for the `docker-simple-on-ubuntu` template ([link](https://github.com/Azure/azure-quickstart-templates/tree/master/docker-simple-on-ubuntu)).

1. Take a look at the UI for the Quickstart Templates [in the Azure Portal](https://azure.microsoft.com/en-us/documentation/templates/). Again, look for the *Deploy an Ubuntu VM with Docker Engine* template ([link](https://azure.microsoft.com/en-us/documentation/templates/docker-simple-on-ubuntu/)). 

1. In the next example, we are going to need a [Docker](https://www.docker.com/) host. Use the button *Deploy to Azure* in the [Quickstart Template](https://github.com/Azure/azure-quickstart-templates/tree/master/docker-simple-on-ubuntu) to deploy a Docker host in your Azure subscription.<br/>
   ![Deploy to Azure](img/deploy-to-azure.png)

1. Use the following settings when deploying the Docker host (note that you have to choose your own unique names for storage account and DNS name):<br/>
   ![Deploy to Azure settings](img/deploy-to-azure-settings.png)

1. Make sure that your deployment was successful. If it was, you are prepared for the next exercise.<br/>
   ![Deployment successful](img/deployment-successful.png)

   