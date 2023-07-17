    Generic Types, Traits, and Lifetimes

Alright, my friends, let's dive into the wonderful world of generics, traits,
and lifetimes in Rust. These are the tools that help us tackle code duplication
and make our programs more flexible and powerful.

Generics are like placeholders for types. They allow us to write code that can
work with different types without knowing the specific type in advance. It's
like having a magic box that can handle any kind of data you throw at it. We've
already seen generics in action with Option<T>, Vec<T>, and Result<T, E>.
They're the superheroes of code reusability!

Now, let's talk about reducing code duplication. We all hate repeating
ourselves, right? So, we extract common code into functions. It's like creating
a recipe that can be used with different ingredients. But what if we have two
functions that are almost the same, except for the types of their parameters?
Well, my friends, we can use generics to create a single function that can
handle both cases. It's like having a Swiss Army knife that adapts to any
situation.

But generics alone are not enough. We need a way to define behavior in a generic
way. That's where traits come in. Traits allow us to specify certain behaviors
that a type must have. It's like having a set of rules that a type must follow
to be considered part of a specific club. By combining traits with generic
types, we can constrain our code to accept only types that have the desired
behavior. It's like having a bouncer at the door, ensuring that only the right
types get in.

Last but not least, let's talk about lifetimes. Lifetimes help the compiler
understand how references relate to each other. They allow us to provide enough
information to ensure that our references will be valid in various situations.
It's like giving the compiler a map so it knows where references can safely go
without getting lost.

So, my friends, let's embrace the power of generics, traits, and lifetimes. They
are the tools that make our code more flexible, reusable, and reliable. With
generics, we can handle any type of data. With traits, we can define behavior in
a generic way. And with lifetimes, we can guide the compiler and ensure the
safety of our references.

    Removing Duplication by Extracting a Function

Alright, folks, let's take a look at a program that finds the largest number in
a list. We have a bunch of numbers in a vector called number_list. We start by
assuming that the first number in the list is the largest, and we store a
reference to it in a variable called largest. Then, we go through each number in
the list, and if we find a number that's greater than the current largest, we
update largest to point to that number. It's like a little competition between
the numbers to see who's the biggest!

We begin with the short program in Listing 10-1 that finds the largest number in
a list.

Filename: src/main.rs

```rust
fn main() {
    let number_list = vec![34, 50, 25, 100, 65];

    let mut largest = &number_list[0];

    for number in &number_list {
        if number > largest {
            largest = number;
        }
    }

    println!("The largest number is {}", largest);
}
```

Listing 10-1: Finding the largest number in a list of numbers

Now, let's talk about code duplication. We have a similar pattern of finding the
largest number in different scenarios. What if we want to find the largest
number in a list of floats? Or in a list of strings? We don't want to repeat the
same code over and over again, do we? So, how can we solve this problem without
generics? Well, we can extract the finding-the-largest-number logic into a
separate function that takes a list as a parameter. This way, we can reuse this
function with different types of lists.

But wait! We can go even further and make this function generic! Instead of
having separate functions for different types, we can have a single function
that works with any type. It's like having a magical function that can find the
largest element in any kind of list you throw at it.

So, my friends, by recognizing code duplication and extracting it into a
function, we can eliminate repetitive code and make our programs more efficient.
And with the power of generics, we can create flexible functions that work with
various types. It's like a beautiful dance between code reusability and
flexibility. Now, let's dive into the syntax of generics and see how we can
unleash their full potential!

Alright, let's take a look at this new code. We have two lists of numbers, and
we want to find the largest number in each of them. But wait a minute, what's
going on here? We have the same code repeated twice! It's like deja vu all over
again.

Duplicating code is a pain in the neck. It's like copying your neighbor's
homework and pretending it's your own. It's tedious, error-prone, and worst of
all, it requires you to remember to update the code in multiple places if you
want to make a change. Who's got time for that?

Filename: src/main.rs

```rust
fn main() {
    let number_list = vec![34, 50, 25, 100, 65];

    let mut largest = &number_list[0];

    for number in &number_list {
        if number > largest {
            largest = number;
        }
    }

    println!("The largest number is {}", largest);

    let number_list = vec![102, 34, 6000, 89, 54, 2, 43, 8];

    let mut largest = &number_list[0];

    for number in &number_list {
        if number > largest {
            largest = number;
        }
    }

    println!("The largest number is {}", largest);
}
```

Listing 10-2: Code to find the largest number in two lists of numbers

But fear not, my friends! We can put an end to this madness by creating an
abstraction. We'll define a function that can operate on any list of integers
passed in as a parameter. This way, we can write the code once and use it to
find the largest number in any list we want. It's like having a reusable code
module that can do the heavy lifting for us.

By abstracting the code into a function, we make our code clearer and more
expressive. We can now talk about finding the largest number in a list in a more
abstract way, without worrying about the nitty-gritty details of the
implementation. It's like talking about pizza delivery without having to explain
how the dough is made or how the cheese is melted. We can focus on the
high-level concept and let the function handle the rest.

Alright, my friends, let's take a look at this new code. We've extracted the
code that finds the largest number into a function called largest. This function
is a game-changer, let me tell you. It takes a parameter called list, which is a
slice of i32 values. And guess what? This function can handle any list of i32
values we throw at it. It's like a Swiss Army knife of number finding!

Filename: src/main.rs

```rust
fn largest(list: &[i32]) -> &i32 {
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

    let number_list = vec![102, 34, 6000, 89, 54, 2, 43, 8];

    let result = largest(&number_list);
    println!("The largest number is {}", result);
}
```

Listing 10-3: Abstracted code to find the largest number in two lists

Inside the largest function, we have some familiar code. We start by
initializing a variable called largest with the first element of the list. Then,
we iterate through the rest of the list, comparing each element with largest and
updating it if we find a larger number. It's like a game of "Who's the biggest
number?" and we keep track of the reigning champion.

Once we've gone through the entire list, we return largest as the result. It's
like the grand finale of a fireworks show, where the biggest explosion takes
center stage. And with this function, we can find the largest number in any list
we want, without duplicating code or breaking a sweat.

Now let's put this function to the test, shall we? In our main function, we
create two lists of numbers, just like before. But this time, instead of
repeating the code, we simply call our trusty largest function and pass in the
lists as arguments. The function does its magic and returns the largest number,
which we then print out for all the world to see.

Alright, folks, let's recap the steps we took to improve our code from Listing
10-2 to Listing 10-3. It's all about eliminating duplication and making our code
more efficient, just like getting rid of those annoying duplicate jokes in a
comedy routine.

Step one: Identify the duplicate code. We saw that we had the same code to find
the largest number in two different lists. That's like telling the same joke
twice, and nobody wants that.

Step two: Extract that duplicate code into a function. We created a function
called largest that takes a slice of values and finds the largest one. It's like
having a go-to joke that never fails to get laughs.

Step three: Update the code to call the function instead of duplicating it. We
replaced the duplicated code in our main function with calls to the largest
function. It's like having a punchline ready to go whenever we need it.

Now, my friends, let's apply these steps to a new challenge: dealing with two
functions that find the largest item in different types of slices. We could have
one function for i32 values and another function for char values, but that's
like telling the same joke in two different languages. It's a lot of unnecessary
work.

Instead, we'll use generics to make our code more flexible. Just like a comedian
who can adapt their jokes to any audience, generics allow us to write code that
can operate on abstract types. We can create a single function that finds the
largest item in any type of slice. It's like having a universal joke that always
gets a laugh, no matter who's listening.
