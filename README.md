Prerequisite: Annotations: https://github.com/sivaramdraksharam/Fullstack-Training/tree/8afda5c99334463fdbb7dd848a415b9094f6571e/mybuiltinannotations
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
Inside myTest() try the following code:
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.Test;
public class LaunchBrowser
{
	@Test
	public void myTest()
	{
		System.setProperty("webdriver.chrome.driver",".drivers/chromedriver.exe");//download appropriate driver and copy  it in drivers folder
	Webdriver driver=new ChromeDriver();//instantiate driver
	driver.get("https://www.lambdatest.com/");//open a web site
	String title=driver.getTitle();
	System.out.println(title);
	driver.quit();
	}
}
//rightclick-->run as-->TestNG class

Day-3
-----
//Running test on cloud machine - comment the driver in day1 code
//creare setup() method in LaunchBrowser class as follows:

class LaunchBrowser{

//create RemoteWebDriver
RemoteWebDriver driver;

//annotate with @BeforeTest
@BeforeTest
public void setup()
{
	DesiredCapabilities capabilities = new DesiredCapabilities();
 	capabilities.setCapability("build", "your build name");
  	capabilities.setCapability("name", "your name");
   	capabilities.setCapability("platform" , "windows 11");
    	capabilities.setCapability("browserName", "Chrome");
     	capabilities.setCapability("version", "137.0");
        try{
	driver = new RemoteWebDriver(new URL("loginpage or any url", capabilites));
 	}catch(MalformedURLException e){
  		e.printStackTrace();
	}
}

@AfterTest
public void tearDown()
{
      driver.quit();
}

----------------------------------
==================================
To test a simple web application using Selenium, you'll typically follow these steps:
 1) Set up Selenium WebDriver and a browser driver (like ChromeDriver for Chrome). 
2) Write a Selenium script in a programming language (e.g., Java, Python) to navigate to the web page, locate elements, and perform actions.
 3) Run the script and verify the expected outcomes.

1. Prerequisites:
•	Selenium WebDriver:
Download and install Selenium WebDriver, which allows your script to control the browser. 
•	Browser Driver:
Download the appropriate browser driver for your chosen browser (e.g., ChromeDriver for Chrome, GeckoDriver for Firefox). Ensure the driver is compatible with your Selenium WebDriver version. 
•	Programming Language:
Choose a programming language (like Java, Python) and set up your development environment with the necessary libraries. 
2. Writing the Selenium Script:
•	Initialize WebDriver:
Create an instance of the desired browser driver (e.g., WebDriver driver = new ChromeDriver();).
•	Navigate to the Page:
Use the driver.get() method to navigate to the URL of the web application.
•	Locate Elements:
Identify and locate the web elements you need to interact with (e.g., input fields, buttons) using locators like id, name, xpath, or css_selector.
•	Perform Actions:
Use Selenium methods to interact with the elements (e.g., driver.findElement(By.id("username")).sendKeys("testuser") to enter text into a username field).
•	Verify and Validate:
Use assertions (e.g., assertEquals()) to verify that the application behaves as expected after each action. 
3. Running the Script:
•	Execute the Script:
Run your Selenium script using your programming language's environment (e.g., from an IDE or command line).
•	Inspect Results:
Observe the browser's behavior as the script executes. Check if the actions were performed correctly and if the expected outcomes are achieved. 
Example (Python):
Python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time
# Set up Chrome driver
driver = webdriver.Chrome()

# Navigate to the web page
driver.get("http://example.com")

# Locate an element
search_box = driver.find_element(By.ID, "search")

# Perform an action (e.g., type in the search box)
search_box.send_keys("Selenium tutorial")
search_box.send_keys(Keys.RETURN)

# Wait for the results to load
time.sleep(2)

# Verify that the results page is displayed
results = driver.find_elements(By.CSS_SELECTOR, "h3.r")
assert len(results) > 0

# Close the browser
driver.quit()
4. Best Practices:
•	Clear Code: Write clean, readable code that is easy to understand and maintain.
•	Locators: Use robust and reliable locators to identify elements.
•	Wait Strategically: Use Selenium waits to ensure elements are available before interacting with them.
•	Assertions: Use assertions to verify the expected behavior of the application. 




