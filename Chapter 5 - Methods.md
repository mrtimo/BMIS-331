**Chapter 5 - Methods**

**5.1        Methods as Black Boxes**

- Methods Sequence of instructions with a name
- You've already encountered and used methods charAt() or equalsIgnoreCase()
- You _call_ a method in order to execute its instructions
- Book example: `java double z = Math.pow(2, 3);`
- When main calls the Math.pow method, main is temporarily suspended.
- The instructions of the Math.pow method execute and compute the result.
- The Math.pow method returns its result back to main and main resumes execution.
- Methods can receive multiple parameters, but they return only one value.
- Also possible to have methods with no parametersMath.random()
- Parameter values are supplied when a method is called.
- The return value is the result that the method computes
- You don't need to know how the method is implemented
- You just need to know the specification of the method
- Methods should appear as "black boxes"

**5.2        Implementing Methods**

- When writing a method, you need to:
  - Pick a name for the method (cubeVolume)
  - Give a name and type for each parameter variable (double sideLength)
  - Specify a type for the return value (double)
  - Add the public static modifiers
  - Specify the body of the method
  - Contains the variable declarations and statements that are executed when the method is called.

- The return statement gives the method's result to the caller
- The body of a method is enclosed in braces
- When the method is called with different parameter values, the method returns different results
- Put the methods into a test program

**Syntax 5.1        Static Method Declaration**

- public static returnType methodName(parameterType parameterName, …)
- Method body executed when method called
- return  statement exits method and returns result

**Programming Tip 5.1        Method Comments**

- Always comment method behavior
- Method comments explain the purpose of the method, the meaning of the parameters and return value, as well as any special requirements
- Comments enclosed in /\*\* and \*/ delimiters.

**5.3       **  **Parameter Passing**

- Parameter variables hold the parameter values supplied in the method call
- When a method is called, a variable is created for each parameter ( **parameter variables** / **formal parameters** )
- The method call supplies values for each parameter **parameter values** / **actual parameters** / **arguments**

Parameter Passing Process

- Method call parameter variables created
- Initializing method parameter value passed in the call
- About to return to the caller method computes the expression & value stored in variable
- After method call method returns. All variables are removed, including the parameter variable. Return value is transferred to the caller. The caller put the return value into a variable.

**Programming Tip 5.2        Do Not Modify Parameter Variables**

- Parameter variable just like any other variable
- You can modify the values of parameter variables in the body of a method
- However, this practice is confusing
- To avoid confusion, introduce a separate variable

**Common Error 5.1        Trying to Modify Arguments**

- Common error: trying to modify a variable that was passed to the method
- When the method returns, all of its parameter variables are removed.
- In Java, a method can never change a variable of the calling method. (p. 187)

**5.4        Return Values**

- The return statement terminates a method call and yields the method result
- Use the return statement to specify the result of a method.
- When the return statement is processed, the method exits immediately.
- Every branch of a method needs to return a value.



Two main types of methods: (1) instance methods and (2) class methods

- Instance methods require an object to execute them
- Class methods can be executed without an object declared using the keyword static
- Any variable declared within a method is a local and it is only accessible within the method.
- The formal parameters of a method are treated as local variables within that method.

**Example:**
<script src="https://gist.github.com/mrtimo/53a5f3e2cabd70c6b253.js"></script>
```java
public class Method1
{
	public static void main(String [] args)
	{
		int a = 6;
		int b = 4;
		System.out.println(“The minimum value is “ + showMin(a, b));
	}

	public static int showMin(int x, int y)
	{
		if (x < y)
			return  x;
		else
			return y;
	}
}
```

- The keyword static tells us that this is a class method, and so can be executed without an object.

- All methods generally have a return value. If the return value is of type void, nothing is returned and there is no return statement within the function. In this example, an int is returned.

- A method is executed when it is called. Method call = showMin(a, b);

- The parameters a and b are often referred to as actual parameters. The values of these are passed to the method showMin();

- The method definition has parameters called x and y. These are often referred to as formal parameters. Formal parameters are variables local to the method. These parameters accept the values of a and b.

- The values of x and y are used in the method and the minimum is returned back to the calling statement. This is the call-by-value parameter passing method.

**Common Error 5.2        Missing Return Value**

- It is a compile-time error if some branches of a method return a value and others do no.
- A remedy if to add a statement return 0; to the end of the method.

**How To 5.1        Implementing a Method**

- A method is a computation that can be used multiple times with different parameter values, either in the same program or in different programs.
- Whenever a computation is needed more than once, turn it into a method.
- Step1: Describe what the method should do
- Step 2: Determine the method's "inputs". Make a list of _all_ the parameters that can vary.
- Step 3: Determine the types of the parameters and the return value.
- Step 4: Write pseudocode for obtaining the desired result.
- Step 5: Implement the method body
- Step 6: Test the method.

**5.5        Methods Without Return Values**

- Use the return type of void to indicate that a method does not return a value.
- Sometimes, you need to carry out a sequence of instructions that does not yield a value.
- Often, this type of method doesn't compute any value, but performs some actions and then returns to the caller.
- If you want to return from a void method before reaching the end, you use a return statement without a value.
- For example: return; //Return immediately

**5.6        Problem Solving: Reusable Methods**

Use the process of stepwise refinement to decompose complex tasks into

**5.7        Problem Solving: Stepwise Refinement**

- Use the process of stepwise refinement to decompose complex tasks into simpler ones.
- To solve a difficult task, break it down into simpler tasks.
- Review class IntegerNam p. 195

**Programming Tip 5.4       **  **Keep Methods Short**

- Cost for writing a method
- Need to design, code, and test the method. Method needs documenting.
- Spend some effort to make the method reusable rather than tied into a specific context.
- If a method will not fit on a single screen in the IDE, it should probably be broken up.
- Keep your methods under 20 lines!!!

**Programming Tip 5.5        Tracing Methods**

- Carry out a manual walkthrough on complex methods before entrusting your program to the computer.
- Way to understand the subtle aspects of a method

**Programming Tip 5.6        Stubs**

- For larger programs, it is not always feasible to implement and test all methods at once
- Often need to test a method that calls another, but the other method hasn't been implemented.
- You can temporarily replace the missing method with a **stub**.
- The **stub** returns a simple value that is sufficient for testing another method.

**5.8        Variable Scope**

- The **scope** of a variable is the part of the program in which it is visible.
- The scope of a variable is the **part of the program in which you can access it**.
- The scope of a method's **parameter variable** is the entire method.
- A variable that is defined within a method is called a **local variable**.
- The scope of a local variable ranges from its declaration until the end of the block or for statement in which it is declared.
-  **Note** : a variable declared in a for statement only extends to the end of the for.
- Two local or parameter variables can have the same name, provided that their scopes do not overlap.

**5.9        Recursive Methods (Optional)**

- A recursive method is a method that calls itself.
- A recursive computation solves a problem by using the solution of the same problem with simpler inputs.

Two key requirements to make sure that the recursion is successful:

1. 1.Every recursive call must simplify the task in some way.
2. 2.There must be special cases to handle the simplest tasks directly.

- For a recursion to terminate, there must be special cases for the simplest inputs.

**How To 5.2        Thinking Recursively**

- Step1: Break the input into parts that can themselves be inputs to the problem.
- Step 2: Combine solutions with simpler inputs into a solution of the original problem.
- Step 3: Find solutions to the simplest inputs.
- Step 4: Implement the solution by combining the simple cases and the reduction step.

**Random Fact 5.1        The Explosive Growth of Personal Computers**

- Marcian E. "Ted" Hoff, engineer at Intel, working on a chip for a manufacturer of electronic calculators.
- Decided it would be a better idea to develop a general-purpose chip that could be programmed to interface with the keys and display of a calculator, rather than to do yet another custom design.
- Microprocessor was born.
- 1974 – first computer kit, the Altair 8800
- First bit hit was the Apple II.

**Debugger Session**

- Open BlueJ and create a new class called Int
- Open Blackboard and go to:
- Sample Java Code / Chapter Source Code / Chapter 5 Source Code / IntegerName.java
- Copy that source code into BlueJ into Int and compile
- Identify the methods
  - intName
  - digitName
  - teenName
  - tensName
- FYI these are **terrible** names for methods
- Google "Java naming standards"
- Methods should be in mixed case and use **verbs** to describe what the method does
- Better names would be:
  - getIntName
  - getDigitName
  - getTeenName
  - getTensName
- Run once to see the result
- Set a halt opposite the System.out.println
- Enter 525 in response to the prompt and step through the code
