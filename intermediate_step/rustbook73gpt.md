    Paths for Referring to an Item in the Module Tree

Alright, let's talk about paths in Rust. It's like finding your way in a big
city, but instead of streets and buildings, we're navigating through a module
tree. And just like when you're trying to find a specific location, you need the
right path to get there.

Paths in Rust can be absolute or relative. It's like using GPS coordinates or
giving directions based on your current location. An absolute path starts from
the crate root, while a relative path starts from the current module. Think of
it as saying, "Hey, Rust, the function I'm looking for is right here, or it's
over there, or maybe it's a few steps back!"

In the module tree, paths are formed by connecting identifiers with double
colons (::). It's like following a trail of breadcrumbs, one identifier at a
time. And just like when you're navigating a filesystem, the path tells Rust
exactly where to find the item you're looking for.

Let's go back to Listing 7-1 for a moment. Imagine we want to call the
add_to_waitlist function. So we ask ourselves, "What's the path to this
function?" It's like trying to find a hidden treasure in a maze. But fear not,
my friends! We can use paths to guide us.

Now, in Listing 7-3, we're going to show you two ways to call the
add_to_waitlist function. It's like taking different routes to reach the same
destination. We can use an absolute path, starting from the crate root, or a
relative path, starting from the current module. It's like saying, "Hey, Rust,
here's where you'll find that function!"

But wait, there's a catch. There's always a catch, right? Even though the paths
are correct, there's another problem that will prevent this example from
compiling. Oh, the suspense! Don't worry, folks, we'll explain that in just a
bit. So hold on tight, because we're about to dive into the depths of this
coding mystery!

Alright, let's try to make sense of this code mess. We've got a function
called eat_at_restaurant, and it's part of our library crate's public API. So,
we mark it with the "pub" keyword, meaning it's like a big billboard saying,
"Hey, everyone, come and use this function!"

Filename: src/lib.rs

```rust
mod front_of_house {
    mod hosting {
        fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    // Absolute path
    crate::front_of_house::hosting::add_to_waitlist();

    // Relative path
    front_of_house::hosting::add_to_waitlist();
}
```

Listing 7-3: Calling the add_to_waitlist function using absolute and relative paths

Now, in this wild journey, we encounter two ways to call the add_to_waitlist
function from inside eat_at_restaurant. And oh boy, they are quite different.

The first time, we use an absolute path. It's like we're giving the full address
to the function, starting from the crate root. We use the keyword "crate" to
tell Rust, "Hey, buddy, this function is just a few steps away from the crate
root!" And then, we follow the breadcrumbs, moving from one module to another,
until we reach our destination: add_to_waitlist.

The second time, we take a different approach. We use a relative path. It's like
saying, "Hey, Rust, I'm right here in the front_of_house module. Now, the
function I'm looking for is in the hosting module, just a few steps ahead!" We
don't need the full address this time; we start from where we are and find our
way to add_to_waitlist.

Imagine it's like navigating a busy city. The first time, we use the GPS
coordinates to find our friend's house across town. But the second time, we
start from our current location, which is already in the front_of_house
neighborhood, and we walk to the hosting module to find that elusive
add_to_waitlist function. 

Now, when it comes to choosing between a relative or absolute path, it's like
deciding whether to take a left turn or go straight ahead. It all depends on how
you plan to organize your code and whether you're more likely to move things
separately or together.

Let's dive into some scenarios to make things clearer. Imagine we decide to move
the front_of_house module and the eat_at_restaurant function into a module
called customer_experience. If we go with the absolute path, we'll need to
update the path to the add_to_waitlist function, because now it's nestled deeper
in the module tree. But guess what? The relative path will still work like a
charm, no need to touch it!

On the other hand, let's say we go rogue and move the eat_at_restaurant function
alone into a module called dining. In this case, if we chose the absolute path,
we're golden! The path to the add_to_waitlist call remains intact, pointing to
the same spot as before. But hold on, the relative path won't be so forgiving.
We'd have to update it to match the new module structure.

So, my friends, it's a matter of preference and planning. In general, it's often
wiser to go with absolute paths because they give you more flexibility. You can
move code definitions and item calls independently, like two free birds flying
in the code sky. But hey, it's your call, and you get to navigate the winding
paths of Rust as you see fit!


```rust

$ cargo build
   Compiling restaurant v0.1.0 (file:///projects/restaurant)
error[E0603]: module `hosting` is private
 --> src/lib.rs:9:28
  |
9 |     crate::front_of_house::hosting::add_to_waitlist();
  |                            ^^^^^^^ private module
  |
note: the module `hosting` is defined here
 --> src/lib.rs:2:5
  |
2 |     mod hosting {
  |     ^^^^^^^^^^^

error[E0603]: module `hosting` is private
  --> src/lib.rs:12:21
   |
12 |     front_of_house::hosting::add_to_waitlist();
   |                     ^^^^^^^ private module
   |
note: the module `hosting` is defined here
  --> src/lib.rs:2:5
   |
2  |     mod hosting {
   |     ^^^^^^^^^^^

```
For more information about this error, try `rustc --explain E0603`.
error: could not compile `restaurant` due to 2 previous errors

Listing 7-4: Compiler errors from building the code in Listing 7-3

So, we try to compile this code, and guess what? It's a compilation party with a
side of errors! Let's take a look at the errors and see what Rust has to say
about it.

The first error says, "Hey, buddy, module 'hosting' is private." It's like
trying to crash a private party where only a select few are allowed. Rust is
telling us that the hosting module is not accessible from outside its own
module. It's like the VIP section of the club, and we don't have the right pass
to get in.

The second error repeats the same message: "Module 'hosting' is private." It's
like Rust is saying, "Dude, didn't you hear me the first time? This module is
off-limits!" It points us back to where the module is defined, just to make sure
we're aware of our mistake.

Well, folks, it looks like we have a privacy issue here. The hosting module is
private, and we're trying to access it from outside. It's like trying to peek
through a closed door without an invitation. Sneaky, but not gonna work.

But hey, let's not lose hope! We'll dig into this privacy thing and learn about
the magic keyword called "pub" in the next section. Maybe then we can crash the
party in style.

    Exposing Paths with the pub Keyword

So, we tried to fix the issue by marking the hosting module as "pub" to make it
accessible from the eat_at_restaurant function. It's like putting up a big neon
sign saying, "Hey, everyone, this module is open for business!" But guess what?
The code still won't compile, and the error messages are back to haunt us.

The compiler is throwing a fit and telling us that the add_to_waitlist function
is private. It's like trying to sneak into a private party through the back door
and getting caught by security. The function is locked away, hidden from prying
eyes, and the compiler won't let us touch it.

But wait, didn't we mark the hosting module as "pub"? Shouldn't that give us
access to all its goodies? Well, not quite. You see, the hosting module may be
open for business, but some of its functions are still hiding in the shadows.
It's like having a VIP section in a club where only a select few can enter. The
add_to_waitlist function is one of those VIPs, and we don't have the right pass
to get in.

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    // Absolute path
    crate::front_of_house::hosting::add_to_waitlist();

    // Relative path
    front_of_house::hosting::add_to_waitlist();
}
```

Listing 7-5: Declaring the hosting module as pub to use it from
eat_at_restaurant


Unfortunately, the code in Listing 7-5 still results in an error, as shown in
Listing 7-6.

```rust

$ cargo build
   Compiling restaurant v0.1.0 (file:///projects/restaurant)
error[E0603]: function `add_to_waitlist` is private
 --> src/lib.rs:9:37
  |
9 |     crate::front_of_house::hosting::add_to_waitlist();
  |                                     ^^^^^^^^^^^^^^^ private function
  |
note: the function `add_to_waitlist` is defined here
 --> src/lib.rs:3:9
  |
3 |         fn add_to_waitlist() {}
  |         ^^^^^^^^^^^^^^^^^^^^

error[E0603]: function `add_to_waitlist` is private
  --> src/lib.rs:12:30
   |
12 |     front_of_house::hosting::add_to_waitlist();
   |                              ^^^^^^^^^^^^^^^ private function
   |
note: the function `add_to_waitlist` is defined here
  --> src/lib.rs:3:9
   |
3  |         fn add_to_waitlist() {}
   |         ^^^^^^^^^^^^^^^^^^^^
```

For more information about this error, try `rustc --explain E0603`.
error: could not compile `restaurant` due to 2 previous errors

Listing 7-6: Compiler errors from building the code in Listing 7-5

You see, when you make a module public with pub, it means that its parent
modules can now see it. It's like opening a window between them. But it doesn't
mean you automatically get access to all the goodies inside. The contents of the
module are still hidden, locked away from prying eyes. It's like having a
transparent safe, but the combination is a secret.

And that's where the problem lies. The add_to_waitlist function is still
private. So, even though we made the hosting module visible, the
function is like a shy turtle hiding in its shell. The privacy rules apply to
everything inside a module, whether it's a struct, an enum, a function, or a
method. They're all playing hard to get.

If you want to expose those inner treasures to the world, you'll have to use the
pub keyword once again. Make the add_to_waitlist function public, and now it's
like unlocking the safe and showing off its sparkling contents. But remember,
once you make something public, it's out there for everyone to see. So be
careful with what you choose to reveal.

Rust wants you to be deliberate about your privacy choices. It's like those
fancy clubs where only the chosen ones can enter the VIP section. You can open
the doors, but you still have control over who gets to enjoy the party inside.
So, mark your modules and items with pub strategically, and let the right ones
in.

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    // Absolute path
    crate::front_of_house::hosting::add_to_waitlist();

    // Relative path
    front_of_house::hosting::add_to_waitlist();
}
```

Listing 7-7: Adding the pub keyword to mod hosting and fn add_to_waitlist lets
us call the function from eat_at_restaurant

Alright, so we played the game of "pub" some more, and this time, we made the
add_to_waitlist function public too! It's like unlocking multiple doors to get
into the VIP section of a club. Now we can finally use those paths in
add_to_waitlist without Rust throwing a fit.

Let's break it down. In the absolute path, we start at the very top, the crate
root. The front_of_house module is sitting there, not shouting to the world, but
we can still see it because eat_at_restaurant and front_of_house are like
siblings, hanging out together in the same module. Now, the hosting module is
marked with pub, which means it's like putting a big neon sign that says "Hey,
you can come in!" So we enter, and there it is, the add_to_waitlist function,
also waving its hands, saying, "I'm public too, guys!" And that's why this
function call works like a charm.

Now, for the relative path, it's like we're starting from home base,
front_of_house. We know where it is because eat_at_restaurant and front_of_house
are buddies in the same module. So we confidently follow the path, and when we
hit the hosting module, it's like, "Yeah, come on in, I'm public now!" And we go
in, and there it is again, our friend, the add_to_waitlist function, waving,
saying, "You can call me from here too!" And guess what? This function call is
also good to go!

So, with the power of "pub," we've made everything accessible from where we need
it. It's like a well-organized club where the bouncers let you through the right
doors, and once you're inside, you can enjoy all the perks of the VIP area. Just
remember, with great power comes great responsibility. Don't go making
everything public just because you can. Keep your privacy intact and expose only
what's necessary. And that, my friends, is how we navigate the module tree like
pros!

So, you're planning to share your library crate with the world, huh? Well, let
me tell you, when you do that, your public API becomes your contract with all
those people who want to use your precious code. It's like a handshake, a mutual
agreement on how they can interact with your crate. And let me tell you,
managing changes to your public API is no joke. It's like maintaining a healthy
relationship with your users, making it easier for them to depend on your crate.

    Best Practices for Packages with a Binary and a Library

Now, if you're thinking of having both a binary crate and a library crate in
your package, let me give you some best practices. It's like having a double
act, where both the binary and the library crates work together to make your
package shine. The library crate is where you define the module tree in
src/lib.rs, and it's like the heart and soul of your code. This is where you
share all the juicy functionality with other projects.

But wait, there's more! The binary crate, is like the star of the
show. It's where you start your executable and call code from the library crate.
By starting paths with the name of the package, you can use all those public
items from the library crate in your binary crate. It's like being a user of
your own code, experiencing it from a different perspective. And let me tell
you, it helps you design a kick-ass API. You get to wear both the creator and
client hats!

Now, I must confess, we're just scratching the surface here. There's a whole
chapter, Chapter 12, dedicated to demonstrating this organizational practice
with a command-line program. So, if you're ready to dive deep and explore the
world of packages with both a binary and a library crate, buckle up and get
ready for an exciting ride!
    
Remember, your public API is like your reputation out there. So, make it solid,
make it reliable, and make it something that people can't resist. And with that,
my friend, you're on your way to conquering the Rust world with your amazing
code!

Starting Relative Paths with super

Alright, let's talk about starting relative paths with "super." It's
like constructing a path in Rust that begins in the parent module, rather than
the current module or the crate root. It's like saying, "Hey, I know this item
is in the parent module, so let me get it for you." It's just like starting a
filesystem path with the ".." syntax. You know, when you want to move up the
directory structure? Yeah, it's like that.

Now, using "super" comes in handy when you're rearranging your module tree.
Picture this: you have a chef who needs to fix an incorrect order and personally
brings it out to the customer. We have two functions here. First, we have
"fix_incorrect_order" defined in the "back_of_house" module. This chef knows
that the fix is in the parent module, so they call the "deliver_order" function
by specifying the path starting with "super." It's like saying, "Hey, I know
it's in the parent module, so let me grab it for you." It's like a direct line
to the right place.

Filename: src/lib.rs

```rust
fn deliver_order() {}

mod back_of_house {
    fn fix_incorrect_order() {
        cook_order();
        super::deliver_order();
    }

    fn cook_order() {}
}
```

Listing 7-8: Calling a function using a relative path starting with super

In this case, the "fix_incorrect_order" function is in the "back_of_house"
module. So, we use "super" to go up to the parent module, which happens to be
the crate root. From there, we find the "deliver_order" function and make the
magic happen. It's like a successful rescue mission! Now, we anticipate that the
"back_of_house" module and the "deliver_order" function will stick together,
even if we decide to rearrange the module tree. So, we use "super" to minimize
the code updates in the future. We're playing it smart, my friend.

So, there you have it. "Super" is your ticket to navigate the module tree with
ease. It's like having a secret passageway to the parent module, ensuring that
your code stays intact even when you decide to move things around. It's like a
little trick up your sleeve, ready to save the day.

Remember, my friend, in the world of Rust, knowing how to navigate the module
tree is like being the master of your own destiny. So, go ahead, use "super" and
conquer those module rearrangements like a boss!

    Making Structs and Enums Public

So, here's the deal when it comes to using "pub" with structs and enums in Rust.
It's a bit different than what we've seen before. When we use "pub" before a
struct definition, we make the struct itself public, but guess what? The fields
inside the struct will still be private. Yeah, it's like having a VIP section in
a club, but the fancy stuff inside is off-limits.

Let's take a look at Listing 7-9. We have a module called "back_of_house" where
we define a struct called "Breakfast." Now, this Breakfast struct is public, but
hold on, the fields inside it, like "seasonal_fruit," are still private. It's
like having a restaurant where the customer gets to choose the type of bread
that comes with the meal, but the chef decides the fruit based on what's in
season and in stock. You can't mess with the fruit selection, my friend. It
changes too quickly!

Filename: src/lib.rs

```rust

mod back_of_house {
    pub struct Breakfast {
        pub toast: String,
        seasonal_fruit: String,
    }

    impl Breakfast {
        pub fn summer(toast: &str) -> Breakfast {
            Breakfast {
                toast: String::from(toast),
                seasonal_fruit: String::from("peaches"),
            }
        }
    }
}

pub fn eat_at_restaurant() {
    // Order a breakfast in the summer with Rye toast
    let mut meal = back_of_house::Breakfast::summer("Rye");
    // Change our mind about what bread we'd like
    meal.toast = String::from("Wheat");
    println!("I'd like {} toast please", meal.toast);

    // The next line won't compile if we uncomment it; we're not allowed
    // to see or modify the seasonal fruit that comes with the meal
    // meal.seasonal_fruit = String::from("blueberries");
}
```

Listing 7-9: A struct with some public fields and some private fields

In this example, we have a public field called "toast" in the Breakfast struct.
In the "eat_at_restaurant" function, we can write and read the toast field using
dot notation. It's like customizing your order to your heart's content. But
wait, we can't touch the seasonal_fruit field! It's off-limits because it's
private. If you try to modify the seasonal_fruit field in the code by
uncommenting that line, you'll see an error staring right back at you. Yeah,
Rust won't let you mess with the chef's fruit selection. It's their secret
recipe.

Now, pay attention because this is important. Since the Breakfast struct has a
private field, Rust requires us to provide a public associated function that
constructs an instance of Breakfast. In this case, we have the "summer"
function. It's like the chef saying, "Hey, I'll handle the fruit selection, but
you can choose the toast flavor." If the Breakfast struct didn't have such a
function, we wouldn't be able to create an instance of Breakfast in the
"eat_at_restaurant" function. Yeah, it's like being denied access to a secret
menu item. You just can't have it.

So, when it comes to structs and enums, "pub" gives you control over
what's public and what's private. You can flaunt the struct itself, but keep
those private fields hidden away. It's like having a tantalizing secret that
only the chef knows. Just remember, don't mess with the chef's fruit selection.
It's their domain.

Now go ahead, play around with structs, choose your toast flavor, but always
remember to respect the chef's boundaries. Enjoy your meal in the world of Rust!

When it comes to making enums public in Rust, things are a bit different. If we
slap a "pub" before the enum keyword, all of its variants become public. Yeah,
it's like throwing a grand opening party and inviting everyone in. Open to the
public, baby!

Filename: src/lib.rs

```rust

mod back_of_house {
    pub enum Appetizer {
        Soup,
        Salad,
    }
}

pub fn eat_at_restaurant() {
    let order1 = back_of_house::Appetizer::Soup;
    let order2 = back_of_house::Appetizer::Salad;
}
```

Listing 7-10: Designating an enum as public makes all its variants public

Take a look at Listing 7-10. We have a module called "back_of_house" where we
define an enum called "Appetizer." Now, here's the deal: since we made the
Appetizer enum public by using "pub," all of its variants, like Soup and Salad,
are now open for business. It's like having a menu with all the delicious
options available to you.

In the "eat_at_restaurant" function, we can create orders using the Appetizer
enum. We've got order1 as Soup and order2 as Salad. It's like placing your order
and eagerly waiting for your appetizer to arrive. Enum variants are pretty
handy, and in this case, they're public by default. You don't have to do any
extra work to make them accessible. Rust knows you want to show off those
variants to the world.

Enums without public variants wouldn't be that useful, right? It would be a pain
to annotate each variant with "pub" every single time. So, the default behavior
for enum variants is to be public. It's like having an open-door policy. Come on
in, variants!

Now, here's a little contrast for you. Structs work a bit differently. They can
be useful even if their fields are private. So, by default, struct fields are
private unless you specifically annotate them with "pub." It's like having your
own personal space and keeping things private, unless you decide to invite
someone in.

So, to sum it up: enums love being public, especially their variants, while
structs prefer their privacy by default, unless you explicitly give them
permission to go public. It's like different personalities playing out in the
Rust module system.

But hold on, there's one more thing we need to cover: the "use" keyword. It's
like the cherry on top of our Rust module system sundae.
