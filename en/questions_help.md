# Self-Check Answers for the Theory Defense Questions

Concise, verified answers to the questions in `questions.md`. The answers
are deliberately compressed — for the defense you should be able to expand
on each point in more detail and illustrate it with an example.

## Paradigm and OOP Fundamentals

**1. What is OOP.**
Object-oriented programming is a paradigm in which a program is built as a
collection of interacting objects that bundle together state (data) and
behavior (methods). The classical supporting principles are encapsulation,
inheritance, polymorphism, and abstraction.

**2. Class and object.**
A class is a description (blueprint) of a structure's data and behavior:
which fields and methods an entity will have. An object is a concrete
instance of a class, existing in memory while the program runs, with its
own field values. Many objects can be created from a single class.

**3. Instance vs. class methods/fields.**
Instance fields and methods belong to a specific object: each object holds
its own copy of the field values, and instance methods operate on that
particular object's state. Class (static) fields and methods belong to the
class itself, are shared by all instances, exist regardless of whether any
object has been created, and are invoked through the class name.

**4. "is-a" and "has-a".**
"is-a" is a generalization/specialization relationship, usually implemented
via inheritance or interface implementation (e.g., "a Dog is an Animal").
"has-a" is an ownership relationship, implemented via a field referencing
another object (e.g., "a Car has an Engine"); aggregation and composition
are special cases of it.

**5. Encapsulation.**
A mechanism that lets you bundle data together with the methods that
operate on that data into a single object, and hide the implementation
details from the user. External code interacts with the object only
through its public interface (methods), without direct access to its
internal state — access to that state is either fully closed off or goes
through getters/setters with checks. This protects the object's invariants,
lets you change the internal implementation without touching client code,
and reduces coupling between system components.

**6. Inheritance.**
A mechanism that lets a class (the subclass) acquire the fields and methods
of another class (the base class), establishing an "is-a" relationship and
enabling code reuse. A subclass can extend behavior or override inherited
methods.

**7. Abstraction.**
Singling out the characteristics of an object that are essential to the
problem at hand while hiding irrelevant details. Expressed through abstract
classes and interfaces, which describe a behavioral contract without
specifying a concrete implementation.

**8. Polymorphism, parametric polymorphism, and ad-hoc polymorphism.**
Polymorphism is the ability of objects of different types to be handled
through a common interface, with the actual behavior determined by the
object's real type at runtime (virtual dispatch, method overriding).
Parametric polymorphism (generics) is the ability to write code that works
uniformly with types supplied as a parameter (e.g., `List<T>`), checked at
compile time. Ad-hoc polymorphism is when the same operation (a method or
operator name) behaves differently depending on the types of its arguments;
it's implemented via method or operator overloading.

**9. Multiple inheritance.**
A situation where a class inherits directly from more than one base class
(supported, for example, in C++). In Java and C#, class inheritance is
single, but a class can implement multiple interfaces, which partially
covers the same needs.

**10. The "diamond problem".**
Arises when a class inherits from two classes that share a common base
class: the derived class ends up with ambiguous (duplicated) inherited
members of the shared ancestor. Solutions: virtual inheritance in C++ (a
single shared base-class subobject); disallowing multiple class inheritance
in favor of interfaces (Java, C#); explicit conflict resolution when using
traits/mixins.

**11. Association, aggregation, composition.**
Association is a general relationship where one class uses/references
another, with independent object lifecycles. Aggregation is a weak
"whole-part" relationship: the part can exist without the whole (e.g., a
"Department" and its "Employees"). Composition is a strong "whole-part"
relationship: the part's lifetime is bound to the whole (e.g., a "House"
and its "Rooms" — when the house is destroyed, the rooms cease to exist as
separate entities too).

**12. Constructor.**
A special method invoked when an object is created; it initializes the
object's state and guarantees that the object is in a valid state from the
start. It can be overloaded (several constructors with different
parameters) and can call another constructor of the same class.

**13. The `this` pointer/reference.**
An implicit reference to the current object inside a non-static method.
Used to distinguish an object's field from a same-named parameter, to pass
the current object as an argument to another method, or to call another
constructor of the same class (e.g., `this(...)` in Java).

**14. Access modifiers.**
Keywords that restrict the visibility of class members: `public` —
accessible from anywhere; `private` — only within the class; `protected` —
within the class and its subclasses (in some languages, also within the
package/module); a package/assembly-level modifier (package-private in
Java, `internal` in C#) — accessible within the module.

**15. Getters and setters.**
Methods that provide controlled read (getter) and write (setter) access to
private fields. They let you add validation and other logic when state
changes, preserving encapsulation instead of exposing the field directly.

**16. Interface.**
A contract that specifies a set of method signatures a class must
implement, without specifying their implementation. It lets different
classes be handled uniformly through the interface type, and in many
languages substitutes for multiple class inheritance, since a class can
implement several interfaces.

**17. Mutable and immutable objects.**
A mutable object allows its state to be changed after creation. An
immutable object fixes its state at creation time and cannot be changed
afterward (e.g., `String` in Java, tuples in Python). Immutability
simplifies reasoning about code, including in multithreaded contexts, and
rules out side effects from sharing a reference to the object.

**18. Covariance, contravariance, invariance.**
These describe how the subtyping relationship of composite types (generic
types, arrays, function types) relates to the subtyping of their
components. Covariance — if `B` is a subtype of `A`, then `C<B>` is
considered a subtype of `C<A>` (typical for return values and read-only
collections). Contravariance — the direction is reversed: a type that
accepts a more general parameter can be used where one accepting a more
specific parameter is expected (typical for function/handler parameters).
Invariance — `C<B>` and `C<A>` are not considered related by subtyping even
if `B` is a subtype of `A`; this is the default behavior for mutable
generic containers, in order not to break type safety.

## Design Principles and Quality

**19. SOLID.**
Five principles for designing classes and modules, aimed at making code
easier to extend and maintain.

- **S — Single Responsibility Principle.** A class should have only one
  reason to change, i.e., it should be responsible for one cohesive task.
  Example of a violation: a `Report` class that simultaneously computes
  data, formats it as HTML, and saves it to a file — changing the output
  format would force you to modify the same class as changing the
  computation logic.
- **O — Open/Closed Principle.** Classes should be open for extension but
  closed for modification: new behavior is added via inheritance,
  interface implementation, or composition, rather than by editing
  already-written and tested code. Example: a new payment method is added
  as a new implementation of a `PaymentMethod` interface, without changing
  the existing order-processing code.
- **L — Liskov Substitution Principle.** An object of a subtype must be
  substitutable for an object of the base type without breaking the
  program's correctness: a subclass must not weaken preconditions or
  strengthen postconditions of the base class. The classic violation
  example is a `Square` class inheriting from `Rectangle` and overriding
  `setWidth`/`setHeight` in a way that breaks the invariant of
  independently changeable sides that client code expects.
- **I — Interface Segregation Principle.** Several narrow, specialized
  interfaces are better than one general-purpose "fat" interface: a client
  should not depend on methods it doesn't use. Example: instead of one
  `Worker` interface with `work()` and `eat()` methods, robots that don't
  eat should get a separate `Eatable` interface.
- **D — Dependency Inversion Principle.** High-level modules should not
  depend on low-level modules — both should depend on abstractions
  (interfaces), not on concrete implementations. Example: an `OrderService`
  class should depend on a `NotificationSender` interface, not on a
  concrete `EmailSender` class, so that an `SmsSender` can be substituted
  without changing `OrderService`.

**20. GRASP (General Responsibility Assignment Software Patterns).**
A set of principles for assigning responsibilities to classes in
object-oriented design:

- **Information Expert.** A responsibility is assigned to the class that
  has the data needed to fulfill it: for example, computing an order's
  total is assigned to the `Order` class, since it holds the list of line
  items.
- **Creator.** Class `A` should create instances of class `B` if `A`
  aggregates, contains, or closely uses `B`, or has the data needed to
  initialize it (e.g., `Order` creates `OrderLine` objects).
- **Controller.** Handling a system event is delegated to a separate
  coordinator class (e.g., `OrderController`), unrelated to the UI, which
  distributes work among the domain objects.
- **Low Coupling.** Dependencies between classes should be minimized during
  design, so that changes in one class affect others as little as
  possible.
- **High Cohesion.** A class's responsibilities should be closely related
  and focused on a single task — this makes classes easier to understand
  and reuse.
- **Polymorphism.** Type-dependent behavior should be implemented via
  polymorphic methods in subclasses rather than via conditional constructs
  (`if`/`switch` on the object's type).
- **Pure Fabrication.** If there is no natural domain class for a
  responsibility, an artificial class is introduced that doesn't directly
  reflect the domain (e.g., a `Repository` for persisting objects to a
  database), in order to preserve high cohesion in the domain classes.
- **Indirection.** An intermediary object is introduced between two
  components to avoid direct coupling between them (e.g., a DAO interface
  between business logic and the database).
- **Protected Variations.** Points of likely change in a system are wrapped
  in a stable interface so that internal changes don't affect the rest of
  the system — essentially, the rationale behind the Open/Closed Principle
  achieved through interfaces.

**21. KISS, DRY, BDUF, YAGNI, APO.**
KISS (Keep It Simple, Stupid) — prefer the simplest solution that works.
DRY (Don't Repeat Yourself) — don't duplicate logic/knowledge; extract
shared code into one place. BDUF (Big Design Up Front) — an approach that
does extensive design of the whole system before coding begins (considered
overly rigid in agile compared to iterative design). YAGNI (You Aren't
Gonna Need It) — don't implement functionality until it's actually needed.
APO (Avoid Premature Optimization) — don't optimize code until profiling
shows it's actually necessary.

**22. Cohesion and coupling.**
Cohesion is the degree to which the elements within a single module/class
are logically related to one clearly defined task (high cohesion is a
design goal). Coupling is the degree of interdependency between different
modules/classes (low coupling is a design goal, so that changes in one
module don't require changes in others).

**23. Tell, Don't Ask.**
A design principle: instead of querying an object's state and making a
decision externally, you should "tell" the object what to do and let it
use its own encapsulated state to do it. This reduces coupling and
preserves encapsulation.

Example of violating the principle:

```
if (account.getBalance() >= amount) {
    account.setBalance(account.getBalance() - amount);
}
```

Here, external code queries the balance itself and makes the decision about
changing it itself, bypassing the object's own logic. The correct approach
is to delegate both the check and the state change to the object itself:

```
account.withdraw(amount); // decides for itself whether there are
                           // sufficient funds, and either withdraws
                           // the amount or throws an exception
```

**24. The Law of Demeter.**
Also known as "don't talk to strangers." A method of an object should only
call methods of: itself, its parameters, objects it created itself, or its
own direct fields — but not objects obtained through a chain of calls
(`a.getB().getC().doSomething()`). It reduces coupling between classes.

**25. Inversion of Control.**
A principle whereby control over creating dependencies and the flow of
execution is handed off from the component itself to an external
framework/container (for example, a DI container creates the dependencies
itself and supplies them to the component), rather than the component
actively obtaining/creating them itself.

**26. Separation of Concerns.**
The principle of splitting a program into independent parts, each
responsible for a separate concern (for example, separating business logic
from data access and from the user interface). It improves maintainability
and the ability to reuse code.

**27. The ISO 9126 quality model.**
A layered software quality model with six main characteristics, each
broken down into a set of attributes (sub-characteristics):

- **Functionality** — suitability, accuracy, interoperability, security,
  compliance;
- **Reliability** — maturity, fault tolerance, recoverability;
- **Usability** — understandability, learnability, operability;
- **Efficiency** — time behavior, resource utilization;
- **Maintainability** — analyzability, changeability, stability,
  testability;
- **Portability** — adaptability, installability, co-existence with other
  software, replaceability.

## Code: Smells, Refactoring, Error Handling

**28. Code smells.**
Surface indicators in source code that suggest a likely design problem
(they are not bugs in themselves), for example: an overly long method, a
"god" class, duplicated code, a "feature envy" method, magic numbers,
"shotgun surgery." They signal an opportunity for refactoring.

**29. Refactoring techniques.**
- **Extract Method** — pulling a code fragment out into its own named
  method to improve readability and reuse.
- **Rename Variable** — renaming a variable to a clearer name without
  changing the code's behavior.
- **Inline Temp** — replacing a temporary variable used only once with the
  expression it holds.
- **Replace Conditional with Polymorphism** — replacing type-dependent
  branching with a polymorphic method call on the corresponding subclasses.
- **Move Method** — relocating a method to the class whose data it works
  with the most, to improve cohesion and reduce coupling.

**30. Principles of error handling.**
Exceptions separate error-handling code from the main logic, let an error
propagate up the call stack to where it can be handled, and can carry
additional information about the error. Return codes require the calling
code to explicitly check the result of every call; simple to implement, but
easy to forget to check (typical of C). Fail-fast is an approach in which
an error is detected and reported as early as possible, preventing the
program from continuing to run with corrupted state, which makes
diagnosis easier.

**31. Technical and cognitive debt.**
Technical debt is the implied "cost" of future rework that arises from
choosing a quick but suboptimal solution instead of a better long-term
approach; over time this debt "accrues interest," making further changes
harder. Cognitive debt is the extra mental burden placed on developers by
complex, inconsistent, or poorly documented code/architecture, which
increases the effort needed to work safely with the system.

## Development Processes and Practices

**32. API, SDK, CLI.**
An API (Application Programming Interface) is a formally defined set of
functions, classes, protocols, or endpoints through which one program can
interact with another without knowing the details of its internal
implementation. There's a distinction, for example, between a library API
(a set of classes/functions called within a process) and a web API (REST,
GraphQL, gRPC over HTTP — for interaction between services over a network).

An SDK (Software Development Kit) is a broader toolkit for developers
targeting a specific platform or service: it typically includes one or more
APIs, libraries, build and debugging tools, emulators, and documentation
(for example, the Android SDK for developing Android apps).

A CLI (Command-Line Interface) is a way of interacting with a program via
typed commands in a terminal, as opposed to a graphical interface (GUI). It
is convenient for automation and scripting and is often itself implemented
as a thin layer over the same API/SDK.

**33. CI/CD and DevOps.**
**Continuous Integration** is a practice in which developers merge their
changes into a shared branch frequently (ideally several times a day); each
merge is automatically built and tested on a CI server, which catches
integration errors immediately rather than right before a release.

**Continuous Delivery** extends CI: after a successful build and tests, the
changes are automatically brought to a state ready for production
deployment (an artifact is built, all checks pass), but the final decision
to release is made by a human. **Continuous Deployment** goes a step
further: every change that passes the entire verification pipeline is
automatically deployed to production without manual approval.

**DevOps** is not a specific tool but a culture and a set of practices that
unite development (Dev) and operations (Ops) teams for faster, more
frequent, and more reliable software delivery. Typical practices:
automating build/testing/deployment (CI/CD), infrastructure as code (IaC),
monitoring and logging the production system, fast feedback from operations
back to development, and shared responsibility for the service's quality
and availability.

**34. Driven Development approaches.**

- **TDD (Test-Driven Development).** Development follows a "red — green —
  refactor" cycle: first a unit test is written that checks behavior that
  doesn't exist yet (the test fails — "red"); then the minimal code needed
  to pass it is written ("green"); then the code is improved through
  refactoring without changing behavior, keeping the tests green.
- **BDD (Behavior-Driven Development).** An evolution of TDD in which
  system behavior is described as scenarios in language close to natural
  language and understandable to the customer, typically in Given/When/Then
  form (e.g., using Gherkin/Cucumber): "Given an empty cart, when an item is
  added, then the cart total equals the item's price." Such scenarios serve
  both as requirements and as the basis for automated tests.
- **DDD (Domain-Driven Design).** An approach to designing complex systems
  in which the code's structure and terminology are built around a model of
  the subject domain; a single "ubiquitous language" is established, shared
  by developers and domain experts, and the domain itself is broken down
  into consistent bounded contexts.
- **FDD (Feature-Driven Development).** An iterative process in which work
  is organized around developing a set of small, client-valued features; it
  includes building an overall model, listing features, planning,
  designing, and implementing feature by feature.
- **MDD (Model-Driven Development).** A significant part of the code (or
  all of it) is generated from formal models (UML diagrams, domain-specific
  languages — DSLs) rather than written by hand; the model is the primary
  development artifact.
- **ATDD (Acceptance Test-Driven Development).** Acceptance criteria for a
  piece of functionality are formulated as concrete, verifiable examples
  (tests), agreed upon by developers, testers, and the customer before
  implementation begins; the implementation is considered complete once
  these tests pass.
- **PDD.** Has no generally accepted formal definition in software
  engineering; informally, and often jokingly, expanded as "Pain-Driven
  Development" — a decision to change the architecture is made only once
  the "pain" of maintaining the current solution becomes significant
  enough. At the defense, it's worth explicitly noting that the term is not
  standardized.

**35. Spec-Driven Development (SDD).**
A development approach in which a detailed specification (functional and/or
technical) is fixed as the source of truth and used to drive the
implementation — either by hand or via code generation (including with AI
tools) — with the resulting code subsequently checked for compliance with
that specification.

**36. Approaches to software versioning.**

- **Semantic Versioning (SemVer).** The format `MAJOR.MINOR.PATCH` (e.g.,
  `2.4.1`): `MAJOR` increases for backward-incompatible API changes,
  `MINOR` for adding new backward-compatible functionality, `PATCH` for
  backward-compatible bug fixes. Pre-release labels (`2.5.0-beta.1`) and
  build metadata (`2.5.0+build.42`) are also allowed. Widely used in
  libraries and package managers (npm, Maven, etc.), since it clearly
  signals the level of compatibility to consumers.
- **Calendar Versioning (CalVer).** The version number is built from the
  release date, e.g. `YYYY.MM` (`2026.09`) or `YY.MM.DD`; convenient for
  products with a regular, calendar-driven release cycle (for example,
  Ubuntu uses the `YY.MM` scheme).
- **Sequential (ordinal) versioning.** A simple, ever-increasing version
  counter (`build 1245`, `v1`, `v2`, `v3`, …) with no built-in compatibility
  semantics; often used for internal builds or products with continuous
  deployment, where distinct "releases" as such aren't singled out.
- **Perpetual alpha.** A product that is constantly and frequently updated
  but is deliberately never formally declared "stable" or "final" — an
  approach typical of web services that are updated continuously without
  traditional versioned releases.
- **Snapshot version.** A version that captures the current, not-yet-final
  and potentially unstable state of a component under active development
  (for example, the `-SNAPSHOT` suffix in the Maven/Gradle ecosystem:
  `1.2.0-SNAPSHOT`); such a version can change from build to build and is
  not intended for production use — the suffix is dropped when the release
  ships.
