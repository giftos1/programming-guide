This page contains standard 'patterns' that you should get used to. When you need to perform one of these tasks, follow the standard pattern.

## Error checking

    <priming read - do something the loop depends on>
    while <condition based on something from above>:
        display error message
        <same as the priming read again>
    do next thing now that you know the 'something' is valid

**Example:**

    SECRET = 6
    guess = int(input("? "))
    while guess != SECRET:
        print("Guess again!")
        guess = int(input("? "))
    print("You got it!")

## Exception-based error checking

**Example:**

    valid_input = False
    while not valid_input:
        try:
            age = int(input("Age: "))
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


    filtered_items
    for each item in items
        if item matches what we want
            add item to filtered_items

(note no need for else or continue, it will move to the next item)

Note that Python (and many languages) have neat shortcuts for filtering, e.g. using *list comprehensions*:

    filtered_items = [item for item in items if item matches what we want]

## "Innocent until proven guilty" Boolean validating

