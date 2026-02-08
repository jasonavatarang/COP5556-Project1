# From-zero explanation + runnable starter

This folder is a *starter* project you can push to GitHub and build on.

## What your assignment wants (super simple)
1. Write/extend an ANTLR grammar so it can **parse** the language.
2. Run ANTLR to generate Java parser/lexer code.
3. Write a Java **interpreter** that walks the parse tree and executes code.
4. Add integer **I/O** (read and print).
5. Write **test .pas files** that prove your features work.

This starter already shows:
- `type T = class ... end;`
- `public/private/protected` (simple runtime check)
- `constructor Create(...)` + calling `T.Create(...)`
- field access `obj.x` and method call `obj.Inc()`
- `print(expr);` and `read(x);`

⚠️ This is NOT the full Pascal grammar. It’s a minimal subset so you can run something quickly.

## How to run

You need Java 17+ and the ANTLR jar (tool + runtime), e.g. `antlr-4.13.1-complete.jar`.

### 1) Generate parser
```bash
java -jar antlr-4.13.1-complete.jar -Dlanguage=Java -visitor -no-listener -o generated grammar/delphi.g4
```

### 2) Compile
macOS/Linux:
```bash
javac -cp "antlr-4.13.1-complete.jar:generated" -d out generated/*.java src/main/java/delphi/*.java
```

Windows uses `;` instead of `:`.

### 3) Run
```bash
java -cp "antlr-4.13.1-complete.jar:out" delphi.Main tests/test1.pas
```

Try also:
- `tests/test2.pas` (uses `read`)
- `tests/test3_private_access_error.pas` (should throw an error)
