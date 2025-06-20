# Follow the steps described below

Table of contents:
1. [Personas and their roles](https://github.com/Client-Engineering-Indonesia/Data-Intelligent-Incubation-Feb-2025/blob/main/IBM%20Knowledge%20Catalog/Hands-on%20Lab%20-%20IBM%20Knowledge%20Catalog.md#section1)
2. [Connect your data sources](https://github.com/Client-Engineering-Indonesia/Data-Intelligent-Incubation-Feb-2025/blob/main/IBM%20Knowledge%20Catalog/Hands-on%20Lab%20-%20IBM%20Knowledge%20Catalog.md#section2)
3. [Define Business Vocabulary](https://github.com/Client-Engineering-Indonesia/Data-Intelligent-Incubation-Feb-2025/blob/main/IBM%20Knowledge%20Catalog/Hands-on%20Lab%20-%20IBM%20Knowledge%20Catalog.md#section3)
4. [Curate and enrich data assets](https://github.com/Client-Engineering-Indonesia/Data-Intelligent-Incubation-Feb-2025/blob/main/IBM%20Knowledge%20Catalog/Hands-on%20Lab%20-%20IBM%20Knowledge%20Catalog.md#section4)
5. [Catalog Governed Data](https://github.com/Client-Engineering-Indonesia/Data-Intelligent-Incubation-Feb-2025/blob/main/IBM%20Knowledge%20Catalog/Hands-on%20Lab%20-%20IBM%20Knowledge%20Catalog.md#section5)
6. [Define Policies and Rules](https://github.com/Client-Engineering-Indonesia/Data-Intelligent-Incubation-Feb-2025/blob/main/IBM%20Knowledge%20Catalog/Hands-on%20Lab%20-%20IBM%20Knowledge%20Catalog.md#section6) 
7. [Manage Data Quality](https://github.com/Client-Engineering-Indonesia/Data-Intelligent-Incubation-Feb-2025/blob/main/IBM%20Knowledge%20Catalog/Hands-on%20Lab%20-%20IBM%20Knowledge%20Catalog.md#section7) 
8. [About IBM Knowledge Accelerator](https://github.com/Client-Engineering-Indonesia/Data-Intelligent-Incubation-Feb-2025/blob/main/IBM%20Knowledge%20Catalog/Hands-on%20Lab%20-%20IBM%20Knowledge%20Catalog.md#section7) 



<h1 id="section1">1. Personas and their roles</h1>

| Role | Responsibilities |
| --   |       ---        |
| Data Steward  | 1. Define and publish a complete and meaningful set of business vocabulary **governance artifacts**. <br> 2. Create the **governance rules** that were required by the governance policy that protects sensitive information.<br> 3. Create the **data protection rules** to protect personal and sensitive information based on the approved governance policies and rules.<br> 4. Discover and **import the data assets** that were needed using the Metadata Import tool. <br> 5. Curate the data assets using the **Metadata enrichment** tool to profile, access data quality, and assign business terms and data classes.<br> 6. **Publish the connections and data assets** to a governed catalog.<br> 7. **Augment the cataloged assets** with additional metadata: Tags, Classifications, Related Assets, and Reviews.  |
| Privacy Steward | **Review and approve** the governance policies and rules.|
| Quality Analyst | 1. **Assess** data quality issues and **create a data quality definition** and data quality rules.<br> 2. **Create a Data Quality SLA remediation rule** to monitor data quality issues that invokes the data quality SLA remediation workflow.|
| Business User (Data Scientist) | **Find the data they need** and review the catalog assets and metadata. |

Other than the roles mentioned above, there is another role responsible for managing system configuration, which is the Administrator. In this use case, this role is responsible for:
1. Defining the roles --such as Data Steward, Privacy Steward, Quality Analyst, and Business User--, setting permissions for each role, and assigning roles to users;
2. Defining the data sources that contain the relevant data needed by the project team.

<h1 id="section2">2. Connect to data sources</h1>
The very first step in your journey to establishing Data Intelligence in your organization is to identify all data sources within your company and establish connections to those systems. This step is ideally performed by the Administrator or Senior Data Stewards. Some large organizations grant each data owner (producer) access to their Knowledge Catalog, allowing them to connect their data sources independently.

Before the data governance lifecycle processes can begin, data stewards and data consumers need access to data. As a best practice, identifying and providing access to data sources needs to happen before data stewardship can begin so that the data is accessible to the data steward to begin discovering relevant data, analyzing data content and quality, and enforcing data privacy policies in order to provide timely access to high quality, governed data to the data consumers who will use it for analytics and AI.

Goals:
- [ ] Check platform connections provided by Administrator

Steps
1. Login as Data Steward using the assigned username and password to the Knowledge Catalog platform.
2. Select Data > Connectivity from the menu
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image4.png)
3. You will see 3 available connections on platform level that have been created by the Administator.
![List of platforms connections](images/platform_connections.png)

<h1 id="section3">3. Define Business Vocabulary</h1>

This section creates all the governance artifacts needed to establish a trusted, business ready, governance foundation. It uses a set of CSV files to import and create the artifacts in the upcoming steps so make sure the governance artifacts zip file has been downloaded and unzipped. Download here: [Data Cataloging and Governance](https://github.com/CloudPak-Outcomes/Outcomes-Projects/blob/main/Knowledge-Catalog-L4-PoX-Lab/Knowledge-Catalog-L4-PoX-Lab.zip)

It is essential to establish the business vocabulary first before any data curation, enrichment and cataloging of data assets takes place. This is because governance artifacts, like data classes and business terms, can be automatically assigned to data assets during metadata enrichment and cataloging. If not, all of those tasks would have to be done manually, which defeats taking advantage of the automated and built-in data governance capabilities of Knowledge Catalog.

#### 1. Create custom properties
Custom properties and relationships need to be defined before any data governance artifacts are defined because they will be attributes of those governance artifacts and need to be established before the artifacts are imported and created. 

Goal: 
- [ ] Create a custom property, called Department, that will be added to all business terms. 

Steps
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select Administration > Governance and catalogs from the menu.
![section3_1](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image20-35.png)
3. Select the `Asset and artifact definitions` tile.
4. Select the `Custom properties` definition from the left side menu.
5. Click the `Import from file` button.
![section3_2](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image20-37.png)
6. Click the `Drag and drop file here or upload` link.
7. Select the `governance-custom-attributes.json` file from your download location.
8. Click the `Open` button.
![section3_3](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image20-39.png)
9. Click the `Import` button.
10. A message box will appear with a notification that 1/1 custom attributed was imported successfully.
![section3_4](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image20-41.png)


#### 2. Create categories
Categories act as folders or directories to organize governance artifacts and provide access controls to authorize who can author and manage those artifacts. Categories provide the logical structure for all governance artifacts, except data protection rules. You group governance artifacts in categories to make them easy to find and manage, and to control their visibility. Categories can be organized in a hierarchy based on their meaning and relationships to one another. A category can have subcategories, but a subcategory can have only one direct parent category.

In this section, 3 categories will be imported and created (one parent category and two sub-categories) that will provide the logical structure for the governance artifacts that are defined in this lab.

Goals:
- [ ] Create categories by importing the CSV file containing the list of categories.

Steps
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select `Governance` > `Categories` from the menu.
![section3_5](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image21.png)
3. Using the `Add category` dropdown, select `Import from file`.
![section3_6](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image22.png)
4. Click the `Drag and drop file here or upload` link.
5. Select the governance-categories.csv file from your download location.
6. Click the `Open` button.
![section3_7](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image24.png)
7. Click the `Next` button.
8. Select the `Replace all values merge` option. NB: If you 
9. Click the `Next` button.
![section3_8](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image26.png)
10. Select the `Close` button.
11. Refresh the page. You should see the `[uncategorized]` and `Locations` system categories and the 3 new categories that were imported and created with a parent category named: Business and two sub-categories underneath it named: Employee and Data Privacy.
![section3_9](images/section3_9.png)

#### 3. Create classifications 
Classifications are labels that can be attached to describe data assets. The default classifications available on the platform are Personal Information, Personally Identifiable Information, and Sensitive Personal Information. Additional classifications include, for example, Confidential, Internal, and Public.

Goals:
- [ ] Import classifications from csv file

Steps:
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner). Select `Governance` > `Classifications` from the menu. Using the Add classification dropdown, select `Import from file`.
![section3_10](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image34.png)
2. Click the `Drag and drop file here or upload` link.
3. Select the `governance-classifications.csv` file from your download location.
4. Click the `Open` button.
![section3_11](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image36.png)
5. Click the `Next` button.
6. Select the `Replace only empty values` merge option.
7. Click the `Next` button.
From this point forward, all governance artifacts have to be published. Categories and Data Protection Rules do not need to be published but all other governance artifacts you create or update will be in draft mode until you publish them.
8. Click the `Go to task` button.
![section3_12](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image39.png)
9. Click the `Publish` button.
![section3_13](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image40.png)
10. Click the `Publish` button again without entering a comment.
![section3_14](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image41.png)
11. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner). 
12. Select the `Governance` > `Classifications` menu.
13. Select the `Confidential` classification. The first classification in the list.
![section3_15](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image44.png)
Notice: that the classification has a tag of Employee and that it was also assigned to the `Business` >> `Employee` sub-category as a secondary category. All of the classifications will have the same change applied. If time permits, and you are curious, select the other 3 classifications to see the same changes have been applied.
![section3_16](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image45.png)

#### 4. Create reference data
Reference data sets provide logical groupings of code values (reference data values), such as department and gender codes. These codes are sets of allowed values that are associated with data fields and can be assigned to data classes. Which is why they need to be created before data classes are created.

Reference data sets are created so that enterprise standards can be accessed centrally by users or by consuming applications through APIs. Reference data sets can also be used to provide the matching pattern for data classes, allowing data fields to be automatically classified through data profiling and discovery. These data classes can then be used in data quality analysis to evaluate the quality and consistency of the values in data columns. Which is why you create data classes before you create reference data.

Goals:
- [ ] Add reference dataset of Termination Code from CSV file.

Steps:
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Governance` > `Reference data` menu.
![section3_17](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image47.png)
3. Using the `Add reference data set` dropdown, select `New reference data set`.
![section3_18](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image48.png)
4. Click the `Drag and drop file here or upload` link.
![section3_19](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image49.png)
5. Select the `governance-termination.csv` file from the download location.
![section3_20](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image50.png)
6. Click the `Open` button.
7. Click the Copy button below and paste the value into the Name field:
`Termination Lookup`
8. Click the Copy button below and paste the value into the Description field:
`Valid codes and values for employee termination codes.`
9. Click the `Select` button to select a primary category.
![section3_21](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image51.png)
10. Select the `Business` parent category to open it and see the secondary categories. Do not select the radio button.
11. Select the radio button on the `Employee` sub-category.
12. Click the `Add` button.
![section3_22](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image53-1.png)
13. Click the `Next` button.
![section3_23](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image53-2.png)
14. Make sure the `First row as column header` option is set to `On`.
15. Using the `Column` dropdown, select the `TERMINATION_CODE` column from the list.
16. Using the `Target column` dropdown, select `Code` from the list.
![section3_24](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image53-3.png)
17. Using the `Column` dropdown, select the `TERMINATION_VALUE` column from the list.
18. Using the `Select column` Target columns dropdown, select `Value` from the list.
19. Click the `Next` button.
![section3_25](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image53-4.png)
20. Click the `Create` button.
21. Click the `Publish` button.
![section3_26](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image53-6.png)
22. Click the `Publish` button again without entering a comment.
23. Click the `Reference data` breadcrumb to get back to the reference data home page.
![section3_27](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image53-8.png)

#### 5. Create data classes
In the context of a Knowledge Catalog, Data Classes describe the format of the content in table columns. They provide a description of the data, examples, and the categories to which they belong. They also define data matching capabilities, including criteria, matching methods, and regular expressions. Lastly, they determine relationships with other governance artifacts.

Goals:
- [ ] Import Data Classes from CSV file
- [ ] Configure data matching to Termination Code reference dataset

Steps:
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Governance` > `Data classes` menu.
![section3_28](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image54.png)
3. Using the `Add data class` dropdown, select `Import from file`.
4. Click the `Drag and drop file here or upload` link.
5. Select the `governance-data-classes.csv` file from your download location.
![section3_29](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image57.png)
6. Click `Open`.
7. Click the `Next` button.
8. Select `Replace all values` merge option.
9. Click the `Next` button. The import should complete successfully with 15 new data classes imported.
10. Click the `Go to task` button. You should see 15 new data classes to publish.
11. Click the `Publish` button.
12. Click the `Publish` button again without entering a comment.

Before proceeding, the Termination Code data class needs to be updated to use the Termination Lookup reference data set that was just created in the previous step as the matching criteria for the data class. The matching criteria definition for this data class could not be set in the CSV file that was used to import the data classes because the definition uses the reference data set's unique guid as the name for the reference data set which is different in every environment. This also provides an opportunity to learn how to set matching criteria for a data class to ensure that Knowledge Catalog will use it during the Metadata enrichment process.

1. Select the `Termination Code` data class from the list.
![section3_30](images/section3_30.png)
2. In the `Data matching` section, click the `Add button` to add a matching method. 
![section3_31](images/section3_31.png)
3. Select `Match to reference data` as the matching method.
4. Click the Next button.
![section3_32](images/section3_32.png)
5. Select `Termination Lookup` as the reference data set.
6. Change the `Percentage match threshold` option to ==60==.
7. Click the `Next` button.
![section3_33](images/section3_33.png)
8. Using the `Column data type` dropdown, select `Text`.
9. Enter 3 for the Minimum length of data value field.
10. Enter 3 for the Maximum length of data value field.
11. Click the `Next` button.
![alt text](images/section3_34.png)
12. Set the `Data class priority` to 12.
13. Click the `Save` button.
14. Click the `Publish` button.
15. Click the `Publish` button again without entering a comment.

#### 6. Create business terms
Business terms have references to data classes and classifications, and can be referenced in data governance and data protection rules, so they need to be defined after data classes and classifications but before data governance or data protection rules that reference them. Business terms can also be related to other business terms so they must be imported in a specific order. The business terms in the CSV import file you will use are in the correct order to establish these relationships.

You will import and create 150 business terms. Using the import process for such a large volume of governance artifacts is a prime example of the type of productivity automation that is provided by Knowledge Catalog. This is a huge time saver that runs in minutes. Doing this manually would take a data steward hours or days.

Goal:
- [ ] Import business terms from a CSV file

Steps:
1. Select the `Navigation` menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Governance` > `Business` terms menu.
![section3_35](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image68.png)
3. Using the `Add business term` dropdown, select `Import from file`.
4. Click the `Drag and drop file here or upload` link.
5. Select the `governance-business-terms.csv` file from the download location.
6. Click the `Open` button.
7. Click the `Next` button.
8. Select `Replace all values` as the merge option.
9. Click the `Next` button. The import should complete successfully with 29 new business terms imported.
10. Click the `Go to task` button. You should see 29 new business terms to publish.
11. Click the `Publish` button.
12. Click the `Publish` button again without entering a comment.

<h1 id="section4">4. Curate and enrich data assets</h1>
Now that there is a well defined business glossary established with a complete set of published governance artifacts, the data curation process can begin. Data curation is the process of discovering and adding data assets to a project or a catalog, enriching them by assigning classifications, data classes, and business terms, and analyzing and improving the quality of the data.

### 1. Create the Enrichment Project 
In this section, the project is created that will be used to create and execute the automated Metadata import and enrichment processes to discover and curate the data assets needed by the analytics project team before they are published to the governed Business catalog.

Goals: 
- [ ] Create a project in Data Studio
- [ ] Manage access control
- [ ] Adjust project settings

Steps: 
1. Select the `Navigation` menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Projects` > `All projects` menu.
![section4_01](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image168.png)
3. Click the `New project+` button.
4. Insert the text below into the `Name` field:
`Business Catalog Enrichment`
5. Add `Description`: This project is used to import and enrich the metadata for the data assets that will be published to the Business catalog that will be accessible to the analytics project team for analytics and AI tasks.
![section4_02](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image170.png)
6. Click the `Create` button.

#### Manage Access Control 
In order to manage data quality for the project, the Quality Analyst needs be added to the project with Edit authority.
1. Click the `Manage` tab.
![section4_03](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image171.png)
2. Select the `Access control` project menu.
3. Using the `Add collaborators` dropdown, select `Add users`.
![section4_04](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image172.png)
4. Enter the word 'quality' in the search area.
5. Select the checkbox next to the Quality Analyst user.
6. Using the Role dropdown, select `Admin` for the Quality Analyst user.
7. Click the `Add` button.
![section4_05](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image173-1.png)

#### Adjust Project Settings
The project **Metadata enrichment settings** are distinct to each project and apply to all metadata enrichment assets created in a project. They are available as global project settings that can be set prior to the creation and execution of metadata enrichment jobs. As a best practice, these settings should be reviewed and adjusted in advance of creating and running metadata enrichment jobs to ensure they will produce the most accurate results.
1. Select the `Metadata enrichment` settings project menu.
2. Scroll down until the `Term assignment` settings are at the top of the page.
3. In the Term assignment methods to use area, clear the `Machine learning` and  `Data-class-based assignments` check boxes. The only method that will be used and that wil remain selected is `Name matching`.
4. In the Select assets used for training built in model and adjustment area, select the `From Project` radio button.
5. Click the `Assets` tab.
![section4_06](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image173-2.png)

### 3. Import Platform Connections
The Administrator has connected the platform to DB2 and PostgreSQL databases. Your task as a data steward is to import the connections into the project.

Goal:
- [ ] Import connections to DB2 and PostgreSQl

Steps:
1. Click the `Assets` tab.
2. Click the `New asset +` button.
![section4_07](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image173.png)
3. Select the `Connect to a data source` task. Take some time to review the comprehensive list of data sources that we can connect to. Do you find data sources that are used in your organization?
<img width="1244" alt="image" src="images/section4_1.png" />

4. Enter the word `post` into the search area.
5. Select the `PostgreSQL` data source type from the left side panel.
6. Click the `Select a platform connection` tab.
7. Select the `PostgreSQL` platform connection radio button.
8. Click the `Next` button.
![section4_08](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image175.png)
9. Click the `Create` button.
10. Redo the steps to add `DB2 Warehouse` data sources
![section4_09](images/section4_09.png)

### 4. Import the Data Assets
This section uses the automated Metadata import tool to quickly and easily connect to data source connections to discover and add the data assets that are relevant to the enrichment project.

Goals:
- [ ] Import Employee table from DB2 Warehouse
- [ ] Import some tables from PostgreSQL

In this step, you will create the Metadata Import to import the Employee data asset from the Data Warehouse connection into the project.
1. Click the `New asset +` button.
![section4_10](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image177.png)
2. Select the `Prepare data` goal from the tools menu on the left.
3. Select the `Import metadata for data assets` tool.
![section4_11](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image181.png)
4. Select the `Discover` goal.
5. Click the `Next` button.
![section4_12](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image182.png)
6. Fill `Name` field: `Db2 Warehouse Import`
7. Fill `Description` field: `Discover and import the Employee data asset and associated metadata that were requested by the analytics project team that reside in the Db2 Warehouse data source`.
8. Click the `Next` button.
9. Select `This project (Business Catalog Enrichment)` as the target (it should be selected by default).
10. Click the `Next` button.
![section4_13](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image184.png)
11. Click the `Select connection` button.
12. Select the `Db2 Warehouse` connection from the Connections list on the left.
13. Select the `Arrow` on the `EMPLOYEE` schema. `Do not select the checkbox` next to the `EMPLOYEE` schema. Doing so will select all tables in the schema.
14. Select the checkbox for the `EMPLOYEE` table from the list.
15. Click the `Select` button.
![section4_14](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image186.png)
16. Click the `Next` button. 
17. Take the default Job name and leave the Run definition to Run after job creation. Click the `Next` button.
18. Take the default `Advanced options` that are selected for `Update on reimport`. Click the `Next` button.
19. Click the `Create` button.
![section4_15](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image190.png) The import process should run quickly. In a few seconds, you should begin seeing the import process adding the data assets you selected to the Imported assets list. You can click on the Refresh button at the top of the page to update the results.
20. When the import is complete, you should see a message at the top of the page: `Metadata import complete. 1 assets were imported successfully`. The data asset will appear in the Imported assets list and is now added to the project. Select the `Business Catalog Enrichment` project breadcrumb at the top of the page to get back to the project home page.
![section4_16](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image192.png)

In this step, you will create the Metadata Import to import the Warehouse data assets from the PostgreSQL connection into the project. 
1. Click the `New asset +` button.
2. Select the `Prepare data` goal from the tools menu on the left.
3. Select the `Import metadata for data assets` tool.
4. Select the `Discover` goal.
5. Click the `Next` button.
6. Fill `Name`: `PostgreSQL Import`
7. Fill `Description`: `Discover and import the Warehouse data assets and associated metadata that were requested by the analytics project team that reside in the PostgreSQL data source.`
8. Click the `Next` button.
9. Select `This project (Business Catalog Enrichment)` as the target (It should be selected by default).
10. Click the `Next` button.
11. Click the `Select connection` button.
12. Select the `PostgreSQL` connection from the Connections list on the left.
13. Enter the word 'warehouse' in the schema search area.
14. Select the Arrow on the WAREHOUSE schema. Do not select the checkbox next to the WAREHOUSE schema. Doing so will select all tables in the schema. This method shows you what tables are in the schema so you can see exactly what will be imported.
15. Select the checkbox next to the `WAREHOUSE_SHIFTS`, `WAREHOUSE_STAFF`, and `WAREHOUSE_STAFFING` tables.
16. Click the `Select` button.
![section4_17](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image194.png)
17. Click the `Next` button.
18. Take the default Job name and leave the Run definition to `Run after job creation`. Click the `Next` button.
19. Take the default `Advanced options` that are selected for `Update on reimport`. Click the `Next` button.
20. Click the `Create` button.
When the import is complete, you should see a message at the top of the page: `Metadata import complete. 3 assets were imported successfully.` The data assets will appear in the Imported assets list and are now added to the project.

### 5. Enrich the Data Assets
This section uses the automated Metadata enrichment tool provided by Knowledge Catalog to enrich the data assets that were discovered and imported during the Metadata import processes that was just completed. Metadata imports can be used as input into Metadata enrichment processes to automatically profile the data, analyze and assess data quality, and assign data classifications and business terms by leveraging governance artifacts defined in the business glossary.

Goal:
- [ ] Run metadata enrichment on imported tables.

Steps:
1. Inside the `Project`, click the `New Asset +` button.
2. Select the `Prepare data` goal from the tools menu on the left.
3. Select the `Enrich data assets with metadata` tool.
![section4_18](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image208.png)
4. Fill `Name`: `Business Catalog Enrichment`
5. FIll `Description`: `Enrich the metadata for all the data assets that are being published to the Business catalog for the analytics project team.`
6. Click the `Next` button.
![section4_19](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image209.png)
7. Click the `Select data from project` button.
8. Select the `Metadata Import` from the Asset types list on the left.
9. Select the high level checkbox in the Metadata Imports section to select all the metadata imports you just completed.
10. Click the `Select` button.
![section4_20](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image211.png)
11. Click the `Next` button.
12. Select the checkbox for the `Profile data` Enrichment objective.
13. Select the checkbox for the `Analyze quality` Enrichment objective.
14. Select the checkbox for the `Assign terms` Enrichment objective.
15. Click the `Select categories +` button.
![section4_21](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image213.png)
16. Select the checkbox next to the `[uncategorized]` category.
17. Select the checkbox next to the `Business` category.
18. Click the `Select` button.
![section4_22](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image214.png)
19. Select the `Basic` sampling method (it should be selected by default).
20. Click the `Next` button.
![section4_23](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image215.png)
21. Select `All data assets` for the Data scope of reruns option (it should be selected by default).
22. Click the `Next` button.
![section4_24](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image216.png)
23. Take a minute to review the metadata enrichment before creating it. The Data Scope will be analyzing 2 data assets (these are the 2 metadata imports that contain the 4 data assets that were just created) with an enrichment Objective to Profile data, Analyze quality and Assign terms across 5 Categories using the Basic sampling method. Click the `Create` button.
![section4_25](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image217.png)
24. Select the `Refresh` button to update the status and monitor the progress. Eventually a message will appear notifying you that the Metadata enrichment completed with a Refresh button.
25. Select the `Refresh` button.
26. Select the X in the top right corner of the `About this metadata enrichment` panel to close it to view the data asset enrichment status.
![section4_26](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image219.png)


### 6. Review Enrichment Result
Notice that data classes are not assigned at the asset level and that no business terms were assigned at the asset level. It is more important to have business terms automatically assigned at the column level, especially if business terms are being used to trigger data protection rule actions. Business terms at the data asset level are primarily for informational purposes. 
![section4_27](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image221.png)

**Click the Columns tab.**
Pay close attention to the data class assignments for these 5 columns: `Birth Date`, `Email`, `SSN`, `Fax` and `Work Phone` because we will implement data protection rules against those columns. These columns need to be assigned the correct data class.  If they are not, then set them to the proper data class in the screen shots below.
![section4_47](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image222.png)
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image223.png)
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image224.png)

ⓘ **Note: Metadata enrichment can be unpredictable.** This lab was tested many times over with the same results produced. If for some reason your results for the other non sensitive columns are different, don't worry about them and move on.

**Data Quality Assessment**
As noted when reviewing the data assets, the EMPLOYEE data asset has a quality score of 98.6 so it is inevitable that some of the column data quality scores are going to be below 100%. The Quality Analyst will be looking into data quality in more depth in an upcoming step but we can spend a few minutes to take a look at what columns are contributing to the lower quality score.
1. Scroll up to the top of the page.
2. Click the Data quality column header to sort the columns in descending order (Arrow pointing up).
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image225.png)
3.Select the high level checkbox to select all columns in the list.
4.Using the More action dropdown on the toolbar, select `Mark as reviewed`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image226.png)
5. Click the `Done` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image227.png)
6. Click the `Refresh` button in the top right corner of the message displayed. The Review status columns now has a check mark next to all the columns.
7. Click the `Assets` tab.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image228-2.png)


### 8. Rectify Enrichment Result
In this step, business terms will be added to all the Assets and primary key suggestions will be reviewed and accepted. Knowledge Catalog considers suggested metadata (business terms, data classes and primary keys) as missing so they are not considered during any decision making processes. Therefore, it is a best practice to review all suggestions and either remove or accept them.

Goals:
- [ ] Rectify EMPLOYEE data asset
- [ ] Rectify WAREHOUSE_STAFF data asset

**Rectify EMPLOYEE table**
1. Hover over the `Business terms` column of the `EMPLOYEE` asset, click the `View more` link that appears.
2. Click the `+` sign in the `Business terms` section of the `Governance` tab.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image228.png)
3. Select the checkbox next to the `Date of Birth` business term.
4. Select the checkbox next to the `Email` business term.
5. Select the checkbox next to the `Fax` business term.
6. Scroll down to the bottom of the list, Do not click the `Assign` button until you are instructed.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image229.png)
7. Select the checkbox next to the `Work Phone` business term.
8. Select the checkbox next to the `SSN` business term.
9. Click the `Assign` button. Multiple dialog boxes will appear with notification that the business terms were assigned.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image230.png)
10. Hover over the `Primary key` column of the `EMPLOYEE` asset, click the `View more` link that appears.
11. Scroll down in the `Key`s` tab of the right side panel.
12. Click the `Assign` button for the `EMPLOYEE_CODE` column in the `Keys` tab. A dialog boxes will appear notifying you that the primary key was assigned.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image231.png)

**Rectify WAREHOUSE_STAFF table**
1. Hover over the `Business terms` column of the `WAREHOUSE_STAFF` asset, click the `View more` link that appears.
2. Click the `+` sign in the `Business terms` section of the `Governance` tab.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image232-4.png)
3. Using the search area, enter the words 'skill'.
4. Select the checkbox next to the `Skill Set` business term.
5. Select the checkbox next to the `Skill Required` business term.
6. Select the checkbox next to the `Skill Experience` business term.
7. Click the `Assign` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image232-5.png)
8. Hover over the `Primary key` column of the `WAREHOUSE_STAFF` asset, click the `View more` link that appears.
9. Click the `Assign` button for the `EMPLOYEE_CODE` column in the `Keys` tab. A dialog boxes will appear notifying you that the primary key was assigned.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image232-6.png)

**Mark as Reviewed**
This completes the modifications you will make at the Asset level so the status of the Assets can be set to Reviewed. All assets now have a correct, meaningful and useful set of business terms and primary keys assigned that will provide additional information to help end users understand their content.
1. Select the high level checkbox to select EMPLOYEE and WAREHOUSE_STAFF in the list.
2. Using the `More` dropdown from the toolbar, select `Mark as reviewed`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image232.png)
3. Click the `Done` button.
4. Click the `Refresh` button in the top right corner of the message displayed.
5. The Review status columns now has a check mark next to all the assets indicating that they have been reviewed. Select the `Business Catalog Enrichment` breadcrumb at the top of the page to get back to the project home page.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image235.png)

<h1 id="section5">5. Catalog Governed Data</h1>

The data curation process is complete and the Data Steward is ready to create the governed catalog and publish the fully enriched data assets to the catalog so they are ready for use by the analytics project team to accomplish their data and AI analytical objectives.

### 1. Create the Knowledge Catalog
We will create a **governed** catalog, named `Business`. By governed, it means sensitive, confidential, or personally identifiable information (PII) is protected by data protection rules. We will create this rule in the next section, as a Privacy Steward.
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Catalogs` > `All catalogs` menu.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image317.png)
3. Click the `New Catalog +` button.
4. Fill the `Name` field: `Business`
5. Fill the `Description` field: `This catalog stores governed assets used by the business for analytical and AI projects.`
6. Select the checkbox to `Enforce data protection rules`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image319.png)
7. Click the `OK` button when asked to `Permanently enable rule enforcement?`.
8. Set the switch to `On` in the `Controls` section to `Alow reporting on asset metadata`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image321.png)
9. Click the `OK` button when asked to `Allow reporting on this catalog?`.
ⓘ Note: This setting is mandatory and needs to be set in order for the Data Steward and Quality Analyst to report on and query metadata for this catalog. Turning on this setting allows Knowledge Catalog to collect metadata about this catalog. It stores the metadata in the internal Db2 reporting database that was created at the beginning of the lab.
10. Keep the default option to `Update original assets` in the `Duplicate asset handling` section.
11. Click the `Create` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image322-2.png)
12. Click the `Access control` tab.
13. Using the `Add collaborators` dropdown, select `Add user group`.
14. Select `Viewer` for the access level. It should be selected by default.
15. Enter the wold 'all' in the Groups search area.
16. Select the `All users` group that appears.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image322-5.png)
17. Click the `Add` button.
18. Select the `Catalogs` breadcrumb at the top of the page to go back to the catalog home page.
19. Select the `Navigation` menu (the 4 stacked horizontal lines in the upper left corner).
20. Select the `Projects` > `All projects` menu.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image324.png)
21. Select the `Business Catalog Enrichment` project. 
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image325.png)

### 2. Publish Connections
In this section, the data source connections will be published one at a time, and in the order listed in the instructions below, to the governed Business catalog before any data assets are published. This will place them at the end of the Recently added featured assets category in the catalog, leaving room for the data assets to appear front and center, in order of importance, so they are easily found and viewable.

Goals:
- [ ] Publish Connection data asset to PostgreSQL into the catalog.
- [ ] Publish Connection data asset to DB2 into the catalog.

Steps:
1. Select the `X` in the top right corner of the information panel to close it.
2. From the `Assets types` section on the left, select `Data access` > `Connections`.
3. Select the checkbox next to the `PostgreSQL` connection.
4. Click the `Publish to catalog` button on the toolbar.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image327.png)
5. Make sure the `Business` catalog is selected. It should be selected by default because it is the only governed catalog the `Data Steward` has access to.
6. Select the `Next` button.
7. Fill the `Description` field: `PostgreSQL database that contains the warehouse data needed by the business for analytics and AI.`
8. Click the `Next` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image329.png)
9. Click the `Publish` button.
10. Select the checkbox next to the `Db2 Warehouse` connection.
11. Click the `Publish to catalog` button on the toolbar.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image331-1.png)
12. Make sure the `Business` catalog is selected. It should be selected by default.
13. Select the `Next` button.
14. Fill the `Description` field: `Db2 Warehouse database that contains employee data needed by the business for analytics and AI projects.`
15. Click the `Next` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image331-3.png)
16. Click the `Publish` button.

### 3. Publish Data Assets
In this section, the data assets will be publish to the Business catalog. Like connections, the data assets are published in a specific order, so that the Recently Added eatured assets category in the catalog gets populated properly. The WAREHOUSE data assets will get published first and the EMPLOYEE data asset will get published last.

Goals: 
- [ ] Publish WAREHOUSE_STAFF data asset
- [ ] Publish EMPLOYEE data asset

Steps: 
**Publish WAREHOUSE_STAFF**
1. Select the checkbox next to the `WAREHOUSE_STAFF` data asset.
2. Click the `Publish to catalog` button on the toolbar.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image336.png)
3. Make sure the `Business` catalog is selected. It should be selected by default.
4. Select the `Next` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image333.png)
5. Fill `Description` field: `All employee that work as staff members in the warehouse processing orders.`
6. Click the `Next` button.
7. Click the `Publish` button.

**Publish EMPLOYEE**
1. Select the checkbox next to the `EMPLOYEE` data asset.
2. Click the `Publish to catalog` button on the toolbar.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image339-4.png)
3. Make sure the `Business` catalog is selected. It should be selected by default.
4. Select the `Next` button.
5. Select the checkbox to `Go to the catalog after publishing it`.
6. Fill `Description`: `Official and current Employee master`.
7. Click the `Next` button.
8. Click the `Publish` button.

### 4. Augment DB2 Warehouse
In this section, additional metadata will be added to the cataloged data assets that were just published like classifications, related assets, tags, and reviews so data consumers can better understand and trust the data content and to contribute further to the knowledge base of the Knowledge Catalog search engine to make it easier for users to find what they are looking for.

In this step, classifications, related assets and tag metadata will be added to the Db2 Warehouse connection.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image347.png)

**Add Classifications**
1. Select the `Add classifications +` button in the `Classifications` section. Select the checkbox next to the `Sensitive Information classification`.
2. Select the checkbox next to the `Personal Information classification`.
3. Select the checkbox next to the `Personally Identifiable Information` classification.
4. Click the `Save` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image349.png)

**Add related assets**
1. Using the Add `related items` dropdown, select `Add related assets`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image350.png)
2. Select `Contains` as the relationship type.
3. Click the `Next` button.
4. Select the checkbox next to the `EMPLOYEE` asset.
5. Click the `Add` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image352.png)

**Add Tags**
1. In the `Tags` section of the `About this asset` panel, click the `Add` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image353.png)
2. Using the `Search tags` dropdown, select the `EMPLOYEE` tag.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image354.png)
3. Click the `Apply` button
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image355.png)

**Add Reviews**
1. Click the `Review` tab.
2. Click the `5th` star to the far right to assign a `5 Star` rating.
3. Fill the `Comments` area: `Contains all governed, trusted and quality data approved and published by the data governance team to use for analytical and AI projects. Some of the data is sensitive but data protection rules are in place to govern it`.
4. Click the `Submit` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image356.png)
5. Select the `Business` breadcrumb on the toolbar to get back to the asset list.

### 5. Augment Employee Metadata
1. Click the `EMPLOYEE` data asset from the asset list.
2. Scroll down the Overview section until the `Governance artifacts` section is at the top of the page.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image358-1.png)
**Add Classification**
3. Select the `Add classification +` button in the `Classifications` section.
4. Select the checkbox next to the `Sensitive Information classification`.
5. Select the checkbox next to the `Personal Information classification`.
6. Select the checkbox next to the `Personally Identifiable Information` classification.
7. Click the `Save` button.

**Add related assets**
1. Scroll down to the `Related items` section.
2. Using the `Add related items` dropdown, select `Add related assets.`
![images](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image360.png)
3. Using the search area, enter the word `related`.
4. Select `Is Related to` as the relationship type.
5. Click the `Next` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image361.png)
6. Select the checkbox next to the `WAREHOUSE_STAFF` asset.
7. Click the `Add` button.

**Add Tags**
1. Scroll down to the bottom of the `Overview` section to see the new `Related items` that were added.
2. Scroll down in the `About this asset` panel to the `Tags` section.
3. Click the `Edit` button (looks like a pencil) in the `Tags` section.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image363.png)
4. Using the `Search tags` dropdown, select the `WAREHOUSE` tag.
5. Click `Apply` button.

**Add Reviews**
1. Click the `Review` tab.
2. Click the 5th star to the right to assign a 5 Star rating.
3. Fill `Comments` area: `Contains governed and trusted employee data to use for business analytical projects. This is the full company employee record master. It contains sensitive and personal information, but the data governance office has defined data protection rules to govern that information.`
4. Click `Submit`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image366.png)
5. Select the `Business` breadcrumb on the toolbar to get back to the list.


<h1 id="section6">6. Define Policies and Rules</h1>

In this section, the governance policies and rules and the data protection rules will be created. Governance policies and rules were added to the `Data Privacy Artifacts` governance artifacts workflow definition so they will be sent for approval to the `Privacy Steward`. After approval, they will be automatically published to the business glossary.

### 1. Create governance policy
In this step, a governance policy will be created. This lab's use case only has one policy but will continue to use the import process to assign the appropriate business terms and classifications and then assign the governance and data protection rules to the policy in a subsequent step after they are created. As a reminder, Policies were added as a condition for the Data Privacy Artifacts governance artifact workflow definition so they will have to be reviewed and approved by the Privacy Steward. Once approved, they will be published to the business glossary.

Steps:
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Governance` > `Policies` menu.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image81.png)
3. Using the `Add policy` dropdown, select `Import from file`.
4. Click the `Drag and drop file here or upload` link.
5. Select the `governance-policies.csv` file from the download location.
6. Click the `Open` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image84.png)
7. Click the `Next` button.
8. Select the `Replace all values` merge option.
9. Click the `Next` button.
10. Click the `Go to task` button.
11. Click the `Send for approval` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image88.png)
12. Fill `Comment` field: `This policy describes the standards and guidelines for handling sensitive information. The data used in this project contains sensitive information so this policy must be published. This policy requires the Data Privacy teams approval. Please approve this policy.`
13. Click the `Send for approval` button. 
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image89.png)
14. Select the Notification icon on the toolbar to read the message.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image90-1.png)
This is only a courtesy informational message that there is a new Approve Governance Policy task and that no action needs to be taken. The approval will be done by the Privacy Steward.

### 2. Create governance rules 
Unlike data protection rules, governance rules are descriptive only rules and can't be enforced. A governance rule is a description of the criteria used to determine whether information assets are compliant with business objectives and provide the business definition of the required behavior or actions to be taken to implement a given governance policy or subject area such as information quality, retention, privacy, or regulatory compliance.

Steps: 
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Governance` > `Rules` menu.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image120.png)
3. Using the `Add rule` dropdown, select `Import from file`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image121.png)
4. Click the `Drag and drop file here or upload` link.
5. Select the `governance-rules.csv` file from the download location.
6. Click the `Open` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image123.png)
7. Click the `Next` button.
8. Select the `Replace all values` merge option.
9. Click the `Next` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image125.png)
The import should complete successfully with 4 new Governance rule drafts.
10. Click the `Go to task` button.
11. Click the `Send for approval` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image127.png)
12. Give comment: `The data for this project contains an employees Birth Date, Email Address, US Social Security Number (National Identifier) and Work Phone which must be protected per corporate policy. These rules need the Data Privacy teams approval. Please approve them.`
13. Click the `Send for approval` button.
14. Select the Notification icon on the toolbar to read the message.

### 3. Approve as the Privacy Steward
In order to approve the policy and governance rules in the next step, that were just sent for approval by the Data Steward, logout and login as the Privacy Steward.

**Approve Governance Rules**
Login to the system as the Privacy Steward. 
1. Select the link in the Notifications section to Approve governance rules.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image132-5.png)
As the Privacy Steward, read the comments left by the Data Steward and review the governance rules that have been sent for approval to ensure they meet corporate standards and guidelines based on the sensitivity of the data that was requested by the analytics project team.
2. Click the `Publish` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image132-6.png)
3. Give comment: `I have read the detailed comments and have reviewed the governance rules defined. All the proper rules have been defined. Based on these rules, a data protection rule must also be defined that takes action on these rule definitions. I approve this task!`
4. Click the `Publish` button. The `Governance rules` will be published with one task remaining to `Approve Policies`.

**Approve Governance Policy**
5. Click the Publish button.
6. Give `Comment`: `I have read the detailed comments and have reviewed the proposed governance policy. This is the approved standard corporate policy on how to handle and protect sensitive information that should be defined and published. I approve this task!`
7. Click the `Publish` button.

**Login back as Data Steward**
8. Click the user Avatar on the toolbar.
9. Select Log out from the menu.
10. Log in using username ans password of the data steward.
11. Check Policies and Rules that have just been published. 
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image132-17.png)

### 4. Create Data Protection Rules 
Data protection rules dynamically control access to data in governed catalogs. Data that is added from a governed catalog to a project will only be protected by data protection rules if the data was added to the governed cataloged by a deep enforcement solution.

Data protection rules are **automatically enforced in a governed catalog** when a catalog member attempts to view or act on a data asset in a governed catalog to prevent unauthorized users from accessing sensitive data. However, if the user who is trying to access the asset is the **owner of the asset** (by default, the user who created the asset), then access **is always granted**.

Goals:
- [ ] Create Date of Birth Rule
- [ ] Create Email Address Rule 
- [ ] Associate Rules to Policy 
- [ ] Approve Policy Changes

Steps:
**Create Date of Birth rule**
In this step, a data protection rule will be created to mask data classified as a Date of Birth. The Obfuscate masking method will be chosen and utilize some of the advanced data privacy options that are specific to a date of birth.
1. Using the `Add rule` dropdown, select `New data protection rule`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image132.png)
2. Fill `Name` field: `Protect Date of Birth`
3. Fill `Business definition` field: `Protect all birth dates using the data privacy advanced masking method.`
4. Click the `Next` button. 
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image133.png)
5. In the `When does this rule apply?` section, specify the rule `Criteria` as follows:
Using the If statement dropdown on the left, select `Data class`.
6. Using the If statement dropdown on the right, select `contains any`.
7. Enter the word 'birth' (in lower case) into the `Data class` field.
8. Select `Date of Birth` from the data class list that appears.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image134.png)
9. In the `What does this rule do?` section, specify the rule `Action` as follows:
Using the `Action` dropdown on the left, select `Obfuscate columns`.
10. Using the `When column has` dropdown in the middle, select `Data class`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image135.png)
11. Scroll down to the `Advanced masking options` section.
Using the `Date similarity` dropdown, select `Mask date to same time period`.
12. Select the `Same quarter` option. A sample of the obfuscation results will be displayed in the Example area.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image136.png)
13. Click the `Create` button.

The Advanced masking options for this rule should be set as follows:
| Advanced Option | Option Setting |
| --- | --- |
| Obfuscate method	| Preserve format (default) |
| Date Similarity	| Mask date to same time period with Same quarter option |
| Reversibility	| Irreversible masking |
| Consistency	| Repeatable |
| Input Validation	| Selected and enabled |  

![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image137.png)
14. The `Where are data protection rules enforced?` dialog appears. This dialog will appear every time you create a data protection rule. Read the message and select the `I understand` checkbox.
15. Click the `Continue` button.
16. Select the `Rules` breadcrumb in the upper left corner to return to Rules main page.

**Create Email Address rule**
1. Using the `Add rule` dropdown, select `New data protection rule`.
2. Fill `Name` field: `Protect Email Addresses`
3. Fill `Business definition` field: `Protect all email addresses using the data privacy advanced masking method.`
4. Click the `Next` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image140.png)
5. In the `When does this rule apply?` section, specify the rule `Criteria` as follows:
Using the If statement dropdown on the left, select `Data class`.
6. Using the If statement dropdown on the right, select `contains any`.
7. Enter the word 'email' (in lower case) into the `Data class` field.
8. Select `Email Address` from the data class list that appears.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image141.png)
9. In the `What does this rule do?` section, specify the rule `Action` as follows:
Using the Action dropdown on the left, select `Obfuscate columns`.
10. Using the `When column has` dropdown in the middle, select `Data class`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image142.png)
11. Scroll down to the `Advanced masking options` section.
In the `Domain name` section, select the `Custom` option.
12. Enter `cpd.ibm.com` for the `Custom` domain name.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image143.png)
13. Click the `Create` button.

The Advanced masking options for this rule should be set as follows:
| Advanced Option | Option Setting |
| --- | --- |
| Obfuscate method	| Preserve format (default) |
| Username format	| Generate user name |
| Domain name	| Custom - cpd.ibm.com |
| Consistency	| Repeatable |
| Input Validation	| Selected and enabled |  

![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image144.png)

14. The `Where are data protection rules enforced?` dialog appears. This dialog will appear every time you create a data protection rule. Read the message and select the `I understand` checkbox.
15. Click the `Continue` button.
16. Select the `Rules` breadcrumb in the upper left corner to return to Rules main page.

**Associate Rules to Policy**
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Governance` > `Policies` menu.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image161-1.png)
3. Select the `Protection of Sensitive Personal Information` policy.
4. Scroll down to the `Rules` section. Click the `Add rules +` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image162.png)
5. Select the checkbox next to the `All Birth Dates Must be Protected` rule.
6. Select the checkbox next to the `All Email Addresses Must be Protected` rule.
7. Select the checkbox next to the `All National Identifiers Must be Protected` rule.
8. Select the checkbox next to the `All Phone Numbers Must be Protected` rule.
9. Click the `Add` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image163.png)
10. Click the `Add data protection rules +` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image164.png)
11. Select the checkbox next to the `Protect Date of Birth`rule.
12. Select the checkbox next to the `Protect Email Addresses` rule.
13. Select the checkbox next to the `Protect US Phone Numbers` rule.
14. Select the checkbox next to the `Protect US Social Security Numbers` rule.
15. Click the `Add` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image165.png)
16. Click the `Send for approval` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image166.png)
17. Give comment: `The data protection rules have been created as required and the governance and data protection rules have been assigned to the policy for everyone to easily understand and adhere to them. Please approve and publish these changes.`
18. Click the `Send for approval` button.

**Approve Policy Changes**
Log out from Data Steward account and login as the Privacy Steward. 
1. Select the link in the `Notifications` section to `Approve Policy Personal and Sensitive Information`.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image167-8.png)
2. Click the `Publish` button.
3. Give comment: `Thank you for adding the data protection rules as instructed and for adding all the rules to the policy for everyone to understand and comply with. I trust your changes and approve this task!`
4. Click the `Publish` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image167-10.png)
5. Log in back as the Data Steward and see the changes in `Protection of Personal and Sensitive Information` Policy.

**Explore Relationship**
1. Click the `Explore Relationships` button from the policy.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image167-18.png)
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image167-22.png)
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image167-25.png)


<h1 id="section7">7. Manage Data Quality </h1>

In this section, the Quality Analyst will review the metadata enrichment data quality results produced during the Metadata enrichment by the Data Steward, develop a data quality definition, create a data quality rule, evaluate the quality rule results, and assess data quality SLA rule compliance by implementing a data quality analysis and monitoring process.

First, **Login as the Quality Analyst.**

### 1. Review the Quality Results
In this step, the Quality Analyst will review the metadata enrichment data quality results produced during the Metadata enrichment process.
Steps:
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the `Projects` > `All projects` menu.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image241.png)
3. Select the `Business Catalog Enrichment` project.
4. Click the `Asset` tab.
5. Select the `Business Catalog Enrichment` Metadata Enrichment asset.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image243.png)
The Quality Analyst will focus on the EMPLOYEE data asset because it has the lowest quality score of 98.6% and all the other WAREHOUSE data assets have a quality score of 100%.
6. Select the `X` in the top right corner of the `About this metadata enrichment` panel to close it and gain more real estate.
7. Hover over the `Data quality` column of the `EMPLOYEE` asset, click on the `Data quality score` link when it appears.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image244.png)
8. Click the `Focus and percentage of data with issues` column header twice to sort the dimensions in descending order (arrow pointing down).
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image245.png)
9. Scroll down to see all the data quality checks.
The primary contributing reasons for the lower data quality score is due to Suspect values with 9.4% of values in violation and Unexpected duplicated values with much lower 2.5% of values in violation. The duplicate values are not a big concern because Employee's can live in the same state and zip code and can even have the same work phone extension across different locations, but the suspect values is an indication that the column has not met the columns data classification matching criteria when it was profiled during the enrichment processLet's so we can drill down to the column data quality statistics to take an even closer look.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image246.png)
10. Click the `Columns` tab.
11. Click the `Score` column header once to sort the dimensions in ascending order (arrow pointing up).
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image247.png)
12. Click the X in the top right corner of the `Data quality` details dialog to close it.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image248.png)
13. Select the `Business Catalog Enrichment` breadcrumb at the top of the page to go back to the project home page..

### 2. Add DB2 Connection
Before proceeding with the following data quality tasks, the internal Db2 database platform connection that was created earlier needs to be added to the project so the Quality Analyst can select it as the external output destination to create the data quality exception table that will store data quality exception records during the creation of the data quality rule.

Steps: 
1. Click the `New asset +` button.
2. Select the `Prepare data` goal from the tools menu on the left.
3. Select the `Connect to data source` task.
4. Enter the word db2 into the search area.
5. Select the IBM Db2 data source type from the left side panel.
6. Click the Select a platform connection tab.
7. Select the Db2 Database platform connection radio button.
8. Click the Next button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image252.png)
9. Click the Create button.


### 3. Create Data Quality Definition
A data quality definition is like a blueprint that uses logical expressions to describe what the data should look like or how often it should occur. These logical expressions follow a basic syntax where a variable, such as a word or term, is evaluated based on a specified condition or type of check. The Quality Analyst decides to create a data quality definition for proper US Zip code values. It can be created directly from the data asset by following a specific path.

Steps:
1. Select the `EMPLOYEE` data asset.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image254.png)
2. Click the Data Quality tab.
3. Select the X in the top right corner of the About this asset panel to close it and gain more real estate.
4. Scroll down to the Data quality checks section.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image255.png)
5. Using the Create data quality check dropdown, select Create data quality definition.
6. Fill `Name` : ` US Zip Code Validation`
7. Fill `Description` : `Ensure that US zip codes are properly formatted.`
8. Using the Data quality dimension dropdown, select Validity.
9. Click the Next button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image257.png)
10. Fill `Rule expression` field: `ZIP MATCHES_FORMAT '99999'`
11. Click the Create button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image258.png)
12. Close the new tab that just opened up in your browser.
13. Go back to the original tab in your browser that launched the new tab.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image259.png)
14. Select the `Business Catalog Enrichment` breadcrumb at the top of the page to go back to the project home page.
15. Select the `US Zip Code Validation` data quality definition.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image261.png)

### 4. Create Data Quality Rule
In this step, a data quality rule will be created from the data quality definition. Data quality rules link the logical variables in a definition to the actual data to evaluate and validate the conditions specified in the definition. Each rule run outputs statistics and information about potential exceptions in the rule's output table.

Steps:
1. Click the Create rule + button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image264.png)
2. Fill `Name` field: Validate Zip Codes
3. Fill `Description` field: Ensure that zip codes follow the US zip code format.
4. Click the `Next` button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image265.png)
5. Click the Select column + button under the Bind to column for the zip row to select the column in the data set to bind to Zip Code.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image266.png)
6. Select the EMPLOYEE data asset.
7. Scroll down the list of columns and select radio button next to the ZIP_CODE column.
8. Click the Select button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image267.png)
9. Click the Next button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image268.png)
10. Click the Next button.
11. Click the Next button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image270.png)
12. Toggle the output switch to External.
13. Select the radio button to Write to a new database table in the Output section.
14. Using the Connection dropdown, select Db2.
15. Using the Schema dropdown, select DB2INST1
16. Fill `Table` field: DQ_ZIP_RECORDS
17. Scroll down to the Output content section.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image271.png)
18. Using the Add content output dropdown, select Columns.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image272.png)
19. Select the EMPLOYEE data asset.
20. Click on the Slider and drag it to the right to see the full column names.
21. Select the checkbox next to the EMPLOYEE_CODE column.
22. Select the checkbox next to the STATE_CODE column.
23. Click the Select button. 
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image273.png)
24. Click the Next button.
25. Click the Test button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image275.png)
There are 4 invalid Zip Codes with a value of 2124 which is an invalid format for a US zip code. It appears that the first digit should be a zero and the actual values should be 02124. We know this because the STATE_CODE is provided in the output content and all 4 rows in error are employees in the state of Massachusets (MA), and with a little research, 02124 happens to be the zip code for Boston Massachusets. These rows can now be fixed because the EMPLOYEE_CODE was included in the exception record content so the rows can be easily identified and corrected.
26. Select the X in the top right corner to close the test rule dialog.
27. The test results were enlightening and satisfactory and provided the information needed to remediate the bad zip code values for 4 rows in the EMPLOYEE table so the rule can now be created. Click the Create button.

ⓘ Notice: That a DataStage flow was created in addition to the Data Quality Definition and the Data Quality Rule. The flow was created when the data quality rule was tested to write the exception records to the Db2 database table so Knowledge Catalog could present the results. This is provided by the Enterprise Plus version of DataStage (which is installed in this environment).
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image278.png)

### 5. Create Data Quality SLA Rule
Data quality SLA rules apply to data assets in projects and must be activated for each project separately in the metadata enrichment settings. They are evaluated during metadata enrichment when data quality checks are run, or when data quality rules are run.

Steps:
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the Governance > Rules menu.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image291.png)
3. Using the Add rule dropdown, select New data quality SLA rule.
4. Fill `Name` field: Validate US Zip Codes
5. Fill `Business definition` field: Records that contain US Zip Code values must be correctly formatted.
6. Click the Next button
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image293.png)
7. Using the Any data asset dropdown, select with one of the business terms.
8. Enter the word zip into the business term search area.
9. Select Zip Code from the business term list that appears.
10. Click the Add quality criteria + button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image294.png)
11. Using the must have a dropdown, select validity dimension score.
12. Keep the default equal to or greater than threshold of 100%.
13. Click the Add subcondition + button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image295.png)
14. Using the any column within dropdown, select with one of the business terms.
15. Enter the word zip into the business term search area, select Zip Code from the business term list that appears.
16. Using the must have a dropdown, select validity dimension score.
17. Keep the default equal to or greater than threshold of 100%.
18. Click the Select + button for the Remediation task.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image296.png)
19. Select the Data Quality SQL Rule Remediation workflow.
20. Click the Select button.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image297.png)


### 6. Activate SLA Rule Monitoring
The SLA rule is applied whenever a team member runs metadata enrichment on the data assets that meet the specified criteria, or a data quality rule on such data assets. The remediation task is triggered automatically and assigned by default to the data asset owner. Data quality SLA rules are global, and apply to all projects for which SLA rule monitoring is activated in the metadata enrichment settings.

Steps:
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
2. Select the Projects > All projects menu.
3. Select the Business Catalog Enrichment project.
4. Click the Manage tab.
5. Select Metadata enrichment from the left side settings menu.
6. Scroll down to the SLA rule section.
7. Click the Activate monitoring switch and toggle it to the On position. I will turn green and the label will read Data quality SLA rules active.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image301.png)
8. Click the Assets tab.
9. From the Assets types section on the left, select Metadata enrichments > Metadata Enrichments.
10. Select the Business Catalog Enrichment metadata enrichment.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image302.png)
11. Using the Ellipses... menu, select Enrich all assets.
![image](https://cp4d-outcomes.techzone.ibm.com/img/l4-pox/knowledge-catalog/image303.png)
12. Select the X in the top left corner of the About this metadata enrichment panel to close it.
13. Click the Refresh button to update the status.
14. Click the Refresh button in the notification message.

<h1 id="section8">8. About IBM Knowledge Accelerator </h1>



