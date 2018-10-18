  
The following is a collection of actual comments to students who have completed CP1404 assignments similar to yours and had problems. Reading these might give you some tips about mistakes you've made in your own assignment work. There's nothing new here - it's all based on the assignment requirements and expectations from the core teaching in the subject.    
Don't get bogged down with specifics here - some comments will be totally meaningless or irrelevant to your assignment.  
  
  
# Project reflection
Mostly good, just not much detail.  
Needs more about "process", less about results/difficulties.  
Some sections have minimal detail and insight.  
Some answers are too generic - e.g. obstacles. Be a bit more specific in this kind of reflection.  
   
# Version control
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
   
# Console program
new_book.is_completed = False should be redundant since False is the default/current value.  
Creating a new book just to select and change an existing book is unnecessary.  
   
# GUI layout
Can't press Tab to switch between input fields.  
Books don't start in the sort order the GUI shows.  
Colour changing is inconsistent, can't change back.  
Using "Is_Complete" in GUI is not ideal. Don't change the view to match the underlying code.  
Doesn't show all book details.  
   
# Error Handling
try/except not used for number of pages checking, so crashes when you enter a non-number number of pages.  
Allows negative or 0 number of pages.  
Doesn't check for valid category.  
Error messages (order) don't match requirements.  
   
# Correctness
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
   
# Identifier naming
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
   
# Code constructs
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
   
   
# Functions
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
   
# Classes and methods
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
   
# Commenting
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
   
# Formatting
Lining up variables/values creates a maintenance burden. Just use the standard formatting.  
   

  
  
