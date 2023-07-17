Alright, folks, let's dive into the exciting world of modules and how they help
us organize our code. But before we get into the nitty-gritty details, let me
give you a cheat sheet, a quick reference guide to keep things simple and clear.
Think of it as your trusty map in the module jungle.

Rule number one: modules allow you to organize your code. It's like putting
things in different drawers so you can find them easily. And guess what? We have
paths to name those items in the modules. It's like giving each item a unique
address, a code GPS if you will.

Now, here comes the use keyword. It's like a magic spell that brings a path into
scope. It's like summoning an item from a specific drawer and having it ready to
use. And guess what? We have the pub keyword that makes items public. It's like
saying, "Hey, everyone, check out this awesome code I've got!"

But wait, there's more! We have the as keyword that lets us give items a new
name. It's like giving a code item a cool nickname, a code alter ego, if you
will. And hey, we even have external packages, like those code friends from
outside, joining the party. It's like having a whole new set of code toys to
play with.

And finally, the glob operator. It's like opening up all the drawers and having
access to everything inside. It's like going code wild, exploring all the hidden
treasures in one go.

So there you have it, folks. The module cheat sheet, your handy reference guide
to navigating the world of modules, paths, and keywords. We'll be diving deeper
into each of these rules as we go along, but this cheat sheet will always be
there to remind you of the magic happening behind the scenes.

Alright, let's take a stroll through the fascinating world of crate roots,
modules, and paths. It's like exploring a whole code universe with its own set
of rules. So here's the lowdown, the inside scoop, on how this all works.

When the compiler is compiling a crate, it starts by looking at the crate root
file. That's usually src/lib.rs for a library crate or src/main.rs for a binary
crate. It's like the entry point, the heart and soul of your code.

Now, in this crate root file, you can declare new modules. It's like creating
different sections in your code, like a garden for your plants or a kitchen for
your recipes. And guess what? The compiler will search for the module's code in
three possible places. First, it checks right there in the crate root file,
within curly brackets that replace the semicolon. It's like having an inline
module, right in the middle of the action. But if the code is not found there,
fear not! The compiler will also look for it in separate files: src/garden.rs or
src/garden/mod.rs. It's like having dedicated files for specific modules,
keeping things nice and organized.

But wait, there's more! You can also declare submodules in any file other than
the crate root. It's like having little nooks within a bigger space. For
example, you might declare a "vegetables" submodule in src/garden.rs. And guess
what? The compiler knows just where to find the submodule's code. It checks
within the curly brackets right after the "mod vegetables" declaration. It's
like having an inline submodule, tucked away neatly. But if the code is not
there, it will search for it in separate files: src/garden/vegetables.rs or
src/garden/vegetables/mod.rs. It's like having dedicated files for each
submodule, keeping things nice and tidy.

Now, once you have these modules and submodules set up, you can refer to code
within them using paths. It's like having GPS coordinates for your code. For
example, if you have an "Asparagus" type in the garden vegetables module, you
can find it at crate::garden::vegetables::Asparagus. It's like following the
code breadcrumbs to exactly where you need to be.

But what about privacy, you ask? Well, by default, code within a module is
private to its parent modules. It's like having a secret code that only certain
modules can access. But if you want to make a module public, so that other parts
of your crate can see it, just declare it with pub mod instead of mod. It's like
shouting from the rooftops, "Hey everyone, check out this awesome module I've
got!"

And now, let's talk about the "use" keyword. It's like a magic shortcut that
saves you from typing long paths over and over again. You can create a shortcut
within a scope using the "use" keyword. So instead of writing
crate::garden::vegetables::Asparagus every time you need it, you can simply
write "use crate::garden::vegetables::Asparagus;" and from then on, just use
"Asparagus" in that scope. It's like having a code teleportation device,
instantly bringing the item to your fingertips.

So there you have it, folks! A journey through crate roots, modules, paths, and
keywords. It's like a whole new world of code organization and access. Remember
these rules, and you'll be navigating the code universe like a pro.

Alright, let's take a look at this backyard crate and see how these rules play
out in action. Imagine a little code universe contained within this directory
structure.

So, we've got a crate named backyard. It's like a little world of code, with its
own set of files and directories. Take a look:


backyard
├── Cargo.lock
├── Cargo.toml
└── src
    ├── garden
    │   └── vegetables.rs
    ├── garden.rs
    └── main.rs

Now, the main.rs file is the crate root file in this case. It's like the
epicenter, the starting point of this backyard world. And what do we have in
there? Let me show you:

```rust
use crate::garden::vegetables::Asparagus;

pub mod garden;

fn main() {
    let plant = Asparagus {};
    println!("I'm growing {:?}!", plant);
}
```

Ah, the use of the "use" keyword, creating a shortcut for us. It's like saying,
"Hey, let's bring in that Asparagus from the garden's vegetables module." And
you see that "pub mod garden;" line? It's like opening the gates to the garden
module, telling the compiler to include the code it finds in src/garden.rs.
Let's go deeper into the garden, shall we?

```rust

pub mod vegetables;

```
Here, we have another "pub mod" declaration. It's like saying, "Hey, there's
more to explore! Check out the vegetables module." And guess what? The code in
src/garden/vegetables.rs is included too. It's like an invitation to the
vegetable party. So let's see what's inside that vegetables module:

```rust

#[derive(Debug)]
pub struct Asparagus {}

```
Ah, an Asparagus struct! Look at that #[derive(Debug)] attribute, making it all
fancy and debuggable. And it's marked as "pub", so it's like saying, "Hey,
everyone, check out this Asparagus struct! It's up for grabs!"

And there you have it, folks! A backyard crate with modules and code flowing
through its veins. It's like a microcosm of code organization and exploration.
So dive in, explore, and see what amazing things you can grow in this backyard
of yours!

Alright, let's talk about modules! They're like the organizers of a code party.
You know, like when you throw a party, you gotta organize stuff, right? You want
all the snacks in one place, the drinks in another, and the dance floor, well,
you need a space for that too. That's exactly what modules do in Rust.

So, we're gonna create a library crate, and it's gonna be all about a fancy
restaurant. Oh, la la! We're gonna have functions that make this restaurant
awesome, but for now, we'll just focus on the structure, not the nitty-gritty
details.

Now, in the restaurant biz, there's a front of house and a back of house. The
front of house is where all the customers are, where the magic happens! You've
got hosts seating people, servers taking orders and payments, and bartenders
making delightful drinks.

On the other hand, we've got the back of house, where all the kitchen action is!
This is where the chefs and cooks work their culinary magic. We've got
dishwashers cleaning up the mess (someone's gotta do it!), and managers taking
care of all the admin stuff.

So, how do we organize all this in Rust? Well, we use modules, my friend! We'll
have a module for the front of house, and another module for the back of house.
And guess what? Code within these modules is private by default. It's like
having a VIP area in the party where only special guests are allowed.

But hey, we can make things public too! We'll choose what we want to expose to
the outside world. It's like inviting certain people to the party and keeping
others out. So we'll make some modules and items public, so other code can use
and depend on them.

But hold your horses, we're not gonna fill in all the details right now. We'll
just set up the structure, like drawing a floor plan for the restaurant. Then,
we can fill it with all the delicious code later.

So there you have it, folks! Modules in Rust are like the hosts of a party,
guiding everyone to their respective areas. It's all about organization,
privacy, and control. Now let's get cooking and make this restaurant the talk of
the town!

Alright, folks, it's time to structure our crate! We're gonna build a fancy
restaurant, remember? So let's get down to business.

First things first, we gotta create a new library crate. We'll call it
"restaurant" because, well, that's what it is! So go ahead and run that command
cargo new restaurant --lib. Easy peasy.

Now, in the heart of our restaurant, the lib.rs file, we're gonna set up the
structure. It's like creating the blueprint for our culinary masterpiece. So
check out this code snippet:

```rust

mod front_of_house {
    mod hosting {
        fn add_to_waitlist() {}

        fn seat_at_table() {}
    }

    mod serving {
        fn take_order() {}

        fn serve_order() {}

        fn take_payment() {}
    }
}
```

See what we did there? We created a module called front_of_house. It's like the
entrance to our restaurant, where all the action starts. Inside this module, we
can have more modules, just like nesting dolls. So we've got hosting and serving
modules within front_of_house.

But hey, it's not just about modules! We can also have other cool stuff inside
modules, like structs, enums, constants, traits, and yup, you guessed
it—functions! In this case, we've got some function signatures inside hosting
and serving.

So, we're structuring our code, organizing it like a well-oiled kitchen. It's
all about making things clean, manageable, and delicious. And guess what? Code
within modules is private by default, just like a secret recipe. We'll decide
what we want to reveal to the world.

So there you have it, folks! We're building our restaurant step by step, module
by module. It's gonna be a culinary adventure like no other. So put on your chef
hats and let's keep cooking up some code magic!

Alright, let's dive deeper into modules, folks! They're like little groups of
definitions, all neatly organized and given a name. It's like having a filing
system for our code. And you know what? It makes life easier for programmers
using this code. They can navigate through the code based on these groups
instead of sifting through a mess of definitions. It's like finding your way in
a big city by following the signs!

Imagine you're adding new functionality to this code. You don't want to be lost
in the chaos, right? That's where modules come to the rescue! They give you a
clear roadmap. You know exactly where to place your code to keep things
organized and maintainable. It's like having a designated spot for everything in
your kitchen. No more searching for that spatula in the spice rack!

Now, let's talk about crate roots. You've got src/main.rs and src/lib.rs.
They're the kings of the castle, the masters of their domains. Why? Because the
contents of these files form a special module called... wait for it... "crate"!
Yep, that's right. It's like the root of all modules, the mighty tree trunk from
which everything branches out. We call it the module tree. Fancy, huh?

Take a look at Listing 7-2. It's like a map of our module tree. You can see how
the modules nest inside each other, like those Russian nesting dolls. For
example, "hosting" is a child of "front_of_house". And guess what?
"front_of_house" is the parent of "hosting". It's a family affair, folks! Oh,
and "hosting" and "serving" are siblings, born and raised within the loving
embrace of "front_of_house". Ain't that sweet?

crate
 └── front_of_house
     ├── hosting
     │   ├── add_to_waitlist
     │   └── seat_at_table
     └── serving
         ├── take_order
         ├── serve_order
         └── take_payment


You might even notice a similarity to your computer's directory tree. It's like
a mini digital ecosystem, right? Just like directories in a filesystem, we use
modules to keep our code organized. And just like finding files in a directory,
we need a way to find our modules. It's like a treasure hunt, but instead of
gold doubloons, we're seeking well-structured code.

So there you have it, my friends! Modules are the superheroes of organization,
helping us conquer the chaos and create code that's clean, understandable, and a
joy to work with. It's like a symphony of code harmony. So let's keep exploring
the module tree, finding our way through this coding adventure!
