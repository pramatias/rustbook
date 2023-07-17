Storing Lists of Values with Vectors

Alright, let's talk about vectors, people! Vectors are like the Swiss Army
knives of collections. They let you store multiple values of the same type in
one handy data structure. It's like having a whole bunch of items lined up next
to each other in your memory. Pretty neat, huh?

    Creating a New Vector

Now, to create a fresh new vector, we use the Vec::new function. Check out
Listing 8-1. See that code? We're creating an empty vector here that's gonna
hold values of type i32. But here's the thing: since we haven't put any values
in yet, Rust doesn't know what type of elements we're gonna store. So, we gotta
give it a little nudge with a type annotation. We're saying, "Hey, Rust, this
vector called 'v' is gonna hold some i32s, alright?"

```rust
fn main() {
    let v: Vec<i32> = Vec::new();
}
```
Listing 8-1: Creating a new, empty vector to hold values of type i32

Now, here's a little fun fact for you: vectors are pretty flexible. They're
implemented using generics, which means they can hold any type you throw at 'em.
Talk about versatility! But when we want our vector to hold a specific type, we
gotta let Rust know about it using those fancy angle brackets. In our case,
we're telling Rust that 'v' is gonna be a Vec<i32>.

So, go ahead and create your vectors, fill 'em up with all sorts of values, and
let Rust handle the rest. Vectors are your trusty companions when it comes to
storing lists of items, whether it's lines of text in a file or prices of
goodies in a shopping cart. They've got your back!

Alright, folks, let me tell you about a little shortcut that Rust has for
creating vectors with some initial values. It's called the vec! macro, and it's
like a magic wand for vectors. Check out Listing 8-2, it's gonna blow your mind!

With the vec! macro, you can create a brand new Vec<T> and fill it up with the
values you want. In this example, we've got a vector called 'v' that holds the
numbers 1, 2, and 3. And here's the best part: you don't even need to tell Rust
the type of the values! It's like Rust has psychic powers and can figure it out
on its own. In this case, since we're dealing with integers, Rust knows that 'v'
is gonna be a Vec<i32>. Pretty cool, huh?

```rust
let v = vec![1, 2, 3];
```

Listing 8-2: Creating a new vector containing values

Now, here's the thing: you'll be using the vec! macro quite often because it's
so darn convenient. Rust can infer the type of the vector based on the values
you give it, so you rarely need to do any type annotations. It's like magic!

    Updating a Vector

You know what's great about vectors? You can add stuff to them! It's like
getting a present and then getting more presents on top of it. Let me show you
how it's done in Listing 8-3.

First, we create an empty vector called 'v' using the Vec::new() function. Then,
we start pushing numbers into it like there's no tomorrow. We push 5, then 6,
then 7, and finally 8. It's like a never-ending stream of numbers flowing into
our vector.

```rust
    let mut v = Vec::new();

    v.push(5);
    v.push(6);
    v.push(7);
    v.push(8);
```

Listing 8-3: Using the push method to add values to a vector

But here's the catch: if you want to modify a variable, you gotta make it
mutable. So we use the 'mut' keyword to make 'v' mutable. That way, we can keep
adding more and more numbers to it.

Now, you might be wondering, how does Rust know the type of these numbers? Well,
Rust is pretty smart, my friends. It can figure out the type based on the data
you give it. So in this case, it knows that we're dealing with integers,
specifically i32. That's why we don't need to annotate 'v' with Vec<i32>. Rust's
got it covered.

    Reading Elements of Vectors

Alright, let's talk about how to read elements from a vector. It's like going on
a treasure hunt, searching for that one special value hidden in the depths of
the vector.

In Listing 8-4, we start off with a vector called 'v' that holds the values 1,
2, 3, 4, and 5. Now, let's say we're interested in the third element of this
vector. We can use indexing syntax to get it by specifying the index value
within square brackets. In this case, the third element is at index 2 (remember,
indexing starts from zero), so we write &v[2]. The '&' here means we're getting
a reference to the element, not the element itself. We then print it out and
admire its beauty.

```rust
    let v = vec![1, 2, 3, 4, 5];

    let third: &i32 = &v[2];
    println!("The third element is {third}");

    let third: Option<&i32> = v.get(2);
    match third {
        Some(third) => println!("The third element is {third}"),
        None => println!("There is no third element."),
    }
```
Listing 8-4: Using indexing syntax or the get method to access an item in a
vector

But wait, there's more! We can also use the get method to retrieve an element
from the vector. We pass the index as an argument to the get method, like
v.get(2). But here's the cool part: the get method returns an Option<&T>. This
means it might give us the element if it exists, or it might give us None if the
index is out of bounds. To handle this possibility, we use a match expression.
If we get Some(third), we print out the element. If we get None, we print out a
message saying there is no third element. It's like a game of chance, hoping we
hit the jackpot and get a valid element.

The reason Rust provides these two ways to reference an element is so you can
choose how the program behaves when you try to use an index value outside the
range of existing elements. As an example, let’s see what happens when we have a
vector of five elements and then we try to access an element at index 100 with
each technique, as shown in Listing 8-5.

```rust
    let v = vec![1, 2, 3, 4, 5];

    let does_not_exist = &v[100];
    let does_not_exist = v.get(100);
```

Listing 8-5: Attempting to access the element at index 100 in a vector
containing five elements

First, we use the indexing syntax, like &v[100]. Brace yourself, because this is
where the action happens. When we run this code, it panics! It's like stepping
on a landmine, causing your program to explode into oblivion. The indexing
method is great when you want to live on the edge and crash your program with a
bang if you go beyond the vector's boundaries.

But hey, we're not done yet. We're a little more cautious now, so we decide to
use the get method instead, with v.get(100). This method is like a safety net,
catching you when you fall. When the index is out of bounds, it returns None
without causing a panic. It's a civilized way of handling the situation, giving
you the chance to gracefully deal with the absence of the desired element. It's
like a safety cushion that prevents your program from crashing and burning.

So there you have it. Depending on your preference and the requirements of your
program, you can choose between the thrill of indexing and the safety of the get
method. It's like playing with fire or taking the cautious route. Just remember,
crashing your program might be exhilarating, but sometimes it's better to handle
unexpected situations gracefully and give your users a chance to recover from
their mistakes.

Alright, folks, let's talk about a little conundrum we've got here. In Listing
8-6, we have a vector 'v' that holds the numbers 1, 2, 3, 4, and 5. Now, we
decide to be sneaky and create an immutable reference called 'first' that points
to the first element of the vector, which is 1. So far, so good.

But here comes the tricky part. We get greedy and try to add an element, 6, to
the end of the vector using 'v.push(6)'. Now, you might think this is harmless,
right? I mean, what does adding an element have to do with the reference we
created earlier?

Well, my friends, that's where the borrowing rules of Rust come into play. You
see, when we add an element to a vector, it may require allocating new memory
and copying the old elements if there isn't enough space to fit everything in
the current memory location. In that case, the reference we created to the first
element would be pointing to deallocated memory. And that's a big no-no.

 [This code does not compile!] 

```rust
    let mut v = vec![1, 2, 3, 4, 5];

    let first = &v[0];

    v.push(6);

    println!("The first element is: {first}");
```

Listing 8-6: Attempting to add an element to a vector while holding a reference
to an item

So when we try to compile this code, the Rust compiler says, "Hold on a minute!
You can't have your cake and eat it too. You're borrowing the vector as
immutable with 'first', and now you're trying to mutate it by adding an element.
That's a violation of the borrowing rules, my friend!"


```rust
$ cargo run
   Compiling collections v0.1.0 (file:///projects/collections)
error[E0502]: cannot borrow `v` as mutable because it is also borrowed as immutable
 --> src/main.rs:6:5
  |
4 |     let first = &v[0];
  |                  - immutable borrow occurs here
5 |
6 |     v.push(6);
  |     ^^^^^^^^^ mutable borrow occurs here
7 |
8 |     println!("The first element is: {first}");
  |                                      ----- immutable borrow later used here
```

For more information about this error, try `rustc --explain E0502`.
error: could not compile `collections` due to previous error

And that's why we get an error that tells us we cannot borrow 'v' as mutable
because it is also borrowed as immutable. The borrowing rules exist to protect
us from potential memory issues and ensure that references remain valid.

So, be mindful of the borrowing rules, my fellow Rustaceans. They may seem
strict at times, but they're there to save us from the perils of dangling
pointers and other memory mishaps. Trust me, it's better to have a compiler
yelling at you than dealing with subtle bugs that can drive you insane.

Note: For more on the implementation details of the Vec<T> type, see “The
Rustonomicon”.

    Iterating over the Values in a Vector

So, folks, let's talk about iterating over the values in a vector. You know,
sometimes you just want to go through each element and do something with it,
right? Well, in Rust, we've got a handy way to do that using a for loop.


```rust
    let v = vec![100, 32, 57];
    for i in &v {
        println!("{i}");
    }
```

In Listing 8-7, we've got a vector called 'v' that holds the values 100, 32,
and 57. Now, if we want to access each of these values, we can use a for loop.
We iterate over the vector using the '&v' syntax, which gives us immutable
references to each element. Inside the loop, we simply print each element using
println!(). Easy peasy!


```rust
    let mut v = vec![100, 32, 57];
    for i in &mut v {
        *i += 50;
    }
```

Listing 8-8: Iterating over mutable references to elements in a vector

But wait, there's more! In Listing 8-8, we've got a twist. We're dealing with a
mutable vector this time, called 'v', which holds the values 100, 32, and 57.
Now, what if we want to make changes to each element? Well, fear not, my
friends! We can still use a for loop, but this time we'll iterate over mutable
references to each element using the '&mut v' syntax.

Inside the loop, we can perform any modifications we want. In this case, we're
adding 50 to each element by using the 'i += 50' syntax. Oh, and by the way,
that '' is the dereference operator. It helps us access the value inside the
mutable reference before we can make any changes. We'll dive deeper into the
dereference operator in Chapter 15, so stay tuned for that.

Now, here's the important part. Iterating over a vector, whether immutably or
mutably, is safe in Rust. The borrow checker makes sure of that. If we tried to
insert or remove items while iterating, we would get a nice little compiler
error reminding us that we can't modify the vector while we're holding
references to its elements. It's all about keeping things under control and
avoiding those nasty bugs.

So go ahead and iterate away, my fellow Rustaceans! Access those elements, make
your modifications, and rest assured that the borrow checker has got your back.

    Using an Enum to Store Multiple Types

Alright, let's talk about storing multiple types in one vector. Now, vectors in
Rust are pretty strict when it comes to types. They can only store values of the
same type, which can be a bit of a hassle sometimes. But fear not, my friends!
Rust has a solution for us, and it involves our good ol' friend, the enum.

In Listing 8-9, we've got an enum called SpreadsheetCell. This enum has three
different variants: Int, Float, and Text. Each variant can hold a different type
of value. So, we can have integers, floating-point numbers, and strings all
under the same enum type.

Now, here comes the cool part. We can create a vector that holds values of this
enum type, which means we can store different types in one vector! In this
example, we've created a vector called row that holds different SpreadsheetCell
values. We've got an Int variant with the value 3, a Text variant with the
string "blue", and a Float variant with the value 10.12. All happily coexisting
in one vector!

```rust
    enum SpreadsheetCell {
        Int(i32),
        Float(f64),
        Text(String),
    }

    let row = vec![
        SpreadsheetCell::Int(3),
        SpreadsheetCell::Text(String::from("blue")),
        SpreadsheetCell::Float(10.12),
    ];
```

Listing 8-9: Defining an enum to store values of different types in one vector

By using this enum approach, we can conveniently store different types in one
vector without having to jump through hoops. It's a powerful tool when you need
to handle collections of different types of data.

You know, Rust is quite particular about its types. It needs to know what types
will be in a vector at compile time so it can allocate the right amount of
memory on the heap for each element. And not only that, Rust wants us to be
explicit about what types are allowed in the vector. It's like Rust saying,
"Hey, I need to know what I'm dealing with here!"

So, to handle situations where we want to store different types in one vector,
Rust gives us the enum. But it's not just any enum, it's a superhero enum! By
defining an enum with different variants that can hold different types, we can
create a vector that can store these different types. It's like having a
versatile container that can hold anything we throw at it.

Now, the reason Rust makes us be explicit about the types allowed in the vector
is because it wants to prevent any potential errors. Imagine if Rust allowed any
type in the vector and then we tried to perform operations on those elements
that didn't make sense for some types. Chaos would ensue! But fear not, my
friends, Rust has our back. By using the enum approach and a match expression,
Rust ensures that every possible case is handled, all at compile time. It's like
having a personal assistant that double-checks everything for you.

But hold on, there's a catch. If we don't know all the possible types that our
program will encounter at runtime, the enum technique won't work. In that case,
we can turn to trait objects, which we'll explore in Chapter 17. They're like
the shape-shifters of Rust, able to handle any type that implements a certain
trait.

So, as you dive deeper into the world of vectors, don't forget to check out the
API documentation for Vec<T>. It's a treasure trove of useful methods that can
make your life easier. And remember, if push is your friend, pop is the buddy
that removes and returns the last element. It's all about balance, my friends.

    Dropping a Vector Drops Its Elements

You know, when it comes to structs, vectors are no exception. Just like any
other struct, when a vector goes out of scope, it's freed. It's like saying,
"Hey vector, you've done your job, now it's time to go."

```rust
    {
        let v = vec![1, 2, 3, 4];

        // do stuff with v
    } // <- v goes out of scope and is freed here
```

Listing 8-10: Showing where the vector and its elements are dropped

But here's the cool part. When a vector is dropped, all of its elements get
dropped too. It's like a domino effect of cleaning up. So those integers that
were snugly stored in the vector? They get cleaned up too. It's like a little
tidy-up party happening behind the scenes.

And of course, the borrow checker is there to keep things in check. It makes
sure that any references to the contents of a vector are only used while the
vector is still valid. It's like having a responsible friend who keeps an eye on
things and says, "Hey, don't use that reference once the vector is gone,
alright?"

So remember, when a vector goes out of scope, it's like a little farewell
moment. It gracefully exits the stage, taking care of its elements along the
way. And now that we've covered vectors, it's time to dive into the world of
strings.
