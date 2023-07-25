    Separating Modules into Different Files

Alright, let's talk about separating modules into different files. You know,
when your code starts getting big and messy, it's time to clean house. And one
way to do that is by moving your module definitions to separate files. It's like
giving each module its own little home where it can thrive and be easily
navigated.

Now, let's take a look at an example from Listing 7-17. We had all these
restaurant modules cramped up in one file, and that's just not ideal. So, what
we're gonna do is extract the front_of_house module and give it its own file.
We'll start by removing all the code inside the curly brackets for the
front_of_house module in src/lib.rs. All we'll have left is the mod
front_of_house; declaration. It's like we're setting the stage for something big
to happen.

But wait, hold your horses! This won't compile just yet. We need to create a new
file called src/front_of_house.rs. This is where the body of the front_of_house
module will reside. It's like giving it a cozy little house of its own, away
from the chaos of the crate root file.

So there you have it. We're breaking things apart, giving each module its own
space to breathe.

Filename: src/lib.rs

```rust

mod front_of_house;

pub use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}

```

Listing 7-21: Declaring the front_of_house module whose body will be in
src/front_of_house.rs

Alright, now we're getting down to business. We've created a new file called
src/front_of_house.rs, and it's time to give it some life. We're going to take
all the code that was inside those curly brackets in the front_of_house module
and put it in this new file. It's like moving furniture from one room to
another, but instead of furniture, we're moving code. Exciting stuff!

So, here's what the code in src/front_of_house.rs looks like, as shown in
Listing 7-22:

Filename: src/front_of_house.rs

```rust

pub mod hosting {
    pub fn add_to_waitlist() {}
}
```

Listing 7-22: Definitions inside the front_of_house module in src/front_of_house.rs


This code defines the hosting module, and inside it, we have the add_to_waitlist
function. It's like we're setting up a little gathering place for all the people
waiting to be seated at the restaurant. And by putting it in its own file, we're
giving it some special attention.

Now, here's an important thing to note. Once you've loaded a file using a mod
declaration, you don't need to load it again in your module tree. The compiler
is smart enough to know where to find the code because of the mod statement
you've already used. It's like the compiler has a GPS system built-in, guiding
it to the right place.

And hey, we're not done yet! We're going to take things a step further. We're
going to extract the hosting module to its own file. But wait, this time it's a
little different. Hosting is not a child module of the root module; it's a child
module of front_of_house. So, we're going to create a new directory named
src/front_of_house/ to house this file. It's like giving it its own little
neighborhood within the codebase.

And there you have it. We're splitting and organizing our code, creating
separate files and directories for each module. It's like building a little
ecosystem within your project.

Alright, we're on a roll! Now it's time to continue moving the hosting module to
its own file. Here's what we're going to do:

Filename: src/front_of_house.rs

```rust

pub mod hosting;

```

We're keeping it simple and just saying, "Hey, there's a module called hosting
here." We're not cluttering it with any code because we want to save that for
the hosting module's own file.

Now, we create a brand new directory called src/front_of_house/. It's like
building a little house for our hosting module. And inside this directory, we
create a file called hosting.rs. This is where we'll put all the definitions for
the hosting module.

So, the hosting.rs file, located at src/front_of_house/hosting.rs, looks like
this:

Filename: src/front_of_house/hosting.rs

```rust

pub fn add_to_waitlist() {}

```

In this file, we define the add_to_waitlist function. It's like setting up a
nice little spot for people to put their names down when they want to be seated.
Simple, yet effective.

Now, here's an important thing to remember. If we put the hosting.rs file
directly in the src directory instead of inside the src/front_of_house/
directory, the compiler would get confused. It would expect the code inside
hosting.rs to be part of a hosting module declared in the crate root, not as a
child of the front_of_house module. The compiler follows certain rules about
which files to check for which modules' code, and by organizing our files and
directories in this way, we're making things easier for the compiler to
navigate.

So, keep those directories and files in line with the module tree. Let them
dance together harmoniously, creating a beautiful code symphony.

    Alternate File Paths

Alright, now we're diving into the world of file paths in Rust. And guess what?
There's an alternate style of file path that the Rust compiler supports. It's
like having multiple flavors of ice cream to choose from. Let me break it down
for you.

Let's say we have a module named front_of_house declared in the crate root. The
compiler will look for the code of this module in two places:

```rust
src/front_of_house.rs (what we covered) 
src/front_of_house/mod.rs (older style,
still supported path)
```

Now, let's move on to a submodule named hosting, which belongs to the
front_of_house module. The compiler has two options here as well:

```rust

src/front_of_house/hosting.rs (what we covered)
src/front_of_house/hosting/mod.rs (older style, still supported path)

```

Here's a little heads-up though: if you start mixing both styles for the same
module, the compiler won't be happy. It'll give you an error. So, stick to one
style per module to avoid confusion and keep things running smoothly.

Now, here's the downside of using the older style with files named mod.rs: you
might end up with a bunch of files all named mod.rs in your project. It's like
having a bunch of clones, and that can get pretty confusing when you have them
all open in your editor at the same time. So, be aware of that little quirk.

Alright, we've successfully split our code into separate files, keeping our
module tree intact. It's like organizing your closet, but for code. And guess
what? The function calls in eat_at_restaurant still work like a charm, even
though the definitions now live in different files. It's like magic, my friend.
This technique allows us to easily move modules to new files as they grow larger
and more complex.

Now, here's the thing: the pub use crate::front_of_house::hosting statement in
src/lib.rs hasn't changed one bit. It's still doing its job, making the hosting
module accessible to the outside world. And let me tell you a little secret: the
use statement has no impact on which files are compiled as part of the crate.
It's just there to bring paths into scope and make our lives a bit easier. So,
use it wisely.

    Summary

Alright, we've successfully split our code into separate files, keeping our
module tree intact. It's like organizing your closet, but for code. And guess
what? The function calls in eat_at_restaurant still work like a charm, even
though the definitions now live in different files. It's like magic, my friend.
This technique allows us to easily move modules to new files as they grow larger
and more complex.

Now, here's the thing: the pub use crate::front_of_house::hosting statement in
src/lib.rs hasn't changed one bit. It's still doing its job, making the hosting
module accessible to the outside world. And let me tell you a little secret: the
use statement has no impact on which files are compiled as part of the crate.
It's just there to bring paths into scope and make our lives a bit easier. So,
use it wisely, my friend.

Just a quick recap: Rust gives us the power to split our package into multiple
crates and our crates into modules. It's like building blocks, assembling our
code in a way that makes sense. We can refer to items defined in one module from
another module by specifying absolute or relative paths. And hey, if you want to
use a shorter path for multiple uses of an item within a scope, just bring that
path into scope with a use statement. It's like a shortcut that saves you
typing.

Remember, module code is private by default, but if you want to share the love
and make some definitions accessible outside the module, just add the pub
keyword. It's like opening a window and letting the fresh air in.

So, there you have it. We've covered the ins and outs of organizing our code
into modules and files, making our lives easier and our code more manageable. In
the next chapter, we'll delve into the wonderful world of collection data
structures in the standard library. It's like having a whole toolbox of useful
items at your disposal.
