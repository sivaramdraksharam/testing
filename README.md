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



