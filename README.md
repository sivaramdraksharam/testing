Prerequisite: Annotations: https://github.com/sivaramdraksharam/Fullstack-Training/tree/8afda5c99334463fdbb7dd848a415b9094f6571e/mybuiltinannotations
# testing
Manual and automation testing guidelines

References:

Study software metrics: https://drive.google.com/file/d/1mvZVIbczssdEI52OUT4Q-HhOY6Vjvm0a/view?usp=sharing

java simple programs testing (Unit testing) : https://medium.com/geekculture/unit-testing-of-simple-java-programs-b785a164b440

Automation testing piller- whitepaper: chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.hcltech.com/sites/default/files/documents/resources/whitepaper/files/qex_whitepaper_automation_testing_pillar_selenium.pdf

HCL One test:
chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.hcltech.com/sites/default/files/documents/resources/brochure/files/onetestui.pdf


Topics
------
1. What is HCL one test UI?
2. How to install HCL onetest UI?
   
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


 
To use Selenium testing on an HCL-owned laptop, you'll need to ensure your system is properly configured and that you are using the appropriate tools and methods. You'll likely be using HCL OneTest UI for managing and running your tests, and you can import or create Selenium tests to be used within your HCL workflows. 
1. Set up your environment:
•	Install necessary software:
This includes the Java Development Kit (JDK), an Integrated Development Environment (IDE) like Eclipse or IntelliJ, and Selenium WebDriver. 
•	Configure Selenium:
Ensure you have the correct versions of Selenium and browser drivers (e.g., ChromeDriver for Chrome or FirefoxDriver for Firefox) installed and configured correctly. 
•	Install HCL OneTest UI:
HCL OneTest UI is the platform for managing and running Selenium tests, so you'll need to ensure it's installed and configured on your HCL laptop. 

To install HCL OneTest UI on your HCL laptop, you'll need to download the appropriate installer from the HCL License & Delivery portal and then use the IBM Installation Manager to install it. You can also choose to install it in GUI or silent mode. 
Detailed Steps:
1.	1. Download the Installer:
•	Navigate to the HCL License & Delivery portal.
•	Download the HCL OneTest UI installer that corresponds to your desired version, product variant, and architecture. 
2.	2. Install IBM Installation Manager (if not already installed):
•	If you don't have Installation Manager installed, download and install it from the same portal. 
3.	3. Install HCL OneTest UI:
•	Open Installation Manager.
•	From the "File" menu, go to "Preferences" and then "Repositories".
•	Add the downloaded installer file as a repository by pointing to the setup disk. 
•	On the Installation Manager's "Start page," click "Install". 
•	Follow the on-screen instructions to install HCL OneTest UI. 
Silent Mode Installation: 
•	If you want to install HCL OneTest UI in silent mode, you can use the command-line arguments provided in the documentation. This allows for automated installation without user interaction.
Important Notes:
•	Ensure you have the appropriate HCL OneTest UI license. 
•	You can install HCL OneTest UI as a perspective in the UI of another supported Eclipse-based product if you're using a shell-shared installation. 
•	You can start HCL OneTest UI from the desktop environment or a command-line interface.

2. Create or import Selenium tests:
•	Create new tests:
You can create new Selenium tests directly within HCL OneTest UI using the UI Perfecto extension. 
•	Import existing tests:
You can import Java projects containing Selenium or Appium tests into HCL OneTest UI. 
3. Run Selenium tests:
•	Run tests from the Test Navigator: Once your tests are imported or created, you can run them from the Test Navigator in HCL OneTest UI. 
•	Run compound tests: You can add Selenium tests to larger workflows that also include other types of tests. 
•	View test results: HCL OneTest UI provides tools for viewing test logs and results. 
4. Customization and Extension:
•	Custom code: You can use custom Java code to extend the functionality of your Selenium tests within HCL OneTest UI.
•	API: You can also use the API to extend HCL OneTest UI functionality. 
In essence, you'll be using HCL OneTest UI to manage your Selenium tests, running them from the UI, and viewing the results within the platform. You'll need to ensure your Selenium environment is properly configured and that you have the appropriate drivers installed for your browser(s)
Ref-
https://help.hcl-software.com/devops/test/ui/10.5.3/docs/topics/t_run_se_in_rtwec.html
