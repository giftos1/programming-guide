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

    for each item in items
        if item matches what we're looking for
            return result or set value and break

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
* What if we wanted to rewrite the program's interface in French or Farsi? We should not have to change the processing function because it should not do any user interface things (input or output on the screen).  
* What if we wanted to get our input from a file instead of the user? We should not have to change the processing function because it should not get any user input.
* Same as above for if we wanted to write our output to a file instead of display it on the screen... the processing function shouldn't care where the data (input parameters) comes from, or where the results (return values) go, since that's not it's job.
