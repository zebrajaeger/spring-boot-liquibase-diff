Spring Boot Liquibase Diff
==========================

This is a simple project as demonstration how to generate liquibase change-logs with 
liquibase maven plugin from diff between database and JPA(Hibernate) entities without
writing changelocks manually.

Overview
-----------------
The project consists of two components.
* The App itself
* A Tool project that helps us to generate the changelock with the correct spelling for tables and columns

Prepare / Install
-----------------
First step is installing the jar in local maven repo. Call  
*mvn clean install*   
in &lt;project root&gt;

This step is important because the liquibase plugin has a dependency to the  Tools 
project artefact.

Second step is installing ans starting Postgres DB. Use the shell or pgAdmin Tool to create a new 
database with the name   
*liquibase-test* 

Optional: Change model
--------------------- 
Now you can change the JPA model a little bit in    
de.zebrajaeger.liquibaseconfigtest.persistence.model

Create Diff
------------
To create a diff go to   
*&lt;project root&gt;/app*   
 and call    
*mvn clean compile liquibase:diff* 

This compiles the classes inclusive the model classes (important!) and creates the diff.

The result occurs in &lt;project-root&gt;/app/src/main/resources/liquibase-diff-changeLog.xml

Update App
----------
After copying the changes to liquibase-changeLog.xml (and deletion of  liquibase-diff-changeLog.xml) 
the start of the application class       
*de.zebrajaeger.liquibaseconfigtest.LiquibaseConfigTestApplication*   
should be fine

