Download Link: https://assignmentchef.com/product/solved-lab-1-manipulating-bits-using-c
<br>
<h2><a name="_Toc6066"></a>Overview</h2>

The purpose of this assignment is to become more familiar with data at the bit-level representation. You’ll do this by solving a series of programming “puzzles”. Many of these puzzles may seem artificial, but in fact bit manipulations are very useful in cryptography, data encoding, implementing file formats (e.g., MP3), etc. By working your way through these problems, you will get very familiar with bit representations and hopefully will have some fun. You will also be doing some very basic pointer manipulations and arithmetic. Again, the purpose is to get you familiar with data representations and pointers.

<h2><a name="_Toc6067"></a>Instructions</h2>

<strong>Perform an update to your course-materials directory </strong>on the by running the update-course command from a terminal window. On the script’s success, you should find the provided code for lab1 in your course-materials directory. As a convenience, here is an archive of the course-materials directory as of this lab assignment: <a href="https://spark-public.s3.amazonaws.com/hardware/labs/lab1.tar.gz">lab1.tar.gz</a><a href="https://spark-public.s3.amazonaws.com/hardware/labs/lab1.tar.gz">.</a>

The lab1 folder contains a number of tools, described later, a bits.c file, and a pointer.c file. Both files contain skeletons for the programming puzzles, along with a comment block that describes exactly what the function must do and what restrictions there are on its implementation. Your assignment is to complete each function skeleton using:

<ul>

 <li>only straightline code (i.e., no loops or conditionals);</li>

 <li>a limited number of C arithmetic and logical operators; and</li>

 <li>no constants larger than 8 bits (i.e., 0 – 255 inclusive).</li>

</ul>

The intent of the restrictions is to require you to think about the data as bits – because of the restrictions, your solutions won’t be the most efficient way to accomplish the function’s goal, but the process of working out the solution should make the notion of data as bits completely clear.

Similarly, you will start working with basic pointers and use them to compute the size of different data items in memory and to modify the contents of an array

<h2><a name="_Toc6068"></a>The Bit Puzzles</h2>

This section describes the puzzles that you will be solving in bits.c. More complete (and definitive, should there be any inconsistencies) documentation is found in the bits.c file itself.

<h3><a name="_Toc6069"></a>Bit Manipulations</h3>

The table below describes a set of functions that manipulate and test sets of bits. The Rating column gives the difficulty rating (the number of points) for each puzzle and the Description column states the desired output for each puzzle along with the constraints. See the comments in bits.c for more details on the desired behavior of the functions. You may also refer to the test functions in tests.c. These are used as reference functions to express the correct behavior of your functions, although they don’t satisfy the coding rules for your functions.

<table width="665">

 <tbody>

  <tr>

   <td width="94">Rating</td>

   <td width="105">Function Name</td>

   <td width="465">Description</td>

  </tr>

  <tr>

   <td width="94">1</td>

   <td width="105">bitAnd</td>

   <td width="465">x &amp; y using only ~ and |</td>

  </tr>

  <tr>

   <td width="94">1</td>

   <td width="105">bitXor</td>

   <td width="465">x ˆ y using only ~ and &amp;</td>

  </tr>

  <tr>

   <td width="94">1</td>

   <td width="105">thirdBits</td>

   <td width="465">return word with every third bit (starting from the least significant bit) set to 1</td>

  </tr>

  <tr>

   <td width="94">2</td>

   <td width="105">getByte</td>

   <td width="465">Extract byte n from word x</td>

  </tr>

  <tr>

   <td width="94">3</td>

   <td width="105">logicalShift</td>

   <td width="465">shift x to the right by n, using a logical shift</td>

  </tr>

  <tr>

   <td width="94">4</td>

   <td width="105">bang</td>

   <td width="465">Compute !x without using !</td>

  </tr>

  <tr>

   <td width="94">Extra Credit:3</td>

   <td width="105">conditional</td>

   <td width="465">x ? y : z</td>

  </tr>

 </tbody>

</table>

<h3><a name="_Toc6070"></a>Two’s Complement Arithmetic</h3>

The following table describes a set of functions that make use of the two’s complement representation of integers. Again, refer to the comments in bits.c and the reference versions in tests.c for more information.

<table width="611">

 <tbody>

  <tr>

   <td width="94">Rating</td>

   <td width="105">Function Name</td>

   <td width="412">Description</td>

  </tr>

  <tr>

   <td width="94">2</td>

   <td width="105">fitsBits</td>

   <td width="412">returns 1 if x can be represented as an n-bit, two’s complement integer</td>

  </tr>

  <tr>

   <td width="94">2</td>

   <td width="105">sign</td>

   <td width="412">return 1 if positive, 0 if zero, and -1 if negative</td>

  </tr>

  <tr>

   <td width="94">3</td>

   <td width="105">addOK</td>

   <td width="412">Determine if x+y can be computed without overflow</td>

  </tr>

  <tr>

   <td width="94">Extra Credit:4</td>

   <td width="105">isPower2</td>

   <td width="412">returns 1 if x is a power of 2, and 0 otherwise</td>

  </tr>

 </tbody>

</table>

2

<h3><a name="_Toc6071"></a>Checking Your Work</h3>

We have included two tools to help you check the correctness of your work.

dlc is a modified version of an ANSI C compiler from the MIT CILK group that you can use to check for compliance with the coding rules for each puzzle. The typical usage is:

$ ./dlc bits.c

The program runs silently unless it detects a problem, such as an illegal operator, too many operators, or non-straightline code in the integer puzzles. Running with the -e switch:

$ ./dlc -e bits.c causes <sub>dlc </sub>to print counts of the number of operators used by each function. Type <sub>./dlc -help </sub>for a list of command line options.

btest is a program that checks the functional correctness of the code in bits.c. To build and use it, type the following two commands:

$ make

$ ./btest

Notice that you must rebuild <sub>btest </sub>each time you modify your bits.c file. (You rebuild it by typing <sub>make</sub>.) You’ll find it helpful to work through the functions one at a time, testing each one as you go. You can use the <sub>-f </sub>flag to instruct <sub>btest </sub>to test only a single function:

$ ./btest -f bitXor

You can feed it specific function arguments using the option flags <sub>-1</sub>, <sub>-2</sub>, and <sub>-3</sub>:

$ ./btest -f bitXor -1 7 -2 0xf

Check the file README for documentation on running the <sub>btest </sub>program.

<h3><a name="_Toc6072"></a>Advice</h3>

<strong>Start early on bits.c</strong>, if you get stuck on one problem move on. You may find you suddenly realize the solution the next day. Puzzle over the problems yourself, it is much more rewarding to find the solution yourself than stumble upon someone else’s solution. If you do not quite meet the operator limit don’t worry there will be partial credit, but often times working with a suboptimal solution will allow you to see how to improve it.

Do not include the <sub>&lt;stdio.h&gt; </sub>header file in your bits.c file, as it confuses dlc and results in some non-intuitive error messages. You will still be able to use printf in your bits.c file for debugging without including the &lt;<sub>stdio.h&gt; </sub>header, although <sub>gcc </sub>will print a warning that you can ignore.

You should be able to use the debugger on your code. For example:




$ make gcc -O -Wall -m32 -g -lm -o btest bits.c btest.c decl.c tests.c gcc -O -Wall -m32 -g -o fshow fshow.c gcc -O -Wall -m32 -g -o ishow ishow.c

$ gdb ./btest

GNU gdb (GDB) Fedora (7.1-34.fc13)

Copyright (C) 2010 Free Software Foundation, Inc.

License GPLv3+: GNU GPL version 3 or later &lt;http://gnu.org/licenses/gpl.html&gt; This is free software: you are free to change and redistribute it. There is NO WARRANTY, to the extent permitted by law. Type “show copying” and “show warranty” for details.

This GDB was configured as “i686-redhat-linux-gnu”.

For bug reporting instructions, please see:

&lt;http://www.gnu.org/software/gdb/bugs/&gt;.

Reading symbols from /homes/iws/dvhc/cse351/lab1/src/btest…done.

(gdb) b bitXor Breakpoint 1 at 0x8048717: file bits.c, line 144.

(gdb) r

Starting program: /homes/iws/dvhc/cse351/lab1/src/btest

ScoreRatingErrorsFunction

Breakpoint 1, bitXor (x=-2147483648, y=-2147483648) at bits.c:144 144}

(gdb) p x

$1 = -2147483648

(gdb) p/x x

$2 = 0x80000000

(gdb) q

A debugging session is active.

Inferior 1 [process 12728] will be killed.

Quit anyway? (y or n) y

The <sub>dlc </sub>program enforces a stricter form of C declarations than is the case for C++ or that is enforced by gcc. In particular, in a block (what you enclose in curly braces) all your variable declarations must appear before any statement that is not a declaration. For example, <sub>dlc </sub>will complain about the following code:

int foo(int x)

{

int a = x;

a *= 3;         /* Statement that is not a declaration */ int b = a; /* ERROR: Declaration not allowed here */

}

Instead, you must declare all your variables first, like this:

int foo(int x)

{

int a = x; int b;

a *= 3; b = a;

}

<h2><a name="_Toc6073"></a>Using Pointers</h2>

This section describes the four functions you will be completing in pointer.c that is also in the lab1 folder you downloaded. Refer to the file pointer.c itself for more complete details.

<h3><a name="_Toc6074"></a>Pointer Arithmetic</h3>

The first three functions in pointer.c ask you to compute the size (in bytes) of various data elements (ints, doubles, and pointers). You will accomplish this by noting that arrays of these data elements allocate contiguous space in memory so that one element follows the next. <strong>You are permitted to use casts for these functions.</strong>

<h3><a name="_Toc6075"></a>Manipulating Data Using Pointers</h3>

The fourth function in pointer.c asks you to change the value of an element of an array using only the starting address of the array. You will add the appropriate value to the pointer to create a new pointer to the data element to be modified.

The next two functions deal with boundings checking of pointers and the final function deals with more bit manipulation. You

<h3><a name="_Toc6076"></a>Checking your work</h3>

For pointer.c, we have included a simple test harness: ptest.c. You can test your solutions like this:

$ make ptest

$ ./ptest

This test harness only checks if your solutions return the expected result, not if they meet the specific criteria of each problem. We will review your solutions to ensure they meet the restrictions of the assignment.