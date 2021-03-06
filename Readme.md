# Scheme Interpreter

 *An interpreter written in Standard ML for a subset of the Scheme programming language.*

## How to Run

The Standard ML compiler [MLton](http://mlton.org/ "MLton") is required.  It can be found on package managers, e.g. `sudo apt-get install mlton` or equivalent.  Running `make` in this repo's root directory will build the `scheme` executable, which is run with a single Scheme source code file as the only command-line argument.

## Background

The formal syntax and operational semantics are based largely on the work of Prof. [Norman Ramsey](http://www.cs.tufts.edu/~nr/index.html) (Tufts University) in his book [Build, Prove, Compare](http://www.cs.tufts.edu/~nr/build-prove-compare/ "Build, Prove, Compare").  He defines a subset of Scheme that he calls "uScheme", or "micro-Scheme".

## Design Choices

Standard ML was chosen as the language of implementation for several reasons.  The first is that I have a great interest in functional languages, and this was partly a learning exercise to dive deeper into the functional paradigm.  Another reason is that Standard ML is well-suited to writing compilers and interpreters because of its strict type system and algebraic datatypes.

## TODO
- [ ] Syntax parsing
  -   [x] Definitions
    -   [x] Function definitions: `(define {ident} ({params}*) {exp})`
    -   [x] Variable definitions: `(val {ident} {exp})`
  -   [ ] Expressions
    -   [ ] Literals
      -   [x] Numeric literals: `3`, `-400`
      -   [x] Variables: `x`, `f`
      -   [x] Booleans: `#t`, `#f`
      -   [ ] S-expressions: `'(a b c)`, `'f`
    -   [x] If-expressions `(if {exp} {exp} {exp})`
    -   [x] Lambda expressions `(lambda ({ident}*) {exp})`
- [ ] Code evaluation
  -   [ ] Definitions
    -   [x] Function definitions
    -   [x] Variable definitions
  -   [ ] Expressions
    - [ ] Literals
      - [x] Numeric literals
      - [x] Variables
      - [x] Booleans
      - [ ] S-expressions
    - [x] If-expressions
    - [x] Lambda expressions

## Bugs

- [x] `(val x -)` should bind x to the minus operation; causes UnexpectedException
- [x] `(val x /)` gives `Var "/" not bound`
- [x] Implementing 'currying' gives a type error with primitive +
- [x] `Expected identifier` with `(val x ((curry +) 5))`
- [ ] All branches of if expressions always evaluate
