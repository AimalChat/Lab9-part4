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

32. Create a CalcEngineTester in the project and run the testAll method. Does the output that results help 
you identify where the problem lies? 

32b.

33. Do you feel that the amount of output produced by the fully annotated CalcEngine class is too little, 
too much, or about right? If you feel that it is too little or too much, either add further print 
statements or remove some until you feel that you have the right level of detail. 

33b.

34. What are the respective advantages and disadvantages of using manual walkthroughs or print statements 
for debugging? Discuss. 

34b.

35. Using the calculator-engine project, set a breakpoint in the first line of the testPlus method in the 
CalcEngineTester class. Execute this method. When the debugger appears, walk through the code step 
by step. Experiment with both the Step and Step Into buttons. 

35b.

36. Challenge exercise In practice, you will probably find that Hacker T. Largebrain’s attempt to program 
the CalcEngine class is too full of errors to be worth trying to fix. Instead, write your own version of 
the class from scratch. The calculator-gui project contains classes that provide the GUI shown in Figure 
9.6. You can use this project as the basis for your own implementation of the CalcEngine class. Be sure to 
document your class thoroughly and to create a thorough set of tests for your implementation so that 
your experience with Hacker’s code will not have to be repeated by your successor! Make sure to use a 
dedicated unit test class for your testing, instead of writing tests into a standard class; as you have 
seen, this makes asserting the correct results much easier. 

36b.

37. Open your project again and add better testing by replacing Hacker’s test class with a unit test class 
attached to the CalcEngine. Add similar tests to those Hacker used (and any others you find useful), and
include correct assertions. 

37b.

38. Open the bricks project. Test it. There are at least four errors in this project. See if you can find 
them and fix them. What techniques did you use to find the errors? Which technique was most useful?

38b.
