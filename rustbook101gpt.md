    Generic Data Types

Alright, let's talk about generics and how they can make our code more flexible
and prevent code duplication. It's like having a Swiss Army knife that can
handle any task.

In Rust, we use generics to create definitions for things like function
signatures, structs, enums, and methods. These definitions can then be used with
different concrete data types. It's like having a blueprint that can be used to
build different types of houses.

    In Function Definitions

Let's start with function definitions. When we want to use generics in a
function, we place them in the function signature instead of specifying the
specific data types of the parameters and return value. This allows our function
to be more flexible and provides more functionality to the callers. It's like
having a menu that can cater to everyone's tastes.

Now, let's take a look at Listing 10-4, where we have two functions that find
the largest value in a slice. It's like having two ways to find the funniest
joke in a set. But we can make it even better by combining these functions into
a single function that uses generics. It's like finding the ultimate joke that
works for any crowd.

Filename: src/main.rs

```rust
fn largest_i32(list: &[i32]) -> &i32 {
    let mut largest = &list[0];

    for item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}

fn largest_char(list: &[char]) -> &char {
    let mut largest = &list[0];

    for item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}

fn main() {
    let number_list = vec![34, 50, 25, 100, 65];

    let result = largest_i32(&number_list);
    println!("The largest number is {}", result);

    let char_list = vec!['y', 'm', 'a', 'q'];

    let result = largest_char(&char_list);
    println!("The largest char is {}", result);
}
```

Listing 10-4: Two functions that differ only in their names and the types in
their signatures

Alright, let's take a look at Listing 10-4, where we have two functions that are
almost identical. It's like having two guys telling the same joke with just a
slight difference in delivery.

The first function, largest_i32, finds the largest i32 in a slice. The second
function, largest_char, does the same but for characters. Now, we all know that
code duplication is a big no-no. It's like telling the same joke over and over
again—it gets old real quick.

So, how can we eliminate this duplication and make our code more efficient?
Well, the answer is generics! We can introduce a generic type parameter in a
single function that works for both cases. It's like having a universal
punchline that works for any joke.

To do this, we need to name the type parameter. In Rust, it's common to use a
single letter like T as the type parameter name. T stands for "type," and it's
short and sweet, just like a good punchline.

When we use a type parameter in the body of the function, we have to declare it
in the function signature. It's like telling the audience the setup before
delivering the punchline. By declaring the type parameter, we let the compiler
know what it means and how it should be used.

To define the generic largest function, place type name declarations inside
angle brackets, <>, between the name of the function and the parameter list,
like this:

```rust
fn largest<T>(list: &[T]) -> &T {
```

Alright, ladies and gentlemen, get ready for the grand finale! In Listing 10-5,
we have the generic function we've all been waiting for. It's like the star of
the show, capable of handling any type you throw at it. Brace yourselves!

In the function signature, we declare the type parameter T inside angle
brackets, just like the audience waiting for the punchline. This tells the
compiler that the function largest is generic over some type T. The function
takes a parameter named list, which is a slice of values of type T. And here's
the kicker: the largest function will return a reference to a value of the same
type T. It's like a mirror that reflects the same type it receives.

Now, here comes the exciting part! In the main function, we can call the largest
function with different types of slices: one with i32 values and another with
char values. This function is versatile, my friends. It's like a comedian who
can adapt to any audience, whether they love numbers or characters.

Filename: src/main.rs

```rust
 [This code does not compile!] 
fn largest<T>(list: &[T]) -> &T {
    let mut largest = &list[0];

    for item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}

fn main() {
    let number_list = vec![34, 50, 25, 100, 65];

    let result = largest(&number_list);
    println!("The largest number is {}", result);

    let char_list = vec!['y', 'm', 'a', 'q'];

    let result = largest(&char_list);
    println!("The largest char is {}", result);
}
```

Listing 10-5: But hold on, folks! We have a small caveat here. As much as we'd
like to jump into the laughter and applause, I have to be honest with you. This
code won't compile just yet. I know, I know, it's disappointing. But fear not,
because we'll fix it later in this chapter. So, sit tight and stay tuned for the
next act!

In the meantime, let's appreciate the beauty of generics. They allow us to write
flexible and reusable code that can handle different types effortlessly. It's
like having a comedian who can make everyone laugh, no matter their taste in
humor. So, let's give it up for generics, the true stars of the show!

Alright, folks, let's address the elephant in the room. If we try to compile the
code from Listing 10-5 right now, we're in for a surprise. And trust me, it's
not the good kind of surprise you want in a comedy show. We'll be greeted with
an error message that goes like this:

```rust

$ cargo run
   Compiling chapter10 v0.1.0 (file:///projects/chapter10)
error[E0369]: binary operation `>` cannot be applied to type `&T`
 --> src/main.rs:5:17
  |
5 |         if item > largest {
  |            ---- ^ ------- &T
  |            |
  |            &T
  |
help: consider restricting type parameter `T`
  |
1 | fn largest<T: std::cmp::PartialOrd>(list: &[T]) -> &T {
  |             ++++++++++++++++++++++

For more information about this error, try `rustc --explain E0369`.
error: could not compile `chapter10` due to previous error
```

Oh boy, it's like a punchline that fell flat. This error is telling us that we
can't use the > operator on the type &T. It's like trying to compare apples to
oranges, or in this case, trying to compare references to some unknown type T.
It just doesn't work.

But don't worry, folks! We have a solution up our sleeves. The helpful
suggestion in the error message tells us to restrict the type parameter T to
only those types that implement the PartialOrd trait. Think of it as making sure
we're comparing things that can actually be compared. And you know what? It's a
great suggestion! By following this advice, we can make this code compile and
keep the laughs rolling.

So, here's the fix: we modify the function signature to include the PartialOrd
trait bound on the type parameter T. It's like telling the compiler, "Hey, we
need a type T that knows how to be ordered, alright?" And just like that, the
code will compile smoothly. The standard library has already implemented the
PartialOrd trait for types like i32 and char, so we're good to go!

Now, let's sit back, relax, and enjoy the show as we witness the power of
generics combined with traits. It's like a comedy duo that knows how to deliver
the punchlines perfectly. Stay tuned, folks!

    In Struct Definitions

Alright, folks, let's move on to structs. We all love structs, right? They're
like the building blocks of our programs, holding data and giving structure to
our code. And you know what's even cooler? We can make our structs even more
flexible and versatile with the power of generics!

In Listing 10-6, we have a struct called Point<T>. This struct is like a little
container that holds x and y coordinate values of any type we want. It's like a
chameleon that can adapt to any data type we throw at it. And we do that by
using the <T> syntax, just like we did with functions.

Filename: src/main.rs

```rust
struct Point<T> {
    x: T,
    y: T,
}

fn main() {
    let integer = Point { x: 5, y: 10 };
    let float = Point { x: 1.0, y: 4.0 };
}
```

Listing 10-6: A Point<T> struct that holds x and y values of type T

So, let's take a look at the code. We define our Point struct with two fields: x
and y, both of type T. And here's the beauty of it: we don't have to specify a
concrete data type for T right away. We can leave it as a wildcard, a
placeholder that will be replaced with the actual type when we create an
instance of the struct.

In the main function, we demonstrate how we can create instances of Point with
different types. We have an integer Point with x as 5 and y as 10, and a float
Point with x as 1.0 and y as 4.0. It's like having a Swiss Army Knife that can
handle any kind of data!

So, with generics, our structs become more adaptable and flexible, ready to
handle different types of data without breaking a sweat. It's like having a
comedian who can tell jokes for any audience, whether they're into numbers or
floating-point values.

Alright, let's talk about this code. We have a struct called Point, and it's got
two fields: x and y. Now, here's the problem: both of these fields have the same
generic type, T. And that means they have to be of the same type!

In the main function, we're trying to create an instance of Point, but look at
that: we're assigning 5 to x, which is an integer, and 4.0 to y, which is a
float. And that, my friends, is a big no-no in Rust. The compiler won't let us
get away with it.

Filename: src/main.rs

```rust
[This code does not compile!] 
struct Point<T> {
    x: T,
    y: T,
}

fn main() {
    let wont_work = Point { x: 5, y: 4.0 };
}
```

Listing 10-7: The fields x and y must be the same type because both have the
same generic data type T.

Rust wants consistency, it wants uniformity. It's like going to a party where
everyone is wearing the same outfit, and you show up in a mismatched ensemble.
You stick out like a sore thumb, and the compiler is not happy about it.

So, remember, when using generics in structs, all fields that use the generic
type must be of the same type. It's like having a rule at the party: everyone
has to wear the same outfit. That way, everyone is on the same page, and the
compiler can sleep peacefully at night.

```rust
$ cargo run
   Compiling chapter10 v0.1.0 (file:///projects/chapter10)
error[E0308]: mismatched types
 --> src/main.rs:7:38
  |
7 |     let wont_work = Point { x: 5, y: 4.0 };
  |                                      ^^^ expected integer, found floating-point number

For more information about this error, try `rustc --explain E0308`.
error: could not compile `chapter10` due to previous error
```

Alright, let's take a look at the code. We have a struct called Point, but this
time, it's a bit different. It's not just generic over one type, oh no. It's
generic over two types: T and U. This means that the x field can be of type T,
and the y field can be of type U. We're getting fancy here, folks.

In the main function, we create three instances of Point. We have both_integer,
where x is 5 and y is 10, both_float, where x and y are both floats (1.0 and
4.0), and integer_and_float, where x is an integer (5) and y is a float (4.0).
And you know what? Rust is perfectly fine with that! It doesn't care if the
types are different for x and y anymore. It's like going to a party where you
can wear whatever you want, mix and match, and have a good time.

Filename: src/main.rs

```rust
struct Point<T, U> {
    x: T,
    y: U,
}

fn main() {
    let both_integer = Point { x: 5, y: 10 };
    let both_float = Point { x: 1.0, y: 4.0 };
    let integer_and_float = Point { x: 5, y: 4.0 };
}
```

Listing 10-8: A Point<T, U> generic over two types so that x and y can be values
of different types

So, by using multiple generic type parameters, we can have more flexibility in
our structs. It's like having a wardrobe full of clothes for every occasion. You
can mix and match, wear different types, and still look good. Just like in Rust,
you can have a Point with different types for x and y, and it's all good.

But remember, don't go overboard with the generics. Using too many can make your
code hard to read and understand. It's like wearing too many accessories at
once. You might think it looks cool, but trust me, it's a mess. So, use generics
wisely, and your code will be stylish and functional.

    Enum Definitions

So, here we have the Option<T> enum, folks. This thing is interesting. It's like
a box that can either hold something or nothing at all. It's a flexible
container that can adapt to different types. Let's take a closer look.

The Option<T> enum is generic over type T. This means that T can be any type we
want. It can be an integer, a string, a custom struct, or even a slice of pizza.
It's up to us to decide.

```rust
enum Option<T> {
    Some(T),
    None,
}
```

Now, the Option<T> enum has two variants. First, we have Some, which holds a
value of type T. It's like saying, "Hey, I got something here!" And then we have
None, which doesn't hold any value at all. It's like saying, "Sorry, nothing to
see here."

By using the Option<T> enum, we can express the concept of an optional value.
It's like saying, "Hey, I might have something for you, or I might not." And
because Option<T> is generic, we can use it with any type we want. It's like
having a container that can hold different things, depending on what we need.

So, the Option<T> enum gives us the power to handle situations where a value may
or may not be present. It's like having a safety net, a backup plan. And in the
world of programming, having options is always a good thing.

So, we've got another example of using generics in enums, folks. This time it's
the Result<T, E> enum. This enum is like a magical box that can hold either a
successful result or an error. Let's break it down.

```rust
enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

The Result<T, E> enum is generic over two types: T and E. T represents the type
of the successful result, while E represents the type of the error. It's like
saying, "Hey, I might give you a successful result of type T, or I might give
you an error of type E."

The Result enum has two variants. First, we have Ok, which holds a value of type
T. It's like saying, "Hey, everything went smoothly, and here's the result you
were looking for." And then we have Err, which holds a value of type E. It's
like saying, "Oops, something went wrong, and here's the error that occurred."

By using the Result<T, E> enum, we can handle operations that may succeed or
fail. It's like having a safety net for our code. We can perform an operation
and check if it was successful or if an error occurred. It's like having a
backup plan in case things don't go as expected.

In fact, we used the Result enum to open a file in a previous chapter. If the
file was opened successfully, we got an Ok variant with a value of type
std::fs::File. But if there were any problems opening the file, we got an Err
variant with a value of type std::io::Error. It's a powerful way to handle
different outcomes and make our code more robust.

So, with the Result<T, E> enum, we can handle success and failure in a
structured and flexible way. It's like having a toolbox filled with options for
dealing with different scenarios. And in the world of programming, having
options is always a good thing.

    In Method Definitions

So, folks, we can also use generics in method definitions! Isn't that great? In
this example, we have a struct called Point<T> with two fields: x and y. And
guess what? We can implement methods on this struct using generics too!

Filename: src/main.rs

```rust
struct Point<T> {
    x: T,
    y: T,
}

impl<T> Point<T> {
    fn x(&self) -> &T {
        &self.x
    }
}

fn main() {
    let p = Point { x: 5, y: 10 };

    println!("p.x = {}", p.x());
}
```

In Listing 10-9, we define a method named x on the Point<T> struct. This method
returns a reference to the data in the x field. So, if we have a Point instance
called p, we can call p.x() to get the value of the x field.

To implement this method, we use the impl keyword, followed by the generic type
parameter T, just like we did with structs. By declaring T after impl, Rust
knows that we're implementing methods on the type Point<T>. And you know what's
cool? We can use the same generic parameter name T as we used in the struct
definition. It's like having a comedian with the same material but performing in
different venues. It's consistent and easy to understand.

So, when we call p.x(), Rust knows to use the implementation of the x method
that matches the specific type T of the Point instance. It's like having a
personalized comedy routine for each type we use with Point. Whether T is an
integer, a float, or any other type, we can get the value of the x field by
calling p.x(). It's like having a versatile comedian who knows how to entertain
any type of audience.

So, with generics in method definitions, our code becomes even more flexible and
reusable. We can write methods that work on different types, adapting to the
specific needs of each instance. It's like having a comedian who can customize
their jokes for every person in the crowd. That's what I call versatility!

Here's something interesting, folks! We can actually put constraints on generic
types when defining methods on a type. Let me explain what that means.

Filename: src/main.rs

```rust
impl Point<f32> {
    fn distance_from_origin(&self) -> f32 {
        (self.x.powi(2) + self.y.powi(2)).sqrt()
    }
}
```

In Listing 10-10, we have an implementation block (impl block) for the
Point<f32> type. This means that the methods defined within this block will only
be available for instances of Point with the generic type parameter T set to
f32. It's like saying, "Hey, these methods are exclusively for Point instances
with floating-point values."

In this particular example, we define a method called distance_from_origin. This
method calculates the distance between a Point instance and the origin (0.0,
0.0) using some mathematical operations. However, these operations are only
available for floating-point types.

So, if we have a Point<f32> instance, we can call the distance_from_origin
method to get the distance from the origin. But if we have a Point with any
other generic type, we won't have this method available. It's like having a
special set of jokes that only work with a certain type of audience.

With this feature, we can tailor our methods to work with specific types, making
our code more precise and efficient. It's like having a comedian who knows which
jokes are perfect for a particular crowd. They know exactly what will make the
audience laugh and deliver an exceptional performance.

So, by adding constraints on generic types in method definitions, we ensure that
our methods are applied only to the appropriate instances, giving us more
control over the behavior and capabilities of our code. It's like having a
comedian who knows exactly what jokes to tell to create the best comedy
experience.

Okay, folks, let's take a look at this code. In Listing 10-11, we have a struct
called Point that uses two generic type parameters: X1 and Y1. These parameters
represent the types of the x and y coordinates of a point.

Inside the implementation block for Point<X1, Y1>, we define a method called
mixup. But wait, there's a twist! The method itself introduces two new generic
type parameters: X2 and Y2. These new parameters are independent of the ones
used in the struct definition.

Filename: src/main.rs

```rust
struct Point<X1, Y1> {
    x: X1,
    y: Y1,
}

impl<X1, Y1> Point<X1, Y1> {
    fn mixup<X2, Y2>(self, other: Point<X2, Y2>) -> Point<X1, Y2> {
        Point {
            x: self.x,
            y: other.y,
        }
    }
}

fn main() {
    let p1 = Point { x: 5, y: 10.4 };
    let p2 = Point { x: "Hello", y: 'c' };

    let p3 = p1.mixup(p2);

    println!("p3.x = {}, p3.y = {}", p3.x, p3.y);
}
```

Listing 10-11: A method that uses generic types different from its struct’s
definition

So what does this method do? Well, it takes in another Point, called other, with
coordinates of type X2 and Y2. Then, it creates a new Point instance, p3, with
the x value from the self Point (of type X1) and the y value from the passed-in
Point (of type Y2). It's like mixing and matching coordinates from different
points to create a brand new point.

In the main function, we create two Point instances, p1 and p2, with different
types for their coordinates. We then call the mixup method on p1, passing in p2
as the argument. This creates a new Point instance, p3, with an x value of type
X1 (from p1) and a y value of type Y2 (from p2).

Finally, we use the println! macro to print the values of p3.x and p3.y. In this
case, p3.x will be 5 (from p1) and p3.y will be 'c' (from p2).

This example shows that the generic type parameters used in a struct definition
can be different from the ones used in a method's signature. It gives us the
flexibility to mix and match different types when working with generic
structures. It's like combining the humor styles of different comedians to
create a unique comedic experience.

So, by using generic types in both struct definitions and method signatures, we
can build versatile and customizable code that can handle various types and
combinations. It's like having a comedian who can adapt their jokes to different
audiences and create comedy gold every time.

    Performance of Code Using Generics

Alright, let's talk about performance. You might be wondering if using generic
types comes with a performance cost. Well, the good news is that it doesn't!
Using generics won't slow down your program at runtime compared to using
concrete types.

You see, Rust is a smart cookie. It uses a fancy technique called
monomorphization to optimize the code using generics during compilation.
Monomorphization is like a magician transforming a generic trick into a specific
trick tailored to the situation. It takes the generic code and generates
specialized code for the concrete types that are actually used in the program.

Let's take a look at an example using the Option<T> enum from the standard
library. We create two Option instances: one with an integer value and one with
a floating-point value.

When Rust compiles this code, it goes through the process of monomorphization.
It looks at the values that have been used in the Option<T> instances and
identifies that we have two types: i32 and f64. So, the compiler generates two
specialized versions of the Option<T> code: one for i32 and one for f64. It
replaces the generic definition with these specific versions.

Let’s look at how this works by using the standard library’s generic Option<T>
enum:

```rust
let integer = Some(5);
let float = Some(5.0);
```

This means that when you run your program, there won't be any overhead from
using generics. It's like having a magician who customizes their tricks on the
spot based on the specific objects they're working with. It's efficient and
performs just as well as if you had written the code with concrete types from
the start.

So, don't worry about performance when using generics in Rust. The compiler has
got your back and will optimize your code to run smoothly and efficiently, like
a well-rehearsed comedy routine.

Alright, let's take a look at the monomorphized version of the code. Brace
yourselves, it's going to get technical!

The code that goes through the process of monomorphization looks something like
this (note that the compiler uses different names):

Filename: src/main.rs

```rust
enum Option_i32 {
    Some(i32),
    None,
}

enum Option_f64 {
    Some(f64),
    None,
}

fn main() {
    let integer = Option_i32::Some(5);
    let float = Option_f64::Some(5.0);
}
```

Alright, let's take a look at the monomorphized version of the code. Brace
yourselves, it's going to get technical!

The code that goes through the process of monomorphization looks something like
this (note that the compiler uses different names):

We have two new enums: Option_i32 and Option_f64. Option_i32 has two variants,
Some with an i32 value and None. Option_f64 has the same variants, but with an
f64 value instead.

In the main function, we create instances of these specialized enums: integer of
type Option_i32 with a value of 5, and float of type Option_f64 with a value of
5.0.

What's important to understand here is that the generic Option<T> code is
replaced by the specific definitions generated by the compiler. It's like the
code was custom-made for the types we're using.

The beauty of this process is that there's no runtime cost for using generics in
Rust. The monomorphization ensures that the code performs just as efficiently as
if we had manually written separate definitions for each type. It's like having
a personalized comedy routine for every type you use.

So, rest assured that using generics in Rust won't slow down your program. The
magic of monomorphization makes generics extremely efficient at runtime.
