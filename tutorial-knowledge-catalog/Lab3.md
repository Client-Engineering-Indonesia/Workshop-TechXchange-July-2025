<h1 id="section1">1. Define the Business Vocabulary</h1>
This section creates the category and business term governance artifacts needed to establish a business ready governance foundation. Knowledge Catalog can use a pre-defined CSV file to import and create the business terms.

It is essential to establish the business vocabulary first before any data curation, enrichment and cataloging of data assets takes place. This is because governance artifacts, like data classes and business terms, can be automatically assigned to data assets during metadata enrichment and cataloging. If not, all of those tasks would have to be done manually, which defeats taking advantage of the automated and built-in data governance capabilities of Knowledge Catalog.

#### 1. Create Categories
Categories act as folders or directories to organize governance artifacts and provide access controls to authorize who can author and manage those artifacts. Categories provide the logical structure for all governance artifacts, except data protection rules. You group governance artifacts in categories to make them easy to find and manage, and to control their visibility. Categories can be organized in a hierarchy based on their meaning and relationships to one another. A category can have subcategories, but a subcategory can have only one direct parent category.

In this section, one category will be created that will provide the logical structure for the governance artifacts defined in this lab.

Goal: 
- [ ] Create categories 

Steps: 
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
![section1_1](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image24.png)

2. Select `Governance` > `Categories` from the menu.
![section1_2](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image25.png)

3. Using the `Add category` dropdown, select `New category`.
![section1_3](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image26.png)

4. In the `Name` field put `Employee`

5. In the  `Description` field put `Data governance artifacts related to employees of the company`
![section1_4](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image27.png)

6. Open the `Advanced settings` section. Under `Access controls`, set the `Allow reporting on governance artifacts` switch to `On`.

7. Click the Create button.
![section1_5](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image27.png)

The new category is created and opened for review with the `Name`, `Description` and `Reporting` access control setting that was supplied during creation.

![section1_6](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image28.png)

#### 2. Create Business Terms
Business terms can reference data classes and classifications and can be referenced in governance and data protection rules so they need to be imported after data classes and classifications but before importing or creating governance or data protection rules. Business terms can also be related to other business terms so they must be imported in a specific order. The business terms in the CSV file provided are in the correct order to establish these relationships.

This is a significant time saver that runs in minutes. ***Doing this manually would take a data steward hours or days.***

Goals:
- [ ] Create categories by importing the CSV file containing the list of categories.

Steps:
1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
![section2_1](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image29.png)

2. Select the `Governance` > `Business terms` menu.
![section2_2](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image30.png)

3. Using the `Add business term` dropdown, select `Import from file`.
![section2_3](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image31.png)

4. Click the `Drag and drop file here or upload` link.
![section2_4](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image32.png)

5. Select the `governance-business-terms.csv` file from the download location.
6. Click the `Open` button.
![section2_5]https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image33.png

7. Click the `Next` button
![section2_6](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image34.png)

8. Select `Replace all values` as the merge option.

9. Click the `Next` button.
![section2_7](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image35.png)

10. Click the `Go to` task button.
![section2_8](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image36.png)

11. Click the `Publish` button.
![section2_9](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image37.png)

12. Click the `Publish` button again without entering a comment.
![section2_10](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image38.png)

13. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
![section2_11](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image39.png)

14. Select `Governance` > `Business terms`.
![section2_12](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image40.png)

Scroll down to the bottom of the business term page
![section2_13](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image41.png)

<h1 id="section2">2. Create Data Protection Rules</h1>

Data protection rules are automatically enforced in a governed catalog when a catalog member attempts to view or act on a data asset in a governed catalog to prevent unauthorized users from accessing sensitive data. However, if the user who is trying to access the asset is the owner of the asset (by default, the user who created the asset), then access is always granted.

This section creates two data protection rules that are enforced based on the data class assigned to columns of data assets. The rules will dynamically mask data values for data assets residing in governed catalogs, projects (if the data asset was added from a governed catalog), and virtualized data (if the data protection option is enabled) for the following sensitive information:

- Email Address
- US Social Security Number

1. Select the Navigation menu (the 4 stacked horizontal lines in the upper left corner).
![section3_1](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image42.png)

2. Select `Governance` > `Rules`.
![section3_2](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image43.png)

Goals:
- [ ] Create Email Address Rule
- [ ] Create US Social Security Rule

#### 1. Create Email Address Rule

Steps: 
1. Using the Add rule dropdown, select New data protection rule.
![section3_3](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image44.png)
2. In the `Name` field put `Protect Email Addresses`
3. In the `Business definition` field put `Protect all email addresses using the data privacy advanced masking method`.
4. Click the `Next` button
![section3_4](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image45.png)

In the `When does this rule apply?` section specify the rule `Criteria` for `Condition 1` as follows:
5. Using the `If` statement dropdown on the left, select `Data class`.
6. Using the `If` statement dropdown on the right, select `contains any`.
7. Type the word `email` into the `Data class` field.
8. Select `Email Address` from the data class list that appears. It should be the first entry in the list.
![section3_5](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image46.png)

In the `What does this rule do?` section specify the rule `Action` as follows:
9. Using the `Action` dropdown on the left, select `Obfuscate columns`.
10. Using the `When column has` dropdown in the middle, select `Data class`.

The `Email Address` data class will automatically be filled into the `That contains any` field. Scroll `down` to the `Advanced masking options` section.

![section3_6](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image47.png)

The default `Advanced masking` options set by `Knowledge Catalog` are the correct options for this data protection rule. They should be set as follows:

| Advanced Option | Option Setting |
| --- | ---  | ---    |
| Obfuscate method | Preserve format (default) |
| Username format | Generate user name |
| Domain name| Original | 
| Reversibility | Irreversible masking |
| Consistency | Repeatable |
| Input Validation | Selected and enabled |

Double check that the options are set correctly. If they are not, change them to the proper setting listed above before you create the rule.

11. Click the `Create` button.
![section3_7](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image48.png)

The `Where are data protection rules enforced?` dialog appears. This dialog will appear every time you create a data protection rule.

12. Read the message and select the `I understand` checkbox.
13. Click the `Continue` button
![section3_8](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image49.png)

A Successfully created! message will appear and the new rule is created.

14. Select the `Rules` breadcrumb to return to the rules main page
![section3_9](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image50.png)

#### 2. Create US Social Security Rule
This step creates a data protection rule to mask data classified as a US Social Security Number. It uses the `Obfuscate` masking method using the advanced data privacy options that are specific to a United States social security number.

1. Using the `Add rule` dropdown, select `New data protection rule`.
![section4_1](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image51.png)

2. In the `Name` field put `Protect US Social Security Numbers`
3. In the `Business definition` field put `Protect all US social security numbers using the data privacy advanced masking method`.
4. Click the `Next` button
![section4_2](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image52.png)

In the `When does this rule apply?` section specify the rule `Criteria` for `Condition 1` as follows:
5. Using the `If` statement dropdown on the left, select `Data class`.
6. Using the `If` statement dropdown on the right, select `contains any`.
7. Type the word `social` into the `Data class` field.
8. Select `US Social Security Number` from the data class list that appears. It should be the first entry in the list.
![section4_3](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image53.png)

In the `What does this rule do?` section specify the rule `Action` as follows:
9. Using the `Action` dropdown on the left, select `Obfuscate columns`.
10. Using the `When column has` dropdown in the middle, select `Data class`.

The `US Social Security Number ` data class will automatically be filled into the `That contains any` field. Scroll `down` to the `Advanced masking options` section.
![section4_4](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image54.png)

The default `Advanced masking` options set by `Knowledge Catalog` are the correct options for this data protection rule. They should be set as follows:

| Advanced Option | Option Setting |
| --- | ---  | ---    |
| Obfuscate method | Preserve format (default) |
| Username format | Generate user name |
| Domain name| Original | 
| Reversibility | Irreversible masking |
| Consistency | Repeatable |
| Input Validation | Selected and enabled |

Double check that the options are set correctly. If they are not, change them to the proper setting listed above before you create the rule.

11. Click the `Create` button.
![section4_4](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image55.png)

The `Where are data protection rules enforced?` dialog appears. This dialog will appear every time you create a data protection rule.

12. Read the message and select the `I understand` checkbox.
13. Click the `Continue` button
![section4_5](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image56.png)

A Successfully created! message will appear and the new rule is created.

14. Select the `Rules` breadcrumb to return to the rules main page.
![section4_6](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image57.png)

`Two` new data protection rules should now be visible. These new rules now adhere to the governance rules defined by the business to protect all National Identifiers (i.e. US Social Security Numbers) and Email Addresses.

![section4_7](https://cp4d-outcomes.techzone.ibm.com/img/data-fabric-lab/knowledge-catalog/image58.png)

