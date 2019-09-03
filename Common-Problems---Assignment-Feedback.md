  
The following is a collection of actual comments to students who have completed CP1404 assignments similar to yours and had problems. Reading these might give you some tips about mistakes you've made in your own assignment work. There's nothing new here - it's all based on the assignment requirements and expectations from the core teaching in the subject.    
Don't get bogged down with specifics here - some comments will be totally meaningless or irrelevant to your assignment.  

# Assignment 1 - Console Program


## Correctness
Incorrectly tries to load temp.csv instead of books.csv - doesn't run  
Incorrect display of * for required/completed  
Incorrectly starts book list at 1  
Doesn't seem to add new books (not displayed); incorrectly writes to the file.  
Writing/saving the file should only happen once, at the end.  
Completes wrong book number  
What is 'The list menu must be entered first'? This should not occur.  
Doesn't add new books as required.  
Doesn't display totals.  
Doesn't display # books loaded at start.  
Doesn't show "No books left to read."   
Doesn't sort books.  
Sorting doesn't consider number of pages.  
Sorting pages doesn't work because pages has been stored as a string.  
When no books are required, marking (M) should not display list.  
   
## Error checking  
Doesn't check empty strings  
Doesn't handle invalid book numbers - crashes with IndexError.  
Doesn't handle upper and lower case menu choices.  
Incorrect handling of invalid menu choice  
Allows pages below 1.  
Allows negative pages because you're using if not a loop.  
   
## Similarity to sample output  
Several differences including (most important), book display  
Incorrect output when entering wrong book number.  
book list should start at 1.  
Doesn't display new book (details) added.  
   
## Identifier naming  
Function names should be imperative verb phrases.  
Inconsistent use of case.  
You have a variable with the same name as the function it's in!  
Constants should be in ALL_CAPS.  
Good job with constants for indices like BOOK_TITLE, but they don't sound like indices.  
completed_books sounds like a plural and therefore a collection. Use "number_of..." or similar.  
"for title in book_list" should just be "for book in books" (it's not just a title).  
"verify_author_or_title" doesn't verify/check, it "gets".  
"books" is plural; don't use it for a single book.  
add_new_book doesn't add, it gets.  
Similar function names need differentiation.  
learned_books books_to_learn sounds like it stores books, not a number.  
output_to_file should just be like save_books.  
get_file_contents should be more like load_books - use domain language.  
Names could be closer to the problem domain. E.g. the problem description doesn't use the word "unread".  
Why "print_books_to_file" then write a comment "save books..."? Just call the function "save_books" = self-documenting code :)  
   
## Use of code constructs  
The assignment requires you to load the books once and store them, which you don't do.  
"else: pass" is always redundant.  
line 59 does nothing  
Don't use close() inside with.  
Why use else with your try/except? Put this with your if, not your try. (Inconsistent)  
Put imports at the top, not in functions.  
Menu while condition is invalid (always True), so you need an if again... Please revisit the teaching on this.  
Don't use while True for a menu. Follow our pattern.  
Program should start with the main function.  
Your menu has an extraneous while loop with repeated menu choices. Please follow our pattern.  
Just upper()/lower() the input so you don't need to check for case each time.  
Just upper()/lower() the input so you don't need to do it in each menu if.  
Don't duplicate code like prompting for the menu choice in each option if.  
Duplicated code for printing required/completed book… do you see there's only 1 difference? Make that a variable and reuse the same print statement. (DRY principle)  
DRY principle: you have 2 for loops when you only need 1 for printing books.  
Don't convert inputs (strings) to strings.  
You should store data in its correct format, so year should be stored as an int not a string.  
Don't use a loop to count books, just the len() function.  
Don't use "in" to compare things you expect are the same or different; just use "==".  
Don't use "is" to compare things unless you specially want reference equality, not value equality.  
Close files as soon as you've finished with them.   
Separate load/save file handling.  
.lower() used multiple times when you need it once/twice.  
Don't use global variables.  
Don't use else with while loops.  
Don't iterate through indices unless you need the index - just loop through the elements.  
Oh my, you've used recursion to handle the menu instead of just looping.  
Don't use a loop where the condition doesn't control it.  
Don't store book indices - these are just the existing list indices.  
Don't compare Booleans to True/False.  
Needing a comment like "# while the book name is blank" implies you should have just use more readable code (while name != "")  
Where have your learned to use exit()?  
Why use "while True" to read file? Just use "for line in file".  
while True for basic error checking (e.g. blank book name) is unhelpful.  
You already have a while (Boolean) loop for exception handling of year, so you don't need the nested while loop inside it.  
The books filename and c/r should be constants.  
c/r should be constants. See how many times you use them?  
When you have a constant, you need to use it everywhere you can.  
Sorting can be much simpler with itemgetter as suggested.  
Sorting doesn't consider title.  
Only sort the list when you need to.  
Consider using enumerate to simplify your loops where you need both the index and the element.  
Don't loop over index in range(length) if you don't need the index.  
Instead of using len() to find empty strings, just compare using == "".  
   
## Use of functions  
Because you don't store the books in a list, you don't pass this list. Please make sure you learn this fundamental principle.  
Because you have global variables, you don't pass them to functions. Please make sure you learn this fundamental principle.  
The functions should be passed the list of books.  
You were asked to pass a list of lists, not a list of strings.  
Loading books should be done in a separate function that returns a list of lists (finished processing the file data).  
The loading books function should return a list of lists (finished processing the file data), not a list of strings.  
The load books function should do the whole job including open/close file, rather than this being outside it.  
complete_a_book should do the whole job including getting input. This is not very reusable.  
Adding a book should be a separate function.  
The add_book function should do the whole job, not just part of it.  
Completing a book should be a function... see how much of main it takes up?  
You should have functions for list, add, complete… see how much of main they take up?  
save_books should be a function.  
get_title/author should be combined - see how similar they are?  
The load books function should not print (SRP).  
Main menu options should each be done with a complete function - why split them up like this?  
Missing most expected functions.  
Much of this is confused and messy. Your functions end up reducing readability instead of improving it.  
Functions like check_valid_year do only part of the job - should be complete or only do one thing.  
Load/save needing the file object make them less reusable.  
Don't pass derivable things. E.g. In write_file, you pass book_count, then use len(book_list) anyway.  
menu() should be in main, not a separate function. main should look like the whole program.  
print and sort for adding book should be part of the add function, not in main.  
main has too much code in it that should be in the functions.  
Don't return mutable parameters (books); the variable will already be changed.  
   
## Formatting  
Lining up variables/values creates a maintenance burden. Just use the standard formatting.  
   
## Commenting  
Your function comments are not docstrings.  
Top comment is not a module docstring  
No module docstring  
Top comments should explain the program's basic purpose  
No function docstrings.  
This code could benefit from some inline/block comments in places where the code is less than obvious.  
Inline comments should not extend off to the right too far - put them above the line if they do.  
Far too many noisy comments. Don't do this... who wants/needs to read this?  
Remove old code; don't leave it in comments.  
Use the imperative voice for comments (e.g. "call" instead of "calls").  
Personal commentary like "# Needed something different for the book year" should be avoided.  
Comments like "# menu loop" are noise - don't help anyone  since the code is obvious.  
"" would be unnecessary if the variable name was more meaningful.  
   
## Version control  
Incorrect submission - not a zip file containing your repo.  
Incorrect submission; zip file must be of your project (which will include your .git folder), not your repo downloaded from GitHub.  
GitHub commits show use of "Upload file" instead of what we taught you. Please learn this important skill now.  
Look at our examples for good messages. Some of yours don't say what they really do or are not voiced properly.  
"Add files via upload" means you've used the website interface to upload files, instead of how we've taught you (PyCharm) with good messages. Please make sure you learn this from the prac and lecture notes.  
These 'milestones' are probably a bit small (too many commits), but that's better than the other way around.  
Avoid using the same message for multiple commits - explain the difference.  
Use the imperative voice for commit messages.  
   
## General comments   
This assignment shows that you were working on just trying to get it to work, instead of following the best practices and using the skills we have taught you in class. It seems you did not really read the assignment properly. The assignment details highlight very important things that you are to take note of and do (such as reading the file once and storing the data in a list of lists that you pass to functions; and submitting a zip file).   
Please learn from this that you need to follow the instructions properly. Let's make assignment 2 much different, OK  

  
# Assignment 2 - GUI & Classes

## Project reflection
Mostly good, just not much detail.  
Needs more about "process", less about results/difficulties.  
Some sections have minimal detail and insight.  
Some answers are too generic - e.g. obstacles. Be a bit more specific in this kind of reflection.  
   
## Version control
Use the imperative voice (e.g. "Add X" not "Added X").  
Messages could be improved.  
Commits don't show incremental development that starts with classes + tests.  
Too many commits with poor or repeated messages.  
2nd commit message is inaccurate.  
What does "final commit" mean?  
Inconsistent messages.   
"Add files via upload" is not OK.  
Mismatched messages (e.g. "Add docstring" is not "clear clutter").  
Don't use quotes for your "messages".  
   
## Console program
new_book.is_completed = False should be redundant since False is the default/current value.  
Creating a new book just to select and change an existing book is unnecessary.  
   
## GUI layout
Can't press Tab to switch between input fields.  
Books don't start in the sort order the GUI shows.  
Colour changing is inconsistent, can't change back.  
Using "Is_Complete" in GUI is not ideal. Don't change the view to match the underlying code.  
Doesn't show all book details.  
   
## Error Handling
try/except not used for number of pages checking, so crashes when you enter a non-number number of pages.  
Allows negative or 0 number of pages.  
Doesn't check for valid category.  
Error messages (order) don't match requirements.  
   
## Correctness
Doesn't update status label when book button clicked.  
The program should not change the user's input.  
You should not be limiting text entry in the pages field - that wasn't a requirement and prevents you doing what is a requirement: showing an error message when the user enters text.  
It should clear input fields when you add book.  
It should not clear input fields when you get an error.  
Doesn't clear/change label when you add book - looks like an error still.  
Can't mark a book as required.  
Number of pages to read doesn't update when buttons pressed.  
required/completed are backwards (r = required, not completed)  
Sorting by completed/required does not work properly - it should stay up to date when you click a book.  
Sorting by anything should secondarily sort by title.   
New book is not sorted until you change sorting.  
Sorting by number of pages is alphanumeric (string) instead of numeric (int).  
Title should be an option for sorting  
Saves before closing the program.  
   
## Identifier naming
Method names should usually be verb phrases.  
books.books is not helpful - rename the BookCollection object so it doesn't sound like a normal list.  
In press_button(), title is actually the Button widget, not the title.  
In load, book is not a good name for a line from the file - it's not a Book yet  
Variables and functions should usually not have the same names.  
get_required sounds like it gets required books, not like get_number_required or get_required_count (more obviously returns a number).  
mark_completed also marks required.  
Constants should be ALL_CAPS.  
Don't use generic names like "element" for specific things like "book".  
i is not a good name for a counter.  
I would expect TITLE to be a... title, not an INDEX.  
is_required implies it's a Boolean.  
change_state is too generic (probably taken from spinner demo when it actually changed a state).  
sort_bookcollection would be better as sort or sort_books (we know it's a BookCollection by its class).  
completed doesn't sound enough like a Boolean (use is_completed).  
   
## Code constructs
in Book, number of pages should be an int not a string.  
in Book, is_completed should be a Boolean not a string.  
Unnecessary duplication in Book.str method (DRY principle).  
Unnecessary duplication when creating book buttons (DRY principle).  
Good use of constants.  
Colours and filename could be constants.  
The file name would be a good constant.  
Sort categories should be constant, not defined each time you sort.  
Status Label text could be a StringProperty.  
If using y/n so much, they should be constants.  
Don't compare to Booleans using ==.  
Inconsistent handling of books.csv file (parameter, literal).  
Don't compare using len() to find empty strings. Just use =="".  
imports should be at the top, not inside functions.  
elif for r/c option is unnecessary - just use else as there are only two possibilities.  
Don't use "in" to compare things you expect are the same or different; just use "==". Using "in", you would find "Goanna" when searching for "Go".  
Sorting could be simpler by using attrgetter, as suggested in the requirements.  
Too much duplication (if/elif) for handling sort field conversion. A dictionary would help.  
Too much duplication in if/else for button creation.  
Don't use "for i in range" if you don't need i - just use "for book in books".  
Don't use "for i, book in enumerate" if you don't need i - just use "for book in books".  
Duplication in if/else for save_books - instead, use a variable for the one difference (DRY principle).  
Why use sorted() instead of just sort()?  
Don't use mutable objects ([]) as default parameter values. Did you see the PyCharm warning?  
load_books is cumbersome - why use "(in_file.read()).split("\n")" etc. instead of "for line in file"?  
str(i) not necessary when using str.format().  
Don't reuse Boolean variable as a string (book.is_required = "y").  
try/except for sorting doesn't seem like a good idea - too specific a case, so handle it specifically.  
if/if/if for empty fields should be handled in one if (DRY).  
save_books should use str.format() instead of +.  
You don't close() the file when loading.  
If/else for handling last book differently when saving is unnecessary and inefficient. Use slicing if you need to do this (but you don't).  
Remove "pass" when finished with it.  
Use concise syntax, not verbose - e.g. use "str(book)" not "book.__str__()".  
Don't reuse same name variables for different types (e.g. is_completed).  
Good function design usually involves returning the same type (not str or None).  
sort_books doesn't just sort books (violates SRP).  
There's no need to convert a Book to a list just to access its attributes.  
In BookCollection you set books to the (string!) parameter then replace it with a list.  
The file should be opened and read only once.  
Technique for getting book from button is harder than it needs to be.  
   
   
## Functions
required_count_update takes too much and does too little. It should call the methods to get what you passed in. See how cumbersome this call looks? Hide complexity in the methods, not in the parameters.  
on_start could get its initial sorting from the model (main) not the view (kv).  
Good reuse of handle_clear in add_book  
The main app should not have a book (self.book) - this should be a temporary variable, not an instance variable.  
Good use of List/StringProperty.  
books should not be a class variable but an instance variable.  
Don't define new instance attributes outside init if you can help it. Did you see the PyCharm warning?  
Don't pass self.x (e.g. calling sort); the class already knows self.  
main should get text for book buttons from Book.str.  
BookCollection should be an instance variable in your App, not a global variable.  
Why does "update_status" also remake widgets? (violates SRP).  
Why sort and re-make the Buttons every time add is pressed, even when there's an error?  
When you have a StringProperty associated with a Kivy widget, you don't need to get the text from the widget - it's already in the StringProperty.  
super().__init__() should be the first line of the function.  
Some functions could be combined (e.g. update_*) or replaced with a StringProperty for the status label.  
Functionality in BookCollection (e.g. error checking) should be  in main.  
   
## Classes and methods
sort_books should not return anything (currently it returns None).  
mark_completed() should not return anything - just mark completed.  
save _books should not print anything - no method should.  
You are inheriting BookCollection from list but not using that at all.  
BookCollection should not inherit from Book. Is it true to say, "BookCollection is a Book"?  
Not much done. Clearly you haven't followed the suggestion of writing the classes first with tests as you go. Please learn this for next time.  
The Book.str method would be more useful if it showed the whole book, like on the buttons.  
Book is missing the __str__ method.  
Why are you using a list of lists when you have classes for this? You've missed the point. You do not need to convert (e.g. in save_books).  
Book should not be responsible for converting r/c- that's BookCollection's job. Book doesn't know how it will be used.  
mark_required should not return anything.  
BookCollection should not take a parameter and the default should not be a string (see the warnings?).  
Methods for each sort are unnecessary - just use one with a parameter.  
BookCollection.init should not take a parameter, and it shouldn't be a string.  
You have mark_completed but not mark_required - using only one is inconsistent.  
You should not return self variables.  
You have methods for counting the number of completed/required books, but you don't use them.  
mark_required should not take a parameter.  
Importing from console program makes classes not as reusable/modular.  
   
## Commenting
Don’t write "developer train of thought" kind of comments - just say what the functions will do, not your code choices.  
"List comprehension for finding ..." should just be "Count ..." - just say what the function will do, not your code choices, which might change later (but the docstring shouldn't have to).  
Comments like "#Boolean to mark book as not required" are just for your learning, not helpful for readers.  
Some docstrings missing. All functions, modules and classes should have docstrings.  
"function" is always redundant in docstrings.  
"This method will create …" should just be "Create …"  
Old code should be removed instead of left commented.  
Lecturer-provided todo comments should be removed  
No helpful inline comments.  
Docstrings must be inside methods, not before.  
docstrings should start with triple quotes: """docstrings""", not hash: #  
Put single-line docstrings on one line.  
Please learn how to write docstrings.  
Comments in classes should only be about classes, not an app that might use them (e.g. """this appends a new book taken from kivy into the books list""").  
Inconsistent wording (use imperative voice; keep it simple.)  
Lined-up block comments are a maintenance burden. Just put them after the line, or above it.  
   
## Formatting
Lining up variables/values creates a maintenance burden. Just use the standard formatting.  
   

  
  
