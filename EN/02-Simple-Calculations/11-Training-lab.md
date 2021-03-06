[slide]
# Exam Problems

Now, after having revised how to make simple calculations and how to read and print numbers from the console, let' s go to the tasks. We will solve a few **problems from a SoftUni entrance exam**.

## Problem: Training Lab

[code-task title="Training lab" executionStrategy="csharp-dot-net-core-code" requiresInput]

[code-editor language=csharp]
[/code-editor]

[task-description]
**A training lab** has a rectangular size **l** to **w** meters, without columns on the inside. The hall is divided in two parts- left and right, with a hallway approximately in the middle. In both of the parts, there are **rows with desks**. In the back of the hall, there is a big **entrance door** and in the front, there is a **podium** for the lecturer. A single **working place** takes up **70 to 120 cm** (a table with size 70 to 40 cm + space for a chair with size 70 to 80 cm). **The hallway** width is at least **100 cm**. It is calculated that due to the **entrance door** (which is with 160 cm opening), **exactly one working space is lost**, and due to the **podium** (which is with size 160 to 120 cm), exactly **two working spaces** are lost. Write a program that receives the size of the training lab as input parameters and calculates the **number of working places in it**(look at the figure).
[/task-description]

[code-io /]

[/code-task]

### Input Data

**Two numbers** are read from the console, one per line: **l** (length in meters) and **w** (width in meters).

Constraints: **3 ≤ w ≤ l ≤ 100.**

### Output Data

Print an integer: the **number of working places** in the training lab.

### Sample Input and Output

|   Input   | Output | Figure |
|-----------|--------|--------|
|15<br>8.9  |  129   | [image src=https://github.com/SoftUni/Programming-Basics-Book-CSharp-EN/blob/master/assets/chapter-2-2-images/01.Training-lab-01.png alt="Training Lab" /] |
|8.4<br>5.2 |  39    | [image src=https://github.com/SoftUni/Programming-Basics-Book-CSharp-EN/blob/master/assets/chapter-2-2-images/01.Training-lab-02.png alt="Training Lab" /] |

#### Clarification of the examples:

In the first example, the hall length is 1500 cm. **12 rows** can be situated in it (12 * 120 cm = 1440 + 60 cm difference). The hall width is 890 cm. 100 cm from them are for the hallway in the middle. The rest 790 cm can be situated by **11 desks per row** (11 * 70 cm = 770 cm + 20 cm difference). **Number of places = 12 * 11 - 3** = 132 - 3 = **129** (we have 12 rows with 11 working places = 132 minus 3 places for podium and entrance door).

In the second example, the hall length is 840 cm. **7 rows** can be situated in it (7 * 120 cm = 840, no difference). The hall width is 520 cm. 100 cm from them are for the hallway in the middle. The rest 420 cm can be situated by **6 desks per row** (6 * 70 cm = 420 cm, no difference). **Number of places = 7 * 6 - 3** = 42 - 3 = **39** (we have 7 rows with 6 working places = 42 minus 3 places for podium and entrance door).

### Hints and Guidelines

Try to solve the problem on your own first. If you do not succeed, go through the hints.

#### Idea for Solution

As it is with any programming task, **it is important to build an idea for its solution**, before having started to write code. Let' s carefully go through the problem requirements. We have to write a program that calculates the number of working places in a training lab, where the number depends on the hall length and height. We notice that the received input will be **in meters** and the information about how much space the working places and hallway take, will be **in centimeters**. To do the calculations, we will use the same measuring units, no matter whether we choose to convert length and height to centimeters or the other data in metres. The first option is used for the presented solution.  

Next, we have to calculate **how many columns and how many rows** with desks will fit. We can calculate the columns by **subtracting the width by the necessary space for the hallway (100 cm) and divide the difference by 70 cm** (the length of a working place). We find the rows by **dividing the length by 120 cm**. Both operations can result in **a real number** with whole and fractional part but we have to **store only the whole part in a variable**. In the end, we multiply the number of rows by the number of columns and divide it by 3 (the lost places for entrance door and podium). This is how we calculate the wanted value.

#### Choosing Data Types

From the example, we see that a real number with whole and fractional part can be received as an input, therefore, it is not appropriate to choose data type `int`. This is why we use `double`. Choosing data type for the next variables depends on the method we choose to solve the problem. As with any programming task, this one has **more than one way to be solved**. Two methods will be shown here.

#### Sample Implementation of the Solution

It is time to go to the solution. We can divide it into three smaller tasks:
- **Reading input from the console**.
- **Doing the calculations**.
- **Printing the output on the console**.

The first thing we have to do is read the input from the console. With `Console.ReadLine()` we read the values from the console and with the function `double.Parse(…)` string is converted into `double`.

[image src=https://github.com/SoftUni/Programming-Basics-Book-CSharp-EN/blob/master/assets/chapter-2-2-images/01.Training-lab-03.png alt="Code" /]

Let' s go to the calculations. The special part here is that after having divided the numbers, we have to store only the whole part of the reslt in a variable.

<table><tr><td><img src="https://github.com/SoftUni/Programming-Basics-Book-CSharp-EN/blob/master/assets/alert-icon.png" style="max-width:50px" /></td><td><b>Search in Google!</b> Whenever we have an idea how to solve a particular problem but we do not know how to write it in C# or we are dealing with one that many other people have had before us, the easiest way to solve it is by looking for information on the Internet.</td></tr></table>

In this case, we can try with the following search: [anchor href=https://www.google.com/?q=c%23+get+whole+number+part+of+double]**c# get whole number part of double**[/anchor]. One possible way is to use the method `Math.Truncate(…)` as it works with `double` data types. For the number of rows and columns we create variables of the same type.

[image src=https://github.com/SoftUni/Programming-Basics-Book-CSharp-EN/blob/master/assets/chapter-2-2-images/01.Training-lab-04.png alt="Code" /]

Second method: As we already know, the operator for division `/` operates differently on integers and decimals. **When dividing integer with integer,the result is also an integer**. Therefore, we can search how to convert the real numbers, which we have as values for the heigth and the width, into integers and then divide them.

In this case, there could be **data loss** after having removed the fractional part, so it is necessary that it is converted **expressly** (explicit typecasting). We use the operator for converting data `(type)` by replacing the word **type** with the needed **data type** and place it **before the variable**. (you can learn more about data type conversion here [anchor href=http://www.introprogramming.info/intro-csharp-book/read-online/glava3-operatori-i-izrazi/#_Toc298863977]Svetlin Nakov, Veselin Kolev and team: "Programming Basics with C#", стр. 153-157[/anchor]).

[image src=https://github.com/SoftUni/Programming-Basics-Book-CSharp-EN/blob/master/assets/chapter-2-2-images/01.Training-lab-05.png alt="Code" /]

With `Console.WriteLine(…)` we print the result on the console.

[image src=https://github.com/SoftUni/Programming-Basics-Book-CSharp-EN/blob/master/assets/chapter-2-2-images/01.Training-lab-06.png alt="Code" /]

#### Test in the Judge system

Test your solution here: [anchor href=https://judge.softuni.bg/Contests/Practice/Index/505#0]https://judge.softuni.bg/Contests/Practice/Index/505#0
[/anchor].
[/slide]
