This is a test project to generate liquibase change-logs with 
liquibase maven plugin from diff between database and JPA(Hibernate) entities

First step is installing the jar in local maven repo. Call
mvn clean install
in <project root>

This step is important because the liquibase plugin has a dependency to this project artefact.
This project contains the class   
de.zebrajaeger.liquibaseconfigtest.PhysicalNamingStrategyImpl   
that modifies the generated names of hibernate to match the required names in the liquibase changeLog.   

Now you can change the JPA model a little bit in    
de.zebrajaeger.liquibaseconfigtest.persistence.model

To create a diff go to <project root> and call    
mvn clean compile liquibase:diff 

The result occurs in <project-root>\src\main\resources\liquibase-diff-changeLog.xml

After copying the changes to liquibase-changeLog.xml the start of the application   
de.zebrajaeger.liquibaseconfigtest.LiquibaseConfigTestApplication
should be fine

