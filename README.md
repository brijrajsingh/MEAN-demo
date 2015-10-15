# Aim of the Demo is to bring to light performance considerations when designing a Scalable MEAN Applicaiton
# App will be deployed on Azure using ARM
# initial code base taken from # 
# https://github.com/Azure/azure-quickstart-templates/tree/master/node-mongodb-high-availability and also ARM template for Centos VM Cluster template

# initial copy of chirp app taken from https://github.com/MicrosoftLearning/chirp/ 

# Demo 1 using front end NODEJS cluster and Single mongoDB Replica Set
# Show effect of mongodb configurations, including write concern on the performance

# Steps to get things started
# Execute following from Powershell



# 1 you will be prompted for your azure accound credentials after this command
Add-AzureAccount

# 2
Switch-AzureMode AzureResourceManager

# 3 Create ResourceGroup and Storage Account (Optional)
 New-AzureResourceGroup -Name 1resgrp -Location "West US"
## Remove-AzureResourceGroup -Name 7resgrp
 
 New-AzureStorageAccount -Name 1stoacc -Location "WEST US" -AccountType Standard_LRS -ResourceGroupName 1resgrp
 
# 4 You will be promted for username, password, storage account, frontendstorage account and Dns name for node cluster . The username and password will have root access on the Ubuntu VMs as well as admin acess on the mongodb replica set
New-AzureResourceGroupDeployment -Name mongo-deploy-2 -ResourceGroupName  5-res-grp -TemplateUri https://raw.githubusercontent.com/maninderjit/MEAN-demo/master/Centos-nojejs-nodes-mongodb-one-replica-set/azuredeploy.json -Verbose



# To Debug you can use following 
#  Get-AzureResourceGroupLog -ResourceGroup 1resgrp -Status Failed -DetailedOutput