# C++ Programming 101s

A–Z Beginner-Friendly C++ Programming Guide

> Goal: Teach you C++ from scratch in a simple, practical way — using clear explanations and small examples.
>
> You can use this as a GitHub README or as your personal notes.
>
> Tip: This guide often uses `using namespace std;` so we can write `cout`, `cin`, `string`, `vector` without `std::`.

---

## Table of Contents

- A. About C++ & What You Need
- B. Basic Structure of a C++ Program
- C. Compiling & Running Your Code
- D. Data Types & Variables
- E. Expressions & Operators
- F. Flow Control – if, else, and switch
- G. Getting Repetition – Loops
- H. Handling Input & Output (`cin` / `cout`)
- I. Introducing Functions
- J. Joining Code with Header & Source Files
- K. Keeping Things Organized with Namespaces
- L. Lists: Arrays and `vector`
- M. Memory Basics: Stack vs Heap
- N. Null Pointers and Smart Pointers (Beginner View)
- O. Object-Oriented Basics: Classes & Objects
- P. Parameters, References, and `const`
- Q. Quick Look at `string` & Characters
- R. Reading and Writing Files
- Project Workflow & File Checklist
- S. Standard Template Library (STL) Overview
- T. Templates & `auto` (Very Simple Intro)
- U. Using C++ Safely: RAII & Initialization
- V. Vectors, Ranges, and Range-based Loops
- W. Working with Errors & Exceptions
- X. eXplaining Common Compiler Errors
- Y. Your First Mini Project
- Z. Zero to Next Steps – How to Keep Learning

---

## A. About C++ & What You Need

C++ is a powerful, general-purpose language used for:

- Games (Unreal Engine)
- Desktop apps (Qt)
- Embedded systems (microcontrollers)
- High-performance systems (databases, trading systems)

What you need to start:

1. A C++ compiler
   - Windows: MinGW-w64, MSYS2, or Visual Studio (install "Desktop development with C++")
   - macOS: Xcode command-line tools
     ```bash
     xcode-select --install
     ```
   - Linux (Debian/Ubuntu):
     ```bash
     sudo apt install build-essential
     ```
2. A code editor or IDE: Visual Studio Code, CLion, Qt Creator, Visual Studio

---

## B. Basic Structure of a C++ Program

Minimal program:

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, world!\n";
    return 0;
}
```

Breakdown
- `#include <iostream>` — input/output functionality
- `using namespace std;` — allows `cout` instead of `std::cout`
- `int main()` — entry point
- `cout << "Hello";` — print to screen

---

## C. Compiling & Running Your Code

Assume a file called `hello.cpp`:

```bash
g++ hello.cpp -o hello    # compile
./hello                   # run (Windows: hello.exe)
```

If it compiles you should see:

```
Hello, world!
```

---

## D. Data Types & Variables

A variable is a named box in memory.

Common types:

```cpp
int age = 20;        // whole numbers
double price = 9.99; // decimal numbers
char grade = 'A';    // single character
bool isHappy = true; // true or false
```

Printing variables:

```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 20;
    cout << "Age: " << age << "\n";
}
```

---

## E. Expressions & Operators

Core operators:

- Arithmetic: `+`, `-`, `*`, `/`, `%`
- Comparison: `==`, `!=`, `<`, `>`, `<=`, `>=`
- Logical: `&&` (AND), `||` (OR), `!` (NOT)

Example:

```cpp
int a = 10;
int b = 3;
int sum = a + b;
int remainder = a % b;
bool bigger = a > b;
bool between = (a > 5 && a < 20);
```

---

## F. Flow Control – if, else, and switch

if / else:

```cpp
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
```

`else if` example and `switch` example are similar — use `switch` for discrete integer-based choices.

---

## G. Getting Repetition – Loops

while:

```cpp
int i = 1;
while (i <= 5) {
    cout << i << "\n";
    i++;
}
```

for:

```cpp
for (int i = 1; i <= 5; ++i) {
    cout << i << "\n";
}
```

do...while (runs body at least once):

```cpp
int x;
do {
    cout << "Enter a number (0 to quit): ";
    cin >> x;
} while (x != 0);
```

---

## H. Handling Input & Output (`cin` / `cout`)

Output:

```cpp
cout << "Hello" << " " << "C++!\n";
```

Input:

```cpp
int age;
cout << "Enter your age: ";
cin >> age;
cout << "You entered: " << age << "\n";
```

Read a full line with `getline` (include `<string>`):

```cpp
string name;
getline(cin, name);
```

---

## I. Introducing Functions

Functions are reusable blocks:

```cpp
int add(int a, int b) {
    return a + b;
}

void greet() {
    cout << "Hello from a function!\n";
}
```

Call them from `main()`.

---

## J. Joining Code with Header & Source Files

Split bigger programs into `.h` (declarations) and `.cpp` (definitions).

Example structure:

- main.cpp
- include/math_utils.h
- src/math_utils.cpp

math_utils.h:

```cpp
#pragma once
int add(int a, int b);
int multiply(int a, int b);
```

Compile both `.cpp` files together:

```bash
g++ main.cpp src/math_utils.cpp -Iinclude -o app
```

---

## K. Keeping Things Organized with Namespaces

The standard library is in `std`.

Custom namespace example:

```cpp
namespace maths {
    int add(int a, int b) { return a + b; }
}

int result = maths::add(1, 2);
```

---

## L. Lists: Arrays and `vector`

C-style array:

```cpp
int arr[5] = {1,2,3,4,5};
cout << arr[0] << "\n";
```

`vector` (recommended):

```cpp
vector<int> nums;
nums.push_back(10);
cout << nums.size();
for (int x : nums) cout << x << "\n";
```

---

## M. Memory Basics: Stack vs Heap

Stack (automatic): local variables exist for the scope of a function.

Heap (dynamic): allocated with `new` and freed with `delete`.

Beginner advice: prefer automatic variables, `vector`, and `string`. Avoid `new`/`delete` until needed.

---

## N. Null Pointers and Smart Pointers (Beginner View)

Raw pointer example:

```cpp
int value = 42;
int* ptr = &value;
cout << *ptr << "\n";
```

Use `nullptr` to represent no pointer.

Smart pointer (unique_ptr) example:

```cpp
auto p = make_unique<int>(5);
cout << *p << "\n";
```

Smart pointers manage lifetime automatically.

---

## O. Object-Oriented Basics: Classes & Objects

```cpp
class Person {
private:
    string name;
    int age;
public:
    Person(string name, int age) : name(name), age(age) {}
    void greet() const {
        cout << "Hi, I'm " << name << " and I'm " << age << " years old.\n";
    }
};

Person p("Alice", 25);
p.greet();
```

---

## P. Parameters, References, and const

Pass by value (copy):

```cpp
void increment(int x) { x++; }
```

Pass by reference (modify original):

```cpp
void increment(int& x) { x++; }
```

Const reference (read-only, efficient):

```cpp
void printName(const string& name) { cout << name << "\n"; }
```

---

## Q. Quick Look at `string` & Characters

```cpp
string s = "Hello";
cout << s << "\n";
cout << "Length: " << s.size() << "\n";

for (char c : s) cout << c << "\n";
```

---

## R. Reading and Writing Files

Write:

```cpp
ofstream out("output.txt");
if (!out) return 1;
out << "Hello file!\n";
```

Read:

```cpp
ifstream in("output.txt");
if (!in) { cout << "Could not open file.\n"; return 1; }
string line;
while (getline(in, line)) cout << line << "\n";
```

---

## Project Workflow & File Checklist

Quick checklist when starting a small console project:

1. Create project folder. Example layout for a slightly bigger project:

```
MyFirstApp/
  src/
    main.cpp
    math_utils.cpp
  include/
    math_utils.h
  build/   # optional
  README.md
```

2. Workflow:
- Plan in plain English
- Create a minimal `main.cpp` and compile
- Add features incrementally and compile often
- Split into headers/source as it grows
- Tidy up and reduce warnings

3. File checklist for a small finished program:

- main.cpp (entry point)
- one or more implementation files (src/*.cpp)
- matching header files (include/*.h)
- README.md (how to compile & run)
- optional: build/, tests/, .gitignore

---

## S. Standard Template Library (STL) Overview

Common containers: `vector`, `string`, `map`, `set`.

Common algorithms: `sort`, `find`, `count`.

Example:

```cpp
vector<int> v = {5,2,9,1};
sort(v.begin(), v.end());
for (int x : v) cout << x << " ";
// Output: 1 2 5 9
```

---

## T. Templates & auto (Very Simple Intro)

Function template:

```cpp
template<typename T>
T add(T a, T b) { return a + b; }

cout << add(2,3) << "\n";      // int
cout << add(2.5,3.1) << "\n";  // double
```

`auto` lets the compiler deduce the type:

```cpp
auto x = 5;      // int
auto y = 3.14;   // double
```

---

## U. Using C++ Safely: RAII & Initialization

RAII — resource management by scope. Example: file streams close when they go out of scope.

Always initialize variables:

```cpp
int x{};      // 0
string s{};   // empty
```

---

## V. Vectors, Ranges, and Range-based Loops

```cpp
vector<int> nums = {1,2,3,4};
for (int x : nums) cout << x << "\n";
for (auto x : nums) cout << x << "\n";
```

---

## W. Working with Errors & Exceptions

Throw and catch exceptions:

```cpp
int divide(int a, int b) {
    if (b == 0) throw runtime_error("Division by zero");
    return a / b;
}

try { cout << divide(10, 0) << "\n"; }
catch (const exception& ex) { cout << "Error: " << ex.what() << "\n"; }
```

---

## X. eXplaining Common Compiler Errors

1. Missing semicolon — check the line before the reported error.
2. Undeclared identifier — did you include the right header or use the correct namespace?
3. Type mismatch — check function signatures and argument types.
4. Undefined reference (linker) — function declared but not defined or missing .cpp in compile.

---

## Y. Your First Mini Project

Simple console to-do list:

```cpp
struct Task { string description; bool done = false; };
vector<Task> tasks;
// menu loop: add, list, mark done, exit
```

Covers: structs, vector, loops, input handling.

---

## Z. Zero to Next Steps – How to Keep Learning

- Practice small daily projects: calculators, guessing games, file readers
- Read other people’s code on GitHub
- Learn modern features: `unique_ptr`, lambdas, `optional`, `variant`
- Use tools: debugger, sanitizers, static analysis (clang-tidy)
- Build up: console apps → small GUI → simple game (SFML)

---
