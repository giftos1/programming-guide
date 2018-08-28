This page contains standard 'patterns' that you should get used to. When you need to perform one of these tasks, follow the standard pattern.

## Main program structure
For most programs, you will have a `main` function and a number of other functions.  
Think of main as the whole program with the other functions as the tools that main uses, with the details abstracted away.  
main should go at the top of your file, and someone reading your code for the first time should be able to look at main and understand what the program does... that is, main should "look like" the whole program. Example structure:

    """ module-level docstring """
    import statements
    constants

    function main()
        opening statement
        do_step1()
        result = do_step2()
        do_step2(result)
        closing statement
    
    function step1()
        ...
    
    function step2(parameter)
        ...
        return result

    main()

## Loops
In most languages, there are multiple kinds of loops and you should choose the most appropriate kind.  
The most common choice is:

- Use *for loops* for definite iteration, like `for item in sequence...`
- Use *while loops* for indefinite iteration, like `while condition...`

Using a while loop and maintaining your own counter (e.g. using a while loop to iterate through the numbers from 1 to 10) would be considered an *anti-pattern*, since this is what for loops are for!  
Using a for loop and maintaining your own counter (e.g. iterating through elements in a list and manually using +1 for the index) would also be poor, since for loops can do this for you. In Python, if you need _both_ the index and the element, use `enumerate`.

## While loops
Almost all while loops follow the same standard pattern (as below with menus and error checking).  
Do not force the loop to be True the first time by setting a value for your loop condition variable, and do not use `while True`... unless this is really the best way to do it.

    <priming read - do something the loop will depend on, e.g. get/calculate a number>
    while <condition based on something from above>:
        <body of the loop - do the thing you want to repeat>
        <same as the priming read again>
    <do next thing now that the loop is finished (condition was false)>

Example - number guessing game:

    SECRET = 6
    guess = int(input("? "))
    while guess != SECRET:
        print("Guess again!")
        guess = int(input("? "))
    print("You got it!")

## Menus
Use the if/elif.../else pattern in Python (switch statements in other languages)

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

## Error checking

    <priming read - do something the loop depends on>
    while <condition based on something from above>:
        display error message
        <same as the priming read again>
    do next thing now that you know the 'something' is valid

**Example:**

    age = int(input("Age: "))
    while age < 0:
        print("Invalid age!")
        age = int(input("Age: "))
    print("You are {} years old".format(age))

## Exception-based error checking

**Example:**

    valid_input = False
    while not valid_input:
        try:
            age = int(input("Age: "))
            if age < 0:
                print("Age must be >= 0")
            else:
                valid_input = True
        except ValueError:  # or just  except:
            print("Invalid (not an integer)")
    print("Next year you will be", age + 1)

## Function with error checking

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

## Finding

    function find(needle)
        for each item in items
            if item == needle (or however we compare to find the needle in the haystack)
                return result, or set value and break
        return None (since we did not find it)

(note no need for else or continue, it will move to the next item)

## Filtering


    filtered_items = new list
    for each item in items
        if item matches what we want
            add item to filtered_items

(note no need for else or continue, it will move to the next item)

Note that Python (and many languages) have neat shortcuts for filtering, e.g. using *list comprehensions*:

    filtered_items = [item for item in items if item matches what we want]


## Working with Booleans

You never need to compare to `True` or `False`. E.g. instead of:

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

In general, there are 3 kinds of functions, those that are designed to:  
* get input (from the user or another source)
* process data
* produce output (to the console, file, or another sink)

Very commonly, the structure in terms of parameters and return statements will look something like (example):

    def main():
        data = get_input()
        result = process(data)
        display(result)

(This is a simplification to make the point about reusability, not a rule that never changes.)  
That is:   
* input-getting functions don't take in parameters, but they do return what they get.  
* data-processing functions do take in parameters (they do NOT get the input data from the user or other source), and they do return the results (they do NOT display/print/save the result)
* output-producing functions do take in parameterr (what they are to display), but do not return anything

### Why is this important?
Some good ways to understand function design include asking these questions about function *reuse*:  
* What if we wanted to rewrite the program's interface in French or Farsi? We should not have to change the processing function, because it should not do any user interface things (input or output on the screen).  
* What if we wanted to get our input from a file instead of the user? We should not have to change the processing function because it should not get any user input. A well-designed function *can* be used with input either from the user or a file (or anywhere), because it takes in the input as parameters.
* Same as above for if we wanted to write our output to a file instead of display it on the screen... the processing function shouldn't care where the data (input parameters) comes from, or where the results (return values) go, since that's not it's job.
* Functions designed like this are more **testable**. You can write test code that passes in inputs and compares outputs (returned values) to known correct results for those inputs (e.g. using the `assert` statement, or `doctest` module). You really can't easily "test" functions that get user input and print results in any automated way.

## Data storage
Always store data in the best, most correct, format. E.g. if you read a *price* from a file, it will be a string, but you should store it as a float. If you want to print it using string formatting (e.g. `$23.40`), don't store it as a string, just print it... leaving the variable as a float.

In general, don't store derivable data. E.g. don't store *age* if you already have a *date of birth* (DOB).  
Doing so can lead to inconsistency, e.g. your age doesn't get updated when "date - DOB" results in a different age. Just calculate the age when you need it and it can't be wrong.  
This is a *maintenance burden*. Even if your code works correctly, when you maintain it and add to it, you have to remember to update the same information in multiple places.  

## Never
Here are a few things you should _never_ do... You can consider these to be "anti-patterns".   
("Never" is a strong word, and there will likely be some rare situations where you might maybe sometimes want to do these things, but it's very unlikely.)

* Never replace function parameters: If you have a function that takes in a parameter (x), you will never want to set that variable (x) immediately... otherwise, why would you pass it in?
* Never convert to the same type: don't convert from type A to type A. E.g. in Python, the `input` function _always_ returns a _str_ type, so you *never* need to write something like `x = str(input("?"))`... or `y = int(0)`.
* Never use the verbose (unbound) syntax for method calls unless you need it: You should always prefer the concise (bound) format. E.g. use `"Hello".upper()` not `str.upper("Hello")`.
* Never use `while True` loops if you can easily enough use a "standard" while loop. If you have to write an if statement to break out of a loop, that if-condition should probably just be your normal loop condition.
