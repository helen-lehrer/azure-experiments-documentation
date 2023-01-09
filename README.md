---
description: >-
  Using Azure to host a MySQL database and an MVC web app that uses that
  database.
---

# MySQL database & MVC app Experiment

### Vocab

#### Resource Group :&#x20;

* A container that holds related resources for an Azure solution. The resource group includes those resources that you want to manage as a group. You decide which resources belong in a resource group based on what makes the most sense for your organization.

#### Subscription:

* A logical container for your resources. Each Azure resource is associated with only one subscription. Creating a subscription is the first step in adopting Azure.

#### App Service

* Azure App Service is a fully managed platform for hosting web applications and APIs in Azure.

1/9/23

1\. Create an Azure Database for MySQL - Flexible Server

* Create Flexible Server
* Public Access
* add curent IP address

2\.  Connect the Server to our MySQL Workbench

* Launch MySQL Workbench and find the **+** icon to create a new MySQL connection.
* &#x20;Set \`Hostname\` as our Server name, and set \`username\` as Server admin login name.&#x20;
* The port should always be `3306` when using Azure.
* Test & Create connection

3\. Create an App Service

* Runtime stack- .NET 6.0

4\. Connect the Web App to MySQL Database

* Service Type- DB for MySQL flexible server
* MySQL flexible server- choose the flexible server just setup&#x20;

\




\
