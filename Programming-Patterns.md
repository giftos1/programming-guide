This page contains standard 'patterns'

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

## Filtering

## "Innocent until proven guilty" Boolean validating

