# C++-Programming-101s

A–Z Beginner-Friendly C++ Programming Guide
Goal: Teach you C++ from scratch in a simple, practical way — using clear explanations and small examples.
You can use this as a GitHub README or as your personal notes.
💡 Note: In this guide we’ll often write
using namespace std;
so we can use cout, cin, string, vector without std::.
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
A C++ compiler:
Windows:
MinGW-w64
Or install via MSYS2
Or use Visual Studio (with “Desktop development with C++” workload)
macOS:
Install Xcode Command Line Tools:
xcode-select --install
Linux:
Install g++ (Debian/Ubuntu):
sudo apt install build-essential
A code editor or IDE:
Beginner-friendly: Visual Studio Code, CLion, Qt Creator, or Visual Studio.
B. Basic Structure of a C++ Program
Minimal C++ program using using namespace std;:
#include <iostream>  // input/output library
using namespace std;

int main() {         // program starts here
    cout << "Hello, world!\n";
    return 0;        // optional in modern C++, but good to show
}
Breakdown
#include <iostream> – adds functionality for input/output.
using namespace std; – lets us write cout instead of std::cout.
int main() – the entry point of your program.
{ ... } – defines a block of code.
cout << "Hello"; – prints text to the screen.
; – every C++ statement ends with a semicolon.
C. Compiling & Running Your Code
Assume a file called hello.cpp.
Using g++ (Linux, macOS, Windows with MinGW)
g++ hello.cpp -o hello    # compile
./hello                   # run (Windows: hello.exe)
If it compiles with no errors, you’ll see:
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
<< “streams” or “sends” data to cout.
You can chain multiple << operators.
E. Expressions & Operators
Some core operators:
Arithmetic: +, -, *, /, % (remainder)
Comparison: ==, !=, <, >, <=, >=
Logical: && (AND), || (OR), ! (NOT)
Example:
int a = 10;
int b = 3;
int sum = a + b;                 // 13
int remainder = a % b;           // 1
bool bigger = a > b;             // true
bool between = (a > 5 && a < 20); // true
F. Flow Control – if, else, and switch
if and else
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
switch (multiple discrete choices)
#include <iostream>
using namespace std;

int main() {
    int day = 3;
    switch (day) {
        case 1: cout << "Monday\n"; break;
        case 2: cout << "Tuesday\n"; break;
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
        i++;  // i = i + 1
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
do...while loop (runs at least once)
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

// function declaration & definition
int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(3, 4);
    cout << "3 + 4 = " << result << "\n";
}
Key ideas:
int add(int a, int b) – function takes two ints and returns an int.
return gives back the result.
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
For bigger programs, you split code into files.
Example structure:
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
The standard library lives in a namespace called std.
Normally you would write:
#include <iostream>

int main() {
    std::cout << "Hello\n";
}
But if you add:
using namespace std;
you can write:
#include <iostream>
using namespace std;

int main() {
    cout << "Hello\n";
}
For beginners: using namespace std; is okay in small files.
In big projects, people often avoid it and use std::cout etc.
You can create your own namespace:
namespace maths {
    int add(int a, int b) { return a + b; }
}

int main() {
    int result = maths::add(1, 2);
}
L. Lists: Arrays and vector
C-style arrays
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    cout << arr[0];  // first element
}
Downside: fixed size, no bounds checking.
vector (recommended for beginners)
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
int x = 10;     // lives on the stack
Heap – dynamic storage (you manually request and release).
Old way (manual):
#include <iostream>
using namespace std;

int main() {
    int* p = new int(5); // allocate
    cout << *p;          // use
    delete p;            // free
}
Modern C++ prefers containers and smart pointers (vector, string, unique_ptr, etc.) that manage memory for you.
As a beginner, focus on:
Using normal variables
Using vector and string
Avoiding new / delete until you understand them better.
N. Null Pointers and Smart Pointers (Beginner View)
A pointer holds a memory address.
#include <iostream>
using namespace std;

int main() {
    int value = 42;
    int* ptr = &value;    // ptr points to value
    cout << *ptr << "\n"; // prints 42 (dereference)
}
nullptr
Represents “no object”:
#include <iostream>
using namespace std;

int main() {
    int* p = nullptr;
    if (p == nullptr) {
        cout << "No value yet.\n";
    }
}
Smart pointers (safer, modern C++)
#include <iostream>
#include <memory>
using namespace std;

int main() {
    auto p = make_unique<int>(5);  // unique_ptr manages memory
    cout << *p << "\n";
} // memory automatically freed here
As a beginner: just know they exist and are safer than raw new / delete.
O. Object-Oriented Basics: Classes & Objects
A class defines a new type with data and functions.
#include <iostream>
#include <string>
using namespace std;

class Person {
private:
    string name;
    int age;

public:
    // constructor
    Person(string name, int age)
        : name(name), age(age) {}

    void greet() const {
        cout << "Hi, I'm " << name
             << " and I'm " << age << " years old.\n";
    }
};

int main() {
    Person p("Alice", 25); // creates an object
    p.greet();
}
Key ideas:
private – hidden data, only accessible inside the class.
public – functions/data that users of the class can access.
Constructor sets initial values.
P. Parameters, References, and const
By value (copy)
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
By reference (no copy)
#include <iostream>
using namespace std;

void increment(int& x) { // reference
    x++;
}

int main() {
    int a = 5;
    increment(a);
    cout << a << "\n"; // now 6
}
const reference
Use when you don’t want to modify the value and want to avoid copying.
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
string
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s = "Hello";
    cout << s << "\n";
    cout << "Length: " << s.size() << "\n";
}
Characters (char)
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
R. Reading and Writing Files
Writing to a file
#include <fstream>
#include <string>
using namespace std;

int main() {
    ofstream out("output.txt");
    if (!out) return 1;

    out << "Hello file!\n";
}
Reading from a file
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
S. Standard Template Library (STL) Overview
The STL gives you powerful ready-made tools:
Containers
vector<T> – dynamic array
string – dynamic text
map<Key, Value> – key-value dictionary
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
Function templates
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
auto
Let the compiler figure out the type:
#include <iostream>
#include <string>
using namespace std;

int main() {
    auto x = 5;                // int
    auto y = 3.14;             // double
    auto s = string("Hello");  // string
}
U. Using C++ Safely: RAII & Initialization
RAII (Resource Acquisition Is Initialization):
Acquire resources in a constructor
Release them in the destructor
Use objects to manage resources
Example with file:
#include <fstream>
using namespace std;

int main() {
    {
        ofstream out("log.txt");
        out << "Hello\n";
    } // out goes out of scope, file is closed automatically
}
Always initialize your variables:
#include <string>
using namespace std;

int main() {
    int x{};        // x = 0
    string s{};     // empty string
}
V. Vectors, Ranges, and Range-based Loops
Range-based for loop
#include <vector>
#include <iostream>
using namespace std;

int main() {
    vector<int> nums = {1, 2, 3, 4};

    for (int x : nums) {
        cout << x << "\n";
    }
}
With auto
for (auto x : nums) {
    cout << x << "\n";
}
W. Working with Errors & Exceptions
Throwing & catching exceptions
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
For beginners: use exceptions mainly for serious errors (e.g., file not found, division by zero).
X. eXplaining Common Compiler Errors
Some classic errors:
1. Missing semicolon
error: expected ';' before 'return'
Fix: check the line before return or the line indicated.
2. Undeclared identifier
error: 'cout' was not declared in this scope
Possible fixes:
Forgot #include <iostream>
Forgot using namespace std; (or use std::cout).
3. Type mismatch
error: no matching function for call to 'add(double, int)'
Fix: check the types you are passing to the function.
4. Linker error (undefined reference)
undefined reference to `add(int, int)'
Often means:
You declared a function in a header
But did not define it in any .cpp
Or you forgot to compile/link that .cpp file.
Y. Your First Mini Project
Try building a simple console app that:
Stores a list of tasks (to-do list)
Lets the user:
Add tasks
List tasks
Mark a task as done
Example sketch
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
        cin.ignore(); // clear newline

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
This project touches:
struct
vector
User input
Loops & conditionals
Z. Zero to Next Steps – How to Keep Learning
To go from beginner to intermediate:
Practice small problems daily
Simple calculators
Guessing games
Text menus
File processing (e.g., reading a list of names from a file)
Read other people’s code
Look at simple C++ projects on GitHub.
Learn more modern C++ features
optional, variant, lambdas, unique_ptr, etc.
Use tools
Debugger (VS Code, CLion, Visual Studio)
Static analysis (clang-tidy, etc.)
Build real projects
Console apps
Small Qt GUI app
Simple game using a library like SFML
