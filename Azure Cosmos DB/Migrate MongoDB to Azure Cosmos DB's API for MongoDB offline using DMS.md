<h1>Migrate MongoDB to Azure Cosmos DB's API for MongoDB offline using DMS</h1>

<h2>Use case scenario</h2>
<p>Contoso wants to migrate an on-premises MongoDB database to Azure Cosmos DB. As a Data Analyst you need to migrate a dataset in MongoDB hosted in an Azure Virtual Machine to Azure Cosmos DB's API for MongoDB by using Azure Database Migration Service.</p>

<h2>Solution Architecture</h2>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/1.PNG"/>
<p>We migrate a database in the Mongo DB hosted in Azure Database Migration Service (DMS) to Cosmos DB.</p>

<h2>Prerequisites</h2>
<p>To perform this demo, users must have the following resource:</p>
  <p>Valid Azure Subscription.</p>
  <p>Mongo DB.</p>
  <p>Azure Database Migration Service (DMS).</p>
  <p>Cosmos DB.</p>
  <p>Create a Virtual Network.<.p>

<h2>Steps:</h2>
<p>1. Log-in to Azure portal with your account using www.portal.azure.com. Select Subscription in the All Service to register the Microsoft.DatabaseMigration, search the migration in the Resource Provider to register.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/2.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/2.1.png"/>
<p>2. Now select Azure Database Migration Service in All Service and then click on Add icon to create a service.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/3.png"/>
<p>3. Now create the Migration service with the following configurations:</p>
  <p>Service Name: Give a valid service name.</p>
  <p>Subscription: Select a valid subscription.</p>
  <p>Resource Group: Select the existing Resource Group or create new one.</p>
  <p>Location: Select a valid location.</p>
  <p>Virtual Network: Select the existing virtual network or create new one.</p>
  <p>Pricing Tier: Select the standard pricing tier.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/4.png"/>
<p>4. Once your deployment is complete now you will be creating a new migration project in the existing migration service. Select +New Migration Project in the Migration service you created. Create the Migration project with the following configuration and then select Create and run activity.</p>
  <p>Project Name: Give a valid name.</p>
  <p>Source Server Type: Select Mongo DB as source server.</p>
  <p>Target Server Type: Select Cosmos DB as target server.</p>
  <p>Type of Activity: Select offline data migration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/5.png"/>
<p>5. Once your deployment is complete, now select the created migration project and then select +New Activity icon. A Migration Wizard page will appear, now create the source details in the Select Source with the following configurations and then select Save.</p>
  <p>Mode: Select standard mode.</p>
  <p>Source server name: select the server name.</p>
  <p>Server port: Select the default port.</p>
  <p>User Name: Give a valid user name.</p>
  <p>Password: Give a valid password.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/6.png"/>
<p>6. Once you save the source details the next step is to create the target details in the Select Target section with the following configuration and then select Save.</p>
  <p>Mode: select Cosmos DB target.</p>
  <p>Subscription: Select a valid subscription.</p>
  <p>Cosmos DB Name: Select the Cosmos DB you have created.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/7.png"/>
<p>7. The next step is to map the source and target database for migration in the Database Settings section. If the target database contains the same database name as the source database, Azure Database Migration Service selects the target database by default. Once the map is complete click Save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/8.png"/>
<p>8. On the Collection setting screen, expand the collections listing, and then review the list of collections that will be migrated. Azure Database Migration Service auto selects all the collections that exist on the source MongoDB instance that don't exist on the target Azure Cosmos DB account.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/9.png"/>
<p>9. Next step in the Migration summary screen, in the Activity name text box, specify a name for the migration activity and then select Run Migration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/10.png"/>
<p>10. When you select Run Migration a migration window will appear, once the migration is complete you can see the in the Status indicating Complete.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/11.png"/>
<p>After the migration completes, you can check your Azure Cosmos DB account to verify that all the collections were migrated successfully in the Data Explorer section.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-4/12.png"/>
