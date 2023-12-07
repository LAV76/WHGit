# Local conflict branch conflict
## Authorization 

Before pushing any code into the remote repository, you'll need to authorize 
your machine to do so in your Github user settings. 
We'll do this by adding our machine's SSH public key to the authorized list 
of keys in Github.com -> Settings -> SSH and GPG keys. 
 
If you do not, yet, have an SSH key for your Linux user, run the following. 
```
  ssh-keygen
```
 
By default, this will create a key pair under your home directory. 
```
  ~/.ssh/id_rsa
  ~/.ssh/id_rsa.pub
``` 

The first is your private key while the second is your public key. 
Paste the content of your public key in a New SSH key to authorize your machine.

Lastly, git requires you identify yourself when pushing into a remote repository. 
For this, you'll need to run the following. 
```
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

```

## Using a repository

The easiest way to create a new repository is initializing it in Github.com 
and, using the SSH URL provided in the repository's "Clone or download" button,
 run 
```
  git clone git@github.com:username/repository_name.git

```

Because we already have a repository, we won't create one. To begin working
on an existing repository, we still clone it the same way mentioned above.
This clone allows us to comfortably work locally and commit any change we want
on disk. This is done like so
```
  git add -A
  git commit -m "My first commit, exercising the git syntax."
```

The first line, `git add -A` "stages" our changes for a commit. In simple terms,
it marks all files in our repository to have their changes (new files, changed
or deleted) commited locally. Once we run a commit, it'll be "saved" 
to our local history of changes.
The -m flag adds a comment to our commit so we, and others, 
better understand what we've done.

To apply committed changes to the remote repository, we'll push them with
```
  git push
```

This updates the remote repository with our changes and brings it to
the latest version. Otherwise, no changes we commit locally will be visible
to the rest of the project group or public.



# Python variables, conditionals and loops
## Variables

One of the basic building blocks of any program is variables. Their function
is to store values throughout our code. With them, we can determine the state
our program and decide on an appropriate course of action. Their values can
stem from a wide variety of sources. From user input, to calculated data as
insight. 

In Python, we initiate a variable like so
```
x = 42
my_var = 1984
```

We do not need to specify the type of variable and can, simply, instruct
the interpreter what value to assign a new, or existing, variable. The
interpreter will determine the type. In the example above, we've created
two variables, `x` and `my_var`, with the integer values of 42 and 1984,
respectively. The assignment works from right to left. Whatever is on the right
 side of '=' is assigned to whatever is on the left side of '='.

> Create your own two variables, y and this_var, with the values 24 and 4891.

While integers are whole numbers (...,-2, -1, 0, 1, 2,...), anything inbetween
is called a floating number. To define one, we'll let Python guess the type.
```
my_float = 3.14
```
> Create your own float, floater, with the value 3.1415.


The last interesting type, for today, is string. If we want to hold data
composed of one or more characters (a-z, 0-9, !@#$%^ etc), we'll assign
them to a variable by enclosing the value with either double or single
quote marks (must begin and end with the same type of quote).
```
classic = "Hello, world"
works = 'yes'
```
> Create your own string, my_str, with the value '1ee7'.


## Types

If we try to add my_var and x, we'll see a reasonable result. But, if we try
to add works with my_var, we'll get an error. This is because these two types
of variables cannot be added together. Python's interpreter knows what it means
to add two numbers together, as it is defined in its code, but it doesn't know
what it means to add an integer to a string. 

Each variable has a type. The type defines how it behaves when used in
different ways. For example, if we add two strings together, they'll be
appended to each others' end. If we add two numbers, we'll get the
mathematical result of their addition.

The last thing we need is an operation to convert between the two. To convert
an integer to a string, we can use the `str()` function. To convert a string
to an integer, we can use the `int()` function.
```
bad = '21'
good = int(bad)
print(good*2)
print(bad*2)
```

We converted the string '21' into an integer so we'll be able to calculate
its multiplication by 2.

> What does `print(bad*2)` result in?


## Conditionals

Now, that we have some data, let's take a look at another fundamental
building block of any program; Conditionals. They fall under the category
of flow control. We use them to control in which directions our code will go.
An intuitive example is error checking, such as incorrect login credentials.
If, the user entered correct credentials, we'll take him to the main web page.
If, the user entered incorrect credentials, we'll display an error message.
Let's see how if works in Python.
```
if x == 42:
    print("This looks like an answer to many things.")
```

We see two things. First, the structure of the if statement. It starts
with `if` and ends with `:` while inbetween them we write the condition
we want to check. If the condition is met, in our example we're asking
if the variable x is equal to 42, the interpreter will execute whatever
is within the code block. 
Which brings us to the second point, the code block. The code block is the
line[s] of code the interpreter will execute "together" (analogous to a 
paragraph). It is marked with consistent indentation (in other programming
languages you might have seen this as { }). It begins where the interpreter
 first sees a prefix of 4 additional spaces (or 1 tab) to the line of code 
and ends when the prefix reverts to its previous value. 
Let's look at another example.
```
if x == 42:
    print("This line is within the code block.")
    print("And so is this.")
print("The above code block has ended.")
```

This time, the code block includes 2 lines. Once they're executed, the
interpreter continues. Were the condition false, both lines wouldn't be
executed.
```
if x == 41:
    print("There's one thing missing.")
    print("Or, as they say, close but no cigar.")
print("Boom.")
```

After we saw how the basic if statement works, let's review more complex
options it has.
```
if x == 41:
    print("It is 41.")
else:
    print("It is not 41.")
```
The first we see here is a simple if else statement that checks a condition
and has an explicit code block executed in case the condition isn't met.
```
if my_var != 1984:
    print("It is not equal to 1984.")
elif my_var > 1984:
    print("It is greater than 1984.")
    print("Might be much greater but definitely greater.")
elif my_var < 1984:
    print("It is smaller than 1984.")
else:
    print("It is neither different, greater or smaller than 1984.")
print("Done")
```
Here, we see how to check for a few conditions before "giving up" and
executing a line of code when none of the conditions are met. If any condition
is met, its code block is executed and the interpreter skips the rest of the if
structure.
```
if works == 'no':
    print("It doesn't work.")
elif works == 'maybe':
    print("It works. Maybe.")
print("I don't care if none of the conditions are met")
```
The else keyword is permissible. We don't have to use it. But, it must come after
`if` and any `elif` in the structure.

Each one of the 3 if statements above are a single structure. They begin
with an if, have the condition and semicolon. The other keywords are used
 according to our needs.

Another two noteworthy operators are `>=` and `<=`.

If we want to combine boolean statements, we can do so with `or` and `and` as
well as parenthesis.

```
if (x == 42 and my_var == 1984') or ( x == 42.0 and my_var == 1984.0):
    print("Variables remained unchanged.")
```

> Create a test for your assignments, so far, that checks all variables have their new value. e.g., x == 24

## Loops

As we continue on our hill climb, we'll now look at loops. They're operations
defined inside a code block to run many times. The first loop `while` is
controlled by a condition. It will start executing and continue to do so
as long as the condition is met.

```
while 1 == 1:
    print("Don't run this code.")
    print("Unless you like dancing lights in the darkness.")
```

Reminds us of the `if` structure. Here it begins with the `while` keyword
followed by the condition to check, each beginning of a loop, and ended
by a semincolon before the code block is written with an indentation.
Here, we check if 1 is equal to 1 and, while it is true, we print a couple
of sentences. Because this statement, 1 is equal to 1, is always true, this
loop will continue to execute forever.

```
x = 0
while x < 42:
    print("What is the answer, I wonder?")
    x = x + 1
print("I think it is forty two.")
```

This time, we chose to print a question 42 times while we increase the
value x. Once its value reaches 42, the statement becomes false and, the
loop breaks. It will stop executing whatever is in the code block and
continue to the next line after the while structure.

> Create your own loop that exits when x is 24 or larger but increments its value by one each iteration. Before the loop, assign 0 to x.
> Create your own loop that exits when x is at 24 and my_var is 19. Both variables should start at 0, before the loop. But, they cannot be incremented more than once each iteration. And, they cannot surpass their value by the time the loop ends.

Lastly, Python also allows the use of the `for` loop that we'll see next time.


## Input/Output

What is a program if it cannot communicate with us or others? We've seen a few
instances of print throughout our code examples. As our intuition might've
suggested, it writes to the screen whatever we supply it. Now, we'll see how
we can have the user input into the program (the user "writes" to us).

```
variabl1 = input("Please enter a value ")
```

When our code reaches this line, the program prints the message "Please enter
a value" and halts. It will not continue until the user, who started the code,
presses enter. Once the user pressed enter, whatever he typed before it (can
even be nothing) will be stored, as a string, in the variable on the left of
the equal sign. In other words, `variable1` will contain the typed value.

The primary usecase for this tool is to make our program interactive through
the terminal. If a browser interacts with us through a nice GUI, we can now
make a program that interacts with a nice black and white terminal.

## Finals

Write a program that asks the user to input his name and age.
Then, print a greeting message with his name and the year he was born.
```
Hello, Name! The year of 1949 was fully booked.
```


Write a program that asks for the user's age and prints out what century the
user was born in as well as if he's a kid (3-12), a teen (12-18) or an
adult (18 and over).


Write a program that asks the user for a number and a mathematical operator
(*, -, +, / etc). Print the sign, to the screen, as many times as the user's
number is.


Write a program that asks the user for two numbers and prints a rectangle. The
rectangle's size is determined by the numbers receives. The first is the rows
and the second is the columns. Use `*` as the building block of the shape.


Write a program that lets the user choose, from 3 shapes, which shape to print 
and at what size the shape should be.
The shapes are square, triangle and a rhombus. They should all be equilateral.
```
Square
****
****
****
****

Triangle
  *
 ***
*****

Rhombus
  *
 ***
*****
 ***
  *
```

If you're feeling brave, let the user choose a non-equilateral version.
