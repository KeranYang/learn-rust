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
