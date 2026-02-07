# Compilers

It’s one type of translator that converts high-level source code into machine code.

Compilers are grouped in three stages: front end, middle-end (optimization), and back end (code generation).  [Compiler - Wikipedia](https://en.wikipedia.org/wiki/Compiler)  You’ll find different articles or videos online, such as this one, [Compiler Architecture](https://cs.lmu.edu/~ray/notes/compilerarchitecture/), showing that the exact number of stages can vary. In this case, the stages are grouped into analysis and synthesis. They’re the same stages, just organized differently.

# Compilers

There are many existing compilers out there: GCC, Clang/LLVM, Rustc, etc. I’m trying to focus on Clang’s compiler when learning this. You can find definitions here: https://clang.llvm.org/docs/UsersManual.html.
## Front-end

| Term                                                                             | Description                                                   |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| [Lexer](https://en.wikipedia.org/wiki/Lexical_analysis)                          | Converts characters into tokens                               |
| [Parser](https://en.wikipedia.org/wiki/Parsing)                                  | Converts tokens into an AST                                   |
| [Token](https://en.wikipedia.org/wiki/Lexical_analysis#Token)                    | Atomic units: keywords, identifiers, literals, symbols        |
| [AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree)                        | Abstract Syntax Tree - tree representation of code structure  |
| [Symbol table](https://en.wikipedia.org/wiki/Symbol_table)                       | Maps names to declarations (functions, variables, and types)  |
| [Semantic Analysis](https://en.wikipedia.org/wiki/Semantic_analysis_(compilers)) | Type checking, scope resolution, name binding                 |
| [Type system](https://en.wikipedia.org/wiki/Type_system)                         | Checks type correctness of expressions                        |
| [IR](https://en.wikipedia.org/wiki/Intermediate_representation)                  | Intermediate Representation - compiler’s internal code format |
A minimal lexer:
```python
code = "5 + 6"
for char in code:
    if char != ' ':
        if char.isdigit():
            print("DIGIT")
        if char == '+':
            print("ADDITION")
```
Output:
```
DIGIT
ADDITION
DIGIT
```

The text of the source code is broken down into `tokens` where token is the **smallest element** of a program.
### Parsing

The most popular way to build a parser is a [recursive descent parser](https://en.wikipedia.org/wiki/Recursive_descent_parser)–a top-down parser using recursive function. You’ll find that some front end designs mix or separate the lexer and parser.

These are some other forms of writing a parser:
- [LL parser](https://en.wikipedia.org/wiki/LL_parser) - left-to-right, leftmost-derivation parser
- [LR parser](https://en.wikipedia.org/wiki/LR_parser) - left-to-right, rightmost-derivation parser

Definitions:
- [Formal grammar](https://en.wikipedia.org/wiki/Formal_grammar) - formal description of syntax rules
- [Operator precedence](https://en.wikipedia.org/wiki/Operator-precedence_parser) - grammar rules for operator precedence

There are [parser generator tools](https://en.wikipedia.org/wiki/Compiler-compiler) that generate parser from grammar (yacc, menhir, etc)

At the end of this, the front-end generates an Abstract Syntax Tree (AST) that is then lowered into IR.
```
Module
  Expr
    BinOp (+)
      Constant: 5
      Constant: 6
```
This was generated using Python’s AST module.

In my opinion, the lexer and the parser are the most boring parts of a compiler. I think the most interesting parts are working on the bounds checking, sanitizers, and lifetime analysis. Also, this is by no means everything. I’m missing a lot of theoretical related concepts, such as CFGs, parse trees, nonterminal/terminal, and more.

---
## Middle-end

This is the optimization stage (not target specific)  before the assembly generation.




---
## Back-end

