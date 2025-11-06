------------------------------------------------------------------------
Super Calculator
Author: Hacker T. Largebrain
------------------------------------------------------------------------

This program implements a highly efficient calculating engine for
a pocket calculator. It includes a complete test rig to demonstrate
that the engine works as it should.

31. Open the calculator-engine-print project and complete the addition of print statements to each method 
and the constructor.

31b.
/**
 * The main part of the calculator doing the calculations.
 * This version incorporates debugging print statements. 
 * @author Hacker T. Largebrain (version 1.0)
 * @version 1.1
 */
public class CalcEngine
{
    // The value in the display.
    private int displayValue;
    // The previous operator typed (+ or -).
    private char previousOperator;
    // The left operand to previousOperator.
    private int leftOperand;

    /**
     * Create a CalcEngine instance.
     */
    public CalcEngine()
    {
        displayValue = 0;
        previousOperator = ' ';
        leftOperand = 0;
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
    }

    /**
     * Return the value of the calculator that should appear in the display right now.
     * @return The value to be shown on the calculator display.
     */
    public int getDisplayValue()
    {
        return displayValue;
    }

    /**
     * A number button was pressed. Process it.
     * @param number The single digit.
     */
    public void numberPressed(int number)
    {
        System.out.println("numberPressed called with: " + number);
        
        displayValue = displayValue * 10 + number;
        
        reportState("end of numberPressed");
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
    }

    /**
     * This method should be called when the '+' button was pressed. 
     */
    public void plus()
    {
        System.out.println("plus called");
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
        applyPreviousOperator();
        previousOperator = '+';
        displayValue = 0;
        reportState("end of plus");
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
    }

    /**
     * This method should be called when the '-' button was pressed.
     */
    public void minus()
    {
        applyPreviousOperator();
        previousOperator = '-';
        displayValue = 0;
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
    }
    
    /**
     * This method should be called when the '=' button was pressed.
     */
    public void equals()
    {
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
        System.out.println("equals called");
        if(previousOperator == '+') {
            displayValue = leftOperand + displayValue;
            System.out.println(displayValue);
            System.out.println(previousOperator);
            System.out.println(leftOperand);
        }
        else {
            displayValue = leftOperand - displayValue;
            System.out.println(displayValue);
            System.out.println(previousOperator);
            System.out.println(leftOperand);
        }
        leftOperand = 0;
        reportState("end of equals");
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
    }

    /**
     * This method should be called when the 'C' (clear) button was pressed.
     */
    public void clear()
    {
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
        System.out.println("clear called");
        displayValue = 0;
        reportState("end of clear");
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
    }

    /**
     * Return the name of this calculator to be shown as the title of the application.
     * @return The title of this calculation engine.
     */
    public String getTitle()
    {
        return "Super Calculator";
    }

    /**
     * Return the name of the author of this application.
     * @return The author of this engine.
     */
    public String getAuthor()
    {
        return "Hacker T. Largebrain";
    }

    /**
     * Return the version number of this application.
     * @return The version number of this engine.
     */
    public String getVersion()
    {
        return "version 0.2";
    }

    /**
     * Print the values of this object's fields.
     * @param where Where this state occurs.
     */
    public void reportState(String where)
    {
        System.out.println("displayValue: " + displayValue +
                           " leftOperand: " + leftOperand +
                           " previousOperator: " + previousOperator + 
                           " at " + where);
    }
    
    /**
     * An operator button has been pressed. Apply the immediately preceding operator to
     * calculate an intermediate result. This will form the left operand of the new operator.
     */
    private void applyPreviousOperator()
    {
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
        System.out.println("applyPreviousOperator called");
        if(previousOperator == '+') {
            leftOperand += displayValue;
        }
        else if(previousOperator == '-') {
            leftOperand -= displayValue;
        }
        else {
            // There was no preceding operator.
            leftOperand = displayValue;
        }
        reportState("end of applyPreviousOperator");
        System.out.println(displayValue);
        System.out.println(previousOperator);
        System.out.println(leftOperand);
    }
}


32. Create a CalcEngineTester in the project and run the testAll method. Does the output that results help 
you identify where the problem lies? 

32b.Somewhat, its not terrible but isnt precise enough to help direcctly point out logic errors, thats 
what I think.

33. Do you feel that the amount of output produced by the fully annotated CalcEngine class is too little, 
too much, or about right? If you feel that it is too little or too much, either add further print 
statements or remove some until you feel that you have the right level of detail. 

33b.I think its too little, because it shows only the before and after results and not what happens each 
step of the way.

34. What are the respective advantages and disadvantages of using manual walkthroughs or print statements 
for debugging? Discuss. 

34b.With manual walkthroughs, you can focus on truly making sure your reasoning is sound without relying 
on the compiler, which is normal since we all prefer easy and conveniency. However, with that comes the 
time consumming aspcet of doing this approach, not to mention the possibility of losing track where you 
are, either the current line of code, variables, methods, step intos and other things. With print 
statements you can find yourself in many, many, many lines of code that clutter the source code, which 
you'll have to remove later on. However, this approach is much less time consuming and helps sound out 
reasoning wihtout too much hastle compared to paper walkthroughs.

35. Using the calculator-engine project, set a breakpoint in the first line of the testPlus method in the 
CalcEngineTester class. Execute this method. When the debugger appears, walk through the code step 
by step. Experiment with both the Step and Step Into buttons. 

35b.Did it! It works as intended after I stepped through each step checking the CalcEngineTester' seperate states after each one and everything adds up well!

36. Challenge exercise In practice, you will probably find that Hacker T. Largebrain’s attempt to program 
the CalcEngine class is too full of errors to be worth trying to fix. Instead, write your own version of 
the class from scratch. The calculator-gui project contains classes that provide the GUI shown in Figure 
9.6. You can use this project as the basis for your own implementation of the CalcEngine class. Be sure to 
document your class thoroughly and to create a thorough set of tests for your implementation so that 
your experience with Hacker’s code will not have to be repeated by your successor! Make sure to use a 
dedicated unit test class for your testing, instead of writing tests into a standard class; as you have 
seen, this makes asserting the correct results much easier. 

36b.Im sorry.


37. Open your project again and add better testing by replacing Hacker’s test class with a unit test class 
attached to the CalcEngine. Add similar tests to those Hacker used (and any others you find useful), and
include correct assertions. 

37b.


import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

/**
 * The test class CalcEngineTest.
 *
 * @author  (Aimal)
 * @version (2025-11-05)
 */
public class CalcEngineTest
{
    private CalcEngine calcEngi1;

    /**
     * Default constructor for test class CalcEngineTest
     */
    public CalcEngineTest()
    {
    }

    /**
     * Sets up the test fixture.
     *
     * Called before every test case method.
     */
    @BeforeEach
    public void setUp()
    {
        calcEngi1 = new CalcEngine();
    }

    /**
     * Tears down the test fixture.
     *
     * Called after every test case method.
     */
    @AfterEach
    public void tearDown()
    {
    }

    @Test
    public void testPlus()
    {
        //make sure the calculator is in a state to perform.
        calcEngi1.clear();
        //display value should now be 5.
        calcEngi1.numberPressed(5);
        //previous operand should be + after this line.
        calcEngi1.plus();
        //left operand is now 5 and display value is 3 now
        calcEngi1.numberPressed(3);
        //calculate.
        calcEngi1.equals();
        //should return display value at 8.
        assertEquals(8, calcEngi1.getDisplayValue());
    }

    @Test
    public void testMinus()
    {
        //make sure the calculator is in a state to perform.
        calcEngi1.clear();
        //display value should now be 1.
        calcEngi1.numberPressed(1);
        //previous operand should be - after this line.
        calcEngi1.minus();
        //left operand is now 1 and display value is 6 now
        calcEngi1.numberPressed(6);
        //calculate.
        calcEngi1.equals();
        //should return display value at -5.
        assertEquals(-5, calcEngi1.getDisplayValue());
    }

    @Test
    public void testClear()
    {
        //pretend to calculate 9 - 7.
        calcEngi1.numberPressed(9);
        calcEngi1.minus();
        calcEngi1.numberPressed(7);
        calcEngi1.clear();
        //should display 0 for all 3.
        assertEquals(0, calcEngi1.getDisplayValue());
        assertEquals(0, calcEngi1.getLeftOperand());
        assertEquals(' ', calcEngi1.getPreviousOperator());
    }
}


38. Open the bricks project. Test it. There are at least four errors in this project. See if you can find 
them and fix them. What techniques did you use to find the errors? Which technique was most useful?

38b.There were many errors, such as the weight method labeled incorrectly, that method was rather for the 
mass. ALSO, the depth parameter was so confusing so I put in what shouldve been there, length. I did add a 
getDepth in case it was needed. Also, witht the renaming of the getWeight method, I made it abundently 
clear that you first multiply and then divide. Though im sure theres a way to just write one line, I felt 
more comfortable doing it this way. In the getSurfaceArea method there was a small mistake where the 
orginal code added the side1 twice, ignoring side2 and giving a faulty output. Then in the pallet class, I 
changed the name of weight to mass, since, once again, we are not dealing with gravity and such. In the
newly changed getWeight method(renamed as getMass), they did add the base mass of the pallet, meaning it 
only outputted the mass of the bricks. Finally for the last explicit error I found, the getHeight method. 
Rather than using a modulus operator, it should have been a multiplication of a brick * how many bricks 
layers of bricks there are. For me, the most useful technique was the unit test classes. As I was able to 
spot the mistakes, after having understood what the classes' roles were, also manual walktrhough did help 
surprisngly, I was able to easily trace back what was either wrong or lacking in the methods. I did not 
use print statements unfortunately.

//Brick & its respective unit tester

/**
 * Brick models a simple brick.
 * 
 * @author: Michael Kölling and David J. Barnes
 * @version 7.0
 */
public class Brick
{
    // Constant.
    private static final int DENSITY_PER_CM3 = 2;  // mass/density of material per cubic cm in grams

    private int height;
    private int width;
    private int length;

    /**
     * Create a Brick given edge lengths in centimeters.
     * @param height The brick's height.
     * @param width The brick's width.
     * @param depth The brick's length.
     */
    public Brick(int height, int width, int length)
    {
        this.height = height;
        this.width = width;
        this.length = length;
    }
    
    public int getDepth()
    {
        int depth = getVolume()/(height*width);
        return depth;
    }
    
    public int getWidth()
    {
        return width;
    }
    
    public int getLength()
    {
        return length;
    }

    /**
     * @return The surface area of this brick in square centimeters.
     */
    public double getSurfaceArea()
    {
        double side1 = length * width;
        double side2 = length * height;
        double side3 = width * height;
        double total = (side1 + side2 + side3) * 2;//repeated side 1 twice

        return total;
    }

    /**
     * @return The mass of this brick in kg.
     */
    public double getMass()
    {
        double mass = getVolume() * DENSITY_PER_CM3;
        return mass / 1000;//error found!
    }

    /**
     * @return The volume of this brick in cubic centimeters.
     */
    public int getVolume()
    {
        return width * height * length;
    }

    /**
     * @return The height of this brick in centimeters.
     */
    public double getHeight()
    {
        return height;
    }
}



import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

/**
 * The test class BrickTest.
 *
 * @author  (your name)
 * @version (a version number or a date)
 */
public class BrickTest
{
    private Brick brick2;

    /**
     * Default constructor for test class BrickTest
     */
    public BrickTest()
    {
    }

    /**
     * Sets up the test fixture.
     *
     * Called before every test case method.
     */
    @BeforeEach
    public void setUp()
    {
        brick2 = new Brick(3, 9, 2);
    }

    /**
     * Tears down the test fixture.
     *
     * Called after every test case method.
     */
    @AfterEach
    public void tearDown()
    {
    }

    @Test
    public void testConstructor()
    {
        assertEquals(9, brick2.getWidth());
        assertEquals(3, brick2.getHeight(), 0.1);
        assertEquals(2, brick2.getDepth());
    }

    @Test
    public void testVolume()
    {
        assertEquals(54, brick2.getVolume());
    }

    @Test
    public void testSurfaceArea()
    {
        assertEquals(102, brick2.getSurfaceArea(), 0.1);//error found!
    }
    

    @Test
    public void testMass()
    {
        assertEquals(0.108, brick2.getMass(), 0.1);//error found!
    }
}

//pallet class and its unit tester


/**
 * A pallet is a stack of bricks on a wooden base.
 *
 * @author: Michael Kölling and David J. Barnes
 * @version 7.0
 */
public class Pallet
{
    private static final double BASE_MASS = 6.5;  // in kg
    private static final double BASE_HEIGHT = 15;  // in cm

    private Brick aBrick;
    private int bricksInPlane;
    private int height;

    /**
     * Create a pallet with a given number of bricks.
     * @param bricksInPlane The number of bricks in each level on the base.
     * @param height The number of bricks stacked on top of each other.
     */
    public Pallet(int bricksInPlane, int height)
    {
        this.bricksInPlane = bricksInPlane;
        this.height = height;
        aBrick = new Brick(8, 20, 12);
        //Means that volume = 1920
        //means that mass = 3.84
    }

    /**
     * @return The mass of the pallet (in kg)
     */
    public double getMass()
    {
        int numberOfBricks = bricksInPlane * height;
        return (aBrick.getMass() * numberOfBricks) + BASE_MASS;//ERROR found!
        //did not add the base mass.
    }

    /**
     * @return The height of this stack (in cm)
     */
    public double getHeight()
    {
        return (aBrick.getHeight() * height) + BASE_HEIGHT;//error found!
        //not modulus operator that is needed but rather *, a multiplication.
        
    }
}



import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

/**
 * The test class PalletTest.
 *
 * @author  (your name)
 * @version (a version number or a date)
 */
public class PalletTest
{
    private Pallet pallet1;

    /**
     * Default constructor for test class PalletTest
     */
    public PalletTest()
    {
    }

    /**
     * Sets up the test fixture.
     *
     * Called before every test case method.
     */
    @BeforeEach
    public void setUp()
    {
        pallet1 = new Pallet(10, 2);
    }

    /**
     * Tears down the test fixture.
     *
     * Called after every test case method.
     */
    @AfterEach
    public void tearDown()
    {
    }

    @Test
    public void testMass()
    {
        assertEquals(83.3, pallet1.getMass(), 0.1);
    }

    @Test
    public void testHeight()
    {
        assertEquals(31, pallet1.getHeight(), 0.1);
    }
}



