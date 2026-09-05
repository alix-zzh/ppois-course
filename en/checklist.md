# Instructor Checklist for Reviewing a Lab Assignment

A practical checklist for quickly reviewing a submitted lab assignment.
Detailed rationale for each item is in `common_requirements.md`,
`grade.md`, and the corresponding lab file (`lab1.md`–`lab4.md`).

## 1. Repository and Process

- [ ] The work is pushed to a git repository accessible to the instructor.
- [ ] The repository has no files unrelated to the source code (build
      artifacts, IDE files, temporary files) — a `.gitignore` is in place.
- [ ] Work happened in separate feature branches; changes reached `main`
      only through a Pull Request approved by the instructor.
- [ ] Commit messages are meaningful (not `commit 1`, `fix`, `wip`, `asdf`,
      or the like) and explain what was changed and why.

## 2. Testing and Build

- [ ] Unit tests exist with **over 90%** coverage.
- [ ] Tests run from the console, not tied to a specific IDE.
- [ ] The project builds from the console, without using an IDE.
- [ ] A CI/CD pipeline is set up on GitHub that automatically:
  - [ ] runs the tests and checks code coverage;
  - [ ] checks code quality (static analysis / linting);
  - [ ] builds a release artifact and publishes it to Releases.
- [ ] The Releases artifact can be downloaded and run independently of the
      development environment.

## 3. Code Quality (Common Mistakes)

- [ ] No magic numbers or hardcoded values (extracted into constants or a
      config).
- [ ] No overcomplicated constructs or unnecessary abstractions.
- [ ] Loop/`if-else` nesting does not exceed 3 levels within a single
      method.
- [ ] Methods/functions are no longer than ~20 lines.
- [ ] Lines of code are no longer than ~150 characters.
- [ ] Variable, function, and class names are informative (no `temp`, `k`,
      `p`, `buffer`, `help`, etc.).
- [ ] Naming and formatting style is consistent throughout the project.
- [ ] No commented-out or dead code, no `TODO`s in the final version.
- [ ] No long chained calls without intermediate variables.

## 4. Requirements Specific to Each Lab

### Lab 1 (OOP fundamentals: a class)

- [ ] The chosen assignment variant is fully implemented.
- [ ] Documentation is generated with the language's standard generator
      (Doxygen / Javadoc / XML docs+DocFX / Sphinx-pdoc).
- [ ] A console program with a menu exists to test the class.
- [ ] The class is encapsulated; the console UI is separated from the
      class implementation.
- [ ] Implemented where relevant: copy constructor and copy assignment,
      correct resource cleanup, equality comparison, reading/writing the
      object to/from a text stream.
- [ ] The class and the UI that uses it are mutually independent; the
      declaration is separated from the implementation using the
      language's own means.
- [ ] If the language is not C++ — the C++-specific constructs (operator
      overloading, `.h`/`.cpp`) are correctly carried over to the chosen
      language's means (see the correspondence table in `lab1.md`).

### Labs 2 and 3 (large-scale OOP project, two different domains)

- [ ] The domains for labs 2 and 3 are genuinely different.
- [ ] At least **50 classes**.
- [ ] At least **150 fields** in total.
- [ ] At least **100 unique, meaningful behaviors** (not
      getters/setters).
- [ ] At least **30 associations** between classes.
- [ ] At least **12 custom exception classes**.
- [ ] The repository has a README describing all classes, fields, methods,
      associations, and exceptions.

### Lab 4 (generic programming)

- [ ] **Both** required parts are done — sorting and the graph (not just
      one of the two).
- [ ] The generic sorting function works on both arrays and the language's
      standard dynamic collection, for built-in and custom types; a demo
      custom class exists.
- [ ] A graph is implemented per the assigned variant (representation:
      adjacency/incidence matrix, adjacency list, ordered edge lists,
      orthogonal adjacency list, Wirth structure, etc.).
- [ ] The container has a generic type parameter and does not expose its
      internal representation.
- [ ] Implemented: default constructor, copy constructor/deep copy, empty
      check, clear, copy assignment, comparison operations,
      access/add/remove element methods, bidirectional iterators
      (vertices, edges, incident edges, adjacent vertices) with reverse
      and const variants, iterator-based removal, a text representation
      built via iteration, exceptions thrown on error conditions.
- [ ] During the defense, the student is comfortable with the chosen
      language's generics and standard container library.

## 5. Extra Assignment (if assigned)

- [ ] A handwritten (on-paper) walkthrough of the algorithm/data structure
      is submitted together with the defense.
- [ ] The walkthrough covers: a step-by-step trace on a numeric example,
      time and space complexity (Big O) with justification, and — for data
      structures — the invariants it maintains and how they're preserved
      across modifying operations.

## 6. Defense

- [ ] Oral theory defense: **5 questions** from `questions.md` answered.
- [ ] Written theory defense: **10 questions** from `questions.md`
      answered.
- [ ] Code: **3 random spots** were picked, and the student fully explained
      what happens and why it's written that way (on failure — a
      handwritten walkthrough of the spot and a repeat defense with new
      spots, until fully successful).

## 7. Final Theory Mini-Lecture (submitted once, after all labs)

- [ ] Answers are given to **every** question in `questions.md`.
- [ ] The recording's total length is **more than 40 minutes**.
- [ ] If the video is shorter than 40 minutes — some answers were covered
      too shallowly and need to be expanded and re-recorded.

## 8. Academic Integrity

- [ ] The work was done independently and has passed a plagiarism check.
- [ ] Overlap with other work does not exceed the acceptable level (~30%
      of typical constructs); overlap above **50%** is grounds for
      assigning an extra lab (see section 5 above).

## 9. Outcome

- [ ] The number of labs submitted and the submission deadline are
      determined — cross-check against the admission/grade table in
      `grade.md`.
