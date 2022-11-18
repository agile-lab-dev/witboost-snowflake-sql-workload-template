# Snowflake SQL workload template

Use this template to automatically load a SQL file that performs a transformation of data in a Snowflake instance. This transformation will be triggered by a MWAA orchestrator so be sure to also add that component to the Data Product after this one. 

## Using the template

### Prerequisites

A Data Product should already exist in order to attach the new components to it.

---

### Component basic information

This section includes the basic information that any Component of Data Mesh Boost must have

- Name: Required name used for display purposes on your Data Product
- Fully Qualified Name: Workload fully qualified name, this is optional as will be generated by the system if not given by you
- Description: A short description to help others understand what this Workload is for.
- Domain: The Domain of the Data Product this Workload belongs to. Be sure to choose it correctly as is a fundamental part of the Workload and cannot be changed afterwards.
- Data Product: The Data Product this Workload belongs to, be sure to choose the right one.
- Identifier: Unique ID for this new entity inside the domain. Don't worry to fill this field, it will be automatically filled for you.
- Development Group: Development group of this Data Product. Don't worry to fill this field, it will be automatically filled for you.
- Depends On: If you want your workload to depend on other components from a Data Product, you can choose this option (Optional).
- Reads From: This is filled only for DataPipeline workloads, and it represents the list of output ports or external systems that is reading (Optional).

*Example:*

**Name:** Snowflake SQL Workload

**Description:** Uploads the transformation SQL file to calculate COVID per day recoveries 

**Domain:** domain:marketing

**Data Product:** system:marketing.covidrecoveries.0

***Identifier:*** Will look something like this: *marketing.covidrecoveries.0.snowflake-sql-workload*

***Development Group:*** Might look something like this: *group:dataanalysis* Depends on the Data Product development group 

---

### SQL file Details

- Snowflake SQL file name: The name of the .sql file located in the artifacts/ folder of the component, you can choose the name of your .sql file but it must be saved in the artifacts/ folder in order for the component to recognize it.

*Example:*

**Source name:** snowflake.sql

---

### Choose a location

Every component needs a host where the generated code will be saved. The default is `gitlab.com`. Refer to your team to understand the structure on how to use your repository to save this components.

- Host: The host where the repository will be created. By default is `gitlab.com`
- User/Group: A group or a user that the repository belongs to, e.g. 'group/sub-group/sub-sub-group' or 'name.surname'. There are two ways of creating a new component. One way of creating it is by making a monorepo (in that way you will never change the field 'Repository' and it will always be a repository containing your data product and you will only need to change the root directory). The second way of creating a new component is by doing it always in another repository (in that case the root directory will always be '.' and you will always change the repository field).
- Repository: The name of the repository
- Root Directory: The path that will be used as the repository root for this component. For monorepos this will be different for each component.

*Example:*

***Host:*** gitlab.com

**User/Group:** MyCompany/Sandbox

**Repository:** AirbyteSandboxComponent

**RootDirectory:** .

After this the system will show you the summary of the template and you can go back and edit or go ahead and create the Component. After clicking on "Create" the registering of the Component will start. If no errors occurred it will go through the 3 phases (Fetching, Publishing and Registering) and will give you the links to the newly created Repository and the component in the Catalog.