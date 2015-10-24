## BMIS331 – Java Programming
### Chapter 4 - Loops

**Loop or Repetition – a loop (repeat) at the end of the loop**
    - Either go back and repeat the block of code
    - Or continue with the next instruction after the block

Programs with loops are more likely to contain mistakes than simpler programs

Loop statements repeatedly execute instructions until a goal has been reached

- 3 basic Looping constructs

1. **while**
2. **do-while**
3. **for**

**4.1  while Loops**

Executes a block of code repeatedly

A condition controls how often the loop is executed

Loop is repeated _while_ the controlling Boolean expression is true
```java
while (condition)
(
        statements;
}
```

The while loop "indefinite" because execution is event controlled
```java
while (balance < TARGET)
(
        years++
        double interest = balance \* RATE / 100;
        balance = balance + interest;
}
```

**NOTE** : When you declare a variable **inside** the loop body, the variable is created for each iteration of the loop and removed after the end of each iteration.  \*\*\*p. 142\*\*\*

On the other hand, balance and years variables were declared **outside** the loop body. Those variables are used for all iterations of the loop.



Body of a **while** loop can be executed **zero** times because the condition is checked before the loop body and you only execute when the condition is true.

Execution of a **while** loop:

 1.Controlling boolean expression evaluated
 2.If boolean = false, loop body is not executed, not even once.

>####Common Error 4.1        Don't Think "Are We There Yet?"

>-while  loop the **condition** determines how long the loop will keep going

>####Common Error 4.2        **Infinite Loops**
>Loop runs forever and can be stopped only by killing the program or restarting the computer. 
>Program seems to "hang".

>Common reason for infinite loop forgetting to update the variable that controls the loop or 
>accidentally incrementing a counter that should be decremented (or vice versa)

>####Common Error 4.3        **Off-by-One Errors**

>Should a controlling variable start at 0 or at 1? Think through a couple of test cases and use the 
>information from the test cases to come up with a rationale for your decisions.

**4.2   Problem Solving: Hand-Tracing**

- Simulation of code execution
- You step through instructions and track the values of the variables

**4.3 for Loops  **  [One of the most common loop types]

Specialized loop statement (pseudo code)

You use a for loop when a variable runs from a starting to an ending value with a constant increment or decrement sometimes called a count-controlled loo also called a definite loop

`for (initialization; condition; increment)`

**Code:**
```java
for (count = 1; count <= 3; count++){
System.out.println(count);
System.out.println("Go");
}
```
Iteration for loop body controlled by the line:

`for (count = 1; count <= 3; count++)`

(1)  What happens before the loop body is executed the 1st time

(2)  Boolean expression that determines when the loop will end

(3)  Executed after each iteration of the loop body

`for (initializing\_action; condition; update\_action)`

- Initialization executed **once** before the loop is entered
- The condition is checked before each iteration
- The update is executed after each iteration

**4.4 do Loops**

Loop body **always** executed at least onc sometimes called a post-test loop because the condition is tested after completing the loop body.

```java
do{ 
statement 1;
statement 2;
etc.;
}

while (condition);
```

Execution of a **do-while** loop:

 1.Loop body is executed **first**
 2.Then the condition is tested
 3.After that, **do-while** behaves in the same way as a **while** loop



**4.5 Application: Processing Sentinel Values**

Learn how to write loops that read and process a sequence of input values (prompts)

**Sentinel** value denotes the end of a data set, but it is **not** part of the data!

Simply a signal for termination.

Use caution when setting the initial value for the sentinel.

Frequently, a `Boolean` variable is used as the sentinel.

Look at samples of code.

**4.6 Problem Solving: Storyboards**

- When designing a program that interacts with users, you need to make a plan for the interaction!

- What does the user need to provide? In what order?
- What information will your program display? In which format?
- What should happen if an error occurs? When does the program quit?



**4.7        Common Loop Algorithms**

**4.7.1 Sum and Average Value** What is important here?

- Pay attention to when the variable declaration is **inside** the loop and when it is **outside** the loop
- Loop while there is still input coming in and sum all the inputs
- To compute an average, keep a total and a count of all values

**4.7.2 Counting Matches** What is important here?

- Pay attention to when the variable declaration is **inside** the loop and when it is **outside** the loop
- Count how many uppercase letters are in a string.
- This loop can also be used for scanning inputs read text, a word at a time `(in.hasNext())`, and count the number of words having at most three letters
- To count values that fulfill a condition, check all values and increment a counter for each match

**4.7.3 Finding the First Match** What is important here?

- Pay attention to when the variable declaration is **inside** the loop and when it is **outside** the loop
- Also pay attention to the condition statement
- Count the values that fulfill a condition (Look at all values)
- When you find a match, exit the loop
- This loop find the first lowercase letter in a string
- You want to find a match, and then you can stop as soon as the condition is fulfilled
- If a match is found, then the variable found is true
- If the loop did not find a match, then found remains false after the end of the loop
-  **Note** : input is declared outside the while loop because you will want to use the input after the loop has finished.

**4.7.4 Prompting Until a Match is Found** What is important here?

- Keep prompting until the user provides a correct input
- Note which variables are declared out the loop

**4.7.5 Maximum and Minimum** What is important here?

- To compute the largest value in a sequence, keep a variable that stores the largest element that you have encountered, and update it when you find a larger one
-  Requires that there is at least one input
- To compute the smallest value, simply reverse the comparison


**4.7.6 Comparing Adjacent Values** What is important here?

- When processing a sequence of values in a loop, you sometimes need to compare a value with the value that just preceded it
-  **Challenge** : how can you compare the current input with the preceding one?
- Must store the previous input  in a variable
- Next challeng when the loop is entered for the first time, input has not yet been set
- Solve with an initial input operation **outside** the loop

Writing a Loop

1. Decide what work must be done **inside** the loop.
2. Specify the loop **condition**.
3. Determine the loop **type**
4. Set up **variables** for entering the loop for the first time
5. ** Process the result**after the loop has finished
6. ** Trace** the loop with typical examples.
7. ** Implement **the loop in** Java**.

**4.8        Nested Loops**

- Nested loop loop inside another loop statement
- When processing tables, nested loops occur naturally
-  **Outer loop** iterates over all rows of the table
- An **inner loop** deals with the columns in the current row
- Example: The hour and minute displays in a digital clock
  - The hours loop 12 times, and for each hour, the minutes loop 60 times

**4.9        Application: Random Numbers and Simulations**

-  **Simulation** program uses computer to simulate an activity in the real world
- Simulations commonly used for predicting climate change, analyzing traffic, picking stocks, and many other applications in science and business
- In many simulations, one or more loops are used to modify the state of a system and observe the changes

**4.9.1        Generating Random Numbers**

Java library has a random number generator, which produces numbers that appear to be completely random

- Calling `Math.random()` yields a random floating-point number that is >= 0 and <1.
- Call `Math.random()` again, and you get a different number.
- Actually the numbers are not completely random.
- Drawn from sequences of numbers that don't repeat for a long time.
- Often called pseudorandom numbers

**4.9.2        Simulating Die Tosses**

In actual applications, you need to transform the output from the random number generator into different ranges.

For example, to simulate the throw of a die, you need random integers between 1 & 6.

- General recipe for computing random integers between two bounds a and b
- Programming Tip 4.4 on page 141 informs us that there are b – a + 1 values between a and b, including the bounds themselves.
- First compute `(int) (Math.random() \* (b – a + 1))` to obtain a random integer between 0 and b – 1
- Then add a, yielding a random value between a and b

-  **Demo** Dice.java
