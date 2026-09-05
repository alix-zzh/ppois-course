# Lab Assignment #4. Generic Programming: Sorting and Containers

The assignment is historically phrased in C++ terms (templates, STL). When
implementing in another allowed language (see `common_requirements.md`),
read "template" as "generic type/function" in that language's terminology:
`template` in C++, generics in Java and C#, plain functions and classes
(with optional type annotations and duck typing) in Python.

The lab assignment consists of **two mandatory parts** — "Task 1" and
"Task 2" below must both be completed; they are not alternative variants to
choose between.

## Task 1. Sorting

According to your variant, implement a generic sorting function (or several
functions). The function must be able to sort both arrays and the
language's standard dynamic collections (`std::vector` in C++, `List<T>` in
Java and C#, `list` in Python) for elements of any type — both built-in and
user-defined. To demonstrate sorting user-defined objects, create your own
class and sort an array (or collection) of its objects.

For comparison, it is useful to study the ready-made sorting implementation
in the chosen language's standard library: `std::sort`/`std::stable_sort` in
C++, `Collections.sort`/`Arrays.sort` and the `Comparable`/`Comparator`
interface in Java, `Array.Sort`/`List<T>.Sort` and the
`IComparable`/`IComparer` interface in C#, the built-in `sorted()`/
`list.sort()` with a `key` parameter in Python.

### Variants

1. Bubble sort. Patience sorting.
2. Cocktail sort. Strand sort.
3. Comb sort. Tournament sort.
4. Gnome sort. Pigeonhole sort.
5. Selection sort. Bucket sort.
6. Insertion sort. Counting sort.
7. Shell sort. LSD Radix sort.
8. Binary tree sort. MSD Radix sort.
9. Library sort. Spreadsort.
10. Merge sort. Bozo sort.
11. In-place merge sort. Bogosort.
12. Heapsort. Stooge sort.
13. Smoothsort. Simple pancake sort.
14. Quicksort. Sorting networks.

## Task 2. Graphs

Implement a generic container (in C++, a class template) according to your
chosen variant. The implemented container must satisfy the following
requirements:

- have at least one generic type parameter specifying the type of the
  elements the container stores;
- expose public type aliases/descriptions where customary for the chosen
  language (`typedef`/`using` in C++; type parameters and nested types in
  Java and C#; type annotations in Python); the full list is determined by
  the assignment variant and the developer;
- a default constructor that creates an empty container;
- a copy constructor (in languages without an explicit copy constructor, a
  deep-copy method, e.g. `Clone`/`copy` or a similar static factory method);
- a destructor, if the language provides one and it's needed to release
  resources (or an equivalent mechanism: `Dispose`/`using`,
  `try-with-resources`, `__del__` — if explicit resource release beyond
  garbage collection is required);
- an emptiness check (an `empty`/`is_empty` method);
- clearing the container (a `clear` method);
- copy-assignment: an overloaded `=` operator in C++; in languages where
  such overloading isn't possible (Java, C#, Python), a named state-copying
  method (`assignFrom`/`CopyFrom`);
- comparison operations: `==`, `!=`, `>`, `<`, `>=`, `<=` (as operators in
  C++ and C#; via `equals`/`Comparable` in Java; via the magic methods
  `__eq__`, `__lt__`, etc. in Python);
- methods for accessing container elements (the exact list depends on the
  assignment variant);
- methods for adding elements to the container (the exact list depends on
  the assignment variant);
- methods for removing elements from the container (the exact list depends
  on the assignment variant);
- iterator classes (or objects) for traversing the elements, and methods
  for creating them (the iterator type and method list depend on the
  assignment variant); use the idiomatic iteration mechanism for the
  language — custom iterators satisfying the STL iterator concept in C++;
  the `Iterator`/`Iterable` interfaces in Java; `IEnumerator`/`IEnumerable`
  and `yield` in C#; the `__iter__`/`__next__` protocol in Python;
- a textual representation of the container, built using its iterators and
  a generic traversal algorithm (`operator<<` with `std::for_each` in C++;
  an overridden `toString()`/`ToString()`/`__str__` that iterates over the
  container in Java, C#, Python);
- throwing an exception when an error condition occurs.

The testing mechanism is up to the developer: a console menu or unit tests.

When defending the lab assignment, the student must be able to work with
the chosen language's generic types, know the structure and properties of
that language's standard container library, the types of iterators, and how
to use generic algorithms and function objects (functors/lambda
expressions/delegates).

### Variants

For all variants below, the general requirements are described in "Task 2"
above. The container must not expose how the graph is represented
internally — only methods and iterators are exposed externally. The
container must have one type parameter defining the type of value stored
at a graph vertex.

Every variant must implement:

- checking whether a vertex is present in the graph;
- checking whether an edge exists between two vertices;
- getting the number of vertices;
- getting the number of edges;
- computing the degree of a vertex;
- computing the degree of an edge;
- adding a vertex;
- adding an edge;
- removing a vertex;
- removing an edge;
- a bidirectional iterator for traversing vertices;
- a bidirectional iterator for traversing edges (hint: consider a value
  pair similar to `std::pair` — a tuple/record in other languages);
- a bidirectional iterator for traversing the edges incident to a vertex;
- a bidirectional iterator for traversing the vertices adjacent to a
  vertex;
- removing a vertex via a vertex iterator;
- removing an edge via an edge iterator;
- reverse variants for all iterators;
- const (read-only) variants for all iterators.

Whether to create generic wrapper classes to represent vertices and edges
is up to the developer.

1. **2.1.1 Undirected graph (adjacency matrix).**
2. **2.1.2 Directed graph (adjacency matrix).** Requirements — see 2.1.1.
3. **2.1.3 Undirected graph (incidence matrix).** Requirements — see 2.1.1.
4. **2.1.4 Directed graph (incidence matrix).** Requirements — see 2.1.1.
5. **2.1.5 Undirected graph (adjacency list).** Requirements — see 2.1.1.
6. **2.1.6 Directed graph (adjacency list).** Requirements — see 2.1.1.
7. **2.1.7 Undirected graph (ordered edge lists).** Requirements — see 2.1.1.
8. **2.1.8 Directed graph (ordered edge lists).** Requirements — see 2.1.1.
9. **2.1.9 Undirected graph (orthogonal adjacency list).** Requirements — see 2.1.1.
10. **2.1.10 Directed graph (orthogonal adjacency list).** Requirements — see 2.1.1.
11. **2.1.11 Undirected graph (Wirth's structure).** Requirements — see 2.1.1. For traversing adjacent vertices, additionally implement a forward-only (single-direction) iterator.
12. **2.1.12 Directed graph (Wirth's structure).** Requirements — see variants 2.1.1 and 2.1.11.
13. **2.1.13 Undirected graph (modified Wirth's structure).** Requirements — see 2.1.1.
14. **2.1.14 Directed graph (modified Wirth's structure).** Requirements — see 2.1.1.
