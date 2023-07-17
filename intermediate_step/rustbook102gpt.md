    Traits: Defining Shared Behavior

Traits, my friends, are all about defining shared behavior. It's like setting a
standard, a set of rules that types can follow to be part of a cool club. And
let me tell you, it's a fancy club where members can do cool things together.

So, what exactly is a trait? Well, it's a way to define functionality that a
type can have and share with other types. It's like saying, "Hey, if you want to
be in this club, you gotta be able to do these things."

In Rust, we can use traits to define shared behavior in an abstract way. It's
like having a blueprint for how things should behave, without worrying about
their specific types. We can use trait bounds to say, "Hey, any type that has
this behavior can be part of the gang."

Now, let's be clear, traits are not exactly the same as interfaces in other
languages. They have their own Rust flavor. But hey, it's like comparing apples
and oranges. Both are fruits, but they have their own unique taste.

Traits give us the power to define common behavior and create generic types that
can work with any type that follows those rules. It's like having a set of
skills that can be shared among different types. It's a beautiful way to promote
code reuse and ensure that types can play nicely together.

    Defining a Trait

So, imagine you have different types that can hold text, like a news article or
a tweet. They may have different structures and details, but they share
something in common: the ability to provide a summary.

Now, let's say you're building a media aggregator library called "aggregator."
You want this library to be able to display summaries of the data stored in
these types. But how can you make sure that each type provides a summary in a
consistent way?

That's where traits come in! In Rust, we can define a trait called Summary that
represents the behavior of having a summarize method. It's like saying, "Hey, if
you want to be part of the summary club, you gotta have a summarize method."

In Listing 10-12, we define a public trait called Summary. This trait has a
single method called summarize, which takes a reference to self and returns a
String. This method will be implemented differently for each type that wants to
be part of the Summary club. But no matter how they implement it, they will all
provide a summary when asked.

By defining this trait, we're creating a common language that these types can
speak. They may have different structures and details, but they all share the
ability to summarize themselves. It's like having a group of friends who can all
tell you about their day in their own unique way.

So, with the Summary trait, we ensure that any type that wants to be part of our
media aggregator library must provide a way to summarize itself. It's a powerful
way to enforce behavior and create more flexible and reusable code.

Filename: src/lib.rs

```rust
pub trait Summary {
    fn summarize(&self) -> String;
}
```

So, here's what's going on in Listing 10-12. We've got ourselves a trait called
Summary, and we declare it using the keyword "trait." We want this trait to be
accessible to other crates as well, so we make it "pub."

Inside the curly braces, we define the behavior that types implementing this
trait should have. And in this case, we're talking about the summarize method.
It's like saying, "Hey, if you want to be part of the Summary club, you gotta
have a method called summarize!"

The method signature is pretty straightforward: it takes a reference to self
(which means it's a method we call on an instance of the type) and it returns a
String. But here's the twist: we don't provide an actual implementation for this
method. Instead, we just put a semicolon after the method signature.

Why the heck would we do that? Well, my friend, it's because each type that
implements this trait will provide its own custom implementation for this
method. The compiler will make sure that any type claiming to be a part of the
Summary club will have the summarize method defined exactly like this.

And you know what's cool? This trait can have multiple methods in its body. It's
like having a club with different activities, and all the members need to
participate in each activity. Each line in the trait body represents a method
signature, and they all end with semicolons.

So, that's the Summary trait for you! It's a way to define shared behavior among
different types, making sure they all have the same method with the same
signature. It's like setting the ground rules for a party and saying, "Hey, if
you want to join, you gotta bring your own dance moves!"

    Implementing a Trait on a Type

So, in Listing 10-13, we're implementing the Summary trait on our NewsArticle
and Tweet types. It's like saying, "Hey, NewsArticle and Tweet, you guys are now
official members of the Summary club!"

To do this, we use the "impl" keyword, followed by the name of the trait we want
to implement, which in this case is Summary. Then we use the "for" keyword, and
specify the name of the type we're implementing the trait for.

Filename: src/lib.rs

```rust
pub struct NewsArticle {
    pub headline: String,
    pub location: String,
    pub author: String,
    pub content: String,
}

impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{}, by {} ({})", self.headline, self.author, self.location)
    }
}

pub struct Tweet {
    pub username: String,
    pub content: String,
    pub reply: bool,
    pub retweet: bool,
}

impl Summary for Tweet {
    fn summarize(&self) -> String {
        format!("{}: {}", self.username, self.content)
    }
}
```

Listing 10-13: Implementing the Summary trait on the NewsArticle and Tweet types

Inside the curly braces, we define the method(s) that the trait requires us to
implement. And in this case, it's just the summarize method. So for the
NewsArticle, we implement summarize by formatting the headline, author, and
location into a nice summary string. And for the Tweet, we format the username
and the content into the summary string.

We use the format! macro to create the summary strings. It's like using a
template where we can fill in the variables with the actual values from our
NewsArticle or Tweet instances.

Now, when we have a NewsArticle or a Tweet instance, we can call the summarize
method on them because they've implemented the Summary trait. It's like having a
shared behavior that we can rely on across different types.

And that's how we implement traits on types in Rust! It's like giving our types
some extra capabilities and saying, "Hey, now you guys can do this cool thing!"

So, let's take a look at how we can use the Summary trait in our binary crate,
which depends on the aggregator library crate.

```rust
use aggregator::{Summary, Tweet};

fn main() {
    let tweet = Tweet {
        username: String::from("horse_ebooks"),
        content: String::from(
            "of course, as you probably already know, people",
        ),
        reply: false,
        retweet: false,
    };

    println!("1 new tweet: {}", tweet.summarize());
}
```

First, we bring the Summary trait into scope using the "use" keyword. This
allows us to use the trait methods without fully qualifying them with the crate
name. In this case, we also bring the Tweet type into scope from the aggregator
crate.

In our main function, we create a new Tweet instance with a username and some
content. Then, we call the summarize method on the tweet and print the result.
It's like saying, "Hey Tweet, summarize yourself!"

The code will output: "1 new tweet: horse_ebooks: of course, as you probably
already know, people."

This shows how the Summary trait allows us to define a shared behavior that can
be used across different types. It doesn't matter if the types are defined in
different crates, as long as the trait is brought into scope, we can call its
methods on instances of those types.

It's like having a language that allows different dialects to understand each
other as long as they speak the same language. In this case, the Summary trait
is the language that allows different types to communicate through the summarize
method.

And remember, we can also implement traits on our own types within the
aggregator crate.

You know, there's a rule in Rust called the orphan rule, and it's there to
prevent some crazy chaos from happening. You see, we can't just go around
implementing traits on any type we want, especially if those types are defined
outside of our crate. That would be like crashing someone else's party and
making all the decisions.

For example, let's say we want to implement the Display trait on the Vec<T> type
in our aggregator crate. That would be pretty convenient, right? But here's the
thing: the Display trait and the Vec<T> type are both defined in the standard
library, not in our crate. So, it's like trying to paint someone else's house
without their permission. It's just not allowed.

This restriction is called the orphan rule, and it's all about maintaining order
and preventing conflicts. Imagine if two crates implemented the same trait for
the same type. It would be like two comedians telling the same joke at the same
time. The audience would be confused, and chaos would ensue.

So, the orphan rule ensures that we can't mess with other people's code, and
they can't mess with ours. It keeps the peace and ensures that our code is
reliable and predictable. It's like having rules at a comedy show to ensure that
each comedian gets their own time on stage.

    Default Implementations

Alright, my friends, let's talk about default behavior in traits. Sometimes, we
don't want to force every type to implement every method in a trait. That would
be a bit too demanding, wouldn't it? Instead, we can have default behavior for
some or all of the methods in a trait, and let the types decide whether to keep
or override that behavior.

Check out this code snippet, listed as 10-14. We're defining a trait called
Summary, and this time, we're not just providing the method signature. Oh no,
we're going a step further. We're giving it a default implementation for the
summarize method. How cool is that?

Filename: src/lib.rs

```rust
pub trait Summary {
    fn summarize(&self) -> String {
        String::from("(Read more...)")
    }
}
```

Listing 10-14: A Summary trait with a default implementation for the summarize
method

In this case, the default implementation says that if you don't provide your own
fancy summary, we'll give you a generic "(Read more...)" string. It's like
having a fallback option, just in case you're feeling a bit lazy.

Now, let's see how we can use this default behavior with our NewsArticle type.
To make use of the default implementation for summarizing NewsArticle instances,
we simply need to provide an empty impl block with impl Summary for NewsArticle
{}. It's like saying, "Hey, NewsArticle, you have the option to use the default
summarize method or do your own thing."

So, my friends, with default implementations in traits, we have the power of
choice. We can provide sensible defaults for methods, saving us from repeating
code everywhere. And if a type wants to spice things up and have its own
implementation, it's free to do so.

Keep exploring, keep customizing, and keep embracing the flexibility that traits
bring to your Rust programs. It's like having a box of chocolates, with default
behaviors as the trusty classics and custom implementations as the daring new
flavors.

Now, let's see how this default behavior works in action. Even though we didn't
define the summarize method directly on our NewsArticle type, we're still able
to call it thanks to the default implementation we provided in the Summary
trait. Isn't that neat?

Check out this code snippet. We have an instance of NewsArticle called article,
with all its juicy details:

```rust

    let article = NewsArticle {
        headline: String::from("Penguins win the Stanley Cup Championship!"),
        location: String::from("Pittsburgh, PA, USA"),
        author: String::from("Iceburgh"),
        content: String::from(
            "The Pittsburgh Penguins once again are the best \
             hockey team in the NHL.",
        ),
    };

    println!("New article available! {}", article.summarize());

```

This code prints New article available! (Read more...).

And what do we get? The result is "New article available! (Read more...)". We're
using the default implementation of the summarize method here, just like we
defined it in the Summary trait. It's like a safety net, catching us when we
forget to provide our own implementation.

Now, here's the cool part: creating a default implementation doesn't require us
to change anything about our Tweet type in Listing 10-13. The syntax for
overriding a default implementation is the same as implementing a trait method
from scratch. It's all about options, my friends. You can keep the default
behavior, or you can go wild and unleash your own creativity.

So, let's embrace the power of default implementations. They save us time, keep
our code DRY (Don't Repeat Yourself), and allow us to have consistent behavior
across types that implement the same trait.

Here's a fun twist, my fellow Rustaceans. Default implementations can call other
methods in the same trait, even if those other methods don't have their own
default implementations. Talk about teamwork!

Imagine we have the Summary trait once again, but this time we're adding a
little extra flavor. We now have a summarize_author method that implementors
must define, and a summarize method that has a default implementation which
calls the summarize_author method.

Check out the code snippet:

```rust
pub trait Summary {
    fn summarize_author(&self) -> String;

    fn summarize(&self) -> String {
        format!("(Read more from {}...)", self.summarize_author())
    }
}
```

Now, when we implement the Summary trait on our Tweet type, we only need to
define the summarize_author method:

Isn't that cool? The summarize method now takes advantage of the
summarize_author method to provide a complete summary. It's like a dynamic duo,
working together to give us the best of both worlds. We get the flexibility of
implementing our own summarize_author method, while still having the convenience
of a default implementation for summarize.

```rust
impl Summary for Tweet {
    fn summarize_author(&self) -> String {
        format!("@{}", self.username)
    }
}
```

Now, here's an interesting tidbit for you, folks. Once we've defined the
summarize_author method, we can go ahead and call summarize on instances of the
Tweet struct. And guess what? The default implementation of summarize will
automatically invoke the definition of summarize_author that we've provided.
It's like a chain reaction of awesomeness!

Just take a look at this code snippet:

```rust
    let tweet = Tweet {
        username: String::from("horse_ebooks"),
        content: String::from(
            "of course, as you probably already know, people",
        ),
        reply: false,
        retweet: false,
    };

    println!("1 new tweet: {}", tweet.summarize());
```

When we run this code, it prints out: "1 new tweet: (Read more from
@horse_ebooks...)". How cool is that? The summarize method uses the
summarize_author method that we implemented, giving us the desired behavior
without any extra code on our part.

But hold your horses, because here's an important note: we can't call the
default implementation from an overriding implementation of the same method.
It's a one-way street, my friends. So keep that in mind when you're crafting
your code.

Alright, keep on harnessing the power of default implementations and unleash
your creativity with traits.

    Traits as Parameters

Alright, listen up, folks. We've reached the next level of trait wizardry. Now,
buckle up because we're about to define functions that can accept a wide range
of types. How do we do that? Well, with the power of traits, of course!

Let's take a look at this example. We've got the Summary trait that we
implemented on the NewsArticle and Tweet types in Listing 10-13. Now, we want to
define a function called notify that takes a parameter called item. But here's
the twist: we want this item parameter to be of any type that implements the
Summary trait. How do we achieve that? Simple! We use the impl Trait syntax.

Check out this code snippet:

```rust
pub fn notify(item: &impl Summary) {
    println!("Breaking news! {}", item.summarize());
}
```

See what we did there? Instead of specifying a concrete type for the item
parameter, we use the impl keyword followed by the trait name. This means that
our notify function can accept any type that implements the Summary trait.
Inside the body of notify, we can call any methods that come from the Summary
trait, like summarize.

So now, we can call notify and pass in any instance of NewsArticle or Tweet, and
it will work like a charm. But beware, my friends! If you try to call this
function with any other type, like a String or an i32, Rust won't let you
compile. It's all about those types that play by the rules and implement the
Summary trait.

So go ahead, use the power of traits to write versatile functions that can
handle a multitude of types. Your code will be more flexible, reusable, and just
downright awesome!

    Trait Bound Syntax

Alright, folks, let's dive a little deeper into the world of traits. We've been
using the impl Trait syntax to define functions that can accept any type
implementing a certain trait. But guess what? There's another way to achieve the
same result. It's called trait bound syntax, and it's a bit more explicit.

Check out this code snippet:

```rust
pub fn notify<T: Summary>(item: &T) {
    println!("Breaking news! {}", item.summarize());
}
```

Now, this may look a little more verbose, but bear with me. In this longer form,
we're using a trait bound to specify that the generic type parameter T must
implement the Summary trait. We place the trait bound after a colon and inside
angle brackets, right next to the generic type parameter declaration.

So what's the deal with this trait bound syntax? Well, it's essentially
equivalent to the previous example with impl Trait. It gives us the same
functionality, allowing our notify function to accept any type that implements
Summary. It's just a more explicit way of stating our requirements.

Now, you might be wondering, which syntax should you use? Well, it's up to you.
If you prefer a more concise and elegant approach, go with impl Trait. But if
you like to be explicit and leave no room for confusion, then the trait bound
syntax is your friend.

Alright, my fellow Rustaceans, let's talk about the difference between the impl
Trait syntax and the trait bound syntax. They both have their own strengths and
use cases.

Let's say we have a function called notify that takes two parameters, item1 and
item2, both of which implement the Summary trait. With the impl Trait syntax, we
can write it like this:

```rust
pub fn notify(item1: &impl Summary, item2: &impl Summary) {
```

Using impl Trait allows item1 and item2 to have different types as long as both
types implement the Summary trait. It provides flexibility and convenience in
cases where you want to accept different types without specifying their exact
concrete types.

But what if we want to enforce that both item1 and item2 must have the same
type? That's where the trait bound syntax comes into play:

```rust
pub fn notify<T: Summary>(item1: &T, item2: &T) {
```

Here, we use the generic type parameter T and specify a trait bound T: Summary.
This means that both item1 and item2 must have the same type, which is the
concrete type represented by T.

So, which syntax should you choose? It depends on your specific requirements. If
you need the flexibility to accept different types, go with impl Trait. But if
you want to enforce the same type for multiple parameters, the trait bound
syntax is your friend.

    Specifying Multiple Trait Bounds with the + Syntax

Sometimes, we want to require that a type implements multiple traits. Well, Rust
has got us covered with the "+ syntax".

Let's take our trusty notify function as an example. We want to modify it to not
only require the Summary trait but also the Display trait for the item
parameter. Here's how we can do it using the impl Trait + Trait syntax:

```rust
pub fn notify(item: &(impl Summary + Display)) {
```

With this syntax, we specify that item must implement both Summary and Display
traits. It's a way of saying "Hey, item, you better have all these traits if you
want to be part of this function!"

But that's not all! We can also achieve the same result using the trait bound
syntax with generics:

```
pub fn notify<T: Summary + Display>(item: &T) {
```

In this version, we use the generic type parameter T and specify the trait
bounds using the T: Trait1 + Trait2 syntax. It means that item must have both
the Summary and Display traits.

By specifying multiple trait bounds, we're getting the best of both worlds. We
can call methods from both traits within the notify function and unleash the
power of formatting and summarizing!

So, whether you prefer the impl Trait + Trait syntax or the trait bound syntax
with generics, Rust provides us with flexible ways to specify multiple trait
bounds. It's all about finding the syntax that makes your code clean and
expressive.

    Clearer Trait Bounds with where Clauses

Let's talk about making our code more readable when it comes to specifying trait
bounds in Rust. We all love clean and organized code, right? Well, Rust has a
solution for us: the mighty "where" clause!

Imagine you have a function with multiple generic type parameters, and you want
to specify trait bounds for each of them. Now, writing those bounds directly in
the function signature can quickly become a mess. It's like trying to untangle a
bunch of tangled headphones. Not fun.

But fear not! Rust comes to the rescue with the "where" clause. It allows us to
move all those trait bounds to a separate section, making our function signature
much cleaner and easier to read. Let me show you:

Instead of writing this:

```rust
fn some_function<T: Display + Clone, U: Clone + Debug>(t: &T, u: &U) -> i32 {
```

we can use a where clause, like this:

```rust
fn some_function<T, U>(t: &T, u: &U) -> i32
where
    T: Display + Clone,
    U: Clone + Debug,
{
```

See the difference? Now, the function's name, parameter list, and return type
are closer together, free from the clutter of trait bounds. It's like organizing
a messy room and finally being able to breathe.

By using the "where" clause, we can keep our code clean, readable, and
maintainable. It's a small change that makes a big difference.

    Returning Types that Implement Traits

Hey, check out this cool Rust feature! You can use the impl Trait syntax in the
return position to return a value of some type that implements a trait. It's
like getting a surprise gift without knowing exactly what's inside!

In the example below, the function returns_summarizable returns an
implementation of the Summary trait. But here's the catch: we don't have to
specify the concrete type! Instead, we use impl Summary as the return type,
leaving the compiler to figure out the exact type behind the scenes. It's like
letting the universe surprise us!

```rust
fn returns_summarizable() -> impl Summary {
    Tweet {
        username: String::from("horse_ebooks"),
        content: String::from(
            "of course, as you probably already know, people",
        ),
        reply: false,
        retweet: false,
    }
}
```

By using this impl Trait syntax, we can keep the return type concise and
abstract. The calling code doesn't need to know the specific type being
returned; it's like getting a gift without knowing what's inside the box. It's a
little mystery that makes our code more flexible and reusable.

This feature becomes especially handy when working with closures and iterators,
which we'll explore in Chapter 13. These constructs often create complex types
that are best left to the compiler to handle. With impl Trait, we can specify
that a function returns some type that implements a trait, without the need for
lengthy type declarations.

So, embrace the joy of surprises and let the impl Trait syntax simplify your
code. It's like receiving a present and not knowing exactly what's inside, but
knowing it's exactly what you need.

You know what's funny? This Rust feature called impl Trait is really handy when
it comes to returning types that implement a trait. It's like having a magic
trick up your sleeve!

Take a look at this code snippet:

```rust
 [This code does not compile!] 
fn returns_summarizable(switch: bool) -> impl Summary {
    if switch {
        NewsArticle {
            headline: String::from(
                "Penguins win the Stanley Cup Championship!",
            ),
            location: String::from("Pittsburgh, PA, USA"),
            author: String::from("Iceburgh"),
            content: String::from(
                "The Pittsburgh Penguins once again are the best \
                 hockey team in the NHL.",
            ),
        }
    } else {
        Tweet {
            username: String::from("horse_ebooks"),
            content: String::from(
                "of course, as you probably already know, people",
            ),
            reply: false,
            retweet: false,
        }
    }
}
```

Here's the beauty of it: we don't have to specify the concrete type that
returns_summarizable returns. Instead, we use impl Summary as the return type,
and the Rust compiler will figure out the exact type for us. It's like
performing a trick and letting the audience guess what's inside the hat!

This impl Trait syntax is especially handy when dealing with closures and
iterators. These constructs often create types that are long and complex, making
the code harder to read. But with impl Trait, we can simply specify that the
function returns some type that implements a trait, without diving into the
nitty-gritty details.

But hey, there's a catch! You can only use impl Trait if you're returning a
single type. So, unfortunately, the code snippet that tries to return either a
NewsArticle or a Tweet won't work. It's like trying to pull off two tricks at
once and ending up with a tangled mess.

But don't worry, we'll cover how to handle situations like this in Chapter 17,
where we'll explore trait objects that allow values of different types.

So, embrace the magic of impl Trait and let the Rust compiler handle the
trickery of returning types that implement traits.

    Using Trait Bounds to Conditionally Implement Methods

You know, sometimes we want to conditionally implement methods based on certain
traits. It's like having different sets of tools for different types. Let me
show you an example of how we can do that with Rust's trait bounds.

Check out this code snippet:

Filename: src/lib.rs

```rust
use std::fmt::Display;

struct Pair<T> {
    x: T,
    y: T,
}

impl<T> Pair<T> {
    fn new(x: T, y: T) -> Self {
        Self { x, y }
    }
}

impl<T: Display + PartialOrd> Pair<T> {
    fn cmp_display(&self) {
        if self.x >= self.y {
            println!("The largest member is x = {}", self.x);
        } else {
            println!("The largest member is y = {}", self.y);
        }
    }
}
```

Here's what's happening: we have a type called Pair<T> that holds two values of
the same type T. In the first impl block, we provide a generic implementation of
the new function, which creates a new instance of Pair<T>. Simple enough, right?

But in the second impl block, things get interesting. We use a trait bound to
specify that Pair<T> only implements the cmp_display method if T satisfies two
conditions: it must implement the Display trait for printing and the PartialOrd
trait for comparison.

By doing this, we conditionally implement the cmp_display method based on the
traits that T supports. It's like saying, "Hey, if T can be printed and
compared, then we can use this method!" It's like having a secret handshake that
only certain types can perform.

Now, when we call cmp_display on an instance of Pair<T>, the method will only be
available if T supports both printing and comparison. Otherwise, the code won't
compile, because we're not allowed to use the method with incompatible types.

So, with trait bounds, we can conditionally implement methods for different
types based on their capabilities. It's like tailoring our code to fit the
specific traits of the types we're working with.

You know, Rust is pretty clever when it comes to trait implementations. It has
this concept called blanket implementations that allows you to conditionally
implement a trait for any type that satisfies another trait. It's like giving a
trait a special power and saying, "Hey, if you meet this condition, you can have
this trait too!"

Let me give you an example from the Rust standard library. They implemented the
ToString trait for any type that implements the Display trait. Check out this
code snippet:

```rust
impl<T: Display> ToString for T {
    // --snip--
}
```

With this implementation, we can call the to_string method, defined by the
ToString trait, on any type that implements Display. It's like saying, "Hey, if
you can be displayed, you can be turned into a string too!" It's a nice little
shortcut that saves us from writing repetitive code.

For example, we can turn an integer into its corresponding string value using
the to_string method:

```rust
let s = 3.to_string();
```

And just like that, we have a string representation of the number 3. Thanks to
the blanket implementation, we can use the to_string method on any type that
satisfies the Display trait.

These blanket implementations are pretty handy. They appear in the documentation
for the trait, giving us a clear view of which types have access to the trait
through the blanket implementation.

With traits and trait bounds, Rust lets us write code that is both generic and
specific. We can reduce duplication by using generic type parameters, while also
specifying the behavior we expect from those types. The compiler checks that all
the concrete types we use provide the correct behavior, catching potential
errors at compile time. No runtime surprises here!

And you know what's even better? We don't have to write code that checks for
behavior at runtime because we've already done it at compile time. It's like
getting performance and safety in one package.
