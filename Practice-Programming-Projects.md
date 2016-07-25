# IT@JCU - Projects for Programming Practice

Here is a collection of projects for you to practise your programming with, arranged by topic.

## Selection

1. Write a program to check if someone can vote. They need to be 18 or over and be enrolled to vote.   
You could do two versions - one with nested ifs and one with the 'and' operator.
2. Implement an expert system based on a flowchart you make or find. Each diamond (in a properly drawn example) is a question.  
Examples:
    1. <http: 3.bp.blogspot.com="" _gy_nfovztsk="" rjjxel2wesi="" aaaaaaaaafm="" eeyntwkhyw0="" s400="" problemsolving_flowchart.png="">
    2. <http: xkcd.com="" 627="">
    3. <http: www.mathworks.com="" help="" techdoc="" creating_plots="" driver_flowchart.png="">
    4. <http: www.mentalfloss.com="" blogs="" wp-content="" uploads="" 2010="" 05="" 345horse.jpg="">

## Loops

1. Write a menu-driven program that loops until the user quits. The options are (G)et name, (U)ppercase, (L)owercase, (Q)uit.  
The program should start by asking the user for their name before the menu, but they can (G)et a new name. U/L print the name in either uppercase or lowercase.
2. Print the square of numbers between a given range. Ask the user for a lower number and a higher number, then print all of the squares of the numbers in that range (inclusive).   
Error-check the second number to make sure it is higher than the first.
3. (Write this as a function if you like.)  
Print a "progress bar" based on a percentage (number). E.g. 50% would print something like: `|*****-----|`, 10% would print `|*---------|`  

4. Modify your previous progress bar code so you can specify a width for the bar (if using a function, pass in the percentage and width). E.g. 50% of 18 would be:`|*********---------|`

## Functions

1. Write a function that calculates which of two products is cheaper based on a quantity and price. The function will take 4 parameters - the quantity and price of each product, and output either "First" or "Second".
2. Modify your house cost program from the pracs so it uses functions. For the calculation function, pass it the options the user chose (including premium and family discount).
3. Write a function

### Recursion

1. Write a recursive function that prints all of the numbers from a given input down to 0.
2. Write a recursive function that displays all of the letters in a string. (Each function call displays one letter.)
3. Write a program that prints a string from the outside in, using recursion.  
E.g. if the string to print is "Programming", your program should print: "P g r n o i g m r m a".  
Remember to analyse and design this problem first. Think about the base and recursive cases - when will it stop (base) and how will it reduce the problem (recursive) each time?
4. Write a recursive function to determine if a string is a palindrome (e.g. hannah is a palindrome, but han is not).

## File I/O

1. Modify the GPA program from your prac (week 5) so you read the scores from a file. The program should print each score and the corresponding grade pluse the final GPA at the end.
2. (GPA stands for Grade Point Average. You should aim to have a high one! [Here's JCU's page about GPA and how it is calculated][1].)

Write a program that uses functions to do the following:

    * Use a menu to present the user with options, as shown in the output below. Make a function for your menu that displays the menu text, gets the user's choice and converts it to uppercase (and returns it).
    * Calculating a grade is based on the user's score and works like: &lt;50 = N, 50-64 = P, 65-74 = C, 75-84 = D, &gt;= 85 = HD.   
(Floats should be handled, e.g. 74.95 is a C.)  
Use a function that only calculates the grade, but does not display it.   
**NOTE:** Very important. You could write a function that takes no parameters and returns nothing, but asks the user for a score and prints the grade, BUT then you could ONLY use this function in the situation where you want to do those two things. What if you wanted to read a file of scores and write the grades to another file? You'd need another nearly-identical function. **SO INSTEAD**... Pass the score in as an input parameter and return the grade (string) - displaying it should be done in the main function.
    * Use a "dummy" function for calculateGPA. So write a function definition that just prints "Your GPA is ...", but set up the main program so it calls this.  
This sort of programming is useful when you want to do a bit at a time - you can set it up and get your structure right, then come in and fill in the details later (see extension).
    * You should have 4 functions including main. Think about what you should name them (verbs) and what the parameters and return values should be.  

&gt; &gt;         Name: Jimbo
&gt;         Hello Jimbo. Choose:
&gt;         (D)etermine Grade
&gt;         (C)alculate GPA
&gt;         (Q)uit
&gt;         &gt;&gt;&gt; i
&gt;         Invalid option
&gt;         Hello Jimbo. Choose:
&gt;         (D)etermine Grade
&gt;         (C)alculate GPA
&gt;         (Q)uit
&gt;         &gt;&gt;&gt; d
&gt;         What is your total score? 67
&gt;         C
&gt;         Hello Jimbo. Choose:
&gt;         (D)etermine Grade
&gt;         (C)alculate GPA
&gt;         (Q)uit
&gt;         &gt;&gt;&gt; D
&gt;         What is your total score? 85
&gt;         HD
&gt;         Hello Jimbo. Choose:
&gt;         (D)etermine Grade
&gt;         (C)alculate GPA
&gt;         (Q)uit
&gt;         &gt;&gt;&gt; c
&gt;         Your GPA is ...
&gt;         Hello Jimbo. Choose:
&gt;         (D)etermine Grade
&gt;         (C)alculate GPA
&gt;         (Q)uit
&gt;         &gt;&gt;&gt; q
&gt;         Thank you.

    * Add the calculateGPA facility to your grade program:
        * It should ask the user for each of their subject scores (raw numbers), convert the score to a grade, convert the grade to a weight, then calculate the average of those.
        * Use a while loop to ge their scores until they enter a negative value (that's the sentinel or stopping condition).   
If we were able to use lists, we could store each score for later and our GPA function could accept a list, but we will just calculate the total on the fly (like we did for average age last week), so we need to keep track of the number of subjects.
        * Weights for GPA are: N = 1.5, P = 4, C = 5, D = 6, HD = 7
        * Think about what functions you need to write and what functions you can reuse.
3. Modify the above program so that the file also has subject codes - i.e. each line looks something like `CP1404 86`
4. Write a program that allows the user to find how many times a word appears in a file. They should enter the filename and a word, and it tells them how many times the word is in that file.

## Lists &amp; Dictionaries

1. Let's see if you can cheat on multiple-choice exams... Write a program to determine which answers appear most frequently (a, b, c, d...). The tutorial solutions contain some multiple-choice answers, so store these in a text file, then write a program that prints the answers (sorted) and how frequently they occur. E.g. it might print: B: 13, C: 12, D: 9, A: 4
2. Modify the price checker program from the functions section so that product information is stored in a list - the checking function will take two parameters - lists that each contain description, quantity and price.
3. Modify the word-counting program (from File I/O) so that the user can enter an arbitrary number of words and it prints the number of times each of those words occurs.
4. Write a program to store your phone book in a dictionary. Give the user choices (menu) for adding, deleting, modifying and searching for entries.
5. **_HARD _**_Sieve of Eratosthenes (about prime numbers)  
_Let's say you need to display all the prime numbers from 2 to 10 billion (1010), because you want to impress your boss or something. To work out if a number is prime, you need to see if any of the prime numbers less than its square root divide it. So for numbers around 10 billion, we'd need to check every prime number up to about 100,000 to see if it's a divisor. But we don't want to waste our time recomputing all those prime numbers every single time we want to test a big number for primality. We want a list of primes up to 100,000, and the best (non-highly complicated) way to construct such a list is the Sieve of Erastosthenes (it's very likely that you don't know anywhere near enough maths to try the faster Quadratic Sieve. You can look it up on Wikipedia, or follow the guide below.

Start off with a list of 100,001 Boolean values, all **True** (because let's assume a number is prime until we prove otherwise), so let's write **primalityList = [True] * (NUMBER_OF_PRIMES + 1)**.  
Here's the algorithm. Start off by setting primalityList[0] and primalityList[1] to False (because 0 and 1 are not primes). Then, **biggestPrimeSoFar = 2**. Now skip through the list and set every multiple of biggestPrimeSoFar to False. Then, find the first index of primalityList that has the value True, and set biggestPrimeSoFar to that. We're using nested loops here, and we'll finish when biggestPrimeSoFar hits the square root of NUMBER_OF_PRIMES or higher. At that point, primalityList has True **only for prime numbers up to NUMBER_OF_PRIMES**.

For determining primality of numbers up to NUMBER_OF_PRIMES squared, we want a list that **contains** those numbers instead of True or False. So build it! primes = [], iterate through primalityList and add the indexes that have True. Done!

Now, for numbers up to NUMBER_OF_PRIMES squared, you just need to see if any of the numbers in **primes** divides it to determine if it's prime. This is dramatically quicker than recalculating the primes each time.

## Classes

1. Create classes and client for each of the following items. For each one, think about what internal attributes it might have and what methods might be useful.
    1. computer
    2. building
    3. car
    4. phone
    5. clothing item
    6. etc. (you think of more)
2. Take some of the earlier questions in the subject and in this projects list and convert them to use objects. Anywhere that you might have used multiple data items that were related can be combined (encapsulated) into a class.

## More Study Ideas

1. Pair up, then each of you write some code that prints things (use some/all of loops, if/elif/else, functions)… and get the other person to write the output. ("What is the output of the following code: ?")
2. Take the list of exam topics from the PPT notes, save these in a text file (phrases separated by commas, all on one line). Load this file and print the contents in sorted order.  

3. Extending the previous program, use a dictionary to print the topics in sorted order with their occurrences, e.g. functions: 5, loops: 4, recursion: 1  

4. Extending…write the topics to a file, sorted and only one instance of each  

5. Take some textbook, tutorial, practical, or other questions and write similar questions… and then answer them… and share them with each other  

6. For some of the existing (or new) questions, write pseudocode instead of Python  

7. Write a program to determine your expected grade in the subject based on your current and expected marks – either from user input or from a file.

[1]: http://www.jcu.edu.au/student/assessment/JCUDEV_011378.html
  </http:></http:></http:></http:>