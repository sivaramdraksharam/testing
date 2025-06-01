# testing
Manual and automation testing guidelines

References:

Study software metrics: https://drive.google.com/file/d/1mvZVIbczssdEI52OUT4Q-HhOY6Vjvm0a/view?usp=sharing

java simple programs testing (Unit testing) : https://medium.com/geekculture/unit-testing-of-simple-java-programs-b785a164b440

Topics
------
1. What is Selenium? Selenium can automate browser. It supports most of the languages and browsers as well.
2. What is driver? Selenium directly can not interact with a browser. It requires driver.
3. Types of locators
4. Interactions with input fields
5. Interactions with buttons

Day-1
------
1. How to launch the browser?
   Steps:
   a. Create Maven project
   b. Open pom.xml
   c. Add <dependencies></dependencies> to pom.xml
   d. Add selenium dependency
   e. Add testng dependency
   f. <scope>test</scope> need to be removed from pom.xml as it restricts testing scope for only that folder
   g. create a package com.satyam.lambdatestdemo under src/test/java
   h. Create 'LaunchBrowser' class inside the above package
   i. create a method public void myTest(){System.out.println("Hello World");} inside that class
   j. annotate with @Test
   k. rightclick--> Run As--> TestNG test
   l. allow Eclipse IDE for access
   m. watch the output


   

   



