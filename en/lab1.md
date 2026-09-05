# Lab Assignment #1. OOP Fundamentals: Designing a Class

## Assignment

Implement one of the variants listed below in one of the allowed
programming languages (see `common_requirements.md`). For the class, you
must prepare documentation generated with the standard documentation
generator for the chosen language (Doxygen for C++, Javadoc for Java,
XML documentation and DocFX for C#, Sphinx/pdoc for Python).

To verify the class, implement a console program with a menu. When running
unit tests, coverage must be **over 90%**, using a suitable unit
testing library for the chosen language (e.g., UnitTest++/Catch2/GoogleTest
for C++, JUnit for Java, NUnit/xUnit for C#, pytest/unittest for Python).

Every implemented class must have the following properties regardless of
the implementation language:

- encapsulation;
- separation of the program's console user interface from the class
  implementation;
- a copy constructor and copy-assignment operation, where appropriate for
  the class;
- proper resource release (destructor, `Dispose`/`using`,
  `try-with-resources`, a context manager, etc. — depending on what the
  language provides), where necessary;
- equality comparison operations (`==`, `!=`);
- operations for reading an object from text/a stream and writing it to
  text/a stream;
- mutual independence of the class and the user interface that uses it;
- separation of the class's declaration (interface) from its
  implementation, to the extent the language supports it.

## Porting C++-Specific Requirements

The variant descriptions are historically oriented toward C++ (operator
overloading, `.h`/`.cpp` separation). When completing the assignment in
another language, implement the same semantics using that language's own
tools. See the correspondence table below.

| Requirement | C++ | Java | C# | Python |
|---|---|---|---|---|
| Separating declaration and implementation | header file (`.h`) and implementation file (`.cpp`) | an interface plus a separate implementation class | `partial class`, or an interface plus an implementation class | an abstract base class (`abc.ABC`) plus an implementation class, separate modules |
| Equality comparison | `operator==`, `operator!=` | overriding `equals()` and `hashCode()` | overriding `Equals()` and `GetHashCode()`, optionally the `==`/`!=` operators | the magic methods `__eq__`, `__hash__` |
| Writing/reading an object | `operator<<`, `operator>>` | `toString()` plus a static `parse(String)` method | overriding `ToString()` plus a static `Parse`/`TryParse` method | `__str__`/`__repr__` plus a `from_string` method (`@classmethod`) |
| Arithmetic operations (`+`, `-`, `*`, `/` and their compound forms) | overloading the corresponding operators | named methods (`add`, `subtract`, `multiply`, `divide`), since Java has no operator overloading | operator overloading (`public static T operator +(...)`) | magic methods (`__add__`, `__sub__`, `__mul__`, `__truediv__`, `__iadd__`, …) |
| Indexing (`[]`) | `operator[]` | named methods (`get(i)` / `set(i, v)`) | an indexer `this[int i] { get; set; }` | `__getitem__` / `__setitem__` |
| Pre-/post-increment and decrement (`++`, `--`) | `operator++`, `operator--` | named methods `increment()` / `decrement()` (Java has no operator overloading) | overloading `operator ++` / `operator --` | methods `increment()` / `decrement()` (Python has no postfix operators) |
| Conversion to another type (e.g., to `double`) | a custom conversion operator | a `doubleValue()` method | a custom conversion operator (`explicit operator double`) | the `__float__` method |
| Order comparison operations (`>`, `>=`, `<`, `<=`) | overloading the comparison operators | implementing `Comparable<T>` (`compareTo`) | implementing `IComparable<T>` or overloading the operators | the magic methods `__lt__`, `__le__`, `__gt__`, `__ge__` |

If the chosen language has no language-level feature for a given point,
implement functionally equivalent behavior via a named method, preserving
encapsulation and testability. In the variant descriptions below, the word
"operator" should be read as "operation (a language operator or a named
method — see the correspondence table)".

## 1.1 Vector

Describe a class for working with a vector defined by its endpoint
coordinates in three-dimensional space. The class must implement the
following capabilities:

- retrieving the vector's endpoint coordinates;
- computing the vector's length;
- adding two vectors (`+`, `+=`);
- subtracting two vectors (`-`, `-=`);
- the cross product of two vectors (`*`, `*=`);
- multiplying a vector by a number (`*`, `*=`);
- dividing a vector by a number (`/`, `/=`);
- computing the cosine of the angle between two vectors;
- comparing two vectors by length (`>`, `>=`, `<`, `<=`).

## 1.2 English–Russian Dictionary

Describe a class implementing an English–Russian dictionary based on a
binary search tree (each node stores a word pair, with the English word as
the key). The class must implement the following capabilities:

- adding a new English word and its translation (`+=`); in C++, provide an
  overload for both C-strings (`char*`) and `std::string`;
- removing an existing English word from the dictionary (`-=`);
- looking up the translation of an English word (`[]`);
- replacing the translation of an English word (`[]`);
- determining the number of words in the dictionary;
- loading the dictionary from a file.

## 1.3 Rectangle

Describe a class for a rectangle whose sides are parallel to the coordinate
axes. The vertex coordinates must be integers. The class must implement the
following capabilities:

- retrieving the vertex coordinates;
- moving the rectangle;
- resizing it;
- increasing the size by one along each axis (pre- and post-increment);
- decreasing the size by one along each axis (pre- and post-decrement);
- constructing the smallest rectangle containing two given rectangles
  (`+`, `+=`);
- constructing the rectangle that is the intersection of two rectangles
  (`-`, `-=`).

## 1.4 Set Theory

Describe a "Set" class. The class must implement the following
capabilities:

- an element of the set may itself be another set;
- checking whether the set is empty;
- adding an element;
- removing an element;
- determining the cardinality of the set;
- checking whether an element belongs to the set (`[]`);
- the union of two sets (`+`, `+=`);
- the intersection of two sets (`*`, `*=`);
- the difference of two sets (`-`, `-=`);
- constructing the power set (the set of all subsets) of a given set.

### 1.4.1 Set

Describe an "Unordered Cantor Set" class (elements are not repeated and are
unordered). The class must additionally support building a set from a
string (for example, `{a, b, c, {a, b}, {}, {a, {c}}}`).

### 1.4.2 Multiset

Describe an "Unordered Multiset" class (elements may repeat). The class
must additionally support building a set from a string (for example,
`{a, a, c, {a, b, b}, {}, {a, {c, c}}}`).

## 1.5 Games

All game programs must have a console interface and a game menu.

### 1.5.1 Tic-Tac-Toe

Describe a class implementing the game of Tic-Tac-Toe (a board of arbitrary
size) for two players. The class must implement the following
capabilities:

- checking whether a mark (X/O) can be placed at a given position;
- retrieving the value at a given position (`[]`);
- setting the value at a given position (`[]`);
- checking whether one of the players has won.

### 1.5.2 15 Puzzle

Describe a class implementing the "15 Puzzle" game. The initial tile
placement is random. The class must implement the following capabilities:

- a random initial placement of the numbered tiles;
- rearranging tiles;
- retrieving the value of a tile (`[]`);
- checking whether the tiles are arranged correctly (solved).

### 1.5.3 Rubik's Cube

Describe a class implementing the Rubik's Cube puzzle. The class must
implement the following capabilities:

- a random initial arrangement of colors;
- loading the initial color arrangement from a file;
- rotating a face of the cube;
- checking whether the colored cells are arranged correctly (solved).

## 1.6 Mathematics

### 1.6.1 Signed Proper Fraction

Describe a class implementing the "signed proper fraction" data type. The
fraction must always be stored in reduced (simplified) form. The class
must implement the following capabilities:

- retrieving the numerator, denominator, and integer part;
- adding two fractions (`+`, `+=`);
- adding an integer to a fraction (`+`, `+=`);
- subtracting two fractions (`-`, `-=`);
- subtracting an integer from a fraction (`-`, `-=`);
- multiplying two fractions (`*`, `*=`);
- multiplying a fraction by an integer (`*`, `*=`);
- dividing two fractions (`/`, `/=`);
- dividing a fraction by an integer (`/`, `/=`);
- pre- and post-increment, pre- and post-decrement;
- comparing two fractions and a fraction with an integer (`>`, `>=`, `<`,
  `<=`);
- conversion to a floating-point type (`double`).

### 1.6.2 Single-Variable Polynomial

Describe a class for a single-variable polynomial defined by its degree and
an array of coefficients. The class must implement the following
capabilities:

- retrieving coefficient values (`[]`);
- evaluating the polynomial at a given argument (the "call the object as a
  function" operation — `operator()` in C++, `__call__` in Python, an
  `evaluate`/`apply` method in Java and C#);
- adding two polynomials (`+`, `+=`);
- subtracting two polynomials (`-`, `-=`);
- multiplying two polynomials (`*`, `*=`);
- dividing two polynomials (`/`, `/=`).

### 1.6.3 Signed Long Integer

Describe a class implementing an unbounded-length "signed long integer"
data type and operations on it. The class must implement the following
capabilities:

- converting the long integer to a built-in integer type;
- adding two long integers (`+`, `+=`);
- adding a regular integer to a long integer (`+`, `+=`);
- subtracting two long integers (`-`, `-=`);
- subtracting an integer from a long integer (`-`, `-=`);
- multiplying two long integers (`*`, `*=`);
- multiplying a long integer by an integer (`*`, `*=`);
- dividing two long integers (`/`, `/=`);
- dividing a long integer by an integer (`/`, `/=`);
- pre- and post-increment, pre- and post-decrement;
- comparing two long integers (`>`, `>=`, `<`, `<=`);
- comparing a long integer with a regular integer (`>`, `>=`, `<`, `<=`).

## 1.7 Matrix Theory

Describe a class implementing the "real-valued matrix" data type. The class
must implement the following capabilities:

- a matrix of arbitrary size with dynamic memory allocation (in languages
  with automatic memory management — using the language's standard dynamic
  structures);
- pre- and post-increment, pre- and post-decrement (increasing/decreasing
  every matrix element by one).

### 1.7.1 Real-Valued Matrix

The class must implement the following additional capabilities:

- changing the number of rows and columns;
- loading a matrix from a file;
- extracting a submatrix of a given size;
- checking the matrix type (square, diagonal, zero, identity, symmetric,
  upper triangular, lower triangular);
- transposing the matrix.

### 1.7.2 Real-Valued Matrix (Advanced Variant)

The class must implement the following additional capabilities:

- adding two matrices (`+`, `+=`);
- adding a number to a matrix (`+`, `+=`);
- subtracting two matrices (`-`, `-=`);
- subtracting a number from a matrix (`-`, `-=`);
- multiplying two matrices (`*`);
- multiplying a matrix by a number (`*`, `*=`);
- dividing a matrix by a number (`/`, `/=`);
- raising a matrix to a power (`^`, `^=`, or a named `pow` method);
- computing the determinant;
- computing the norm.

## 1.8 Abstract Machines

Describe classes implementing an abstract machine, its tape, its program
and rules, its head, its alphabet, and strings. The set of classes depends
on the type of abstract machine: the number of classes may vary but must
not be fewer than three. The classes must implement the following
capabilities:

- loading a program from an input stream;
- loading the tape's state from a stream;
- adding, removing, and viewing rules;
- setting and changing values on the tape;
- performing a single step and interpreting the entire program (increment
  and decrement operations may be used to move the head).

The program must accept, as a command-line argument, the path to a file
containing the abstract machine's initial state and the program to
interpret. On startup, the program reads the file's contents and executes
the rules. If the `-log` flag is given on the command line, the console
must print the current state of the abstract machine after each rule
execution.

### 1.8.1 Post Machine

Describe classes implementing a Post machine.

### 1.8.2 Turing Machine

Describe classes implementing a Turing machine.

### 1.8.3 Markov Algorithms

Describe classes implementing normal Markov algorithms.
