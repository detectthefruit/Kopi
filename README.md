# Kopi

Kopi is a tiny, simple programming language built for learning and experimenting. It is meant to be easy to read, easy to change, and easy to understand.

## What Kopi is for

- Learn how a language works by reading the source code.
- Experiment with new ideas like functions, loops, and simple control flow.
- Build short programs without getting lost in complex syntax.
- Share ideas and grow a small community around language design.

## Run Kopi

Use the interpreter with a `.kopi` file:

```bash
kopi run examples/basics.kopi
```

Or use Python directly:

```bash
python3 main.kopi examples/basics.kopi
```

### Automatic PATH setup

In the Kopi dev container (Codespaces), the `kopi` command is automatically available in your PATH. After rebuilding the container, you can use:

```bash
kopi run examples/basics.kopi
kopi update
```

### Making `kopi` available globally (outside dev container)

To use `kopi` from anywhere outside the dev container, add the Kopi directory to your PATH:

```bash
export PATH="$PATH:/path/to/Kopi"
```

Then you can run:

```bash
kopi run path/to/file.kopi
kopi update
```

### Updating the VS Code extension

To update the Kopi language support extension in VS Code:

```bash
kopi update
```

This will automatically uninstall and reinstall the latest version of the extension.

## What separates Kopi from Java and Python

Kopi is designed to be both easy to write and expressive. Every programmer level gets an upgrade over traditional languages.

### Beginner-friendly advantages

- Clean syntax with optional semicolons and fewer keywords than Java.
- Interactive input/output with `read(...)` and `print(...)` for quick learning.
- Automatic string/number concatenation to reduce beginner type errors.
- Simple `let` declarations and `if` / `while` blocks that feel familiar without boilerplate.

### Amateur-friendly advantages

- Powerful built-ins like `range`, `zip`, `enumerate`, `sorted`, `map`, and `filter` for everyday scripting.
- Native collection literals for lists, dictionaries, and sets with easy slicing and indexing.
- `match` / `case` pattern matching for cleaner branch logic.
- Tuple unpacking and compact loop forms make medium-sized code easier to read than Java or Python.
- Optional type hints (`let x: number = 5`, `def add(a: number, b: number) -> number`) help catch errors at development time without enforcing strict typing.
- Built-in math functions (`math_sqrt`, `math_pow`, `math_floor`, `math_ceil`) and random utilities (`random_rand`, `random_int`, `random_choice`) eliminate dependency management.

### Technical programmer advantages

- `try` / `catch` exception handling and `assert` for more robust code.
- `import` modules, first-class function values, and default function parameters.
- File I/O built-ins and strong collection utilities without extra libraries.
- Lightweight memory footprint—Kopi uses significantly less RAM than Java or Python, making it suitable for embedded systems.
- No external dependencies: pure Python implementation means one file to run, no virtual environment complexity.
- Built-in JSON, HTTP, environment, and path utilities make scripting and automation fast without dependency management.
- Parallel helpers like `parallel_map` and `parallel_filter` let you scale I/O-heavy workloads easily.
- Declarative-style constructs like `match` and concise built-in iteration helpers provide a modern development experience.
- Fast startup time: Kopi programs launch instantly, without JVM warmup or dependency loading delays.

### Seven business-ready Kopi upgrades

1. Built-in JSON and HTTP support eliminates the need for external request/serialization dependencies.
2. `args()` and `env()` make CLI scripting and deployment automation simple for DevOps.
3. `parallel_map()` and `parallel_filter()` let I/O-heavy workloads scale without Python GIL complexity.
4. `path_join()` and `path_exists()` reduce shell-script friction and make filesystem tasks safer.
5. Fast startup and minimal runtime footprint mean quick scripts and lower infrastructural cost.
6. Pure open-source implementation avoids JVM licensing and Python virtual environment overhead.
7. Optional type hints improve reliability without forcing strict typing on every project.

## Why Kopi beats Python's pitfalls

- **Dynamic typing risks?** Optional type hints catch errors early during development, reducing runtime surprises.
- **Dependency hell?** Kopi includes math, random, and core utilities built-in—no pip, no virtual env conflicts.
- **Performance and memory?** Kopi is lightweight and interpreted directly, using less memory than Python or Java.
- **GIL threading issues?** Kopi supports `parallel_map` and `parallel_filter` so scripts can take advantage of concurrency for I/O-heavy tasks.
- **Dependency packaging issues?** Kopi includes JSON, HTTP, path, and environment utilities built in, reducing the need for external packages.

## Why Kopi beats Java's baggage

- **Verbose boilerplate?** Kopi cuts verbosity drastically—write 10 lines instead of 100.
- **Memory overhead?** No JVM means instant startup, minimal footprint, perfect for scripts and embedded systems.
- **Steep learning curve?** Kopi's syntax is beginner-friendly; start with `let` and `print`, scale to pattern matching and exceptions.
- **Slow startup?** Kopi runs instantly—no compilation, no JVM bootstrap delays.
- **Licensing concerns?** Pure open-source, no Oracle licensing costs.
- **Garbage collection pauses?** Kopi's lightweight design minimizes GC overhead and latency concerns.

## What you can write in Kopi

### Values

- Strings are written with double quotes:
  - `"Hello, Kopi!"`
- Numbers are written normally:
  - `42`
  - `-5`
- Booleans are written as `true` or `false`.
- Missing values are written as `none`.
- Lists are written with square brackets:
  - `[1, 2, 3]`
  - `["one", "two", "three"]`

### Variables

Use `let` to create a new name for a value:

```kopi
let count = 3
```

Change a value later using `=`:

```kopi
count = count + 1
```

### Print to the screen

Use `print(...)` to show values:

```kopi
print("Hello, world!")
print(count)
```

### Read from the user

Use `read(...)` to ask the user for input and store their answer:

```kopi
let name = read("What is your name? ")
print("Hello, " + name)
```

### Functions

A function is a named block of code that can use values and return a result:

```kopi
def add(a, b) {
    return a + b
}

let total = add(5, 7)
print(total)
```

### Type hints (optional)

Add type hints to variables and functions to catch errors earlier. Type hints are optional and not enforced:

```kopi
let x: number = 42
let name: string = "Alice"

def greet(person: string, age: number) -> string {
    return "Hello, " + person + "!"
}

print(greet("Bob", 30))
```

Type hints help document code and enable better IDE autocomplete without requiring strict type checking.

### Loops

Use `while` to repeat code until a condition becomes false:

```kopi
let count = 1
while (count <= 5) {
    print(count)
    count = count + 1
}
```

Use `for` to loop with a start, condition, and change:

```kopi
for (let i = 0; i < 5; i = i + 1) {
    print(i)
}
```

Use `break` and `continue` to control loop flow:

```kopi
for (let i = 0; i < 5; i = i + 1) {
    if (i == 2) {
        continue
    }
    if (i == 4) {
        break
    }
    print(i)
}
```

### Lists and indexing

Access list items using `[...]` and find size with `len(...)`:

```kopi
let items = ["red", "green", "blue"]
print(items[0])
print(len(items))
```

Modify a list with `append(...)`:

```kopi
let numbers = [1, 2]
append(numbers, 3)
print(numbers)
```

### Useful built-in functions

- `len(value)` — number of items in a list or length of a string
- `range(n)` — list of numbers from `0` to `n-1`
- `range(a, b)` — list of numbers from `a` to `b-1`
- `range(a, b, step)` — list by step
- `append(list, value)` — add a value to a list
- `pop(list)` — remove and return the last item
- `pop(list, index)` — remove and return a specific item
- `insert(list, index, value)` — insert a value into a list
- `remove(list, value)` — remove a value from a list
- `keys(dict)` — list all dictionary keys
- `values(dict)` — list all dictionary values
- `join(separator, list)` — join list items into a string
- `split(text, sep?)` — split a string into a list
- `replace(text, old, new)` — replace text in a string
- `map(func, iterable)` — run a Kopi function over each item in a list
- `filter(func, iterable)` — keep list items when a Kopi function returns true
- `parallel_map(func, iterable)` — run a function across a list concurrently
- `parallel_filter(func, iterable)` — filter a list concurrently
- `zip(list1, list2, ...)` — combine multiple lists element-wise
- `enumerate(list, start?)` — index elements in a list
- `args()` — get command-line arguments
- `env(name, default?)` — read environment variables
- `json_parse(text)` — parse JSON into Kopi values
- `json_stringify(value)` — serialize a value to JSON
- `http_get(url)` — fetch text from a URL
- `time_ms()` — current timestamp in milliseconds
- `sleep(seconds)` — pause execution for a number of seconds
- `path_join(parts...)` — build a filesystem path
- `path_exists(path)` — check whether a file or directory exists
- `upper(text)` — convert text to uppercase
- `lower(text)` — convert text to lowercase
- `type(value)` — show the type name
- `sum(list)` — add all numbers in a list
- `min(list)` — smallest value in a list
- `max(list)` — largest value in a list
- `sorted(list)` — return a sorted list
- `int(value)` — convert a string to a number
- `str(value)` — convert a value to text
- `any(list)` — true if any item is truthy
- `all(list)` — true if every item is truthy
- `abs(number)` — absolute value
- `copy(value)` — shallow copy of a list or dict
- `startswith(text, prefix)` — check string prefix
- `endswith(text, suffix)` — check string suffix
- `round(number)` or `round(number, digits)` — round a number
- `math_sqrt(number)` — square root of a number
- `math_pow(base, exponent)` — raise base to exponent
- `math_floor(number)` — round down to nearest integer
- `math_ceil(number)` — round up to nearest integer
- `random_rand()` — random float between 0 and 1
- `random_int(min, max)` — random integer between min and max (inclusive)
- `random_choice(list)` — randomly select an item from a list

### Advanced features

Kopi also supports:

- `none` for missing values
- `//` single-line comments and `/* ... */` block comments
- compound assignment: `+=`, `-=`, `*=`, `/=` 
- membership checks with `in`
- dictionary literals and property access: `data["value"]` and `data.value`
- `for (item in list)` loops for easy iteration
- `else if` chains for clearer conditional logic
- `try` / `catch` exception handling
- `assert` validation statements
- first-class functions as arguments to `map` and `filter`

### Conditionals

Use `if` and `else` to run different code paths:

```kopi
let score = 10
if (score > 5) {
    print("Great job")
} else {
    print("Keep trying")
}
```

### Comments

Add comments with `#`:

```kopi
# This is a note for people reading the code
let message = "Hello"
```

## VS Code support

This repo includes local VS Code language support in `.vscode-ext/kopi-language-support`.

To package and install the extension locally:

```bash
./scripts/package-extension.sh
code --install-extension kopi-language-support-1.0.0.vsix --force
```

To uninstall the Kopi extension from VS Code:

```bash
code --uninstall-extension kopi-org.kopi-language-support
```

To reinstall it after uninstalling:

```bash
./scripts/package-extension.sh
code --install-extension kopi-language-support-1.0.0.vsix --force
```
Alternatively
You can also keep the extension recommendation in your workspace so collaborators see it automatically:

- `.vscode/settings.json` maps `.kopi` files to the Kopi language
- `.vscode/extensions.json` recommends the Kopi extension

## Example lesson: `examples/basics.kopi`

This interactive lesson teaches you the basics of Kopi by having you type in your own values! Run it and follow along:

```bash
python3 main.kopi examples/basics.kopi
```

The lesson covers:
- Variables and storing user input
- Loops that run multiple times
- Conditionals that make choices
- Functions that hold reusable code

Each section prompts you to enter information, then uses it in the code.

For a second example that shows lists, `for` loops, built-ins like `len()` and `range()`, and list indexing, run:

```bash
python3 main.kopi examples/advanced.kopi
```

## How Kopi works

- `main.kopi` reads your file and sends it to the lexer, parser, and runtime.
- `lexer.kopi` turns text into small parts called tokens.
- `parser.kopi` turns tokens into a tree of statements and expressions.
- `runtime.kopi` runs that tree and produces output.

## Want to help?

Kopi is best when people try new features and share what works.

- Add more lessons in `examples/`
- Try adding `for` loops or `else if`
- Improve error messages when the code is wrong
- Share your ideas for new Kopi syntax
