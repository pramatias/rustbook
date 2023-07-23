    Bringing Paths into Scope with the use Keyword

You know what's annoying? Having to write out these long, convoluted paths just
to call a simple function. It's like going on a road trip and having to spell
out the entire GPS coordinates every time you make a turn. I mean, who has the
time and patience for that?

But guess what? Rust has a nifty little trick up its sleeve to save us from this
madness. It's called the "use" keyword, and it's like having a magic
teleportation device that takes you straight to your destination without all the
hassle.

In our code, we're bringing in the crate::front_of_house::hosting module into
the scope of the eat_at_restaurant function. It's like saying, "Hey Rust, from
now on, I want to call the hosting module 'hosting,' got it?" And Rust is like,
"Sure thing, buddy! You got it!"

Now, instead of writing out that long-winded
crate::front_of_house::hosting::add_to_waitlist every time we want to add
someone to the waitlist, we can simply say hosting::add_to_waitlist. It's like
having a shortcut, a secret handshake that gets us where we want to go.

Life's all about finding those little shortcuts, those small pleasures that make
things easier. And in Rust, the "use" keyword is one of those little joys that
can brighten your day.

So go ahead, use the "use" keyword, and save yourself from the tyranny of long
paths.

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}
```
Listing 7-11: Bringing a module into scope with use

You know, using the use keyword in Rust is kind of like creating a symbolic link
in the filesystem. It's like saying, "Hey, Rust, let's make a shortcut here,
just like those fancy links on your computer." And Rust is like, "Sure thing,
buddy! Let's make life a little easier."

When we add use crate::front_of_house::hosting in the crate root, it's like
creating a symbolic link to the hosting module. It's as if the hosting module
magically appears in the crate root, just like if you created a symbolic link to
a folder and it suddenly shows up in your current directory. It's pretty cool,
right?

But here's the thing: just like in the filesystem, the paths brought into scope
with use also check privacy. It's like having access to a shortcut, but with
some security measures. You can only access what you're allowed to access.
Privacy rules still apply.

Now, here's something important to note: the use statement only creates the
shortcut for the particular scope it's in. In Listing 7-12, we moved the
eat_at_restaurant function into a new child module named customer. And you know
what? That new module is a whole different scope, man. It's like entering a
different dimension.

So, when we try to use the hosting::add_to_waitlist shortcut inside the customer
module, Rust is like, "Hold on a second, buddy. I don't know what you're talking
about. That shortcut doesn't exist here." And bam! We get a compiler error, just
like when you're trying to access something that's not in your current
directory.

So remember, the use statement is like a symbolic link, but it only works within
the scope it's in.

Filename: src/lib.rs

```rust

mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

use crate::front_of_house::hosting;

mod customer {
    pub fn eat_at_restaurant() {
        hosting::add_to_waitlist();
    }
}
```

Listing 7-12: A use statement only applies in the scope it’s in

Oh boy, looks like we've hit a snag! The compiler is not happy with us, my
friend. It's throwing warnings and errors left and right, making a big fuss
about our code. Let's see what it's complaining about.

```rust
$ cargo build
   Compiling restaurant v0.1.0 (file:///projects/restaurant)
warning: unused import: `crate::front_of_house::hosting`
 --> src/lib.rs:7:5
  |
7 | use crate::front_of_house::hosting;
  |     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  |
  = note: `#[warn(unused_imports)]` on by default

error[E0433]: failed to resolve: use of undeclared crate or module `hosting`
  --> src/lib.rs:11:9
   |
11 |         hosting::add_to_waitlist();
   |         ^^^^^^^ use of undeclared crate or module `hosting`

For more information about this error, try `rustc --explain E0433`.
warning: `restaurant` (lib) generated 1 warning
error: could not compile `restaurant` due to previous error; 1 warning emitted
```

First, we get a warning that says, "Hey, you imported
crate::front_of_house::hosting, but you're not even using it! What's the point,
man?" Yeah, Rust likes to keep things tidy, and unused imports are like clutter
in your code. It's giving you a heads up, saying, "Hey, clean up your mess!"

But that's not the worst part. The real problem is the error that says, "Failed
to resolve: use of undeclared crate or module hosting." Ouch, that hurts. Rust
is like, "I have no idea what you're talking about, buddy. This hosting thing
you're trying to use? It doesn't exist here."

So what can we do to fix this mess? Well, we have a couple of options. One
option is to move the use statement inside the customer module. It's like
saying, "Hey, Rust, this shortcut is only valid in this specific room, got it?"
That way, Rust knows where to find the shortcut, and it's happy again.

Another option is to use the super::hosting syntax within the customer module.
It's like saying, "Hey, Rust, remember that shortcut we talked about in the
parent module? Yeah, let's use that instead." It's a way to bridge the gap
between scopes and make sure Rust can find what it's looking for.

    Creating Idiomatic use Paths

Now, let's talk about some idiomatic Rust code, my friend. In Listing 7-11, you
might have noticed that we used the use keyword to bring
crate::front_of_house::hosting into scope, and then we called
hosting::add_to_waitlist in the eat_at_restaurant function. But why did we do it
that way instead of directly specifying the full path to the add_to_waitlist
function, like in Listing 7-13?

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

use crate::front_of_house::hosting::add_to_waitlist;

pub fn eat_at_restaurant() {
    add_to_waitlist();
}
```
Listing 7-13: Bringing the add_to_waitlist function into scope with use, which
is unidiomatic

Well, let me tell you, there's a reason for that. Listing 7-11 is the idiomatic
way of doing things in Rust. By bringing the function's parent module into scope
with use, we make it clear that the function is not locally defined. It's like
saying, "Hey, this function comes from the hosting module, and I'm using it
right here."

On the other hand, Listing 7-13 might work, but it's not very clear. We brought
the add_to_waitlist function into scope directly using use, without specifying
the parent module. It's like saying, "Hey, I'm using this function, but who
knows where it came from?" It's a bit ambiguous.

In Rust, we like to be explicit about where things come from. It helps with code
readability and understanding. So, even though Listing 7-11 requires a bit more
typing, it's the preferred way to bring functions into scope. We specify the
parent module when calling the function, making it clear where it comes from,
while still keeping the path concise and minimizing repetition.

Let's keep things clear and tidy in our code, just like tidying up our room.
Specify the parent module, bring functions into scope, and let Rust know exactly
what we're talking about. It's all about being clear, both in code
and in life.

Now, here's an interesting tidbit. When it comes to bringing in
structs, enums, and other items with use, things are a bit different. In fact,
it's idiomatic in Rust to specify the full path for these items. Let me show you
an example.

Filename: src/main.rs

```rust
use std::collections::HashMap;

fn main() {
    let mut map = HashMap::new();
    map.insert(1, 2);
}
```

Listing 7-14: Bringing HashMap into scope in an idiomatic way

Take a look at Listing 7-14. Here, we're bringing the mighty HashMap struct from
the standard library into the scope of our binary crate. But guess what? We're
doing it the idiomatic way. We're specifying the full path with use
std::collections::HashMap.

In this case, there's no strong reason or deep philosophy behind this
convention. It's just the way things have evolved in the Rust community. People
have gotten used to reading and writing Rust code in this manner. It's like the
unwritten rule of Rust coding style, you know?

So, when it comes to bringing in structs, enums, and other items with use, go
ahead and specify the full path. Embrace the convention, my friend. It's the
Rust way of doing things. Let your code flow smoothly and gracefully, just like
a well-crafted symphony.

Remember, conventions shape the way we write code. They bring harmony and
understanding to our programs. And in the case of Rust, specifying the full path
for structs and enums with use is part of that beautiful harmony.

Now, here's a little exception to the idiom I just told you about. Brace
yourself for this one. In Rust, if you happen to bring two items with the same
name into scope using use statements, well, guess what? Rust won't allow it.
It's like a clash of the titans, my friend. Two items with the same name,
battling for supremacy.

Filename: src/lib.rs

```rust
use std::fmt;
use std::io;

fn function1() -> fmt::Result {
    // --snip--
}

fn function2() -> io::Result<()> {
    // --snip--
}
```

Listing 7-15: Bringing two types with the same name into the same scope requires
using their parent modules.

But don't worry, there's a way around it. Take a look at Listing
7-15. Here, we're bringing two Result types into scope that have the same name
but different parent modules. Tricky situation, right? But fear not, for Rust
has a solution.

Instead of just specifying use std::fmt::Result and use std::io::Result, we go
the extra mile. We use their parent modules as well, like use std::fmt and use
std::io. This way, we're distinguishing between the two Result types.
Rust can breathe a sigh of relief knowing exactly which Result we're referring
to in our code.

It's like creating a clear path, a distinct identity for each Result type. We're
giving them their own space to shine and be recognized. No more confusion, no
more guessing. Just pure clarity and certainty.

So, remember, when you find yourself in a situation where two items
share the same name, go ahead and specify their parent modules in your use
statements. Let Rust know exactly which item you're referring to. It's like
playing the role of a mediator, settling the dispute and maintaining peace in
the code.

    Providing New Names with the as Keyword

Here's another little trick. When you find yourself in a pickle, with
two types sharing the same name and you want to bring them into the same scope,
Rust has got your back. Introducing the mighty "as" keyword!

Filename: src/lib.rs

```rust
use std::fmt::Result;
use std::io::Result as IoResult;

fn function1() -> Result {
    // --snip--
}

fn function2() -> IoResult<()> {
    // --snip--
}
```
Listing 7-16: Renaming a type when it’s brought into scope with the as keyword

Take a look at Listing 7-16. We have two Result types, but we want to avoid any
conflicts. So, we use the "as" keyword to provide a new name, a fresh alias, for
one of the Result types. It's like giving it a new identity, a secret code name.

In the first use statement, we bring in the std::fmt::Result type just as it is.
No need for a name change here. But in the second use statement, we
take control and say, "Hey, std::io::Result, from now on, you shall be known as
IoResult!" And just like that, we've given it a brand new name, a shiny new
persona.

Now, when we use these types in our code, we can refer to them by their new
names. We call the std::fmt::Result just as Result, and the std::io::Result, now
known as IoResult, can be referenced by its fresh alias. It's like having a
secret language, a special code that only you and Rust understand.

So, whether you prefer the original names or you want to give them
cool new aliases, the choice is yours. Both approaches, Listing 7-15 and Listing
7-16, are considered the "right" way to do it in Rust. It's all about finding
what works best for you and your code.

With the power of the "as" keyword, you can conquer the naming conflicts and
bring harmony to your code. Rust gives you the flexibility to choose your own
path, to create a world where names don't collide and confusion is kept at bay.

    Re-exporting Names with pub use

Let me tell you about a cool technique called re-exporting. You see,
when we bring a name into scope using the use keyword, it's all private and
hidden away. But what if we want others to be able to use that name as if it
were defined in their own code? Well, that's where pub use comes into play.

Take a look at Listing 7-17. We've made a small change to the code from Listing
7-11. See that use statement in the root module? We've added the pub keyword
before it, making it pub use. What does that do? It re-exports the name, my
friend! It brings it into scope and also makes it available for others to bring
into their own scope. It's like sharing a secret with the world!

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

pub use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}
```

Listing 7-17: Making a name available for any code to use from a new scope with
pub use

Before this change, if you wanted to call the add_to_waitlist function from
external code, you had to use the long path
restaurant::front_of_house::hosting::add_to_waitlist(). But now, with the power
of pub use, you can simply use the path restaurant::hosting::add_to_waitlist().
It's like magic, my friend! The name is now accessible from a new scope, and
everyone can enjoy the simplicity and convenience it brings.

Re-exporting is a nifty technique when the internal structure of your code
doesn't align with how other programmers would think about it. It's like
presenting a different face to the world, making your code more intuitive and
user-friendly. In this restaurant metaphor, the folks running the joint think
about the "front of house" and the "back of house," but customers just want to
enjoy a meal without worrying about those details. With pub use, you can
organize your code internally while exposing a different structure to those who
use it. It's all about creating a seamless experience for both the creators and
the users of your code.

So, embrace the power of pub use! Re-export those names, make them
accessible to others, and let your code shine. It's not just about
functionality; it's about making life easier for those who interact with your
code. And who knows, maybe one day, your code will become a widely used library,
and people will appreciate the thoughtfulness you put into its design.

    Using External Packages

Ah, let's talk about using external packages. Remember back in Chapter 2 when we
built that awesome guessing game? We wanted to generate random numbers, so we
turned to an external package called rand. Good times!

Filename: Cargo.toml

```rust
rand = "0.8.5"
```

To use rand in our project, we had to do a couple of things. First, we added a
line to our trusty Cargo.toml file. We simply wrote "rand = "0.8.5"" to tell
Cargo, "Hey, buddy, we need this rand package, so go ahead and fetch it from
crates.io along with any other dependencies."

Once Cargo did its thing and got the package for us, we were ready to bring
those rand definitions into the scope of our project. We used a cool line that
starts with the name of the crate, rand, and then listed the items we wanted to
bring into scope. In our case, we brought in the Rng trait. Remember that? It
allowed us to call the awesome rand::thread_rng() function.

So, in the end, we had this nice line in our code: "use rand::Rng;". It's like
opening a door to the rand crate and saying, "Hey, come on in! I want to use
your Rng trait!"

```rust
use rand::Rng;

fn main() {
    let secret_number = rand::thread_rng().gen_range(1..=100);
}
```

Members of the Rust community have made many packages available at crates.io,
and pulling any of them into your package involves these same steps: listing
them in your package’s Cargo.toml file and using use to bring items from their
crates into scope.

Note that the standard std library is also a crate that’s external to our
package. Because the standard library is shipped with the Rust language, we
don’t need to change Cargo.toml to include std. But we do need to refer to it
with use to bring items from there into our package’s scope. For example, with
HashMap we would use this line:

```rust
use std::collections::HashMap;
```

So, when it comes to using external packages, it's all about listing them in
Cargo.toml, bringing their goodies into your project's scope with "use", and
having a blast exploring the awesome crates.io ecosystem.

    Using Nested Paths to Clean Up Large use Lists

If we’re using multiple items defined in the same crate or same module, listing
each item on its own line can take up a lot of vertical space in our files. For
example, these two use statements we had in the Guessing Game in Listing 2-4
bring items from std into scope:

Filename: src/main.rs

```rust
// --snip--
use std::cmp::Ordering;
use std::io;
// --snip--
```

But fear not, because Rust has got our backs. We can use nested paths
to bring all those items into scope in just one line. It's like a magical
compression technique for our use statements.

Here's how it works. Instead of listing each item separately, we specify the
common part of the path, followed by two colons, and then we wrap the differing
parts of the paths in curly brackets. It's like creating a little cozy nest for
our paths. Let me show you an example.

Filename: src/main.rs

In the good old Guessing Game, we had these two use statements to bring items
from std into scope:

```rust
use std::cmp::Ordering;
use std::io;
```

Now, with the power of nested paths, we can do it all in one line:

```rust
// --snip--
use std::{cmp::Ordering, io};
// --snip--
```

Listing 7-18: Specifying a nested path to bring multiple items with the same
prefix into scope

Boom! Just like that, we compressed those two lines into one. It's like code
compression, but without losing any functionality. Amazing, isn't it?

Now, imagine the possibilities in bigger programs. When you have a ton of items
to bring into scope from the same crate or module, using nested paths can save
you from drowning in a sea of use statements. It reduces the clutter and makes
your code look sleek and organized. It's like tidying up your room, but for your
code!

Rust is full of surprises, and one of them is the ability to use nested paths at
any level. It's like playing with building blocks and creating these awesome
combinations. Let me show you what I mean.

In Listing 7-19, we have two separate use statements. One brings std::io into
scope, and the other brings std::io::Write into scope. But hey, wait a minute!
Look closely, my friends. The second use statement, std::io::Write, is actually
a subpath of the first one, std::io. They're like two puzzle pieces that fit
together.

Filename: src/lib.rs

```rust
use std::io;
use std::io::Write;
```

Listing 7-19: Two use statements where one is a subpath of the other

Now, brace yourselves, because Rust allows us to merge these two paths into one
beautiful use statement using the magical keyword "self". It's like bringing
harmony to the world of paths. Let me show you how it's done in Listing 7-20.

We simply write:

Filename: src/lib.rs

```rust
use std::io::{self, Write};
```

Listing 7-20: Combining the paths in Listing 7-19 into one use statement

Boom! Just like that, we combined std::io and std::io::Write into one use
statement. It's like a path fusion, my friends. Now, both std::io and
std::io::Write are brought into scope with a single line of code. Isn't that
amazing?

Rust gives us this power to create clean and concise code. It's like
decluttering your house, but for your codebase. So go ahead, my friends, and use
nested paths to combine those subpaths. Embrace the elegance and simplicity that
Rust offers.

    The Glob Operator

Alright, folks, hold on tight because we're about to talk about the glob
operator in Rust. It's like opening Pandora's box of code, so buckle up!

If you're feeling a bit lazy or you just want to bring all the public items
defined in a path into scope without specifying each one individually, then the
glob operator is your go-to buddy. It's like a wildcard that says, "Hey, Rust,
give me everything you've got in this path!"

Here's how it works: you simply write the path you want to import, followed by
the * glob operator. For example, take a look at this use statement:

```rust
use std::collections::*;
```

This use statement brings all public items defined in std::collections into the
current scope. Be careful when using the glob operator! Glob can make it harder
to tell what names are in scope and where a name used in your program was
defined.

The glob operator is often used when testing to bring everything under test into
the tests module; we’ll talk about that in the “How to Write Tests” section in
Chapter 11. The glob operator is also sometimes used as part of the prelude
pattern: see the standard library documentation for more information on that
pattern.
