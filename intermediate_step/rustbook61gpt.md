    Defining an Enum

Alright, let's dive into the fascinating world of enums! You see,
while structs are great for grouping related fields and data, enums take things
to a whole new level. They allow us to define values that belong to a specific
set of possibilities. It's like saying, "Hey, this value can be one of these
options, and that's it!"

Let's paint a picture here. Imagine we're dealing with IP addresses. Now, there
are two major standards for IP addresses: version four and version six. And you
know what? Enums are perfect for capturing these possibilities. We can create an
enum that represents all the different types of IP addresses we might encounter.

Here's the beauty of it: an IP address can be either version four or version
six, but never both at the same time. That's the nature of things.
And that's exactly why enums shine in this scenario. An enum value can only be
one of its variants, making it the perfect fit for representing these distinct
types of IP addresses.

But here's the kicker: even though version four and version six addresses are
different, they're still fundamentally IP addresses. And that's where enums
truly excel. They allow us to treat all these variants as the same type when our
code is handling situations that apply to any kind of IP address.

Let's get down to business and define our custom data type for
IP address kinds. We're going to create an enum called IpAddrKind. This enum is
going to represent the different flavors of IP addresses that we can encounter.
And boy, we've got two tasty options on the menu: V4 and V6.

So, our enum looks like this:

```rust
enum IpAddrKind { V4, V6, }
```

Now, IpAddrKind is a brand new type that we can use throughout our code. It's
like creating our very own data category, exclusively for IP address kinds. This
allows us to be more precise and expressive when working with IP addresses. No
more guessing games or vague representations. We've got our enum to keep things
nice and organized.

Now that we've got our IpAddrKind enum all set up,
it's time to play with some enum values. We can create instances of each variant
by using the enum's identifier, followed by a double colon and the variant name.
It's like giving birth to these little enum babies.

Check it out:

```rust
let four = IpAddrKind::V4; 
let six = IpAddrKind::V6;
```

We've got two IP address kinds right here: V4 and V6. They're all snuggled up
under the IpAddrKind namespace, just waiting for us to use them.

But here's the cool part: both V4 and V6 are of the same type, IpAddrKind. That
means we can pass them around, store them in variables, and even use them as
function arguments.

For example, let's say we have this function called route that takes an
IpAddrKind as its parameter. 

```rust
fn route(ip_kind: IpAddrKind) {}
```

We can call this function with either V4 or V6:

```rust
route(IpAddrKind::V4); 
route(IpAddrKind::V6);
```

It's like ordering a pizza with your choice of toppings. You can go for the V4
flavor or spice things up with some V6 goodness. Either way, the route function
knows how to handle both variants because they're all part of the IpAddrKind
family.

So go ahead and have fun with your enum values. Use them to create powerful,
flexible code that can handle different scenarios. Embrace the beauty of Rust's
enums and let your imagination run wild. 

You know, sometimes it's tempting to go with the old familiar approach, like
using structs to solve a problem. But let me tell you, enums have
more tricks up their sleeves. Let's take a look at a scenario where we want to
store both the IP address kind and the actual address data.

In the old way, we had the IpAddrKind enum with its V4 and V6 variants. And now,
to store the data and associate it with the variant, we introduce a struct
called IpAddr. This struct has two fields: kind, which is of type IpAddrKind
(the enum we defined earlier), and address, which is a String.

Just look at this code snippet:

```rust
enum IpAddrKind {
    V4,
    V6,
}

struct IpAddr {
    kind: IpAddrKind,
    address: String,
}

let home = IpAddr {
    kind: IpAddrKind::V4,
    address: String::from("127.0.0.1"),
};

let loopback = IpAddr {
    kind: IpAddrKind::V6,
    address: String::from("::1"),
};
```

IpAddrKind, with two variants: V4 and V6. It's all about representing the kind
of IP address we're dealing with. But hey, the enum alone ain't enough to store
the actual IP address data. We're missing the juicy details!

We create instances of our struct: home and loopback. Home represents an IPv4
address with the kind set to V4 and the address as "127.0.0.1". Loopback, on the
other hand, is an IPv6 address with the kind set to V6 and the address as "::1".
We bundle the kind and address values together using the struct, making sure
each variant is associated with its own data.

Now, here's the thing. While structs are great for grouping related data,
using enums in this case gives us an even more powerful way to express the
concept of IP addresses. With enums, we have variants that can carry their own
associated values directly. It's like having a complete package with the variant
and its associated data all in one.


Check out this new definition of the IpAddr enum. It's slim, it's sleek, and
it's got data directly attached to each variant:

```rust
enum IpAddr {
    V4(String),
    V6(String),
}
```

With this setup, we can create instances of our enum variants and give them
juicy String values. It's like adding toppings to your favorite pizza. Each
variant gets its own String goodness.

For example, we can have our home IP address as V4 with the value "127.0.0.1":

```rust
    enum IpAddr {
        V4(u8, u8, u8, u8),
        V6(String),
    }

    let home = IpAddr::V4(127, 0, 0, 1);

    let loopback = IpAddr::V6(String::from("::1"));
```

And how about that loopback IP address? We can represent it as V6 with the value
"::1".

It's like we're constructing these enum instances using special function calls.
IpAddr::V4() and IpAddr::V6() become these magical constructors that take a
String argument and give us an instance of the IpAddr type. It's like ordering a
custom-made pizza right from the enum factory.

So, embrace the elegance of this enum setup. Say goodbye to the extra struct and
enjoy the simplicity and convenience of attaching data directly to each variant.
Rust does all the heavy lifting for us, providing those handy constructor
functions automatically.

Here's another advantage of using enums over structs: they give you the
flexibility to have different types and amounts of associated data for each
variant. It's like having a toolbox full of different tools for different jobs.
Let me explain.

Let's say we want to represent IP addresses again, but this time we want to
handle version four addresses as four u8 values, and version six addresses as a
single String value. This is where enums shine and structs stumble.

Take a look at this beautiful enum definition:

```rust
    enum IpAddr {
        V4(u8, u8, u8, u8),
        V6(String),
    }

    let home = IpAddr::V4(127, 0, 0, 1);

    let loopback = IpAddr::V6(String::from("::1"));
```

With this setup, we can create instances of our enum variants using different
types and amounts of data. It's like having a Swiss Army knife that can handle
any kind of IP address.

For example, we can have our home IP address as V4 with the values 127, 0, 0, 1 .
And the loopback address? We can represent it as V6 with the value "::1" wrapped
in a cozy String:

With enums, you can handle different types and amounts of associated data
effortlessly. Say goodbye to the constraints of structs and embrace the
versatility of enums.

So, turns out, we don't have to reinvent the wheel when it comes to storing IP
addresses in Rust. The smart folks behind the standard library have already
thought about it and provided us with a nifty definition for IpAddr. Let's take
a peek at their implementation and see what they've done.

In their version, they use two different structs to encapsulate the address data
for each IP version. We have Ipv4Addr for version four and Ipv6Addr for version
six. These structs probably have some cool stuff inside, but I'll just leave
that to your imagination. Trust me, they're snazzy.

Then, they take these structs and embed them nicely inside the enum variant
definitions. Voilà! We have the same enum structure we've been playing with, but
with a touch of elegance from the standard library.

Here's how it looks:

```rust
struct Ipv4Addr { // --snip-- }

struct Ipv6Addr { // --snip-- }

enum IpAddr { V4(Ipv4Addr), V6(Ipv6Addr), }
```
You see, you can put anything inside an enum variant: strings, numbers, structs,
or even another enum. It's like having a nesting doll of data structures, each
one holding a little surprise inside. And hey, the standard library's types
aren't much fancier than what we've been playing with.

Now, here's an interesting tidbit: even though the standard library has its own
definition for IpAddr, we can still create and use our own definition without
any conflict. Why? Because we haven't brought the standard library's version
into our scope. We're free to do our own thing and experiment with our own
definitions. Rust gives us that freedom.

Alright, let's dive into another example of an enum. Get ready for a wild
ride because this one's got a smorgasbord of types embedded in its variants.
It's like a buffet of data!

Check out this enum called Message, listed as 6-2. It's got four variants, and
each one is a unique flavor:

```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}
```

So you see, this enum is a versatile beast. It can hold all sorts of data—empty
variants, named fields, strings, and even a trio of integers. It's like a
jack-of-all-trades, accommodating all your data needs.

First up, we have Quit. It's a variant that says "I don't need any data, I'm
good on my own." No strings attached, no fields to worry about. Just a simple
Quit. Hey, sometimes you just gotta say, "I'm out!"

Then we have Move. Now, this variant is fancy. It has named fields,
just like a struct. It's like the enum version of a well-organized move. It
knows exactly where it's going with its x and y coordinates. Smooth moves, my
friends.

Next in line is Write. This variant comes with a special gift—a single
String. It's like someone handing you a note, but instead of paper, it's
wrapped in a variant of an enum. How poetic.

Last but not least, we have ChangeColor. This variant brings a burst of
color to the party with not one, not two, but three i32 values. It's like a
triple threat of integers, ready to paint the town with its RGB magic.


You know, defining enums is kind of like defining different kinds of structs,
but without all the fancy "struct" keywords cluttering up your code. It's like
cutting through the noise and getting straight to the point.

Check out these structs that could hold the same data as the enum variants we
saw earlier:

```rust
struct QuitMessage; // unit struct
struct MoveMessage {
    x: i32,
    y: i32,
}
struct WriteMessage(String); // tuple struct
struct ChangeColorMessage(i32, i32, i32); // tuple struct
```
But you know what? If we used these different structs, each one would have its
own type, making things a bit messy. It's like having a bunch of unique
snowflakes, and you have to handle each one differently.

That's where enums come in handy again! With enums, you can group all these
variants together under one single type. It's like having a neat little package
that can hold different kinds of messages. So, you can define a function that
takes any of these message types without breaking a sweat.

You know, enums and structs have more in common than you might think. Just like
we can define methods on structs using "impl," we can do the same with enums.
It's like giving your enum a little extra power!

Check out this method named "call" that we can define on our Message enum:

```rust
impl Message { 
    fn call(&self) { 
        // We'd put the method's body here, you know, the code that does stuff
        } 
    }
let m = Message::Write(String::from("hello"));
m.call();

```
Now, what does this method do? Well, it uses "self" to get the value that we
called the method on. So, if we have a variable like "m" with the value
Message::Write(String::from("hello")), when we call "m.call()", "self" will
refer to that value inside the method body.

It's all about having that extra flexibility and convenience. You can define
methods that work with your enum values and do whatever you need them to do.
It's like adding a personal touch to your enums, making them more versatile and
useful.

But wait, there's more! Let's talk about another popular and handy enum in the
standard library: Option. It's a real game-changer. It's like a superhero,
swooping in to save us from the clutches of null values. You see, Option is all
about handling scenarios where a value could be something or could be nothing at
all.

Imagine you have a list, and you want to grab the first item. If the list is not
empty, you'll get a value. But if it's empty, you'll get... well, nothing.
Option steps in and says, "Hey, let's handle this situation in a type-safe way."
By using Option, the compiler can check if you've dealt with all the possible
cases, which helps prevent those pesky bugs that plague other languages.

Now, let's talk about null. Null is like a wildcard, a value that means there's
no value. Many languages have it, but Rust? Nah, Rust doesn't play that game.
It's a language that knows the importance of excluding certain features. And let
me tell you, null has caused quite a mess in the programming world.

In fact, Tony Hoare, the genius behind null, called it his billion-dollar
mistake. He wanted to create a type system that ensured safety and caught errors
before they wreaked havoc. But he couldn't resist the temptation of adding null
because, hey, it was easy to implement. Little did he know that null would
unleash an army of errors, vulnerabilities, and system crashes, causing a
mind-boggling amount of pain and damage. Oops!

But fear not! Rust takes a different approach. With Option, we can
handle the absence of a value in a much safer and more controlled manner. It's
like having a guardian angel watching over our code, keeping it robust and
error-free.


Alright, let's tackle the notorious null values once again. The problem with
null is that it's like a landmine waiting to explode. If you mistakenly treat a
null value as a not-null value, boom! You get an error that throws your whole
program off track. It's a mess, my friends, a mess!

But here's the thing: the concept behind null isn't all bad. It's trying to tell
us that a value is currently invalid or missing for some reason. It's like
saying, "Hey, I don't have a valid value to offer right now."

The real problem lies in how null is implemented. That's where Rust steps in and
says, "Hold on a second, let's do this differently." Rust doesn't have null, but
it has something even better: Option<T>. It's like a cool kid on the block,
ready to handle the presence or absence of a value in a safe and elegant way.

So, what is Option<T>? Well, it's an enum, my friends. A fancy enum defined by
the standard library. It goes like this:

```rust
enum Option<T> { None, Some(T), }
```

See, it's simple yet powerful. Option<T> gives you the flexibility to express
whether a value is present or absent. It's like having two friends: None and
Some(T). None represents the absence of a value, while Some(T) wraps around the
actual value you're looking for.

Now, here's the cool part: Option<T> is so darn useful that it's already
included in the prelude. You don't even have to bring it into scope explicitly.
It's like Rust saying, "Hey, I got you covered, buddy." And you can directly use
Some and None without any fancy Option:: prefix. It's all right there, ready to
make your coding life easier.

So, let's bid adieu to the treacherous null and embrace Option<T>. Rust has your
back, protecting you from those null-related mishaps. It's a game-changer, a
real game-changer.

Alright, let's talk about this funky <T> thing in Rust. It's like a secret code
that we haven't cracked yet, but don't worry, we'll get there. So, <T> is
actually a generic type parameter, my friends. It's like a wild card that can
represent any type you want. We'll dive deeper into generics later on, but for
now, just know that <T> means we can have different flavors of Option<T>,
depending on the type we use.

Let me give you some examples to make things clearer. We can use Option to hold
numbers or characters. Check this out:

```rust
let some_number = Some(5); 
let some_char = Some('e');

let absent_number: Option<i32> = None;
```
See, we've got some_number with a value of 5, and some_char with a value of 'e'.
But here's the cool part: the type of some_number is Option<i32>, while the type
of some_char is Option<char>. They might look similar, but they're actually
different types, my friends. Rust is smart enough to figure out these types
because we provided a value inside the Some variant.

Now, let's talk about the absent_number. It's a bit trickier. Since it's empty,
Rust needs a little help to figure out the type. So, we annotate it explicitly.

By saying Option<i32>, we're telling Rust that this absent_number is an Option
that should hold an i32 type. It's like giving the compiler a nudge in the right
direction.

So, in a nutshell, <T> is a powerful tool that allows us to create different
flavors of Option. It's like having a menu with endless possibilities. We'll
explore more about these generic types in Chapter 10. But for now,
let's embrace the flexibility of Option<T> and keep our code clean and
error-free.

Alright, let's tackle the question: Why is Option<T> better than good ol' null?

Here's the deal. With Option<T>, we have a whole new level of safety. The thing
is, Option<T> and T are not the same types. And that's a good thing! The
compiler won't let us use an Option<T> value as if it's a surefire valid value.
Let me show you an example:

```rust

let x: i8 = 5; 
let y: Option<i8> = Some(5);
let sum = x + y;

```
Now, this code won't even compile. Why? Because it's trying to add an i8 and an
Option<i8>. It's like mixing apples and oranges, my friends. Rust is like, "Hold
on a second, I can't just magically combine these different types for you."

```rust
$ cargo run Compiling enums v0.1.0 (file:///projects/enums) error[E0277]: cannot
   add `Option<i8>` to `i8` --> src/main.rs:5:17 | 5 | let sum = x + y; | ^ no
   implementation for `i8 + Option<i8>` | = help: the trait `Add<Option<i8>>` is
   not implemented for `i8` = help: the following other types implement trait
   `Add<Rhs>`: <&'a i8 as Add<i8>> <&i8 as Add<&i8>> <i8 as Add<&i8>> <i8 as
   Add>

For more information about this error, try `rustc --explain E0277`. error: could
not compile `enums` due to previous error
```

When we have a value of a certain type, like i8, Rust ensures that we always
have a valid value. We can trust that we're working with the real deal. But when
we're dealing with Option<i8> or any other Option<T>, we have to be cautious
because there might not be a value at all. Rust wants us to handle that
possibility before we do anything crazy with the value.

So, Option<T> gives us a safety net. It forces us to think about the
potential absence of a value and handle it gracefully. No more null-related
mishaps and unexpected crashes. Rust has got our back.

With Option<T>, we can navigate the treacherous world of missing values with
confidence. The compiler will keep us in check and ensure that we handle all the
cases, my friends. It's like having a responsible friend who always reminds you
to double-check before making a move. And trust me, that's a friend you want to
have.

Let's talk about converting an Option<T> to a T. This is where the real magic
happens. See, by doing this conversion, we eliminate the risk of assuming
something isn't null when it actually is. And let me tell you, that's a
game-changer.

In Rust, if you want a value that can be null, you gotta be upfront about it.
You gotta opt in. How? By making the type of that value Option<T>. By slapping
that Option<T> label on it, you're saying, "Hey, this value might be null, and I
wanna be responsible about it."

Now, when you use that value, Rust won't let you take any chances. You're
required to explicitly handle the case when the value is null. No more assuming
things, my friends. You gotta face the truth head-on.

And here's the cool part: everywhere you see a value that's not an Option<T>,
you can rest assured that it's not null. It's like a guarantee. Rust
is all about limiting null's power and keeping us safe. It's like having a
superhero by your side, protecting you from the evils of null-related mishaps.

But wait, how do we actually get the T value out of a Some variant? Well, the
Option<T> enum has got your back with a bunch of useful methods. Check out the
documentation, get familiar with them, and they'll be your trusty sidekicks in
your Rust journey.

Now, when it comes to using an Option<T> value, you gotta handle each variant.
You want code that runs only when you have a Some(T) value, so you can access
that sweet inner T. And you want some other code to handle the None case, where
there's no T value available. It's like a dance. And the match
expression is your partner. It's your way of saying, "Hey, let's do this
together," and it runs different code based on the variant it has. It's all
about control flow.

So remember, in Rust, handling Option<T> is the name of the game. It's about
being responsible, confident, and in control. It's like leveling up your
programming skills, one match expression at a time. And let me tell you, that's
a beautiful thing.
