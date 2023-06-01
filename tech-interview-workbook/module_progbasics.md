# Programming Basics questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
- Storing an ordered collection of items.
append() - Adds elements at the end of the list
copy() - Returns a copy of your list
pop() - Removes the item from the specified position
remove() - Removes the item with specified value
sort() - Sorts the list
-reverse() - Reverses the order of your list

#### What is the difference between a list/array and a set?
Sets are unindexed, unordered and immutable. Set's items are unique so there is no duplicated items.

#### What is the purpose and methods of a dictionary/map data structure?
They hold key-value pairs to store data. It cannot be indexed, but it is ordered and it is fairly
simple to search for any key Methods like : .get(), del, .pop(), and they all expect indexes

### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
def fib(n):
    if n > 1:
        return fib(n-1) + fib(n-2)
    return n
#### f(n) = f(n-1)+f(n-2)

#### How do you find a max value in a list/array if you can’t use any built-in functions?
max = list[0]
for x in list:
    if x > max:
        max = x
print max

#### How do you find the average of values in a list/array if you can’t use any built-in functions?
sum=0
list=[1,2,2,3]
for i in list:
	sum=sum+i
average=sum/len(list)
print(average)
#### What do we call an *in-place* sort?
A sort algorithm in which the sorted items occupy the same storage as the original ones.
A method like list.sort() modifies the object (rather than create and modify a new one).

#### Explain an algorithm which sorts a list!
N = len(array)
i = 0
j = 0
while j < N - i -1:
    if array[j] > array[j+1]: 
        array[j], array[j+1] = array[j+1], array[j] 
    j += 1
    if j >= N - i - 1:
        j =0 
        i += 1
print(array)

### Programming paradigms - procedural

#### What is the call stack?
It's a data structure, that stores information about the active subroutines of the program.

#### What is “Stack overflow”?
A stack overflow is a programming error when more memory is used on the call stack rather than what is available.

#### What are the main parts of a function?
name, parameters, the actual code/body

### Programming languages - Python 
 
#### How do you use a dictionary in Python?
It's contains key:value pairs.
dict = {key:value}
Referencing keys value in dictionary: dict['key'] --> It gives back the value 
Referencing key in dictionary: dict['key'].key() --> It gives back the key

#### What does it mean that an object is immutable in Python?
The object's state can't be modified after declaring it.
These are of in-built types such as: int, floeat, bool, string, unicode, tuple.

#### What is conditional expression in Python?
Conditional expressions return different values based on the result of boolean expression spcified by the programmer (based on the condition being true or false). The result of boolian expression is either True or False.

#### What are different types of arguments in Python?
1.default arguments (assigning default values with =)
2.keyword arguments (assigning values, disregarding argument positions)
3.arbitrary arguments (using packing/unpacking with *, **)

#### What is variable shadowing? (context: variable scope)
A variable declared within a certain scope which has the same name as a variable declared in an outer scope. This outer variable is said to be shadowed by the inner variable, while the inner identifier is said to mask the outer indertifier. This can lead to confusion, as it may be unclear which variable subsequent uses of the sahdowed variable name refer to.

#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
With add (append): The iteration continues without an issue, albeit with different ammount of elements.
With delete/drop: The program breaks with an index error.

#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
Avoiding global variables use.
The golden rule means that variables should only be accessible where they are use.

In python the LEGB rule is used to decide the order in which the namespaces are to be searched for scope resolution.
LEGB stand for:
    1. Local: Defined inside the function
    2. Enclosed: Defined inside enclosing functions (nested funcions concept)
    3. Global: Defined at the uppermost level
    4. Built-in: Reserved names in Python built-in modules

#### If you need to access the iterator variable after a for loop, how would you do it in Python?
Just assign it to another variable inside the foor loop and the new variable can be used afterwards outside the for loop.

#### What type of elements can a list contain in Python?
basically any. Bool, int, float, string, list, tuple, dictionary, object.

#### What is slice operator in Python and how to use?
slice(start,end,step) -> is a function in python, which returns a slice object. Slice object is used to specify how to silce a sequence.
start maarks the start of the slicing and end is where to end it.You can use the step parameter to specify to slice only every n-th item.
ex:
slice(1,5,2) -> this will slice a string from the 1st charachter to the 4th as the last is not in the slicing sequence. And the slice will only slice every 2nd item

#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
The + operator concatenates two lists. In other words, it appends one list's elements to another's.
The * operator multiplies a list's elements by an integer.
The - and / operators are unsupported and result in an error.

#### What is the purpose of the in and not in membership operators in Python?
IN operators check if the value is inside a list/set/dictionary.
NOT operators is a negation statement, and it checks if the value is NOT equal to the control value
NOT IN: Reserve of the in oparator

#### What does the + operator mean when used with strings in Python?
It is used to add characters or other strings at the end of strings or to join mutliple string together

#### Explain f strings in Python?
f strings are strings that contain the value of a variable in themself and this making them dynamic
f'string {variable} string'

#### Name 4 iterable types in Python!
List, tuple, dictionary, string

#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
List/set/dictionary comprehensions create the entire collection at once, while generators can evaluate elements on demand.
List/set/dictionary can be reffered to by themselves. Generator expressions can only be reffered to in loops. Generator functions contain one or more yield statements instead of a return statement.

#### Does the order of the function definitions matter in Python? Why?
Yes, it matters if you want to use one function inside another. Then the inner function must be defined before the outer definition.

#### What does unpacking mean in Python?
Unpacking is a way where arguments can be given to a function from a list/set/dictionary. Unpacking is done by the * or the ** operator.

#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?
The value will be None and that will be assigned to the variable and its type will become NoneType.

## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
You can print out values manually, you can use the debugger, and see all the active variables values in the debugging window

#### What does step over, step into and step out mean while using the debugger?
Step over: steps over the next line or loop in the code (skip a certain function)
Step into: steps into definitions or loops and checks the functions line by line
Step out: does the opposite that step into.

#### How can you start to debug a program from a certain line using the debugger?
Place a break points in the IDE at the line where you want to start debugging at.
The breakponts where the the built in debugger tool stop the running code.


### Version control

#### What are the advantages of using a version control system?
You can record and follow every change throughout the project.
Multiply people can work on the same code at the same time.
If comething goes wrong, you can always go back to a previous version.

#### What is the difference between the working directory, the staging area and the repository in git?
Working directory: The current, active directory that you modify on you computer.
Staging area: contains the files that are added from the working directory.
(Local git) repositry: storage of commited changes, which can be restored or merged later if needed (and than pushed to github)

#### What are remote repositories in git?
These are online storages of the git, repositories that are not on the computer you are working on.
It can be used to share code with colleagues by git push/pull command and to manage multiple branches and merges between the versions.

#### Why does a merge conflict occur?
A conflict arises when two separate branches have made edits to the same line in a file or when a file has been deleted in one branch but edited in the other.

#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
git status (to check for rmodifications to make sure)
git add my_file
git commit -m "bugfixes"
git push origin master

#### What does it mean atomic commits and descriptive commit messages?
Atomic commit means you make a commit every time you make changes or finish a feature, making commit after 2 feature chagne does not go as an atomic commit. 
Descriptive commit messages mean when you give a commit message you describe shotrly but meaningfully the changes and modifications you made on the feature/programme.

#### What’s the difference between git and GitHub?
Git is a version control system that lets you manage and keep track of your source code history. GitHub is a cloud-based hosting service that lets you manage Git repositories.


## Software design

### Clean code

#### What does clean code mean?
A clean code is a code that is easy to understand and easy to change.
    -easy to understand the execution flow of the entire application
    -easy to understand how the different objects collaborate with each other
    -easy to understand the role and responsibility of each class
    -easy to understand what each method does
    -easy to understand what is the purpose of each expression and variable

#### What steps do we usually do during a clean code refactoring?
1. Rename badly named variables and funcions (name magical number)
2. Fix badly formatted code
3. Clear repetitive code
4. Refactor long methods
5. Fix wrond comment usage
6. Delete dead codes


### Error handling

#### What is exception handling?
Exceptions are use to handle possible errors occurring during the program execution.
Exceptions can anticipate the error type (it it is given) and when the error occurs
it will execute the coded lines inside the exceptions instead of crashing the program.

#### What are the basics of exception handling in Python?
We use try-except block.
It the try block runs to failure, it jumps to the except block rather than crasing.
The except block contains the logic that deals with the exception gracefully.

#### In which case should we catch an exception? Why?
Any time a specific error can be excepted it is wise to use exceptions.
For example: when user input is used and the input type is important or when we are liking for files which my not exist or when we need to translate object but it is not clear if it can be done.

#### What can/should we do with an exception in the ‘except’ block?
Print and understandable error massage (such as ValueError). 
And tell the program how to continue executing our code (or not)

#### What does the else and finally statement do in a try-except block in Python?
Else is called when nothing went wrong and the except block doesn't catch an exception.
Finally block: code is always executed, whether the program executer properly or it raised an exception.


## Software Development Methodologies

#### What is the main goal of a retrospective meeting?
The goal is to discuss among the team members how the work went during the last spring,
what was good, what was bad, and what steps each member can take to improve the personal
and team work.


## Programming environment

### Unix

#### What is UNIX and what is Linux?
UNIX is a family of multitasking multiuse computer operating system from the 70's that
meant to be easier to handle for programmers than conventional operating system.
It has a modular design and command line interface (CLI)

LINUX is a family of open source Unix-like operating system based on the Linux kernel.
Linux is free (open source) and currently maintained and updated by the Linux community,
but UNIX is licensed. Unix-like systems are very similar to UNIX, even though they are
not certified to be UNIX system.
Linux also has a GUI (Graphical User Interface)

#### What do we call the shell in Linux?
A Shell is a command interpreter in Linux used mainly in the Linux Terminal.
It provides a computer user an interface to the UNIX/GNU Linus system so that the
user can run different command or utilities/tools with some input data
(then executed by the operating system)

#### What does root means in a Linux environment?
root is the user name or account that by default has access to all commands and files
on a Linux

#### How do you access your personal files in Linux?
Through the file browser of by the treminal with the "cd" command

#### How can you install an application in Linux?
sudo apt-get install file-name

#### What is package management in Linux, what are repositories?
Package management is a method of installing, updating, removing, and keeping track of software updates from specific repositories.
A software repository, or “repo” for short, is a storage location for software packages.

#### How do you navigate in the filesystem with the command line?
use cd command to navigate between folders , and ls to list the content of the
folder you are located in

#### What does the following commands do: mkdir, rm, cat, cp, touch?
mkdir : creates a folder
rm : rm command is used to delete directories and the contents within them
cat: will show the content of a given file
cp: cp stands for copy. This command is used to copy files or group of files or directory.
touch: create files 

#### How can you look up what does a command do in Linux if you have no internet connection?
man <command name>
<command name> --help

#### What does the following commands do: head, tail, more, less?
head: Print the first 10 lines to standard output
tail: Print the last 10 lines to standard output
more: View one screenful of text at a time
less: similat to more, but faster and you can navigate through the file. Better for large files

#### How do you download a file from internet using the terminal?
wget <URL>
