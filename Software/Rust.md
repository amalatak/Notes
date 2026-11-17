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
| Character       | char       |
| Boolean         | bool       |
Strings are noted with "", whereas chars are noted by ''

The default for ints it i32 and floats is f64, and without annotation the compiler will infer. The processor reads in data in "words".

Going to mostly ignore this stuff for now, if I get into data processing, come back to this section more. 

There are also bitwise operations e.g. `40 >> 2` to move all bits the right two spaces, making the value smaller. 

### Printing

Print statements can be made simply as such

```
println!("The value of x is {}", x);
```

### Shadowing

Variables cannot be redefined outside of mutability notation. If they're defined in a different scope, the variables are treated as different pieces of memory and are separate. 

In the same scope, rust will complain. ??? Will it tho??? 

### Logic

Boolean Operators are

| Operator/value | Value       |
| -------------- | ----------- |
| && or AND      | And         |
| \|\| or OR     | Or          |
| ! or NOT       | Not         |
| false          | False       |
| true           | True        |
| ==             | is equal to |

# Looping

A loop in rust is as such

```
for i in 0..5 {
	// do x;
}

for character in 'a'..='z' {
	// do y;
}
```

Range is from the value to the last one NOT inclusive. To add the last one do "..=int"

## Match Statements
These function as switch statements in other languages. Example: 
```
let number = 3;

match number {
    1 => println!("One"),
    2 => println!("Two"),
    3 => println!("Three"),
    _ => println!("Something else"),
}
```

And match can return an actual value, so we could say in the example above to assign the description to the result and then print it. 
```
let description = match number
...
println!("{}", description);
```

You can also match multiple values/ranges
```
let number = 7;

match number {
    1 | 2 => println!("One or two"),
    3..=5 => println!("Three through five"),
    6..=10 => println!("Six through ten"),
    _ => println!("Something else"),
}
```




# Functions
A function is a block of reusable code, takes arguments and returns a result. Diverging functions never complete. 

The `panic()!` function is an exit function to end a program. 
The `unimplemented!()` and `todo!()` functions can be placeholders. 

Can define an objects return type in a function declaration with the `->` notation e.g.
`fn get_something(var: u8) -> option<i32>`. 

## Ownership

Rust has an ownership system that do memory management. If these rules are violated then the code won't compile. 
1. Each value has an owner
2. There can only be one owner at a time
3. When the owner goes out of scope, the value will be dropped. 

All of this weird ownership stuff is used to prevent
* Dangling pointers - pointers to nowhere or garbage values
* Double free - free memory that's already free
* Memory leaks - not freeing memory that should have been
#### Scope
The range within a program for which an item is valid. 
* Global scope - is accessible throughout an entire program
* Local scope - accessible only within a particular function or block of code

#### Memory
Stores data and instructions, generally in RAM. Random Access Memory (RAM) - is volatile, when powered off all memory is lost. There are two types used by a program at runtime
* Stack Memory - Last in, first out (Like a stack of plates, top on top off)
	* All data in this must have a known, fixed size (int, bool, etc) 
	* Pushing to the stack is faster than allocating on the heap because new location is always the "top"
	* Types of unknown size will get allocated to the heap and a pointer to the value is pushed to the stack because a pointer is fixed size
* Heap Memory - Data of no known, fixed size goes on the heap
	* Allocating data on the heap will return a pointer (an address to allocated data)
	* Allocating on the heap is slower
	* Accessing data on the heap is also slower, it has to be accessed using a pointer. 
	* Heap could be e.g. a `String`; it's mutable
The pointer is a fixed size with a few values: ptr address, length, and capacity (amount of memory from the allocator). 

When values get "copied" to another value, there are two methods
* Copy - The value is actually copied to the memory for a second variable. E.g. assigning `x` a value and then `y=x;`
* Move - A pointer to the memory gets copied to the value. This happens for strings and mutable memory. Generally the first variable becomes unusable after this. 

Pointer data can be duplicated using the clone method, which is explicitly called. 
# Modules

Modules are imported as 
```
use std::ops::{Ramge, RangeInclusive}; 
// this would import range from the standard library
```