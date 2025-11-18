C++ Programming 101s
A–Z Beginner-Friendly C++ Programming Guide
Goal: Teach you C++ from scratch in a simple, practical way — using clear explanations and small examples.
You can use this as a GitHub README or as your personal notes.
💡 In this guide we’ll often write using namespace std; so we can use cout, cin, string, vector without std::.
Table of Contents
A. About C++ & What You Need
B. Basic Structure of a C++ Program
C. Compiling & Running Your Code
D. Data Types & Variables
E. Expressions & Operators
F. Flow Control – if, else, and switch
G. Getting Repetition – Loops
H. Handling Input & Output (cin / cout)
I. Introducing Functions
J. Joining Code with Header & Source Files
K. Keeping Things Organized with Namespaces
L. Lists: Arrays and vector
M. Memory Basics: Stack vs Heap
N. Null Pointers and Smart Pointers (Beginner View)
O. Object-Oriented Basics: Classes & Objects
P. Parameters, References, and const
Q. Quick Look at string & Characters
R. Reading and Writing Files
Project Workflow & File Checklist
S. Standard Template Library (STL) Overview
T. Templates & auto (Very Simple Intro)
U. Using C++ Safely: RAII & Initialization
V. Vectors, Ranges, and Range-based Loops
W. Working with Errors & Exceptions
X. eXplaining Common Compiler Errors
Y. Your First Mini Project
Z. Zero to Next Steps – How to Keep Learning
A. About C++ & What You Need
C++ is a powerful language used for:
Games (Unreal Engine)
Desktop apps (Qt, etc.)
Embedded systems (microcontrollers)
High-performance systems (databases, trading systems, etc.)
What you need to start
A C++ compiler
Windows
MinGW-w64
Or install via MSYS2
Or use Visual Studio (with “Desktop development with C++” workload)
macOS
Xcode command-line tools:
xcode-select --install
Linux (Debian/Ubuntu)
sudo apt install build-essential
A code editor or IDE
Visual Studio Code
CLion
Qt Creator
Visual Studio
B. Basic Structure of a C++ Program
Minimal C++ program with using namespace std;:
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, world!\n";
    return 0;
}
Breakdown
#include <iostream> – adds functionality for input/output.
using namespace std; – lets us write cout instead of std::cout.
int main() – entry point of your program.
{ ... } – block of code.
cout << "Hello"; – prints text to the screen.
; – ends the statement.
C. Compiling & Running Your Code
Assume a file called hello.cpp.
g++ hello.cpp -o hello    # compile
./hello                   # run (Windows: hello.exe)
If it compiles with no errors, you should see:
Hello, world!
D. Data Types & Variables
A variable is a named box in memory that stores a value.
Common data types
int age = 20;          // whole numbers
double price = 9.99;   // decimal numbers
char grade = 'A';      // single character
bool isHappy = true;   // true or false
Printing variables
#include <iostream>
using namespace std;

int main() {
    int age = 20;
    cout << "Age: " << age << "\n";
}
Notes:
<< “streams” / sends data to cout.
You can chain multiple << operators.
E. Expressions & Operators
Some core operators:
Arithmetic: +, -, *, /, %
Comparison: ==, !=, <, >, <=, >=
Logical: && (AND), || (OR), ! (NOT)
int a = 10;
int b = 3;
int sum = a + b;
int remainder = a % b;
bool bigger = a > b;
bool between = (a > 5 && a < 20);
F. Flow Control – if, else, and switch
if / else
#include <iostream>
using namespace std;

int main() {
    int age;
    cout << "Enter age: ";
    cin >> age;

    if (age >= 18) {
        cout << "You are an adult.\n";
    } else {
        cout << "You are a minor.\n";
    }
}
else if
if (mark >= 75) {
    cout << "Distinction\n";
} else if (mark >= 50) {
    cout << "Pass\n";
} else {
    cout << "Fail\n";
}
switch
#include <iostream>
using namespace std;

int main() {
    int day = 3;
    switch (day) {
        case 1: cout << "Monday\n";    break;
        case 2: cout << "Tuesday\n";   break;
        case 3: cout << "Wednesday\n"; break;
        default: cout << "Unknown day\n"; break;
    }
}
G. Getting Repetition – Loops
while loop
#include <iostream>
using namespace std;

int main() {
    int i = 1;
    while (i <= 5) {
        cout << i << "\n";
        i++;
    }
}
for loop
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        cout << i << "\n";
    }
}
do...while loop
#include <iostream>
using namespace std;

int main() {
    int x;
    do {
        cout << "Enter a number (0 to quit): ";
        cin >> x;
    } while (x != 0);
}
H. Handling Input & Output (cin / cout)
Output with cout
#include <iostream>
using namespace std;

int main() {
    cout << "Hello" << " " << "C++!\n";
}
Input with cin
#include <iostream>
using namespace std;

int main() {
    int age;
    cout << "Enter your age: ";
    cin >> age;
    cout << "You entered: " << age << "\n";
}
Reading a whole line (getline)
#include <iostream>
#include <string>
using namespace std;

int main() {
    string name;
    cout << "Enter your full name: ";
    getline(cin, name);
    cout << "Hello, " << name << "!\n";
}
I. Introducing Functions
A function is a reusable block of code.
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(3, 4);
    cout << "3 + 4 = " << result << "\n";
}
You can also have void functions (don’t return a value):
#include <iostream>
using namespace std;

void greet() {
    cout << "Hello from a function!\n";
}

int main() {
    greet();
}
J. Joining Code with Header & Source Files
Split bigger programs into separate files.
Example structure
main.cpp
math_utils.h
math_utils.cpp
math_utils.h
#pragma once

int add(int a, int b);
int multiply(int a, int b);
math_utils.cpp
#include "math_utils.h"

int add(int a, int b) {
    return a + b;
}

int multiply(int a, int b) {
    return a * b;
}
main.cpp
#include <iostream>
#include "math_utils.h"
using namespace std;

int main() {
    cout << add(2, 3) << "\n";
    cout << multiply(4, 5) << "\n";
}
Compile:
g++ main.cpp math_utils.cpp -o app
./app
K. Keeping Things Organized with Namespaces
The standard library lives in namespace std.
With using:
#include <iostream>
using namespace std;

int main() {
    cout << "Hello\n";
}
Custom namespace example:
#include <iostream>
using namespace std;

namespace maths {
    int add(int a, int b) { return a + b; }
}

int main() {
    int result = maths::add(1, 2);
    cout << result << "\n";
}
L. Lists: Arrays and vector
C-style arrays
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    cout << arr[0] << "\n";  // first element
}
vector (recommended)
#include <vector>
#include <iostream>
using namespace std;

int main() {
    vector<int> nums;   // empty

    nums.push_back(10);
    nums.push_back(20);
    nums.push_back(30);

    cout << "Size: " << nums.size() << "\n";

    for (int x : nums) {
        cout << x << "\n";
    }
}
M. Memory Basics: Stack vs Heap
Stack – automatic storage:
int x = 10;   // on the stack
Heap – manual dynamic storage:
#include <iostream>
using namespace std;

int main() {
    int* p = new int(5); // allocate on heap
    cout << *p << "\n";  // use
    delete p;            // free
}
For beginners, prefer:
Normal variables
vector, string
Avoid new / delete until later.
N. Null Pointers and Smart Pointers (Beginner View)
Raw pointer
#include <iostream>
using namespace std;

int main() {
    int value = 42;
    int* ptr = &value;
    cout << *ptr << "\n";  // 42
}
nullptr
#include <iostream>
using namespace std;

int main() {
    int* p = nullptr;

    if (p == nullptr) {
        cout << "No value yet.\n";
    }
}
Smart pointer
#include <iostream>
#include <memory>
using namespace std;

int main() {
    auto p = make_unique<int>(5);
    cout << *p << "\n";
} // automatically freed
O. Object-Oriented Basics: Classes & Objects
#include <iostream>
#include <string>
using namespace std;

class Person {
private:
    string name;
    int age;

public:
    Person(string name, int age)
        : name(name), age(age) {}

    void greet() const {
        cout << "Hi, I'm " << name
             << " and I'm " << age << " years old.\n";
    }
};

int main() {
    Person p("Alice", 25);
    p.greet();
}
P. Parameters, References, and const
By value
#include <iostream>
using namespace std;

void increment(int x) {
    x++;
}

int main() {
    int a = 5;
    increment(a);
    cout << a << "\n"; // still 5
}
By reference
#include <iostream>
using namespace std;

void increment(int& x) {
    x++;
}

int main() {
    int a = 5;
    increment(a);
    cout << a << "\n"; // now 6
}
const reference
#include <iostream>
#include <string>
using namespace std;

void printName(const string& name) {
    cout << name << "\n";
}

int main() {
    string n = "Bobby";
    printName(n);
}
Q. Quick Look at string & Characters
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s = "Hello";
    cout << s << "\n";
    cout << "Length: " << s.size() << "\n";
}
Characters:
#include <iostream>
using namespace std;

int main() {
    char c = 'A';
    cout << c << "\n";
}
Loop through a string:
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s = "Hello";

    for (char c : s) {
        cout << c << "\n";
    }
}
Sample output:
H
e
l
l
o
R. Reading and Writing Files
Write to a file
#include <fstream>
#include <string>
using namespace std;

int main() {
    ofstream out("output.txt");
    if (!out) return 1;

    out << "Hello file!\n";
}
Read from a file
#include <fstream>
#include <iostream>
#include <string>
using namespace std;

int main() {
    ifstream in("output.txt");
    if (!in) {
        cout << "Could not open file.\n";
        return 1;
    }

    string line;
    while (getline(in, line)) {
        cout << line << "\n";
    }
}
Project Workflow & File Checklist
Use this section as a repeatable checklist every time you start a new C++ console project.
1. Create a project folder
Example structure:
C++Projects/
  MyFirstApp/
Inside MyFirstApp/ you can start with:
main.cpp
For slightly bigger projects:
MyFirstApp/
  src/
    main.cpp
    math_utils.cpp
  include/
    math_utils.h
  build/        # (optional) compiled files
  README.md
2. Per-project workflow
Plan quickly in plain English
What should the program do?
What inputs does it take?
What outputs should it show?
Create a minimal main.cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello from MyFirstApp!\n";
    return 0;
}
Compile and run:
g++ main.cpp -o app
./app
Add features step by step
Add one new feature (e.g., menu, extra function).
Compile & run after each change.
Fix errors immediately.
Split into .h and .cpp when it grows
Put declarations in include/*.h.
Put implementations in src/*.cpp.
Keep main.cpp as the “traffic controller” of the app.
Final tidy-up
Remove unused variables/functions.
Test with different inputs (including “weird” ones).
Make sure compile warnings are minimal (or zero).
3. File checklist for a small finished program
At minimum for a console project:
✅ main.cpp
Has int main()
Calls other functions/classes
✅ One or more implementation files:
e.g. src/math_utils.cpp, src/tasks.cpp
✅ Matching header files:
e.g. include/math_utils.h, include/task.h
✅ README.md
What the program does
How to compile
How to run
Example input/output
Optional but useful:
✅ build/ or bin/ folder for executables
✅ tests/ with small test programs
✅ A .gitignore if you’re using Git
S. Standard Template Library (STL) Overview
Containers
vector<T> – dynamic array
string – text
map<Key, Value> – key/value
set<T> – unique sorted values
Algorithms
sort(begin, end)
find(begin, end, value)
count(begin, end, value)
Example:
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {5, 2, 9, 1};

    sort(v.begin(), v.end());

    for (int x : v) {
        cout << x << " ";
    }
    // Output: 1 2 5 9
}
T. Templates & auto (Very Simple Intro)
#include <iostream>
using namespace std;

template<typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    cout << add(2, 3) << "\n";       // int
    cout << add(2.5, 3.1) << "\n";   // double
}
auto lets the compiler guess the type:
#include <iostream>
#include <string>
using namespace std;

int main() {
    auto x = 5;               // int
    auto y = 3.14;            // double
    auto s = string("Hello"); // string
}
U. Using C++ Safely: RAII & Initialization
RAII = Resource Acquisition Is Initialization.
#include <fstream>
using namespace std;

int main() {
    {
        ofstream out("log.txt");
        out << "Hello\n";
    } // file closed automatically here
}
Always initialize:
#include <string>
using namespace std;

int main() {
    int x{};      // 0
    string s{};   // empty
}
V. Vectors, Ranges, and Range-based Loops
#include <vector>
#include <iostream>
using namespace std;

int main() {
    vector<int> nums = {1, 2, 3, 4};

    for (int x : nums) {
        cout << x << "\n";
    }

    for (auto x : nums) {
        cout << x << "\n";
    }
}
W. Working with Errors & Exceptions
#include <iostream>
#include <stdexcept>
using namespace std;

int divide(int a, int b) {
    if (b == 0) {
        throw runtime_error("Division by zero");
    }
    return a / b;
}

int main() {
    try {
        cout << divide(10, 0) << "\n";
    } catch (const exception& ex) {
        cout << "Error: " << ex.what() << "\n";
    }
}
X. eXplaining Common Compiler Errors
1. Missing semicolon
error: expected ';' before 'return'
Check the line before return.
2. Undeclared identifier
error: 'cout' was not declared in this scope
Did you include <iostream>?
Did you add using namespace std; or use std::cout?
3. Type mismatch
error: no matching function for call to 'add(double, int)'
Check the function signature and argument types.
4. Undefined reference (linker error)
undefined reference to `add(int, int)'
Function declared but not defined
Or the .cpp file with the definition wasn’t compiled/linked.
Y. Your First Mini Project
Goal: Simple console to-do list app.
#include <iostream>
#include <vector>
#include <string>
using namespace std;

struct Task {
    string description;
    bool done = false;
};

int main() {
    vector<Task> tasks;
    int choice;

    do {
        cout << "\n1. Add task\n2. List tasks\n3. Mark done\n0. Exit\n> ";
        cin >> choice;
        cin.ignore(); // clear leftover newline

        if (choice == 1) {
            Task t;
            cout << "Task description: ";
            getline(cin, t.description);
            tasks.push_back(t);
        } else if (choice == 2) {
            for (size_t i = 0; i < tasks.size(); ++i) {
                cout << i << ": "
                     << (tasks[i].done ? "[x] " : "[ ] ")
                     << tasks[i].description << "\n";
            }
        } else if (choice == 3) {
            size_t index;
            cout << "Enter task index: ";
            cin >> index;
            if (index < tasks.size()) {
                tasks[index].done = true;
            } else {
                cout << "Invalid index.\n";
            }
        }

    } while (choice != 0);
}
Covers:
struct
vector
Loops & menus
Input handling
Z. Zero to Next Steps – How to Keep Learning
Practice daily
Calculators, guessing games, mini-menus, file readers.
Read code
Explore small C++ projects on GitHub.
Learn more modern features
unique_ptr, lambdas, optional, variant, array, unordered_map.
Use tools
Debuggers (VS Code, CLion, Visual Studio).
Static analysis (clang-tidy, sanitizers).
Build projects
Console apps → small Qt GUI → simple game (e.g. SFML).
