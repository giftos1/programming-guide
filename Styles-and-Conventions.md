# References - The official styles for Python
Here are some useful references for Python style conventions, as expected in CP1404/CP5632  
(PEP = Python Enhancement Proposal)

* The main standard style guide for Python is described in PEP 8 https://www.python.org/dev/peps/pep-0008
* PEP 257 for docstrings https://www.python.org/dev/peps/pep-0257
* Here's an example demonstrating PEP 257 docstring styles http://dolphm.com/pep257-good-python-docstrings-by-example

# Commenting
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
