# Guide to Good Pseudocode

Pseudocode is a useful early step in designing and planning computer programs. The idea is that it is easier and more natural to think in terms of an algorithm (the steps to achieve a solution) rather than in terms of actual computer code. Writing code _after_ writing pseudocode should be a simple translation process – converting the algorithm to a program in a specific language. The exact implementation will depend on the language, which is why pseudocode should be "language agnostic".

There are no rules to produce "perfect" pseudocode, since it doesn't have to compile, but this document provides guidelines for writing *good* pseudocode.

## Attributes of Good Pseudocode

1. Completeness as a solution
2. General concepts and conventions
3. Clarity, explicitness, and good formatting
4. Concise expression
5. Parsimony
6. Good organisation

## 1. Completeness as a solution

Pseudocode must solve the problem at hand using well-defined operations. The programmer who translates pseudocode should be able to do so almost mechanically. There should be no need to develop algorithms or solve problems at the programming stage.

Software development is a multi-stage process, and most of the hard work should take place during design, rather than construction. There's an analogy here to writing, say, an essay. The hard part is coming up with your ideas and arguments; getting the grammar and spelling right should be the easy part. In software development, the design of algorithms is the hard part, and the translation to a programming language implementation should be easy.

**Bad**

    Calculate the tax

**Good**

    tax = 0
    if income > TAX_FREE_THRESHOLD
        tax = income × TAX_RATE

## 2. General concepts and conventions

Pseudocode should not be specific to a particular programming language; it should use general concepts and conventions.

**Bad**

    import random module
    temperature = random.randint(LOW, HIGH)

**Good**

    temperature = random integer between LOW and HIGH inclusive

Why is "import random module" bad? Not every language has a random module, and even if they all did, importing that module is not an essential part of the algorithm. You're not telling the programmer how to write a program, you're telling her how to solve a problem. You can assume that the programmer who implements your pseudocode has enough intelligence and knowledge to use the tools available in her programming language.

## 3. Clarity, explicitness, and good formatting
Pseudocode needs to be well-indented, well-spaced and be consistent in style, so that it doesn't confuse or annoy the programmer who reads it. Variable names must be consistent and clear, and be used explicitly.

**Bad**

    if a     >  B           # poorly spaced
        display message     # unclear (what kind of message?)
        get x               # poor variable name
        if this is "y"      # not explicit
            vent the gas    # not explicit

**Good**

    if pressure > CRITICAL_PRESSURE
        display critical error message
        get ventGasChoice
        if ventGasChoice is "y"
            ventGas()

**Note:** variable names don't have to be in camel-case (e.g. "vent gas choice" or "vent_gas_choice" are okay). This is part of being language independent – there is no fixed or language-related convention. Having said that, you may find it convenient to use the convention for the language you expect to implement in since you can copy and paste into code more easily.

## 4. Concise expression

Pseudocode should be concise. Write instructions as simply as you can without sacrificing clarity.

**Bad**

    get input from the user and store it in a variable called "value"
    store the number one in a variable called "value"
    make c equal to the sum of a and b

**Good**

    get value
    value = 1
    c = a + b

Note that the "good" example looks a lot like code, and that's OK. You don't have to go out of your way to make pseudocode look unlike code. Just be simple, conventional and clear.

## 5. Parsimony

Pseudocode should solve the problem, but that's it! There should be no superfluous material. It's OK to have comments in pseudocode, but the instructions themselves should not speak about the intention.

**Bad**

    if x < LEFT_BOUND or x > RIGHT_BOUND then the train could derail
        haltTrain() to stop the train from derailing

**Good**

    (check if the train is about to derail and stop it)
    if x < LEFT_BOUND or x > RIGHT_BOUND
        haltTrain()

There should be no instructions that don't achieve anything.

**Bad**

    Define the constants

"Define the constants" is bad because the programmer knows she has to define variables! Such a statement adds no information. Statements like the above often occur when software developers work backwards from the code when writing their pseudocode.

## 6. Good organisation

Pseudocode should be organised into appropriate functions, as is the case for code. There should be a one-to-one mapping between functions in pseudocode and functions in code. I.e. if _do_something_ is a function in pseudocode, then it should appear as a function in the code, and vice versa.

The pseudocode within functions should have the five quality attributes already discussed. Each individual function should be specified separately; the pseudocode for a function should not be written where it is called.
When writing pseudocode for functions, make sure to include any parameters (see examples below).

## Pseudocode Patterns

### Comments
If comments are really necessary, write them on their own lines, surrounded by parentheses.

    (check if the train is about to derail and stop it)

### Terminal input: how to get data into a variable

    get name
    get age

### Terminal output: how to display a variable or message

    display "Hello world"
    display name  # where name is a variable
    display name, age and gender
    display venting gas message

**Note:** it is not necessary to replicate the interface in pseudocode by writing the details. The programmer should have access to that part of the planning, and so will know what the "venting gas message" is. Including large quotes makes pseudocode harder to read.

### Arithmetic

    gross = hours * rate
    nett = gross – tax
    average = total / count (use floating point arithmetic)

### Selection

    if age >= 65
        price = price – seniorDiscount

    if temperature > 60
        display "Too hot!"
    else if temperature < 40
        display "Too cold!"
    else
        display "Just right :)"

Strings like "Too hot!" are short enough that they don't detract from readability, and so can be directly included.
Note that we can use "else if" or "otherwise if" but NOT "elif" because that is specific to Python and not normal English.

### Repetition

    repeat while price > 0
        total = total + price
        get price

    for count from 1 to 10
        display count

    for each grade in grade_list
        display grade

    repeat n times
        display horizontal line

### Function definitions

    function do_something(x, y)
        return (x + y) * (y – x)

### Function calls

    do_something(azimuth, altitude)

### File input

    open "info.txt" as fileIn for reading
    get name from fileIn
    get age from fileIn
    close fileIn

### File output

    open "stats.dat" as fileOut for writing
    for each datum in data
        write datum to fileOut
        write newline to fileOut
    close fileOut

### Exception handling

    try
        get number as integer
        display my_list[number]
    catch invalid number error
        display invalid number message
    catch index error
        display invalid index message

Don't worry about the exact values for your exception names; just make sure it's clear.

### String manipulation

    response = response in uppercase
    words = split sentence on whitespace
    comma_position = find first comma in sentence

### Lists

    price_list = empty list
    add price to price_list
    price_list[0] = 0.0
    if index < length of price_list
        display price_list[index]

Note how similar pseudocode for lists/arrays looks to real code – that's fine. We don't need to make it harder, just to try and be less like code.

### Maps (a.k.a. dictionaries or associative arrays)

    name_to_phone = empty map/dictionary
    name_to_phone[name] = number
    display name_to_phone[name]

    for each name in the keys of name_to_phone
        display name

    for each name:number in name_to_phone
        display name and number

### Classes

    class Person
        constructor(name, age, gender)
            instance.setName(name)
            instance.setAge(age)
            instance.setGender(gender)

        basic getters for name, age, gender

        basic setters for name, age

        method setGender(gender)
            if gender in lowercase is not "male" or "female"
                gender = "female"
                instance.gender = gender

**Note:** getName() etc. are so simple that it's only necessary to specify that they will exist
(e.g. **basic getters for name, age, gender** ), rather than writing pseudocode.


## Complete example with Python code implementation

### Pseudocode
    function main()
        get name
        while name is not blank
            get age
            if is_adult(age)
                display name is an adult
            else
                display name is a minor
            get name

    function is_adult(age)
        return age >= 18


### Python
```python
    def main():
        name = input("Enter your name (blank to quit): ")
        while name != "":
            age = int(input("Enter your age: "))
            if is_adult(age):
                print(name, "is an adult")
            else:
                print(name, "is a minor")
            name = input("Enter your name (blank to quit): ")

    def is_adult(age):
        return age >= 18

    main()
```

Some things to note:

- Minor details like how to display the output strings are excluded.
- Obvious things like the need to call main to run the program and that age should be an integer are excluded. It's not wrong to include these, but they're mostly unnecessary.
- "while name is not blank" could be implemented in lots of different ways in different languages… this pseudocode clearly says what to do, not how to do it.
- It looks like simple code. (Python looks a lot like good pseudocode.)
- Very common "syntax" characters like brackets for functions are included, but not language-specific things like colons after else (that's only in some languages).


This document was developed by Trevor Andersen and Lindsay Ward, Discipline of IT, James Cook University.
