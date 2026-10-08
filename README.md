ASSIGNMENT: PYTHON PROJECT SETUP, GIT, AND GITHUB WORKFLOW

Project Name: python_lab
GitHub Repository: python-lab

============================================================
PART A - PROJECT SETUP USING THE CLI
============================================================

Commands used:

cd ~
mkdir python_lab
cd python_lab
mkdir src tests docs
touch src/main.py src/utils.py src/config.py
echo "My Python Lab Project." > docs/README.md
tree

If tree is not available:
find . -print

Expected project structure:

python_lab/
├── docs/
│   └── README.md
├── src/
│   ├── config.py
│   ├── main.py
│   └── utils.py
└── tests/

Explanation:

The cd command moves to a directory. The mkdir command creates directories.
The touch command creates empty files. The echo command together with output
redirection (>) writes the required text into README.md. The tree command
displays the directory structure recursively.

Separating code into src, tests, and docs is good practice because each
directory has a clear purpose. The src directory contains application code,
tests contains testing files, and docs contains project documentation.
This organization makes a project easier to understand, maintain, test,
and expand as it grows.


============================================================
PART B - GIT INITIALIZATION AND FIRST COMMIT
============================================================

Commands used:

git init
touch .gitignore
echo "__pycache__/" >> .gitignore
echo "*.pyc" >> .gitignore
echo ".env" >> .gitignore
cat .gitignore
git add .
git status
git commit -m "Set up Python lab project structure"
git log --oneline

Contents of .gitignore:

__pycache__/
*.pyc
.env

Explanation:

The .gitignore file tells Git which files and directories should not be
tracked. The __pycache__/ pattern ignores Python cache folders, while *.pyc
ignores compiled Python bytecode files. These files are automatically
generated and normally do not need to be stored in Git. The .env entry helps
prevent environment files containing private configuration information,
such as passwords or API keys, from being committed.

The Git commit history records changes made to the project over time. It
shows commit identifiers, messages, authorship, and the sequence of project
development. This makes it easier to understand changes and return to an
earlier version when necessary.


============================================================
PART C - WRITING AND COMMITTING PYTHON CODE
============================================================

FILE: src/utils.py

def square(n):
    return n ** 2


def is_even(n):
    return n % 2 == 0


def celsius_to_fahrenheit(c):
    return (c * 9 / 5) + 32


FILE: src/main.py

from utils import square, is_even, celsius_to_fahrenheit

number = float(input("Enter a number: "))

print("Square:", square(number))

if is_even(number):
    print("The number is even.")
else:
    print("The number is odd.")

print("Fahrenheit:", celsius_to_fahrenheit(number))


RUNNING THE PROGRAM

From the src directory:

cd src
python main.py

Or, on systems where Python 3 uses the python3 command:

python3 main.py


SAMPLE TEST 1

Enter a number: 5
Square: 25.0
The number is odd.
Fahrenheit: 41.0


SAMPLE TEST 2

Enter a number: 10
Square: 100.0
The number is even.
Fahrenheit: 50.0


SAMPLE TEST 3

Enter a number: 20
Square: 400.0
The number is even.
Fahrenheit: 68.0


IMPORT EXPLANATION

Python's import system allows one Python file to use functions defined in
another Python file. In this project, main.py uses:

from utils import square, is_even, celsius_to_fahrenheit

This tells Python to find the utils.py module and import the three specified
functions. Because main.py and utils.py are in the same src directory, Python
can locate the utils module when the program is run from that directory.
Separating reusable functions into utils.py makes the program easier to
maintain and reuse.

Commit commands:

cd ..
git add src/main.py src/utils.py
git commit -m "Add Python utility functions and main program"
git log --oneline


============================================================
PART D - PUBLISHING TO GITHUB AND BRANCH WORKFLOW
============================================================

Create a PUBLIC GitHub repository named:

python-lab

Do not initialize it with a README because the local project already has
files.

Connect the local repository:

git remote add origin https://github.com/YOUR-USERNAME/python-lab.git

Check the remote:

git remote -v

Rename the branch to main:

git branch -M main

Push the existing commits:

git push -u origin main


FEATURE BRANCH

Create the required feature branch:

git checkout -b feature/add-greeting


UPDATED FILE: src/utils.py

def square(n):
    return n ** 2


def is_even(n):
    return n % 2 == 0


def celsius_to_fahrenheit(c):
    return (c * 9 / 5) + 32


def greet(name):
    return f"Hello, {name}! Welcome to the Python Lab."


UPDATED FILE: src/main.py

from utils import square, is_even, celsius_to_fahrenheit, greet

number = float(input("Enter a number: "))

print("Square:", square(number))

if is_even(number):
    print("The number is even.")
else:
    print("The number is odd.")

print("Fahrenheit:", celsius_to_fahrenheit(number))

name = input("Enter your name: ")
print(greet(name))


TESTING THE GREETING

Example:

Enter a number: 10
Square: 100.0
The number is even.
Fahrenheit: 50.0
Enter your name: Diclot
Hello, Diclot! Welcome to the Python Lab.


COMMIT THE FEATURE

git add src/main.py src/utils.py
git commit -m "Add personalized greeting feature"


PUSH THE FEATURE BRANCH

git push -u origin feature/add-greeting


PULL REQUEST

On GitHub, open the python-lab repository.

Create a new pull request with:

Base branch:
main

Compare branch:
feature/add-greeting

Pull request title:
Add personalized greeting feature

Pull request description:

This pull request adds a personalized greeting feature to the Python Lab
project.

Changes made:
- Added a greet(name) function to utils.py.
- Imported the greet function into main.py.
- Added user input for a name.
- Displayed a personalized greeting.
- Tested the updated program successfully.

Purpose:
This feature demonstrates how a reusable function can be added to an
existing Python module and called from the main application.


============================================================
FINAL SUBMISSION CHECKLIST
============================================================

[ ] Part A directory structure completed
[ ] Part A recursive directory screenshot taken
[ ] Part A explanations included
[ ] Part B Git repository initialized
[ ] Part B .gitignore created
[ ] Part B first commit created
[ ] Part B commit-history screenshot taken
[ ] Part C three Python functions created
[ ] Part C main.py completed
[ ] Part C program tested with at least three inputs
[ ] Part C test-output screenshot taken
[ ] Part C changes committed
[ ] Part D public GitHub repository created
[ ] Part D main branch pushed to GitHub
[ ] Part D GitHub repository screenshot taken
[ ] Part D feature/add-greeting branch created
[ ] Part D greeting feature added and tested
[ ] Part D feature branch pushed
[ ] Part D pull request opened
[ ] Part D pull-request screenshot taken

END OF ASSIGNMENT

