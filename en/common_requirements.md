# General Requirements for Lab Assignments

This document describes the requirements common to all lab assignments in
the "Design of Intelligent Systems Software" course. For requirements
specific to a given lab, see the corresponding file (`lab1.md`–`lab4.md`).

## Allowed Programming Languages

You may use one of the following languages: **C++, Java, C#, Python**.

Some assignments are historically phrased in C++ terms (templates, operator
overloading, header/cpp files, etc.). When implementing in another language,
these requirements must be carried over using that language's own means:

- if the chosen language has no direct equivalent of a construct (for
  example, Java has no operator overloading), implement the equivalent
  functionality in an available way — e.g., via named methods (`add`,
  `equals`, `compareTo`, etc.);
- the intent of the requirement (encapsulation, separation of interface and
  implementation, testability) must be preserved regardless of language.

See the corresponding lab file for details on each assignment.

## Using LLMs and GenAI

Using LLMs and other GenAI tools to implement lab assignments is
**allowed**.

Students who plan to rely heavily on LLM/GenAI tools during implementation
are **recommended** (this is not a mandatory requirement) to follow a
Spec-Driven Development (SDD) approach — see `questions_help.md`, question
35 — and to use a dedicated framework for it, such as OpenSpec or SpecKit:
the specification of the solution is fixed first, and the code is then
generated/written against it, which reduces the risk of ending up with code
the student cannot explain (see "Responsibility for Your Code" below).

## Testing Requirements

- Each lab assignment must be covered by unit tests with **over 90%**
  coverage.
- Tests must be runnable from the console (not tied to a specific IDE).

## CLI Requirements

Every lab assignment must have a console interface (CLI/menu) that
demonstrates the meaningful functionality of the implemented domain — this
is a separate requirement, not satisfied merely by running unit tests. The
interface must expose the domain's key behaviors, for example: adding and
removing an employee, placing and shipping a package, computing a salary,
generating a report, and so on — the exact set of operations depends on the
domain and the type of lab assignment (see `lab1.md`–`lab4.md` for details
and special cases). As with other requirements, the CLI must be separated
from the domain implementation.

## Repository Requirements

- All lab assignments live in a **single** GitHub repository — separate
  repositories per lab assignment are not allowed.
- Inside the repository, each lab assignment goes into its own top-level
  folder: `lab1`, `lab2`, `lab3`, `lab4`.
- The repository must not contain files unrelated to the source code
  (build artifacts, IDE files, etc.) — use a `.gitignore`.
- Every commit on GitHub must have a clear, descriptive message (in Russian
  or English) that explains what was changed and why, rather than a
  placeholder note. Messages like `commit 1`, `commit 2`, `fix`, `fix 1`,
  `final fix`, `wip`, `asdf`, and the like are not allowed.
- Changes must never be pushed to `main` directly: work happens in
  separate feature branches, and changes reach `main` only through a
  Pull Request that the instructor has approved.

## Academic Integrity

- All lab assignments must be completed independently and pass a plagiarism
  check.
- A similarity above **50%** is considered a serious violation — in this
  case an extra lab assignment is required.
- An acceptable level of borrowed content (typical language constructs,
  boilerplate code, etc.) is around **30%**.

## Lab Defense

- Oral theory defense: **5 questions** from the question list (see
  `questions.md`).
- Written theory defense: **10 questions** from the question list.

### Responsibility for Your Code

Regardless of whether LLM/GenAI tools were used during implementation, the
student is fully responsible for all submitted code and must understand how
it works.

During the defense, the instructor picks **3 random spots** in the
student's code. The student must fully explain what happens at each spot
and why the code is written that way.

- If the student cannot fully explain a chosen spot, they must go and write
  out, by hand on paper, how that function or piece of code works (similar
  to the handwritten walkthrough described in `additional_labs.md`).
- The code defense is then repeated with new random spots.
- This repeats until the student can fully explain, for 3 random spots, how
  the code works and why it was implemented that way.

## Final Theory Mini-Lecture

At the end of **all** lab assignments (not after each individual one), a
mini-lecture must be recorded answering **every** question from the list
(see `questions.md`), roughly **1–2 minutes per question**. This is a
separate, final deliverable submitted once at the end.

The recording's total length must come out to **more than 40 minutes**. If
the final video is shorter, that's a sign some answers were covered too
shallowly and need to be expanded.

## Build, Testing, and CI/CD

- The project must build and be tested from the console, without using an
  IDE.
- A CI/CD pipeline must be set up on GitHub that automatically:
  - runs the tests and checks code coverage;
  - checks code quality (static analysis / linting);
  - builds a release artifact and publishes it in the repository's Releases
    section.
- The final artifact must be verifiable: it should be downloadable from
  Releases and runnable independently of the development environment.

## Common Mistakes

The following issues come up most often during review — check for them
before submitting:

1. **Magic numbers and hardcoded values.** These should be extracted into
   named constants or a configuration file.
2. **Overcomplicated code.** Do not overengineer the solution beyond what's
   needed — extra abstractions and constructs make the code harder to read.
3. **Deep nesting.** Nesting loops or `if-else` constructs more than 3
   levels deep within a single method is a sign the code should be split
   into separate functions.
4. **Overly large methods.** A method or function longer than ~20 lines
   (roughly one IDE screen) should usually be split into smaller ones.
5. **Overly long lines.** A line of code should not exceed ~150 characters
   (the width of the IDE work area).
6. **Unnecessary files in the repository.** Don't commit files unrelated to
   the source code (build artifacts, IDE files, temporary files) — set up a
   `.gitignore`.
7. **Uninformative names.** Avoid single-character or meaningless names for
   variables, functions, and classes: `temp`, `buffer`, `k`, `p`, `k1`,
   `k2`, `bcv`, `draft3`, `help`, etc.
8. **Inconsistent code style.** Stick to a single naming and formatting
   style throughout the project (don't mix `camelCase` and `snake_case`, or
   inconsistent capitalization, etc.).
9. **Commented-out and dead code.** Remove unused code instead of leaving it
   commented out; don't leave `TODO`s in the final version.
10. **Chained calls without intermediate variables.** Don't pass the result
    of one function directly into another across several nested levels —
    this hurts readability; use intermediate variables with clear names.
