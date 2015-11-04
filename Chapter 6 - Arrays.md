##Chapter 6 – Arrays and Array Lists

###6.1        Arrays

**Array** sequence of values of the same type

- Fundament mechanism for collecting multiple values
- _Collection_ of _related values_
- Allows more than one value to be associated with a variable name
- Individual values of an array stored in **adjacent memory locations** and are indexed
- Array name is followed with a set of **square braces** [ ]  to specify the **number of cells** to be associated with the variable
- First item at **position 0** (zero-based)
- Number of elements --> **length** of the array
- To get to an item you need a position (known as its index or subscript)
- The **new** operator constructs the array

**Array** collection of a fixed number of components of the same data type

**One-dimensional array**  components are arranged in a list form

**6.1.1        Declaring and Using Arrays** (p. 250)

General form of declaring a one-dimensional array:
```java
dataType[] arrayName;    //Line1
double[] values; //Declares an array named "values"(not initialized)
double[] values = **new** double[10]; //Declare & initializes an array (0)
double[] values = {32, 54, 67.5, 29, 35); //Declare & set initial value
```
Because an array is an **object** , arrayName is a **reference variable**

Therefore, to store data we must instantiate (populate) the array object

General syntax to instantiate an array object is:
```java
arrayName = new dataType[intExp];   //Line2
```
**Note** : intExp is any expression that evaluates to a positive integer

Also, intExp specifies the number of components in the array

You can combine the statement in Lines 1 and 2:
```java
dataType[] myArray;    //Line1
myArray = **new** dataType[intExp];   //Line2
dataType[] myArray = **new** dataType[intExp];    //Line3
```
- An object stores its data in **instance variables**
- These variables are declared inside the class
- Instance variables provide information to methods
- Instance variables are declared **in** the class, but outside any methods with the private

>Remember: objects are reference types --> array name is merely the address of the **start** of the array

The statement      `int[] num = new int[5];` declares and creates the array "num" of 5 components.

First item at position 0

The components are num[0], num[1], num[2], num[3], and num[4]

![Empty Int Array of Size 5](http://content.screencast.com/users/mrtimo/folders/Jing/media/f6b469b9-4fa6-4000-83df-579b177096dc/00000049.png)

The statement        `String[] name = {"Amy", "Bill", "Stan", "Mary", "Susan"};` declares and creates the array "name" of 5 components.

**First item at position 0**

The components are name[0], name[1], name[2], name[3], and name[4].

![String Array populated](http://content.screencast.com/users/mrtimo/folders/Jing/media/7227b625-dfb5-400c-9073-6cc291757076/00000050.png)


If your array "list" has 10 components, the components are `list[0]` through `list[9]`

The assignment statement                   `list[5] = 34`; stores 34 in `list[5]` which is the 6th component of the array.


**6.1.2        Array References** (p. 253)

- Variable `data` does not store any number
- Array is stored elsewhere and the `data` variable holds a reference to the array
- Only becomes important when copying array references.

Different than objects

- data stored must be the same type
- small pre-defined methods that may not look like methods
- can't really inherit from them

Many uses:  sorting, finding hi, low, mid

Remember, objects are reference types so the _array name is merely the address_ of the start of the array

**6.1.3        Partially Filled Arrays** (p. 254)

An array **cannot change size** at run time (Problem when you don't know in advance how many elements you need!)

Loop to collect input and fill up the **values** array:
```java
final int LENGTH = 100; //maximum length of the array
double[] values = new double [LENGTH];
int currentSize = 0;
Scanner in = new Scanner(System.in);
while (in.hasNextDouble())
{
if (currentSize < values.length)
{
values[currentSize] = in.nextDouble();
currentSize++
}
}
```

**Common Error 6.1       **  **Bounds Errors**
>Most common error in using arrays  accessing a nonexistent element
```java      
double[] data = new double[10];
data[10] = 5.4;
// Error—data has 10 elements with index values 0 to 9
```
>**No** compiler error message
>Program will generate an exception at run time





**Common Error 6.2       **  **Uninitialized Arrays**

>Common error is to allocate an array variable, but not an actual array
```java
double[] data;
data[0] = 29.95;     // Error—data not initialized
```
- Compiler will catch this error.
- Remedy is to initialize the variable with an array: `double[] data = new double[10];`

**Programming Tip 6.1       **  **Use Arrays for Sequences of Related Values**

- Arrays intended for storing sequences of values with same meaning
- For example: array of test scores makes perfect sense:
-      `int[] scores = new int[NUMBER\_OF\_SCORES];`
- Array that holds a person's age, bank balance, and shoe size in positions 0, 1, 2 is **bad design**.  In this case, it's better to use 3 variables.
-    `int[] personalData = new int[3];`

**Random Fact 6.1        An Early Internet Worm**
- November 1988  student at Cornell launched a virus (worm)
- Worn would attempt to connect to finger, a C program in UNIX operating system for finding information on a user who has an account on a particular computer on the network.
- C does not check that an array index is less than the length of the array!
- Worm purposefully filled the 512-character array with 536 byes to overwrite the 24 byte return address
- Didn't return to the caller but to code supplied by the worm "Buffer Overrun" Attack
- The code ran under the same super-user privileges as finger, allowing the worm to gain entry into the remote system
- Java would generate a run-time exception and never corrupts memory outside the array



**6.2 The Enhanced for Loop**

May want to use the enhancedfor loop to visit all elements of the array

Convenient mechanism for traversing all elements in a collection.

Personally, I don't like the enhanced for loop because it was invented after I had already learned the older form!!

The enhanced for-loop is a popular feature introduced with the Java SE platform in version 5.0. Its simple structure allows one to simplify code by presenting for-loops that visit each element of an array/collection without explicitly expressing how one goes from element to element.

Because the old style of coding didn't become invalid with the new for-loop syntax, you don't have to use an enhanced for-loop when visiting each element of an array/collection. However, with the new style, one's code would typically change from something like the following:

**Old form:**
```java
for (int i=0; i < array.length; i++) {
    System.out.println("Element: " + array[i]);
}
```

to the **newer form:**
```java
for (String element : array) {
    System.out.println("Element: " + element);
}
```

Assuming "array" is defined to be an array of String objects, each element is assigned to the element variable as it loops through the array.
```java
**class** EnhancedForLoop
{
  **public**** static ****void** main(String[] args)
         {
    int primes[] = { 2, 3, 5, 7, 11, 13, 17, 19, 23, 29};
    for ( int t: primes)
        {
      System.out.println(t);
     }
          }
}
```

**Coding exercise – Self Check (p. 255)**

Code #1 and 2 in BlueJ  print out the array after changing the elements

Add #3 changing the array name   print out the array after changing the elements

# Review Exercises  R6.1 – p. 301

 **a)       **
```java
for (int i = 0; i < 10; i++)
{
   values[i] = i + 1;
}
```
 **b)       **
```java
for (int i = 0; i <= 10; i++)
{
   values[i] = i \* 2;
}
```
 **c)       **
```java
for (int i = 0; i < 10; i++)
{
   values[i] = (i + 1) \* (i + 1);
}
```
 **d)       **
```java
for (int i = 0; i < 10; i++)
{
   values[i] = 0;
}
```
 **e)       **
```java
int[] values =  {1, 4, 9, 16, 9, 7, 4, 9, 11};
```
 **f)       **
```java
for (int i = 0; i < 10; i++)
{
   values[i] = 0 % 2;
}
```
 **g)       **
```java
for (int i = 0; i < 10; i++)
{
   values[i] = 0 % 5;
}
```
# Review Exercises  R6.2 – p. 302

**a)**        25
**b)**        13
**c)**        12
**d)**        This loop condition causes an out-of-bounds index error.
If the condition were i < 10, total would be 22.
**e)**        11
**f)**        25
**g)**        12
**h)**        -1
**6.3 Common Array Algorithms [****Nov. 4, 2013]**

This section covers some of the most common algorighms for working with arrays. If you use a partially filled array, remember to replace values.length with the companion variable that represents the current size of the array.

6.3.1 **Filling**

This loop fills an array with squares (0, 1, 4, 9, 26, …)
```java
        for (int i = 0; i < values.length; i++)
        {
                values[i[] = i \* i;
        }
```
6.3.2 **Sum and Average Value**

You have already seen this algorithm in Section 4.7.1. When the values are located in an array, the code looks much simpler:
```java
        double[] values = {1, 2, 3, 4, 5};
        double total = 0;
for (double element : values)
        {
                total = total + element;
        }
        double average = 0;
if (values.length > 0)
{
        average = total / values.length;
}
```
6.3.3 **Maximum and Minimum**

This algorithm keeps a variable for the largest element already encountered.
```java
        double largest = values[0];
        for (int i = 1; i < values.length; i++)
        {
                if (values[i] > largest)
                {
                        largest = values[i];
                }
        }
```
**Note** : the loop starts at 1 because we initialize largest with values[0].

To compute the smallest element, reverse the comparison.

6.3.4 **Element Separators**

When you display the elements of an array, you usually want to separate them, often with commas or vertical lines, like this:

        `32  |  54  |  67.5  |  29  |  35`

**Note** that there is one fewer separator than there are numbers.
```java
        for (int i = 1; i < values.length; i++)
        {
                if (i > 0)
                {
                        System.out.print(" | "):
                }
        }
```
If you want comma separators, you can use the Arrays.toString method. The expression
        `Arrays.toString(values)`
Returns a string describing the contents of the array values in the form `[32, 54, 67, 29, 35]`

6.3.5 **Linear Search**

- Often need to search for the position of a specific element so you can replace or remove it
- Search each item in sequence until you find a match. (p. 260)

6.3.6 **Removing an Element**

- Need a companion variable for tracking number of elements in the array. (e.g. `currentSize`)
- A bit more complicated if the sequence of elements matters
- Find the element you want to remove
- Every element after that will have to be moved up 1 index and decrement the variable holding the size of the array

6.3.7 **Inserting an Element**

- Again, you need companion variable such as `currentSize`
- If order of elements doesn't matter, just insert new elements at the end
- For each insert, increment the currentSize
- More work to insert an element in the middle
- Must move all elements after the insertion location to a higher index before inserting

6.3.8 **Swapping  Elements**

- Requires a temporary variable (p. 262-illustrates the process)

6.3.9 **Copying Arrays**

- Array variable do not hold array elements, they hold reference to the actual array
- If you copy the reference, you get another reference to the array (See p. 263)
- For a true copy, call the `Arrays.copyOf()` method (illustrated in Figure 9-p. 263)
- Must have the following import statement: `import java.util.Arrays;`

6.3.10 **Reading Input**

- If you know how many inputs the user will supply, it is simple to place them into an array:
```java
double[] inputs = new double{NUMBER\_OF\_INPUTS];

for (i = 0; i < inputs.length; i++)

{

inputs[i] = in.nextDouble();}

//This doesn't work if you need to read a sequence of arbitrary length.
//In that case, add the inputs to an array until the end of the input has been reached.

int[] currentSize = 0;

while (in.hasNextDouble() && currentSize < inputs.length)

{

        inputs[currentSize] = in.nextDouble();

        currentSize++;

}
```
Now inputs is a partially filled array, and the companion variable currentSize is set to the number of inputs.

**Review the program**  **** **LargestInArray.java    (p. 265)**

Common Error 6.3        Underestimating the Size of a Data Set

Programmers commonly underestimate the amount of input data that a user will pour into an unsuspecting program.



# R6.1 (p. 301)

 a)
```java
for (int i = 0; i < 10; i++)
{
   values[i] = i + 1;
}
```
 b)
```java
for (int i = 0; i <= 10; i++)
{
   values[i] = i \* 2;
}
```
 c)
```java
for (int i = 0; i < 10; i++)
{
   values[i] = (i + 1) \* (i + 1);
}
```
 d)
```java
for (int i = 0; i < 10; i++)
{
   values[i] = 0;
}
```
 e)        **Skip this one**
```java
int[] values =  {1, 4, 9, 16, 9, 7, 4, 9, 11};
```
 f)
```java
for (int i = 0; i < 10; i++)
{
   values[i] = 0 % 2;
}
```
 g)
```java
for (int i = 0; i < 10; i++)
{
   values[i] = 0 % 5;
}
```
**Alternate Ways to Declare an Array**

Explain the alternate ways to declare arrays, and explain the subtle difference between putting the brackets after the data type and putting the brackets after the identifier.

Array declaration:
```java
_type_ [] _name_ = new _type_ [_size_];
int [] a = new int [400];        //by default all init. to zero
int [] a;        //declares a is a var that can reference this
a = new int[400];        //instantiates array of 400 ints ref by a
```
To get at 6th cell à  a[5] – "off by one error"

** a variable in an array has a 2-part name**
+ the id for the array and the cell [6] where it lives
+ aka indexed var, elements, subscripted var
+ [5] is called an index or subscript

**Don't be confused:**

The integer in brackets in the declaration of the array variable specifies the total number of cells in the array.

`int[] arrayNum = new int[totNum]`

The integer in brackets in an executable statement refers to a specific cell in that array.

`arrayNum[0] = 95;`

arrayNum[1] = 87;            etc.

When using an array in an assignment, condition, input, or output statement, always add the brackets and index at the end of the variable name to indicate which cell of the array you are referencing.

Index does not need to be an integer constant

Can use an integer variable or even a small integer expression

To create an array, you need to deploy the **new** operator, just as need to deploy the **new** operator to create a class instance.

To signal that an array is to be created, you include the type of the elements to be stored and a bracketed number that specifies how many elements the array is to store.  For example, to create an array of four integers, you write:  **new int [4]**

You can declare an integer-array variable and can assign an integer array to that variable:

**int durations [];       ** declare an array variable

**durations = new int [4];       ** create an "new" array

Alternatively, you can combine variable declaration and array creation:

**int durations [] = new int [4];**        declare and create an array



The **index value** specifies the position of the component in the array

**Index values start at 0.**

**In Java, [] is an operator, called the array subscripting operator**

The integer in brackets in the declaration of the array variable specifies the total number of elements in the array.

int[] arrayNum = new int[totNum]

The integer in brackets in an executable statement refers to a specific cell in that array.

arrayNum[0] = 95;

arrayNum[1] = 87;            etc.

An **array** contains a collection of **elements** , all of which have the same primitive type or class, that Java stores and retrieves using an integer **index**.  In Java, the first element of an array is indexed by zero; hence, Java is said to have **zero-based arrays**.

Array indices are from 0 to array.length – 1

After an array is created, you can enter values into the array elements

Java shorthand that combines declaring an array, creating an array, and initializing it at the same time.  Syntax:

     double[] myList = {1.9, 2.9, 3.4, 3.5};

Common Error  Length for String vs Length for Array

Array        a.length

String        a.length()

Size of an array **cannot** be changed after the array is created

Size can be obtained using **array.length**

Array elements are accessed through the index

Array indices are from 0 to (array.length – 1)

**You have to use an assignment operator to write data into the array.**

You can combine array creation and element insertion by using an **array initializer** , in which specific elements appear, separated by commas, and surrounded by brackets:

**int durations [] = {65, 87, 72, 75}**        array initializer

To use an array, once it is created, you need to know how to write into and to read from the various locations in the array, each of which is identified by a numerical index.

**Specifying Array Size during Program Execution**

1. 1.When you include a statement in a program to instantiate an array object, it is not necessary to know the size of the array at compile time.

1. 2.During program execution, you can first prompt the user to specify the size of the array and then instantiate the object.

The array size does not have to be a constant – it can be determined at run time

e.g. Ask how many grades will be entered?

        `input numGrades`

        then…

        `int [] allGrades = new int [numGrades];`

**Array Initialization during Declaration**

1. Like any other primitive data type variable, an array can also be initialized to specific values when it is declared.

1. The initializer list contains values, called initial values, which are placed between braces and separated by commas. Present several examples of declaring arrays using initializer lists.

1. When declaring and initializing arrays, the size of the array is determined by the number of initial values within the initializer list.

1. If an array is declared and initialized at the same time, we do not use the operator new to instantiate the array object.

**Arrays and the**  **Instance Variable**  **length**

The public instance variable length is associated with each array that has been instantiated, and the variable length contains the size of the array.

The declaration of an array variable does not allocate any space in memory for the array

You cannot assign elements to an array unless it has already been created

After an array variable is declared, you can create an array by using the new operator with the following syntax:
```java
    arrayName = new dataType[arraySize];
```
The above statement does 2 things:

1. creates an array using new
2. assigns the reference of the newly created array to the variable arrayName

Declaring an array variable, creating an array, and assigning the reference of the array to the variable can be combined in one statement, as follows:
```java
     dataType[] arrayName = new dataType{arraySize];
     double[] myList = new double[10];
        array variable = myList
       // creates array of 10 elements of double type
       // assigns its reference to myList
```
When space for an array is allocated, the array size must be given to specify # of elements that can be stored in it

Size of an array **cannot** be changed after the array is created

Size can be obtained using `array.length`

Array elements are accessed through the index

Consider **durations** —the one-dimensional array of integers.  To write data into that array, you use assignment statements in which the array name and a bracketed integer index appear on the left side of an assignment operator—the place where you are accustomed to seeing variable names.  The following statement, for example, inserts an integer into the place indexed by the value assigned to the **counter** variable:

`durations [counter] = 65;`

You can combine array creation and element insertion by using an **array initializer** , in which specific elements appear, separated by commas, and surrounded by brackets:

`int durations [] = {65, 87, 72, 75}`

The array initializer shown above specifies that an array is to be created, that the array is to store four elements, and that the initial values are to be 65, 87, 72, and 75.  Thus, one statement takes the place of the following five:
```java
int durations [] = new int [4];
durations[0] = 65;
durations[1] = 87;
durations[2] = 72;
durations[3] = 75;
```
To read data from the `durations` array, once the data have been written, you write an expression containing the array name and a bracketed integer index.  The following expression, for example, yields the integer stored in the place indexed by the value assigned to the counter variable:

`durations [counter]`

To obtain the length of an array, you can use the field-selection operator to obtain the value of the **length** instance variable:

`durations.length`

**Processing One-Dimensional Arrays**

1. Some of the basic operations performed on a one-dimensional array are to initialize the array, input data, output data stored in the array, and find the largest and/or smallest element in the array.

1. If the data type of an array component is numeric, a common operation is to find the sum and average of the elements of the array.

1. Each of these operations requires the ability to step through the elements of the array by using a loop.

1. Explain how to use a for loop to access array elements.

When processing array elements, you will often use the **for** loop because:

1. All of the elements in an array are of the same type

2. Since the size of the array is known, it is natural to use a for loop

Walk through Example 9-3 to explain ways that loops can be used to process arrays, and step through the code in Example 9-4.

**Base Address of an Array**

1. Define the base address of an array as the address (memory location) of the first array element. For example, if list is a one-dimensional array, then the base address of list is the address of the element list[0]. The value of the variable list is the base address of the array—the address of list[0].

1. When you pass an array as a parameter, the base address of the actual array is passed to the formal parameter.

**Declaring Arrays as Formal Parameters to Methods**

Just as you can pass the parameters of primitive types to methods, you can also pass the parameters of array types to methods

Java uses _pass by value_ to pass parameters to a method

Important differences between passing the values of variables of primitive data types and passing arrays:

1. For a parameter of a primitive type value, the actual value is passed.  Changing the value of the local parameter inside the method does not affect the value of the variable outside the method.

1. For a parameter of an array type, the value of the parameter contains a **reference** to an array; this reference is passed to the method.   **Any**** changes **to the** array **that occur inside the method body** will ****affect** the original array that was passed as the argument.

Thus far, we have used **one-dimensional** arrays to model linear collections of elements

To represent a **matrix** or a **table** , it is necessary to use a **two-dimensional** array

Occasionally, you will need to represent _n_–dimensional data structures

In Java, you can create n-dimensional arrays for any integer `n`, as long as your computer has sufficient memory to store the array

In Java, a two-dimensional array is declared as an array of arrays.  Syntax:
```java
dataType[][] arrayVariable
int[][] matrix;     // 2-dimensional array variable matrix of int values
matrix = new int[5][5];  // 2-dimensional array of 5 by 5 int values assigned to matrix
```
2 subscripts are used in a 2-dimensional array, one for the row, one for the column
```java
matrix = new int[5][5];
```
|   | [0] | [1] | [2] | [3] | [4] |
| --- | --- | --- | --- | --- | --- |
| [0] |   |   |   |   |   |
| [1] |   |   |   |   |   |
| [2] |   |   |   |   |   |
| [3] |   |   |   |   |   |
| [4] |   |   |   |   |   |
```java
matrix = new int[2][1] = 7;
```
|   | [0] | [1] | [2] | [3] | [4] |
| --- | --- | --- | --- | --- | --- |
| [0] |   |   |   |   |   |
| [1] |   |   |   |   |   |
| [2] |   | 7 |   |   |   |
| [3] |   |   |   |   |   |
| [4] |   |   |   |   |   |


```java
int[][] array = {{1,2,3},{4,5,6},{7,8,9}'{10,11,12}};
```
|   | [0] | [1] | [2] |
| --- | --- | --- | --- |
| [0] | 1 | 2 | 3 |
| [1] | 4 | 5 | 6 |
| [2] | 7 | 8 | 9 |
| [3] | 10 | 11 | 12 |

**Caution** :  It is a common mistake to use matrix[2,0] to access the element at row 2 and column 0.  In Java, each subscript must be enclosed in a pair of square brackets.

**6.4 Using Arrays with Methods (p. 268)**

- Arrays can occur as method arguments and return values.
- When you define a method with an array argument, you provide a parameter variable for the array
- Methods allow us to structure our solutions
```java
public static double sum(double[] values)
{
        double total = 0;
        for (double element : values)
        {
                total = total + element;
        }
        return total;
}
````

Review the steps on p. 269

- A method can also return an array
- Manipulate within the method and then return the array

**6.5 Problem Solving: Adapting Algorithms**  (p. 272)

- Saw some fundamental array algorithms in section 6.3
- In general, good strategy to have a repertoire of fundamental algorithms you can combine and adapt
- Example: (p. 272)

Given quiz scores of a student

Compute final quiz score (sum of all score after dropping the lowest one)

Steps:
  - Calculate the sum (6.3.2)
  - Find minimum value (6.3.3)
  - Remove the lowest (6.3.6)

- What this means is: you should be familiar with the implementation of fundamental algorithms so you can adapt them

**Programming Tip 6.2 Reading Exception Reports**  (p. 274-275) **Examine!!**

Good idea to figure out how to read/understand exceptions!!

Two pieces of useful information:

1. Name of the exception, such as ArrayIndexOutOfBoundsException (first line)
2. Stack trace, the method calls that led to the exception  line of offending code

**Practice** tracing issues with the Scores.java program (p. 277)  Blackboard

What is this program doing?
What are the method calls?
What is the difference between the method call and the method header?
When does control pass from main to a method?
1st method call -->  readInputs()
2nd method call -->  sum()
3rd method call -->  minimum()
What would be better method names for these methods??
Where should we put the halt in the program to watch the execution of sum and minimum?


**6.6 Problem Solving: Discovering Algorithms by Manipulating Physical Objects**  (p. 279)

- What do you do when none of the standard algorithms work for the task?
- How to solve:
- Given an array of 8 elements, you are to switch the first and the second halves.

Need to work out solutions **manually**!!!

On Friday we will cover **6.7 Two-Dimensional Arrays**

**Please read this section!!!**



**6.7 Two-Dimensional Arrays**** [Nov. 2, 2012]  ** (p. 282)

An arrangement of rows and columns of values  **two-dimensional array** or matrix

Use a two-dimensional array to store tabular data

A two-dimensional array is an **array of arrays**. Can be thought of as having rows and columns.

Like Excel:

        A        B        C        D etc.

1

2

3

| A1 | B1 | C1 | D1 |
| --- | --- | --- | --- |
| A2 | B2 | C2 | D2 |
| A3 | B3 | C3` | D3 |



| Row [0] Col [0] | Row [0] Col [1] | Row [0] Col [2] | Row [0] Col [3] |
| --- | --- | --- | --- |
| Row [1] Col [0] | Row [1] Col [1] | Row [1] Col [2] | Row [1] Col [3] |
| Row [2] Col [0] | Row [2] Col [1] | Row [2] Col [2] | Row [2] Col [3] |

To declare a 2-D array of scores:
```java
double[][] scores = new double[ROWS][COLS];
double[][] scores = new double[3][4];
```
**scores** array is an array of arrays

>The numbers 3 and 4 are size declarators. 3 = rows and 4 = cols

| scores[0][0] | scores[0][1] | scores[0][2] | scores[0][3] |
| --- | --- | --- | --- |
| scores[1][0] | scores[1][1] | scores[1][2] | scores[1][3] |
| scores[2][0] | scores[2][1] | scores[2][2] | scores[2][3] |

Constants!!
```java
final int ROWS = 3;
final int COLS = 4;
double[][] scores = new double[ROWS][COLS];
for (int row = 0; row < ROWS; row++)
{
        for (int col = 0; col < COLS; col++)
        {
                System.out.print("Enter a score: ");
                scores[row][col] = in.nextDouble();
        }
}
```
####6.7.1 Declaring Two-Dimensional Arrays

You get a two-dimensional array by supplying the number of rows and columns

A new int[7][3] array with 7 rows and 3 columns
```java
final int COUNTRIES = 7;
final int MEDALS = 3;
int[][] counts = new int[COUNTRIES] [MEDALS];
```
**or** you could also populate with {  } by grouping each row of data:
```java
int[][] counts =
{
        {1, 0, 1},
        {1, 1, 0},   etc.
}
```
As with one-dimensional arrays, you **cannot change the size** of a two-dimensional array once it has been declared.

6.7.2 Accessing Elements

To access a particular element, you to specify two index values in separate brackets to select the row and column

`int medalCount = counts[3][1];`

To access all elements in a two-dimensional array, you use two nested loops (p. 284)

Notes:

- A 2D array table containing integers is declared using:

`int [][] table = new int [10][10];`

- A nested for loop is used to access the 2D array.
- The inner for loop selects the column position, starting at 0 and progresses to col = 9.
- Once this happens, the row value is incremented.
- Then each of the column positions is revisited for the new row position.
- Within the first loop, it is necessary to multiply together (row + 1) and (col + 1) to obtain each value in the table.
- This is because the first element in an array has an index of 0.
- In the second loop, a tab is used within the inner loop to space the numbers.
- At the end of the row, a println() statement is used to go to the next line.
