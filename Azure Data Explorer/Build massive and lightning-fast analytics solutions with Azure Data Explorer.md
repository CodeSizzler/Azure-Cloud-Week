<h1>Build massive and lightning-fast analytics solutions with Azure Data Explorer</h1>

<h2>Use case scenario </h2>
<p>Contoso is looking to help their customers make business decisions with immediate impact based on real-time terabyte/petabyte of data in seconds Here as a Data Analyst you are supposed to build a near-real-time analytical solution with Azure Data Explorer (ADX), which supports interactive adhoc queries of terabyte/petabyte data.</p>

<h2>Solution Architecture</h2>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/1.PNG"/>
<p>In the Azure Data Explorer you will be creating a database. In that database a query is used to run the program say storm event. Once the query initiated a report will be generated in the power BI, using that report you will managing the results in the Kusto Query Language.</p>

<h2>Prerequisites</h2>
<p>To perform this demo, users must have the following resource:</p>
  <p>Valid Azure Subscription  </p>
  <p>Some knowledge on Azure Data Explorer, Power BI and Kusto Query Language.</p>

<h2>Steps:</h2>
<p>1. Log-in to Azure portal with your account using www.portal.azure.com. Select all service in the left menu in that select Azure Data Explorer. Once it prompts to the page select the created Cluster to add a Database in the existing cluster.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/2.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/2.1.png"/>
<p>2.Once you open the existing cluster select Database section and then create the database by clicking + Add Database icon.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/3.png"/>
<p>3. Create the database with the following configuration and click on Create:</p>
  <p>Database: Give a valid name to the Database</p>
  <p>Retention period: 3650.</p>
  <p>Cache period: 31.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/4.png"/>
<p>4. Now select the database and then select Query section in that select Open in Web UI.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/5.png"/>
<p>5. Once you open the query in the web follow you have to create a sample table by using the following command the query.</p>
  <p>// Create a table</p>
  <p>.create table SampleTable</p>
  <p>(Timestamp:datetime, ApiVersion:string, User:string, RawHeader:dynamic)</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/6.png"/>
<p>6. Now create the table mapping in the web UI with the following command.</p>
  <p>// Create a Json ingestion mapping</p>
  <p>.create table SampleTable ingestion json mapping</p>
  <p>"Mapping01" '[{"column":"Timestamp","path":"$.header.time"},{"column":"ApiVersion","path":"$.header.api_version"},{"column":"RawHeader","path":"$.header"},{"column":"User","path":"$.payload.user"}]'</p>
<p>7. Now run the following command to view the ingestion mapping.</p>
  <p>// View ingestion mappings</p>
  <p>.show table SampleTable ingestion json mappings </p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/7.png"/>
<p>8. Now run the following command for ingesting from the public blob.</p>
  <p>// Ingest from public blob</p>
  <p>.ingest into table SampleTable</p>
  <p>@'https://westuskustopublic.blob.core.windows.net/public/SampleData-500-4394582f-668f-4d03-8bba-58f87a7e48a0.json' with (jsonMappingReference = "Mapping01") </p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/8.png"/>
<p>9. Now connect the Azure Data Explorer in the Power BI by selecting the Get Data in the Power BI and select the more option search for Azure Data Explorer and then select Connect.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/9.png"/>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/9.1.png"/>
<p>10. Now connect your Azure Data Explorer with the following configuration and then select OK.</p>
  <p>Cluster: Help.</p>
  <p>Database: Sample.</p>
  <p>Table name or Azure data Explorer Query: Storm Event.</p>
  <p>Data connectivity mode: Import.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/10.png"/>
<p>11. Now select the Load in the following page once you connect to the Azure Data Explorer.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/11.png"/>
<p>12. Now the new StormEvent is created in the Power BI report.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/12.png"/>
<p>13. Now create a Power BI report. First create a line chart with total number of events by using Start Time in Axis box and EventId in the Values box.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/13.png"/>
<p>14. Now add a map title by using Beginlat in the Latitude box and use Beginlon in the Longitude box.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/14.png"/>
<p>15. Now create a Clustered column chart by putting Event Type in the Axis box and EventId in the Value box.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/15.png"/>
<p>16. Now create 4 separate card tiles with DeathDirect, DeathIndirect, InjuriesDirect and InjuriesIndirect in the Fields box.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/16.png"/>
<p>17. Now create a pie chart of reporting sources by using the Source in the Legend box and by using the EventId in the Values box.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/17.png"/>
<p>18. Once you are done with the report you can view the results in the Query select Get data and select Blank Query.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/18.png"/>
<p>19. Now you can see the results in the Query you have created.</p>
<img src="https://codesizzlergit.blob.core.windows.net/ms-demo-1/19.png"/>
<p>20. You can also manage the results by using the Kusto Query Language.</p>
