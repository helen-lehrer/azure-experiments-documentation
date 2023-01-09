---
description: Using Azure to host a MySQL database and a connected MVC web app
---

# MySQL database & MVC app Experiment

### Step-By-Step Processes

#### 1/9/23

Hosting this repo:  [https://github.com/helen-lehrer/HairSalon.Solution](https://github.com/helen-lehrer/HairSalon.Solution)

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
* Add ASP.NET Core 5.0 (x64) Runtime extension

4\. Connect the Web App to MySQL Database

* Navigate to the App Service just created to the Service Connector tab and Create a new Service Connector
* Service Type- DB for MySQL flexible server
* MySQL flexible server- choose the flexible server just setup. Deploy.
* After the service connector is deployed, find it on the service connector tab, expand it, and copy the connection string.
* Create an appsettings.json in the codebase and add something like:

```
"ConnectionStrings": {
    "AZURE_MYSQL_CONNECTIONSTRING": "Server=hair-salon-sql.mysql.database.azure.com;Database=hair-salon;Port=3306;User Id=<userID>;Password=<password>;SSL Mode=Required"
  }

```

* Navigate to Startup.cs and find where the connection string is passed to the builder instance
* Change it to match the name Azure asks us to use for the connection string, “AZURE\_MYSQL\_CONNECTIONSTRING”
* Run this command to update our database with that connection:

```
dotnet ef database update --connection "Server=hair-salon-sql.mysql.database.azure.com;Database=hair-salon;Port=3306;User Id=<userID>;Password=<password>;SSL Mode=Required"
```

Current Status:

* It works locally and I deployed the site, but I'm getting 'HTTP Error 503. The service is unavailable.'
* When I try to validate the connection string in Azure, it fails and gives the message 'The configured values is validated connectionString of connection is incorrect'
* Currently getting the error ''Your startup project 'HairSalon' doesn't reference Microsoft.EntityFrameworkCore.Design. This package is required for the Entity Framework Core Tools to work. Ensure your startup project is correct, install the package, and try again.' in terminal after running this command:

```
dotnet ef database update --connection "Server=hair-salon-sql.mysql.database.azure.com;Database=hair-salon;Port=3306;User Id=hlehrer;Password=4540!!br;SSL Mode=Required"

```

### Vocab for reference:

#### Resource Group :&#x20;

* A container that holds related resources for an Azure solution. The resource group includes those resources that you want to manage as a group. You decide which resources belong in a resource group based on what makes the most sense for your organization.

#### Subscription:

* A logical container for your resources. Each Azure resource is associated with only one subscription. Creating a subscription is the first step in adopting Azure.

#### App Service

* Azure App Service is a fully managed platform for hosting web applications and APIs in Azure.

\
