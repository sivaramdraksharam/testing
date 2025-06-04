Prerequisite: Annotations: https://github.com/sivaramdraksharam/Fullstack-Training/tree/8afda5c99334463fdbb7dd848a415b9094f6571e/mybuiltinannotations
# testing
Manual and automation testing guidelines

References:

Study software metrics: https://drive.google.com/file/d/1mvZVIbczssdEI52OUT4Q-HhOY6Vjvm0a/view?usp=sharing

java simple programs testing (Unit testing) : https://medium.com/geekculture/unit-testing-of-simple-java-programs-b785a164b440

Day-4 Topics
------
1. What is Junit? Junit is a testing framework to test java programs
2. What is Jupitor? Jupitor is the junit5 version with great features.
3. What is Mockito? Mockito is also another testing framework where we can create mock objects for interaction with the application in order to test it.
4. Can we mock database using mockito? Yes
   

Day-4
------
Practical 1:
Note: Download junit4.jar and hamcrest-all.jar and keep them in your java testing project build path.
Run the following code as Test Case

import static org.junit.Assert.*;
import org.junit.Test;

// Example Calculator class
class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
    public int subtract(int a, int b) {
        return a - b;
    }
    public int multiply(int a, int b) {
        return a * b;
    }
    public int divide(int a, int b) {
        if (b == 0) throw new IllegalArgumentException("Cannot divide by zero");
        return a / b;
    }
}

// JUnit Test Class
public class CalculatorTest {

    @Test
    public void testAdd() {
        Calculator calc = new Calculator();
        assertEquals(5, calc.add(2, 3));
    }

    @Test
    public void testSubtract() {
        Calculator calc = new Calculator();
        assertEquals(1, calc.subtract(3, 2));
    }

    @Test
    public void testMultiply() {
        Calculator calc = new Calculator();
        assertEquals(6, calc.multiply(2, 3));
    }

    @Test
    public void testDivide() {
        Calculator calc = new Calculator();
        assertEquals(2, calc.divide(6, 3));
    }

    @Test(expected = IllegalArgumentException.class)
    public void testDivideByZero() {
        Calculator calc = new Calculator();
        calc.divide(5, 0);
    }
}
Practical 2:
How to perform JUnit Testing with Selenium?
This section focuses on testing the code with Selenium and JUnit. This type of testing comes under automation testing since the workflow and execution of the test are automated. Selenium and JUnit can be combined to make a powerful test combination to test websites. We will test on BrowserStack to check for the login functionality using valid and invalid credentials.

import java.util.concurrent.TimeUnit;

import org.junit.AfterClass; //Importing all the JUnit and Selenium classes
import org.junit.Assert;
import org.junit.BeforeClass;
import org.junit.Test;
import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;

public class FirstTest {
private static FirefoxDriver driver;
WebElement element;

@BeforeClass
public static void openBrowser(){
driver = new FirefoxDriver(); //Initialising the browser driver
}

@Test
public void validUserCredentials(){ //To test successful login

System.out.println("This is the test code " + new Object(){}.getClass().getEnclosingMethod().getName());
driver.get("https://www.browserstack.com");
driver.findElement(By.xpath(".//*[@id='account']/a")).click();
driver.findElement(By.id("log")).sendKeys("userid"); //Sending ID
driver.findElement(By.id("pwd")).sendKeys("userpassword"); // Sending PWD
driver.findElement(By.id("login")).click();
try{
element = driver.findElement (By.xpath(".//*[@id='account_logout']/a"));
}catch (Exception e){
}
Assert.assertNotNull(element); //Checking the element presence
System.out.println("Test End " + new Object(){}.getClass().getEnclosingMethod().getName());
}

@Test
public void WrongUserCredentials()
{
System.out.println("Starting test " + new Object(){}.getClass().getEnclosingMethod().getName());
driver.get("https://www.browserstack.com");
driver.findElement(By.xpath(".//*[@id='account']/a")).click();
driver.findElement(By.id("log")).sendKeys("userid");
driver.findElement(By.id("pwd")).sendKeys("userpassword"); //Entering wrong pwd
driver.findElement(By.id("login")).click();
try{
element = driver.findElement (By.xpath(".//*[@id='account_logout']/a"));
}catch (Exception e){
}
Assert.assertNotNull(element);
System.out.println("Ending test " + new Object(){}.getClass().getEnclosingMethod().getName());
}

@AfterClass
public static void closeBrowser(){
driver.quit(); //Closing the driver once the tests are executed
}
}

The above test is just a sample test to show how JUnit and Selenium work together.

Test Run Selenium with JUnit

Final Thoughts

JUnit testing in Java is the most preferred method as it is robust and continually evolving for better test case execution. It has become a preferred choice for Test-driven development cycle.
Selenium is a convenient tool for automated web testing, and using it along with JUnit is even more beneficial. JUnit supports multiple assertions and annotations. Using BrowserStack Automate, developers can conveniently run unit testing using Java with Selenium.
However, no matter how well crafted, tests cannot be regarded as conclusive if they are not run on real devices. Emulators and simulators cannot replicate end-user conditions properly, especially regarding weak networks and low battery. Run tests directly on a real device cloud to compensate for these inadequacies.
Use parallel testing. Instead of running tests sequentially, parallel testing allows for simultaneous test execution. For example, it enables QAs to run the same test on multiple device-browser combinations simultaneously, significantly reducing time and effort.


