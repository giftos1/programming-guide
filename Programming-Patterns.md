This page contains standard 'patterns' that you should get used to. When you need to perform one of these tasks, follow the standard pattern.

## Main program structure
For most programs, you will have a `main` function and a number of other functions.  
Think of main as the whole program with the other functions as the tools that main uses, with the details abstracted away.  
main should go at the top of your file, and someone reading your code for the first time should be able to look at main and understand what the program does... that is, main should "look like" the whole program. Example (structure).

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

