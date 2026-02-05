# Compilers

Compilers are grouped in three stages: frontend, middle-end (optimization), and backend (code generation).  [Compiler - Wikipedia](https://en.wikipedia.org/wiki/Compiler)  

In my opinion, the lexer and the parser are the most boring parts of a compiler. I think the most interesting parts are working on the bounds checking, sanitizers, and lifetime analysis. Also, this is by no means everything about compilers. I’m missing a lot of theoretical related concepts, such as CFGs, nonterminal/terminal, and more.

# Compilers

There are many existing compilers out there: GCC, Clang/LLVM, RustC, etc.

## Frontend

| Term                                                                             | Description                                                  |
| -------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| [Lexer](https://en.wikipedia.org/wiki/Lexical_analysis)                          | Converts characters into tokens                              |
| [Parser](https://en.wikipedia.org/wiki/Parsing)                                  | Converts tokens into an AST                                  |
| [Token](https://en.wikipedia.org/wiki/Lexical_analysis#Token)                    | Atomic units: keywords, identifiers, literals, symbols       |
| [AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree)                        | Abstract Syntax Tree - tree representation of code structure |
| [Symbol table](https://en.wikipedia.org/wiki/Symbol_table)                       | Maps names to declarations (functions, variables, and types) |
| [Semantic Analysis](https://en.wikipedia.org/wiki/Semantic_analysis_(compilers)) | Type checking, scope resolution, name binding                |
| [Type system](https://en.wikipedia.org/wiki/Type_system)                         | Checks type correctness of expressions                       |

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
### Parsing

The most popular way to build a parser is a [recursive descent parser](https://en.wikipedia.org/wiki/Recursive_descent_parser)–a top-down parser using recursive function.

- [LL parser](https://en.wikipedia.org/wiki/LL_parser) - left-to-right, leftmost-derivation parser
- [LR parser](https://en.wikipedia.org/wiki/LR_parser) - left-to-right, rightmost-derivation parser
- [Formal grammar](https://en.wikipedia.org/wiki/Formal_grammar) - formal description of syntax rules
- [Operator precendence](https://en.wikipedia.org/wiki/Operator-precedence_parser) - grammar rules for operator precedence

There are [parser generator tools](https://en.wikipedia.org/wiki/Compiler-compiler) that generate parser from grammar (yacc, menhir, etc)

## Middle-end


## Backend

