# Project XYZ

This template allows you to deploy a 3 Tier (Web, Biz and SQL) pattern including a Internet facing Management Jumpbox for Project XYZ using the Infrastructure Pattern Template **vm-3tier-poc-1**. 

The Infrastructure Pattern Template **vm-3tier-poc-1** can either deploy a new or attach to an existing Storage Account, create a new or attach to an existing Virtual Network with 4 subnets,  a Public IP Address, Network Security Groups for each Tier. Four D2 v2 size VMs with OS and Data Disk (1 x Management Jumpbox configured with the Public IP), 1 x Web Server configured with IIS, 1 x Business Server, and 1 x SQL Server with SQL Server 2016)

## Usage

Click on the **Deploy to Azure** button below. This will open the Azure Portal (login if necessary) and start a Custom Deployment. The following Parameters will be shown and must be updated / selected accordingly. 

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fmrptsai%2FProjectXYZ%2Fmaster%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Parameters

- baseUrl
  - Select the appropriate Repository Base URL containing Pattern Templates and Resource Templates
  - Default is 'https://raw.githubusercontent.com/mrptsai/'.

- patternName
  - Select the appropriate Infrastructure Pattern.
  - Default is 'vm-3tier-poc-1'.
  - Valid patternName's are:
  ```
       1 - vm-poc-1 (Creates a single VM with a new or existing Storage Account and a new or existing Virtual Network)
       2 - vm-dsc-poc-1 (Creates a single VM running IIS with a new or existing Storage Account and a new or existing Virtual Network)
       3 - vm-3tier-poc-1 (Creates a 3 Tier environment with a new or existing Storage Account and a new or existing Virtual Network, Management Jumpbox with PublicIP and Network Security Groups)
       4 - vm-dual-poc-1 (Creates a public facing Load balancer and 2 web servers with a new or existing Storage Account and a new or existing Virtual Network and a Network Security Group)
  ```

- storageAccountName
  - Enter a unique Name for a new Storage Account or specify the name of an existing Storage Account. Use PowerShell and the following command to generate a unique Storage Account Name:
  
  ```PowerShell
	storage + (-join ((48..57) + (97..122) | Get-Random -Count 15 | % {[char]$_}))
  ```

- storageNewOrExisting
  - Is the Storage Account **New** or **Existing**?
  - Allowed Values are:
  ```
       1 - new
       2 - existing
  ```
 
- storageExistingResourceGroup
  - Specify the existing Storage Resource Group. Leave blank if creating a new Storage Account.
  - Default is '' unless overridden.

- virtualNetworkName
  - Enter a Name for a Virtual Network or specify the name of an existing Virtual Network.

- virtualNetworkNewOrExisting
  - Is the Virtual Network **New** or **Existing**?
  - Allowed Values are:
  ```
       1 - new
       2 - existing
  ```
  
- virtualNetworkExistingResourceGroup
  - Specify the existing Virtual Network Resource Group. Leave blank if creating a new Virtual Network.
  - Default is '' unless overridden.
  
- virtualNetworkPrefix
  - Specify the Virtual Network Prefix to create or to be used
  - Default is '10.1.0.0/16' unless overridden.
  
- subnet0Prefix
  - Specify the Subnet Prefix for the Management Tier
  - Default is '10.1.0.0/26' unless overridden.

- subnet0Name
  - Specify the Subnet name for the Management Tier to create or to be used
  - Default is 'mgmt' unless overridden.
  
- subnet1Prefix
  - Specify the Subnet Prefix for the Web Tier
  - Default is '10.1.0.64/26' unless overridden.

- subnet1Name
  - Specify the Subnet name for the Web Tier to create or to be used
  - Default is 'web' unless overridden.
  
- subnet2Prefix
  - Specify the Subnet Prefix for the Business Tier
  - Default is '10.1.0.128/26' unless overridden.

- subnet2Name
  - Specify the Subnet name for the Business Tier to create or to be used
  - Default is 'biz' unless overridden.
  
- subnet3Prefix
  - Specify the Subnet Prefix for the SQL Tier
  - Default is '10.1.0.196/26' unless overridden.  

- subnet3Name
  - Specify the Subnet name for the SQL Tier to create or to be used
  - Default is 'sql' unless overridden.
  
- publicIPDnsName
  - Specify the DNS Name for the Public IP Address.
  - Default is 'mgmt-jb-pip' unless overridden.

- vmAdminUserName
  - Specify the VM local Logon Account that will have Administration Privileges.
  - Default is 'testuser' unless overridden.
 
- vmAdminPassword
  - Enter a Password for the local Administration Account.
  - Default is 'P@ssword1Password2' unless overridden.

## Prerequisites

Access to Azure

## Versioning

We use [Github](http://github.com/) for version control.

## Authors

* **Paul Towler** - *Initial work* - [ProjectXYZ](https://github.com/mrptsai/ProjectXYZ)

See also the list of [contributors](https://github.com/mrptsai/ProjectXYZ/graphs/contributors) who participated in this project.
