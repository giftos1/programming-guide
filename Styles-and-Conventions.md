# References - The official styles for Python
Here are some useful references for Python style conventions, as expected in CP1404/CP5632  
(PEP = Python Enhancement Proposal)

* The main standard style guide for Python is described in PEP 8 https://www.python.org/dev/peps/pep-0008
* PEP 257 for docstrings https://www.python.org/dev/peps/pep-0257
* Here's an example demonstrating PEP 257 docstring styles http://dolphm.com/pep257-good-python-docstrings-by-example
* This page is a useful collection of naming conventions in some detail https://visualgit.readthedocs.io/en/latest/pages/naming_convention.html

# Naming

The main guideline for good identifier naming is **100% of the identifiers in a program should be meaningful**. Variable names, function names, class names, constants... Choosing good names is surprisingly important! Poor names commonly lead to errors. Good names save time reading and fixing code. Good naming is also a good habit and attitude to get into for increased code quality.

## Conventions for Python names

- `module_name` or `modulename` depending on readability - use the `_` to separate words especially if leaving it out is confusing
- `ClassName` (known as PascalCase or CapWords or upper CamelCase)
- `function_name`, `variable_name` (lowercase_with_underscores)
- `CONSTANT_NAME` (all CAPS with underscores)

Following these conventions means any Python programmer reading your code knows when they see a name like `THIS_THING` it must be a constant, and `ThisThing` must be a class. If they see `ThisThing = 3`, that's just wrong... confusing... takes more work to read and see what's different/wrong.

## Best-practice suggestions:
- Don't be cute, don’t use abbreviations (What is `atm`?)
- Avoid names that imply something that isn't true (including: don't reuse names for different things); avoid "disinformation" and inconsistency. E.g., if you use the word "get" to mean "get from input", e.g. `age = get_age()` then don't _also_ use it to mean the thing you got, `get_name = "Monty"` or use the same verb to mean something else, like `bmi = get_bmi(height, weight)` (this should be more like `bmi = calculate_bmi(height, weight)` since we're not "getting").
- Use pronounceable names (`modymdhms`?)
- Avoid mental mapping (a = number, b = total). If an identifier name needs a comment to explain it, just improve the name.
- Make meaningful distinctions (`account`, `account_data`, `account_details`, `account_info` - what's the difference?)
- Use **nouns for variables** and **verbs for functions**. E.g., `age = get_age()` (`noun = verb()`). `get_result = result()` is confusing.
- Use the phrase "This function will..." to help you name functions, e.g., "This function will determine_status()`" is a valid sentence, but "This function will status()`" is not. 
- Use the phrase "This variable stores..." to help you name variables, e.g. "This variable stores a `name`" is a valid sentence, but "This variable stores a `get_name`" is not.
- Use plurals for collections like lists and avoid plurals for singular values. `for child in children` or `for name in names` works, but if we read `names = "Monty"` or `name = ["Monty", "Python"]`, that's confusing.
- Boolean variables and functions should be named so conditions are readable and usually start with `is_` or `has_` or similar. E.g., `if is_winner:` is readable, but `if status:` is not.
- A reasonable way to name dictionaries (aka maps) is the `key_to_value` pattern, e.g., `name_to_phone` or `level_to_reward` (using something like `phones` or `levels` here would imply they are lists/sets/tuples/etc. not dictionaries).
- There are a number of commonly-used names that you should avoid using for anything else. E.g., `i` is usually an index for a list or similar. `for i in range(n)` makes sense; `for i in children` does not.
- Never use built-in names like `min`, `sum`, `print`, etc. for your own names as this will override the existing names and prevent you from using them. It's also confusing to the reader. This also goes for module names - don't use `os.py` or `random.py` or other names that are existing Python modules.
- Do not include a variable's type in it's name (known as "systems Hungarian notation"). Don't use `name_list` (just `names`) or `str_name` (just `name`).

# Commenting
As always, we follow the [official Python styles for comments](https://www.python.org/dev/peps/pep-0008/#id30).
Comments are to help humans read your code - these should be simple and helpful, written for someone about your own level of understanding. Don't include comments if they don't help.

## Do
* Add comments for anything that you think would likely be difficult to understand when you or someone else (of about your level) reads it. This is not a substitute for writing good clean code with meaningful variable names. If improving your names means you don't need comments, then do that!  
Consider the following examples and decide which is easier to understand:
```python3
# Calculate area of circle by multiplying radius (user_float) by 2 * PI
result = 2 * constant * user_float

# or

area = 2 * math.pi * radius

# or

area = calculate_circle_area(radius)
```

* Write comments in the *imperative voice* (same as commit messages). E.g. `# Calculate chance of rain` not `# Calculates chance of rain`. 

* Remove old commented-out code when you're finished with it.

* Put # inline comments above the code they refer to.  
End-of-line comments are only acceptable if they are short and should not extend off to the right too far - put them above the line if they do. Again, it's about readability. Horizontal scrolling is not good.

* Write function comments at a general level, e.g. a function docstring that says how `main` will use the function is not appropriate. What if we want to use the function in a different way?

## Don't
* `"This function will..."` or similar is always redundant. 

* Don't add comments that are completely obvious. These are considered "noise" because they make your code _harder_ to read. You're not writing a tutorial. E.g. `# initialise variables`, `# import statements`... say nothing useful.
If your code has good names, it's probably already *self-documenting* and doesn't need commenting.  
Consider the following example. What does the comment add that's not already said by the code?... Nothing. 
```python3
# Opens 'places.csv' file for reading
input_file = open('places.csv', 'r')
```

* Don't create *maintenance burdens* with your comments. The above example has the actual filename in the code, so you'd have to change *both* the code *and* the comment if the filename changed.
