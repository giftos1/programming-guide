This page contains standard 'patterns' that you should get used to. When you need to perform one of these tasks, follow the standard pattern.

For the most part, this guide is not language-specific, so many patterns are presented as *pseudocode*.  
*Python 3* is used where actual code is provided... and Python is similar enough to pseudocode that this is usually suitable as a pattern.


- [Main program structure](#main-program-structure)
- [Decision structures](#decision-structures)
  - [if with no else](#if-with-no-else)
  - [if, else](#if-else)
  - [if, elif, else (or switch/case statement)](#if-elif-else-or-switchcase-statement)
  - [if, elif with no trailing else](#if-elif-with-no-trailing-else)
  - [if, if, if](#if-if-if)
  - [Boundary conditions](#boundary-conditions)
- [Repetition structures](#repetition-structures)
  - [For loops (definite iteration)](#for-loops-definite-iteration)
  - [While loops (indefinite iteration)](#while-loops-indefinite-iteration)
  - [Menus](#menus)
  - [Error checking](#error-checking)
  - [Exception-based error checking](#exception-based-error-checking)
  - [Function with error checking](#function-with-error-checking)
  - [Finding](#finding)
  - [Filtering](#filtering)
- [Constants](#constants)
- [Don't Repeat Yourself (DRY)](#tba)
- [Working with Booleans](#working-with-booleans)
- [Function design](#function-design)
  - [Why is this important?](#why-is-this-important)
- [Data storage](#data-storage)
- [Never](#never)

## Main program structure
For most programs, you will have a `main` function and a number of other functions.  
Think of main as the whole program with the other functions as the tools that main uses, with the details abstracted away.  
main should go at the top of your file, and someone reading your code for the first time should be able to look at main and understand what the program does... that is, main should "look like" the whole program.  
In the following example pseudocode, the specifics don't matter, but you can see the program structure and how the functions contain the detail:

    """ module-level docstring """
    import statements
    constants

    function main()
        opening statement
        result = do_step1()
        do_step2(result)
        closing statement
    
    function do_step1()
        ...
        return result
    
    function do_step2(parameter)
        ...


    main()

## Decision structures
When you need to make a decision in your program, you would usually use one of the following patterns.  
(See loops below for when you need to repeatedly make decisions, e.g., for most error-checking.)

The examples below will use situations where you want to print a *result* for a given *score*, where `score` is an integer. Each situation could be stand-alone, or part of a loop, like `for score in scores:`

### if with no else
Use this if you want to do something when the condition is true, but do nothing when it's false.  
In this example, we don't want to print anything for the non-exceptional scores, so there's no else.
    
```python
if score >= 90:
    print("That's exceptional!")
```

Some beginning programmers use else for no reason, like the following example... This is redundant and never of any value... Don't do it.

```python
if score >= 90:
    print("That's exceptional!")
else:
    pass
```

### if, else
Use this if you want to do something when the condition is true, and something different when it's false.  
In this example, we want to print a result for the score no matter what its value is.
Note that we do not need a second condition to handle the "fail" case, because if the score is not >= 50 we already know that it must be < 50.

```python
if score >= 50:
    print("Pass")
else:
    print("Fail")
```

### if, elif, else (or switch/case statement)
Use this if you want to handle all cases in some way - in our example, there will be an output printed for every possible score. This is the pattern that we use for menus as well - handle each menu option we know about and the trailing else handles the invalid option (see below).  
In this example, we always want to print one result for the score no matter what its value is.

```python
if score >= 90:
    print("Excellent")
elif score >= 50:
    print("Passable")
else:
    print("Bad")
```

### if, elif with no trailing else
Similar to the if with no else, use this when you want to handle multiple possible results, but there will be some cases where there is no result handled. The results are mutually exclusive, but you're happy to do nothing in some cases.  
**If you use this pattern, ask yourself, "what cases/inputs do I NOT want to handle?", or "What scenario do I want to ignore?"**  
If there is no answer to that question, you should not use this pattern.  

In the following example, the very high scores win a prize, but the others don't, and we don't need to tell them. (E.g., at graduation, they announce which graduates get a University medal, but they don't say which ones do not get a medal.)

```python
if score >= 90:
    print("You win a car!")
elif score >= 80:
    print("You win a horse :)")  # but you do not win a car AND a horse
```

### if, if, if
Use this when you want multiple outcomes. That is, the results/outcomes are not mutually exclusive. One condition being true does not affect the other conditions.  
In the following example, we want to print all the results that a score could achieve.

```python
if score >= 90:
    print("You win a car!")
if score >= 80:
    print("You win a horse :)")  # here, you can win BOTH a car and a horse
if score >= 50:
    print("You passed")
```

So, as you design your decision structures, recognise what each pattern is for and how it applies to your situation.  
E.g., You would not use the "if, if, if" pattern for determining a grade (N, C, HD...) from a percentage - you know that would be inefficient since those grades are mutually exclusive - as soon as we know what grade it is, we don't need to ask any more.

### Boundary conditions
(This applies to both decision and repetition structures so it's here between them.)  
Some of the most common programming errors happen with boundary conditions and so these should usually always be tested explicitly. In the examples above, 50 is a pass. But if we get our boundary condition wrong, we might have something like:

```python
if score > 50:
    print("You passed")
# or
if score > 49:
    print("You passed")
```
In the first case (`score > 50`), this works for all values _greater than_ 50, but it would make 50 a fail, not a pass as it should be. If you test your code using the boundaries as input values, you will see that 50 is not a pass. If you have a program with 7 boundaries (e.g., N, P, C, D, HD, too high, too low), you'll need to test all 7, plus some others.  
In the second case, this works for now, but we have 2 problems: the *problem domain* specifies that 50 is a pass, so we should use the value `50`, not change it to something we hope works - there's a chance we might make a mistake; secondly, if we change score to be a `float` instead of an `int` we now have failing values like `49.1` that will result in pass when they should not!  

Did you catch that? **Use the values and names in the problem domain** - e.g., the problem description says that a _score_ of `50` or more_ is a _pass_, so use the values and names: `score`, `50`, `pass`.  
It's much harder to make a mistake when you're following what the problem description says... Just check those boundaries when you write them (> 50 or >= 50 or < 50 or <= 50 or == 50...?) and test them!  

## Repetition structures
In most languages, there are multiple kinds of loops and you should choose the most appropriate kind.  
The most common choice is:

- Use *for loops* for **definite** iteration, like `for item in sequence...`
- Use *while loops* for **indefinite** iteration, like `while condition...`

Using a while loop and maintaining your own counter (e.g., using a while loop to iterate through the numbers from 1 to 10) would be considered an *anti-pattern*, since this is what for loops are for!  
Using a for loop and maintaining your own counter (e.g., iterating through elements in a list and manually using +1 for the index) would also be poor, since for loops can do this for you.  

### For loops (definite iteration)
For loops are mostly used when you want to do something with each item in a sequence.   
In Python, if you want a sequence of numbers, this can be generated with `range`.
One tip for variable naming... you will _very often_ end up with loops of the form:

    for singular in plural:
        ...

Example, `for dog in dogs`, `for number in numbers`, `for book in books`...
If you find yourself writing something that doesn't match this, you might be in trouble.  
Example:

```python
names = ["Barry", "Tux", "Ada", "Maggie"]
for i in names:
    print(i, " - ")  # WAIT, what's i? A name?!?
```

In Python, if you need _both_ the index and the element, use the function `enumerate`, e.g.

```python
names = ["Barry", "Tux", "Ada", "Maggie"]
for i, name in enumerate(names):
    print(i, " - ", name)
```

### While loops (indefinite iteration)
Almost all while loops follow the same standard pattern (as below with menus and error checking).  
Do not force the loop to be True the first time by setting a value for your loop condition variable, 
and do not use `while True`... unless this is really the best way to do it.

    <priming read - do something the loop will depend on, e.g., get/calculate a number>
    while <condition based on something from above>
        <body of the loop - do the thing you want to repeat>
        <same as the priming read again>
    <do next thing now that the loop is finished (condition was false)>

*Example - number guessing game*

```python
SECRET = 6
guess = int(input("? "))
while guess != SECRET:
    print("Guess again!")
    guess = int(input("? "))
print("You got it!")
```

### Menus
Use the if/elif.../else pattern in Python (switch statements in other languages) inside a while loop that handles the quit option.

    display menu
    get choice
    while choice != <quit option>
        if choice == <first option>
            <do first task>
        else if choice == <second option>
            <do second task>
        ...
        else if choice == <n-th option>
            <do n-th task>
        else
            display invalid input error message
        display menu
        get choice
    <do final thing, if needed>

Sometimes inexperienced coders use a `while True` or `while Boolean` loop for menus, 
and handle the quit option with an extra if, which makes it less readable than our standard pattern 
since it doesn't clearly indicate how the loop stops.  
With a readable (meaningful) condition you know without having to read the rest of the code how the loop will end.  
Also, by having the "final thing" _outside_ the loop, you have less indenting (a Zen of Python value) 
and it's easier to see that this code runs after the menu loop quits.

### Error checking

    <priming read - get some input>
    while <input is bad>
        display error message
        <same as the priming read again - get some input>
    do next thing now that you know the input is valid

**Example:**

```python
age = int(input("Age: "))
while age < 0:
    print("Invalid age!")
    age = int(input("Age: "))
print("You are {} years old".format(age))
```

### Exception-based error checking

You can't have a 'normal' priming read since it might crash before you get to the condition, so you need your try/except _inside_ a loop that you control.

**Example:**

```python
is_valid_input = False
while not is_valid_input:
    try:
        age = int(input("Age: "))
        if age < 0:
            print("Age must be >= 0")
        else:
            is_valid_input = True
    except ValueError:
        print("Invalid (not an integer)")
print("Next year you will be", age + 1)
```

### Function with error checking

Suppose you have a function that should do a task provided there are no errors, like adding a value to a collection if it's valid.  
In this case, you can check for errors first, then do the task if there are no errors... instead of checking it's valid and doing the task if it's valid.   
The difference is in the nesting level. You want your main task to be at the highest level, not inside an if/else.  
Example structure:  

    function do_task(input)
        if input has error 1
            display error message 1
            return
        if input has error 2
            display error message 2
            return
        do task (knowing we don't have any of the above errors)

### Finding

    function find(needle)
        for each item in items
            if item == needle (or however we compare to find the needle in the haystack)
                return result, or set value and break
        return None (since we did not find it)

(note no need for else or continue, it will move to the next item)

### Filtering


    filtered_items = new list
    for each item in items
        if item matches what we want
            add item to filtered_items

(note no need for else or continue, it will move to the next item)

Note that Python (and many languages) have neat shortcuts for filtering, e.g., using *list comprehensions*:

    filtered_items = [item for item in items if item matches what we want]

## Constants

In some cases, replacing a literal with a named constant can help make your code more **readable** and **maintainable**.  
Consider the following program: 

```python3
print("If you buy over 5 items, save 10%!")
number_of_products = int(input("Number of products: "))
while number_of_products <= 0:
    print("Invalid number")
    number_of_products = int(input("Number of products: "))
total = number_of_products * 32.5
if number_of_products > 5:
    total -= total * 0.1
print(f"{number_of_products} x ${32.5:.2f} products = ${total:.2f}")
```

The above program works, but contains "magic numbers" that are used more than once.  
Magic numbers are not evil. You do NOT need to change any literal into a named constant, but there are some general guidelines to help decide when you should probably use constants.

- If the value is used more than once
- If introducing a name is more helpful than the number

Notice in this program that we reuse the numbers ``5 and `32.5` more than once.  
Again, it's not a _rule_ that we replace these with constants, but it could be considered good practice.  
Note that these numbers are used in both strings and as numbers in calculations.  

A good way to consider the use of constants is to ask yourself a question like:  
_"What if I wanted to change this later?"_  
E.g., what if the threshold for a discount changed from 5 items to 10 items? How many places would I need to change my code? One is better than two, so let's use a constant.

There's another interesting one in this example. `10%` is here twice, so... "what if the discount changed from 10% to 15%?"  
The value `10%` only appears in the string, but the value `0.1` appears in the calculation, and these are the same.  
We do not want to break our program by having a constant for the 0.1 and forgetting to use it for the print 10% part.  
This brings us to a **rule** for using constants:

**If you have a constant, then you MUST use it everywhere the value exists.**  

Here's our code with three introduced constants. It works the same way, but is more _readable_ and _maintainable_ (easier to modify and extend).  
You might notice that the constants are all at the top, like configuration 'variables'.  

One more thing to notice: There's no real benefit in turning the literal `0` into a constant as it's not a value that will ever change or that needs further explaining. It's just... zero (no products or some products).    

```python3
# version 2 - notice how it is easier to read,
# and now we only have one place to change if we need to update the values
DISCOUNT_THRESHOLD = 5
ITEM_PRICE = 32.5
DISCOUNT_RATE = 0.1

print(f"If you buy over {DISCOUNT_THRESHOLD} items, save {DISCOUNT_RATE * 100:.0f}%!")
number_of_products = int(input("Number of products: "))
while number_of_products <= 0:
    print("Invalid number")
    number_of_products = int(input("Number of products: "))
total = number_of_products * ITEM_PRICE
if number_of_products > DISCOUNT_THRESHOLD:
    total -= total * DISCOUNT_RATE
print(f"{number_of_products} x ${ITEM_PRICE:.2f} products = ${total:.2f}")
```

## Don't Repeat Yourself (DRY)

DRY is a principle to help avoid 'bad patterns' rather than a pattern itself.  
Here's a counter-example to show you what NOT to do.

```python3
score = int(input("Score: "))
if score < 0:  # condition 1
    result = score * 2
    print("Bad score :(")
elif score >= 0 and score < 20:  # condition 2
    result = score * 2
    print("Score is OK.")
elif score > 20:  # condition 3
    result = score * 2
    print("Your score is good!")
print("Double your score is", result)
```

This program works, so what's the problem?

- Remember, we don't _just_ want working code, we want _good_ code!
- condition 2 is only checked if condition 1 is False. if condition 1 is False, this is because score must be not < 0,
  so `score >= 0 ` is redundant. It will _always_ be True. condition 2 should be replaced by just `score < 20`
- condition 3 appears to check if condition 2 was False, which we already know, but because this code uses "elif no
  else" we might just make a mistake like getting the boundary condition wrong. What happens if the user enters `20`?
  **Oops!** The right choice of pattern is important! We can fix this by changing condition 3 to `score >= 20` but then
  we ask a question we can guarantee will always be True when we get to it (since the first 2 were False), so that's
  repeating ourselves. DRY.
- Lastly, in all three paths, we repeat the line `result = score * 2`. Again, this works, but is not good. Since we
  always want to do this, it should go _outside_ the decision structure.

Here's the code with these problems fixed. Ah, that's better :)

```python3
score = int(input("Score: "))
if score < 0:
    print("Bad score :(")
elif score < 20:
    print("Score is OK.")
else:
    print("Your score is good!")
result = score * 2
print("Double your score is", result)
```

## Working with Booleans

In most cases, where you are dealing with a condition or value and you care about whether it is true or false, then you never need to compare to `True` or `False`. E.g., instead of:

    if condition == True:
    ... or
    if condition == False:

You can just use:

    if condition:
    ... or
    if not condition:

If you are ever returning (or setting a variable to) True/False depending on a condition, you can just return (or set) to the condition. So, instead of:

    if condition:
        return True
    else:
        return False

You can just use:

    return condition

## Function design

The most important aspect of function design is the **Single Responsibility Principle (SRP)**, which means that functions should "do one thing". What "one thing" means depends on the context, but a single function should be an abstraction of a single task.   

In general, there are 3 kinds of functions, those that are designed to:  
* get input (from the user or another source)
* process data
* produce output (to the console, file, or another sink)

Very commonly, the structure in terms of parameters and return statements will look something like (example):

    function main():
        data = get_input()
        result = process(data)
        display(result)

(This is a simplification to make the point about reusability, not a rule that never changes.)  
That is:   
* input-getting functions don't always take in parameters, but they do return what they get.  
* data-processing functions do take in parameters (they do NOT get the input data from the user or other source), and they do return the results (they do NOT display/print/save the result)
* output-producing functions do take in parameter (what they are to display), but do not return anything

### Why is this important?
Some good ways to understand function design include asking these questions about function *reuse*:  
* What if we wanted to rewrite the program's interface in French or Farsi? We should not have to change the processing function, because it should not do any user interface things (input or output on the screen).  
* What if we wanted to get our input from a file instead of the user? We should not have to change the processing function because it should not get any user input. A well-designed function *can* be used with input either from the user or a file (or anywhere), because it takes in the input as parameters.
* Same as above for if we wanted to write the output to a file instead of display it on the screen... the processing function shouldn't care where the data (input parameters) comes from, or where the results (return values) go, since that's not its job.
* Functions designed like this are more **testable**. You can write test code that passes in inputs and compares outputs (returned values) to known correct results for those inputs (e.g., using Python's `assert` statement or `doctest` module). You really can't easily "test" functions in any automated way if they get user input or print results.

## Data storage
Always store data in the best, most correct, format.  
E.g., if you read a *price* from console or file input, it will initially be a `string`, but you should convert it and store it as a `float`.  
If you want to print it using string formatting (e.g., `$23.40`), don't store it as a string, just print it that way... leaving the variable as a float.  

(Another example) If you're asking the user to make a yes/no choice, they might click a button or type "yes", but then you would convert this and store it as a `Boolean` because that's the most appropriate type to store a yes/no (True/False) state.

In general, don't store derivable data.  
This creates a *maintenance burden*. Even if your code works correctly, when you maintain it and add to it, you have to remember to update the same information in multiple places.  
E.g., don't store *age* if you already have a *date of birth* (DOB). Doing so can lead to inconsistency, e.g., your age might not get updated when the date changes. Just calculate the age when you need it and it can't be wrong.  
Don't store the length of a list... that's derivable and can be retrieved at any time (unless you're using a language where this is not the case).


## Never
Here are a few things you should _never_ do... You can consider these to be "anti-patterns".   
("Never" is a strong word, and there will likely be some rare situations where you might maybe sometimes want to do these things, but it's very unlikely.)

* Never set a variable value you don't use. Why define/set a variable, ignore what you just did and set it to something new?
* Never replace function parameters: If you have a function that takes in a parameter (x), you will never want to set that variable (x) immediately... otherwise, why would you pass it in? (This is the same as the previous point.)
* Never convert to the same type: don't convert from type A to type A. E.g., in Python, the `input` function _always_ returns a _str_ type, so you *never* need to write something like `x = str(input("?"))`... or `y = int(0)`.
* Never use the verbose (unbound) syntax for method calls unless you need it: You should always prefer the concise (bound) format. E.g., use `"Hello".upper()` not `str.upper("Hello")`.
* Never use `while True` loops if you can easily enough use a "standard" while loop. If you have to write an if statement to break out of a loop, that if-condition should probably just be your normal loop condition.
