Rust is very fast and has excellent memory protection. It's fast because it's lightweight and doesn't have a garbage collector. 


# Compiling and Running

Basic rust files are run with .rs extensions. e.g.

`hello.rs`

They are compiled with the command

`rustc <sample_file>.rs`

which will spit out an executable that can be run as such

`./<sample_file>`

All rust functions begin with the **main** function. 
# Syntax

### Variables

Variables are assigned with the `let` keyword, for example with basic structure

```
fn main() {
	let x: i32 = 5; // Initialized variable with value. 
	println!("oranges");
}
```

and stuff can be printed with the `print!()` or `println!()` functions. As of writing I have no idea why they have '!'. 

Type annotation is not required. 

The Scope of a variable is to its block, and **shadowing** allows a variable to be re-declared in the same scope with the same name. Not sure why that's helpful. 

Variables must be initialized AND used (otherwise preppended with an underscore), and lines end with semicolons like C++. 

In general, in rust variables are **immutable**, and must be marked as variables explicitly. For example

```
fn main() {
	let mut x = 1; // set as mutable
	x+=2;          // How to increment by whatever
}
```

#### Type Annotations and Definition

We can also define multiple variables at the same time via tuples. 

```
let (x,y);

(x,...) = (3, 4);
[..., y] = [1, 2];

// This will yield x = 3, y = 2
```

Type table

| Type            | Annotation |
| --------------- | ---------- |
| String          | &str       |
| 32-bit Integer  | i32        |
| 32-bit float    | f32        |
| Unsigned int 16 | u16        |
The default for ints it i32 and floats is f64, and without annotation the compiler will infer. The processor reads in data in "words".

Going to mostly ignore this stuff for now, if I get into data processing, come back to this section more. 

### Printing

Print statements can be made simply as such

```
println!("The value of x is {}", x);
```

### Shadowing

Variables cannot be redefined outside of mutability notation. If they're defined in a different scope, the variables are treated as different pieces of memory and are separate. 

In the same scope, rust will complain. ??? Will it tho??? 