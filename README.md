# learn-rust

1. **Install Rust.**

Install on Mac using the following command.

```bash
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

Verify installation using the following command.

```bash
$ rustc --version
```

Updating and Uninstalling

The name of the command-line tool for managing the version of Rust is `rustup`

```bash
// Update to newly release version
$ rustup update
// Uninstall Rust and rustup
$ rustup self uninstall
```

2. **Hello World**

```rust
fn main() {
  println!("Hello world!");
}
```

```bash
$ rustc main.rs
$ ./main
```

3. **Cargo**

Cargo is Rust’s build system and package manager.

```bash
$ cargo new hello_cargo --vcs=none
$ cd hello_cargo

# Option 1: build and the run the executable in 2 steps
$ cargo build
$ ./target/debug/hello_cargo
# Option 2(more convenient): build and run in one step
$ cargo run

# Check if there is any compiling issue, it skips the step of producing the executable so it's faster than cargo build
$ cargo check

# Build for release
$ cargo build --release

# Remove the target directory
$ cargo clean
```

4. **The guessing game**

* Because the *Cargo.lock* file is important for reproducible builds, it’s often checked into source control with the rest of the code in your project.
* In Rust, variables are immutable by default, meaning once we give the variable a value, the value won’t change.
* Another neat feature of Cargo is that running the `cargo doc --open` command will build documentation provided by all your dependencies locally and open it in your browser.

5. **Immutable by default**

```rust
let x = 1;// x is immutable
let mut y = 2;// y is mutable
```

6. **Constants**

* Constants aren’t just immutable by default—they’re always immutable.

* You declare constants using the `const` keyword instead of the `let` keyword, and the type of the value *must* be annotated.

* Rust’s naming convention for constants is to use all uppercase with underscores between words.

  ```rust
  const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;
  ```

7. **Shadowing v.s. Marking a variable as `mut`**

Declaring a new variable with the same name as a previous variable is called **shadowing**.

```rust
// Shadowing is scoped, it stops when it's scope is over.
fn main() {
    let x = 5;
    let x = x + 1;
    {
        let x = x * 2;
        println!("The value of x in the inner scope is: {x}"); // This will print 12
    }
    println!("The value of x is: {x}"); // This will print 6
}
```

* Shadowing is different from marking a variable as `mut` because we’ll get a compile-time error if we accidentally try to reassign to this variable without using the `let` keyword.
* Shadowing is different from marking a variable as `mut` because when we use the `let` keyword again, we can change the type of the value but reuse the same name.

```rust
let spaces = "   ";
let spaces = spaces.len(); // Not a problem.

let mut spaces = "   ";
spaces = spaces.len(); // Compile error, mismatched types.
```

8. **Data Types**

* Rust is a *statically typed* language, which means that it must know the types of all variables at compile time.
* Scalar Types: integer, floating point, char and boolean.
* Compound Types: tuple, array.

```rust
// Example of arrays
let a = [1, 2, 3, 4, 5];
let a: [i32; 5] = [1, 2, 3, 4, 5];
let a = [3; 5]; // [3,3,3,3,3]
```

9. **Integer Overflow**

When you’re compiling in debug mode, Rust includes checks for integer overflow that cause your program to *panic* at runtime if this behavior occurs.

When you’re compiling in release mode with the `--release` flag, Rust does *not* include checks for integer overflow that causes panics. Instead, if overflow occurs, Rust performs ***two’s complement wrapping***.

10. **Function**

* Rust code uses ***snake case*** as the conventional style for function and variable names, in which all letters are lowercase and underscores separate words.
* A function must declare the types of its parameters.
* In Rust, a curly-brace block like `{ /* ... */ }` is an expression that is allowed to contain statements. It also defines a syntactic scope for let-bindings inside it.

11. **Control Flow**

* Remember that blocks of code evaluate to the last expression in them, and numbers by themselves are also expressions. In this case, the value of the whole `if` expression depends on which block of code executes. This means the values that have the potential to be results from each arm of the `if` must be the same type.

```rust
let number = if condition { 5 } else { "six" }; // This won't compile.
```







