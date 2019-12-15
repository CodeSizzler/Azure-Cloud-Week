<h1>Database Migration using Azure Database Migration Service</h1>

<h2>Use case scenario</h2>
<p>Contoso has assessed the performance of Azure SQL Database service and its feasibility of it for them to use it for deploying their on-premises database into Azure SQL Database service. As a data analyst try to understand how the Azure DMS will help them to migrate their on-prem database to Azure using Database migration Service. They are having databases that must be migrated without making them to go offline and there are also databases that can be migrated by taking them offline. Because of this Contoso is trying to understand how the offline database migration and online database migration offered by the Azure DMS can be used to migrate their databases without any issues. Hence, in this demo, we will be migrating the on-premises SQL Server database of Contoso to Azure SQL Server database.</p>

<h2>Solution architecture</h2>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/01.png"/>

<h2>Pre-requisites</h2>
<p>To perform this demo you must have valid Azure subscription, Azure SQL Database, Azure DMS and DMA.</p>

<h2>Demo</h2>
<p>Log-in to Azure portal with your account using www.portal.azure.com. Select All service in the left menu and then select SQL Database in the Database category.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/02.png"/>
<p>Create the SQL database with the following configuration as shown in the below image.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/03.png"/>
<p>Don't wait for the deployment to complete create a SQL Server Virtual Machine with the configurations as shown in the below image.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/04.png"/>
<p>Then create a SQL Server.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/05.png"/>
<p>Once your deployment is complete select go to resource now connect to the VM you have created earlier.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/06.png"/>
<p>Once you connect to the VM, now disable the IE Enhanced Security configuration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/07.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/08.png"/>
<p>Download SQL Server Setup and install it if in case you don’t have it installed. We need an additional service name SQL Server Full Text Search enabled in the SQL Server for implementing some sample workloads into them. Azure virtual machines do not come with this service enabled in them by default. Hence download the setup of SQL Server from here - https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2017-rtm to modify the SQL Server configuration in VM. After downloading it, open the ISO image.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/09.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/10.png"/>
<p>Now open the setup or find the SQL Server Installer in the start menu and open it. Once you open the setup menu, click on the Installation option and choose the menu as denoted below. Now follow the instructions in the below given screenshots.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/11.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/12.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/13.png"/>
<p>Once you installed the new setup, now add a sample SQL database if don’t have sample database download it from https://github.com/Microsoft/sqlserver-samples. Now, let us add this sample data into the database. Open the file instadwdb which contains script to upload these data into database.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/14.png"/>
<p>Once you open the file, it will navigate to the SQL Server Management Studio (SSMS). Now connect the VM you created in the database engine.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/15.png"/>
<p>Select the query option and then select SQLCDM Mode to verify the executions.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/16.png"/>
<p>Now change the path of the database in the query and then select Execute option to add the database to SQL database.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/17.png"/>
<p>Once the query is executed successfully, now navigate to the Database Migration Assistance to create a new migration and follow the further steps to access the database.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/18.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/19.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/20.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/21.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/22.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/23.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/24.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/25.png"/>
<p>Once the migration is complete, now navigate to SSMS to configure the database recover model as Bulk-logged in the options section.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/26.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/27.png"/>
<p>Now create a new query to enable the database for CDC template by using the following command.</p>

    <p>-- ====</p> 
    <p>-- Enable Database for CDC template </p>
    <p>-- ====</p>
    <p>USE AdventureWorksDW</p>
    <p>GO</p>
    <p>EXEC sys.sp_cdc_enable_db </p>
    <p>GO</p>

<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/28.png"/>
<p>Once the query is executed successfully, now enable the replication of database by selecting the Configure Distribution. Follow the further steps to configure distribution.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/29.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/30.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/31.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/32.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/33.png"/>
<p>Once the configuration is complete, now create the Azure Database Migration Service (DMS) to migrate the database to the Azure SQL Database.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/34.png"/>
<p>Now create the DMS with the following configurations as showm in the below picture.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/35.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/36.png"/>
<p>Once your deployment is complete, now create the Network Security Group in the Network section with the following configuration.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/37.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/38.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/39.png"/>
<p>Add the following in bound rules.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/40.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/41.png"/>
<p>Now navigate to the VM you created early select Subnet in the setting section. Select the default subnet and change the Network Security Group and select Save.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/42.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/43.png"/>
<p>Now navigate to the DMS you have created early and select +New Migration icon to create a new migration and follow the further steps to migrate the database to Azure SQL Database.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/44.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/45.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/46.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/47.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/48.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/49.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/50.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-sql-demo-1/51.png"/>
<p>Once you run the migration the database in the on-premise SQL database will be migrated to the Azure SQL Database.</p>
