    Storing UTF-8 Encoded Text with Strings

Alright, folks, let's dive deep into the world of strings in Rust. Brace
yourselves because this topic has tripped up many new Rustaceans. It's like
navigating a minefield of possible errors, complicated data structures, and the
notorious UTF-8. Trust me, strings in Rust are not your run-of-the-mill data
types. Now, in Rust, we talk about strings within the context of collections.
You see, strings are not just plain old characters. Oh no, they are implemented
as a collection of bytes with some fancy methods to handle all that text
interpretation stuff. It's like a whole ecosystem of functionality built around
those bytes. In this section, we're going to explore the operations on String
that you'd find in any collection type. We're talking about creating strings,
updating them, and reading from them. These are the bread and butter of any
collection, my friends. But here's the twist: String is not like the other
collections. It's a rebel, marching to the beat of its own drum. One of the
things that sets String apart is the complexity of indexing. You see, indexing
into a String is no walk in the park. It's complicated by the differences
between how us humans interpret text and how those computers do it. It's like
trying to bridge the gap between two different worlds, and let me tell you, it
can be a bumpy ride. So buckle up, my friends, because we're about to unravel
the mysteries of strings in Rust. Embrace the challenges, embrace the
complexities, and don't be afraid to ask for help. Together, we'll navigate this
intricate terrain and conquer the world of strings. Let's get coding!

    What Is a String?

Alright, let's talk about strings. In Rust, we have this thing called a string
slice. It's like a fancy reference to some UTF-8 encoded string data that's
stored somewhere else. You know, those string literals you see in your code?
They're actually string slices, just hanging out in the program's binary.

But wait, there's more! We also have the String type, courtesy of Rust's
standard library. This bad boy is a growable, mutable, owned, UTF-8 encoded
string type. It's like the king of strings, ready to conquer any text
manipulation task you throw at it. When we talk about "strings" in Rust, we
could be referring to either the String type or the string slice &str. Both of
them are important players in Rust's standard library, and both of them are
UTF-8 encoded.

So remember, when we talk about strings in Rust, we're not just talking about
one type. It's like a dynamic duo, with String and &str working together to
handle all your string-related needs. And now, let's dive deeper into the
wonderful world of String!

    Creating a New String

So, we've got this String type in Rust, and it's pretty cool. It's like a
wrapper around a vector of bytes, but with some extra bells and whistles. You
can do a lot of the same operations with String as you can with Vec<T>. It's
like Vec<T>'s fancy cousin.

Now, let's talk about creating a new String. Just like with Vec<T>, we can start
with an empty one. Check out this line of code in Listing 8-11:

```rust
    let mut s = String::new();
```

Listing 8-11: Creating a new, empty String

Boom! We've got ourselves a brand new empty String called 's'. It's ready to be
filled with all sorts of glorious text.

But what if we already have some initial data that we want to put into our
String? Well, fear not, my friend, because we've got the to_string method to the
rescue. It's like a magical incantation that can transform any type that
implements the Display trait into a String. Look at Listing 8-12 for some
examples.

```rust

    let data = "initial contents";

    let s = data.to_string();

    // the method also works on a literal directly:
    let s = "initial contents".to_string();
```
Listing 8-12: Using the to_string method to create a String from a string
literal

It's like a little trick that turns your data into a shiny new String. How neat
is that? So go ahead, create your Strings and fill them with all the text you
desire.

So, we've got another way to create a String in Rust. It's called String::from,
and it's pretty handy. Take a look at Listing 8-13:

```rust
    let s = String::from("initial contents");
```

Listing 8-13: Using the String::from function to create a String from a string
literal

Boom! Just like that, we've got ourselves a String with "initial contents" in
it. It's a quick and easy way to get a String from a string literal.

Now, here's the thing. Strings are used for all sorts of stuff, so Rust gives us
a bunch of different ways to work with them. It can seem a bit overwhelming at
times, but trust me, they all have their place.

In this case, both String::from and to_string do the same thing. They both
create a String from a string literal. So which one should you use? Well, it's
really up to you. It's a matter of style and readability. Pick the one that
feels right to you.

```rust

    let hello = String::from("السلام عليكم");
    let hello = String::from("Dobrý den");
    let hello = String::from("Hello");
    let hello = String::from("שָׁלוֹם");
    let hello = String::from("नमस्ते");
    let hello = String::from("こんにちは");
    let hello = String::from("안녕하세요");
    let hello = String::from("你好");
    let hello = String::from("Olá");
    let hello = String::from("Здравствуйте");
    let hello = String::from("Hola");
```

Listing 8-14: Storing greetings in different languages in strings

Oh, and remember that strings in Rust are UTF-8 encoded. That means you can
store any properly encoded data in them. Just look at Listing 8-14. We've got
greetings in different languages stored in strings. How cool is that?

So go ahead, create your Strings and fill them with all sorts of words, phrases,
and greetings from around the world.

    Updating a String

A String can grow in size and its contents can change, just like the contents of
a Vec<T>, if you push more data into it. In addition, you can conveniently use
the + operator or the format! macro to concatenate String values.

    Appending to a String with push_str and push

Alright, so we can update a String just like we can update a Vec<T>. We can make
it grow and change its contents. It's pretty flexible, just like life itself.

To append a string slice to a String, we can use the push_str method. Take a
look at Listing 8-15:

```rust
    let mut s = String::from("foo");
    s.push_str("bar");
```

Listing 8-15: Appending a string slice to a String using the push_str method

Boom! After these two lines, our String s will contain "foobar". It's like we're
building words, one slice at a time.

Now, here's the thing. The push_str method takes a string slice because it
doesn't necessarily want to take ownership of the parameter. It just wants a
little taste, you know? It wants to add the slice to the end of the String
without owning it.

Let's take a look at Listing 8-16 to see how this works:

```rust
    let mut s1 = String::from("foo");
    let s2 = "bar";
    s1.push_str(s2);
    println!("s2 is {s2}");
```
Listing 8-16: Using a string slice after appending its contents to a String

In this code, we can still use s2 after appending its contents to s1. If the
push_str method took ownership of s2, we wouldn't be able to print its value on
the last line. But here, everything works just fine.

It's all about finding that balance, you know? Giving a little, taking a little,
and making sure everyone's happy in the end. That's the beauty of Rust's String.

Alright, here's a little trick for you. If you want to add just a single
character to a String, you can use the push method. It's like adding a tiny
piece to complete the puzzle.

Check out Listing 8-17:

```rust
    let mut s = String::from("lo");
    s.push('l');
```
Listing 8-17: Adding one character to a String value using push

And voila! After these lines, our String s will contain "lol". It's like we're
laughing out loud, one character at a time.

You see, the push method takes a single character as its parameter. It's like
giving a little nudge to the String, saying, "Hey, buddy, here's another letter
for you."

So next time you need to add just a single character to a String, remember this
little trick. It's a simple and efficient way to build up your string, one
character at a time.

    Concatenation with the + Operator or the format! Macro

Often, you’ll want to combine two existing strings. One way to do so is to use
the + operator, as shown in Listing 8-18.

```rust
    let s1 = String::from("Hello, ");
    let s2 = String::from("world!");
    let s3 = s1 + &s2; // note s1 has been moved here and can no longer be used
```
Listing 8-18: Using the + operator to combine two String values into a new
String value

After these lines, s3 will contain "Hello, world!". It's like putting two puzzle
pieces together to form a complete picture. But there's something interesting
going on here. The + operator actually calls a method called add, which takes
ownership of s1 and a reference to s2, and returns a new String. So, after using
the + operator, s1 is no longer valid and can't be used anymore.

```rust
fn add(self, s: &str) -> String {
```

Alright, let's dive into the nitty-gritty of the + operator and understand the
tricky bits. Brace yourselves!

So, in the standard library, the add method used by the + operator is actually
defined using generics and associated types. But don't worry, we'll save the
full explanation for Chapter 10. For now, let's focus on the concrete types
we've used in our example.

In Listing 8-18, we have s1 and s2, two String values that we want to combine.
But there's a twist. The add method expects a parameter of type &str, not
String. So, how does this work?

Here's the secret: the + operator is a master of coercion. It can magically
transform a &String into a &str. How? Well, it uses something called deref
coercion. When we pass &s2 as the second parameter to add, Rust cleverly turns
it into &s2[..]. It's like a magician revealing a hidden trick!

But wait, there's more! The add method takes ownership of the first parameter,
s1. This means that s1 is moved into the add call and can no longer be used
afterwards. It's like a disappearing act! So, even though it looks like we're
making copies and creating a new string, the implementation is actually more
efficient. It's like using sleight of hand to make the operation faster.

Now you understand the inner workings of the + operator and its relationship
with the add method. It's like unraveling a complex puzzle and discovering the
hidden mechanisms behind it. But don't worry, we'll cover generics and
associated types in more detail in Chapter 10. For now, let's move on and
explore more about strings.

Ah, the + operator can get quite messy when we need to concatenate multiple
strings. Just look at all those + and " characters cluttering up the code! It's
like trying to solve a puzzle with too many pieces.

```rust
    let s1 = String::from("tic");
    let s2 = String::from("tac");
    let s3 = String::from("toe");

    let s = s1 + "-" + &s2 + "-" + &s3;
```

But fear not! We have a solution: the format! macro. It's like a magical
incantation that simplifies string combining and makes everything clearer.

In the second code snippet, we use the format! macro to create a new string.
It's like a magician's trick, but instead of pulling a rabbit out of a hat, it
pulls out a nicely formatted string. We pass the format! macro a template string
with placeholders for the values we want to include. In this case, we use {s1},
{s2}, and {s3} as placeholders.

```rust
    let s1 = String::from("tic");
    let s2 = String::from("tac");
    let s3 = String::from("toe");

    let s = format!("{s1}-{s2}-{s3}");
```

When we run the format! macro, it generates a new string with the contents we
desire. It's like a smooth operation, resulting in a clean and readable code.

One cool thing about the format! macro is that it doesn't take ownership of its
parameters. It uses references, so s1, s2, and s3 are still valid and usable
after the macro call. It's like borrowing someone's car for a joyride without
actually taking it away from them.

So, if you find yourself in a string concatenation predicament, remember the
format! macro. It's like a clever shortcut that simplifies your code and makes
it shine.

    Indexing into Strings

You know, in other programming languages, you can easily grab a specific
character from a string by using indexing. It's like reaching into a bag of
letters and picking out the one you want. But in Rust, things are a bit
different. If you try to use indexing syntax with a String, you're in for a
surprise.

Check out this code in Listing 8-19. The poor soul is trying to get the first
character of the string, but it just won't work.

```rust
    let s1 = String::from("hello");
    let h = s1[0];
```

Listing 8-19: Attempting to use indexing syntax with a String

And guess what? It throws an error at you! Rust is like, "Hey buddy, that's not
gonna fly here!"


```rust
$ cargo run
   Compiling collections v0.1.0 (file:///projects/collections)
error[E0277]: the type `String` cannot be indexed by `{integer}`
 --> src/main.rs:3:13
  |
3 |     let h = s1[0];
  |             ^^^^^ `String` cannot be indexed by `{integer}`
  |
  = help: the trait `Index<{integer}>` is not implemented for `String`
  = help: the following other types implement trait `Index<Idx>`:
            <String as Index<RangeFrom<usize>>>
            <String as Index<RangeFull>>
            <String as Index<RangeInclusive<usize>>>
            <String as Index<RangeTo<usize>>>
            <String as Index<RangeToInclusive<usize>>>
            <String as Index<std::ops::Range<usize>>>
```
For more information about this error, try `rustc --explain E0277`.
error: could not compile `collections` due to previous error

The error message is telling you that the type String cannot be indexed by an
integer. It's like trying to stick a square peg in a round hole. Rust is all
about safety, and it won't let you do something that might cause memory issues
or other problems.

But why can't you index into a String in Rust? Well, it has to do with how Rust
stores strings in memory. Strings in Rust are encoded in UTF-8, which means that
a character can be represented by more than one byte. So, grabbing a single
character by index is not as straightforward as it seems.

However, fear not! Rust has other ways to work with strings, like slicing and
iterating. We'll dive into those in the upcoming sections.

So, remember, in Rust, indexing into a String is a no-go. But don't worry, there
are always alternative ways to accomplish what you need.

    Internal Representation

Let's talk about the internal representation of a String in Rust. Brace
yourself, because it's about to get interesting.

You see, a String in Rust is like a fancy package wrapped around a Vec<u8>. It's
like putting a shiny bow on a box filled with bytes. And these bytes? They
represent the characters of the string. But here's the kicker: Rust uses UTF-8
encoding to store these characters.

```rust
    let hello = String::from("Hola");
```

In this case, the string "Hola" is made up of four characters, which means the
underlying vector storing the string is four bytes long. Each character in this
case takes up one byte when encoded in UTF-8. It's like each character has its
own little byte buddy.

But hold on tight, because things can get even more surprising. Brace yourself
for this line:

```rust
    let hello = String::from("Здравствуйте");
```

Now, you might think this string has a length of 12, right? Well, Rust has a
different answer for you. It says, "Hey, buddy, this string is actually 24 bytes
long!" What?! How could that be? Well, each Unicode scalar value in this string
takes up 2 bytes of storage in UTF-8 encoding. It's like the characters decided
to double up on their byte consumption.

So, here's the thing: indexing into the bytes of a string won't always give you
a valid Unicode scalar value. It's like trying to make sense of a jumbled mess.
Rust wants to make sure you don't accidentally step into a landmine of invalid
characters or corrupt data.

So, keep in mind that a String in Rust is a bit more complex than meets the eye.
It's like a magical box filled with bytes, where each character can have its own
byte buddies.

Alright, let's dive into some more Rust code that doesn't quite behave as
expected. Brace yourselves for some compiler errors, folks!

Check out this piece of code that attempts to grab the first letter of a string:

```rust
[This code does not compile!]
let hello = "Здравствуйте";
let answer = &hello[0];
```

Now, you might think that answer will hold the value of the first letter, З. But
here's where things get interesting. When you encode З in UTF-8, you get two
bytes: 208 and 151. So, you might expect that answer would be 208, right? Well,
not quite! You see, 208 is not a valid character on its own. It's like a byte
without a buddy.

So, what does Rust do to prevent this confusion? It refuses to compile this code
altogether. It's like saying, "Hey, buddy, I know what you're trying to do, but
I can't let you go down that road of misunderstanding and potential bugs."

Why does Rust do this? Well, it's all about avoiding unexpected results and
catching misunderstandings early on. Rust wants to make sure you don't end up
with byte values instead of actual characters. Imagine if you asked for the
first letter of a string and got a random byte value instead. That would be
quite confusing, wouldn't it?

So, Rust takes a stand and says, "No, I won't compile this code. Let's prevent
those misunderstandings right from the start." And you know what? It's actually
a pretty smart move. It saves us from potential headaches and bugs down the
road.

So, let's raise a glass to Rust for keeping us on our toes and preventing those
unexpected surprises. Cheers to clarity and avoiding byte mishaps!

    Bytes and Scalar Values and Grapheme Clusters! Oh My!

Alright, let's dig deeper into the wild world of strings and character encoding.
Hold on to your hats, folks!

When it comes to strings in Rust, there are three perspectives you should know
about: bytes, scalar values, and grapheme clusters. It's like looking at a
string from different angles and seeing different things each time.

Let's take the Hindi word "नमस्ते" written in the Devanagari script. Underneath
the surface, it's actually a vector of u8 values. Imagine it as this sequence of
bytes: [224, 164, 168, 224, 164, 174, 224, 164, 184, 224, 165, 141, 224, 164,
164, 224, 165, 135]. That's how computers store this data, in all its
byte-filled glory. It's like peering into the matrix!

```rust
[224, 164, 168, 224, 164, 174, 224, 164, 184, 224, 165, 141, 224, 164, 164,
224, 165, 135]
```

But that's not all! If we put on our Unicode glasses and look at these bytes as
scalar values, we get a different view. We see these char values: ['न', 'म',
'स', '्', 'त', 'े']. There are six of them, but hold on a second—those fourth and
sixth ones aren't actual letters. They're diacritics that don't make sense on
their own. It's like having a bunch of puzzle pieces, but some of them don't fit
quite right.

```rust
['न', 'म', 'स', '्', 'त', 'े']
```

Now, let's take it a step further and examine the bytes as grapheme clusters.
This perspective gives us what a person would call the four letters that make up
the Hindi word: ["न", "म", "स्", "ते"]. It's like putting the puzzle pieces
together to form the complete picture.

```rust
["न", "म", "स्", "ते"]
```

Rust provides these different interpretations of the raw string data so that
each program can choose the one that fits its needs, no matter what human
language the data is in. It's like having a toolbox full of different tools for
different situations.

Now, you might be wondering why Rust doesn't allow us to index into a String and
grab a character. Well, here's the thing: indexing operations are expected to be
lightning-fast, always taking constant time. But with a String, it's a bit more
complicated. Rust would have to go through the entire string from the beginning
to the desired index to figure out how many valid characters there are. It's
like trying to count the grains of sand on a beach while on a tight
schedule—it's just not practical!

So, to keep things snappy and avoid unexpected performance issues, Rust takes a
stand and says, "No indexing into strings for you!" It's all about maintaining
that O(1) performance and keeping things running smoothly.

    Slicing Strings

Alright, folks, let's talk about slicing strings in Rust. Now, indexing into a
string is a tricky business, and Rust knows it. It's like playing a game of
"What do you want me to give you? A byte? A character? A grapheme cluster? A
string slice?" It's a real head-scratcher!

But fear not, my friends, because Rust has a solution. Instead of using a single
number inside those square brackets [], you can use a range to slice and dice
that string just the way you want. Let me show you an example:

We have our string "Здравствуйте", which is quite a mouthful. Now, if we want to
create a string slice with the first 4 bytes, we can do this:

```rust
let hello = "Здравствуйте";

let s = &hello[0..4];
```

In this case, s will be a &str that contains the first 4 bytes of the string.
And remember, each character in this string takes up 2 bytes, so s will be "Зд".
It's like taking a knife and slicing off just the portion you need.

But here's a word of caution: when you're slicing strings using ranges, you need
to be careful. If you try to slice only part of a character's bytes, like
&hello[0..1], Rust won't be too happy. It'll throw a runtime panic at you, just
like when you access an invalid index in a vector. It's like Rust saying, "Hey,
you're going too far! That's not a valid character boundary!"

```rust
$ cargo run Compiling collections v0.1.0 (file:///projects/collections) Finished
   dev [unoptimized + debuginfo] target(s) in 0.43s Running
   `target/debug/collections` thread 'main' panicked at 'byte index 1 is not a
   char boundary; it is inside 'З' (bytes 0..2) of `Здравствуйте`',
   src/main.rs:4:14 note: run with `RUST_BACKTRACE=1` environment variable to
   display a backtrace
```

You should use ranges to create string slices with caution, because doing so can
crash your program.

    Methods for Iterating Over Strings

Alright, my friends, let's talk about how to iterate over strings in Rust. It's
all about being explicit and knowing what you want: characters or bytes. It's
like choosing between a fine wine and a shot of tequila. Both have their place,
but you need to know what you're getting into.

If you want to operate on individual Unicode scalar values, the chars method is
your go-to. Check out this code:

```rust
for c in "Зд".chars() {
    println!("{c}");
}
```

This code separates out and returns two values of type char: З and д. It's like
breaking down the string into its individual characters and having a chat with
each one. You can iterate over them and do whatever you need to do. Just
remember to use those curly braces {} to show your characters some love.

Now, if you're more interested in raw bytes, the bytes method is your ticket.
Take a look at this:

```rust
З
д
```

This code separates out and returns two values of type char: З and д. It's like
breaking down the string into its individual characters and having a chat with
each one. You can iterate over them and do whatever you need to do. Just
remember to use those curly braces {} to show your characters some love.

Now, if you're more interested in raw bytes, the bytes method is your ticket.
Take a look at this:

```rust
for b in "Зд".bytes() {
    println!("{b}");
}
```

This code will give you the four bytes that make up the string: 208, 151, 208,
and 180. It's like going down to the nitty-gritty and seeing the raw data in all
its glory. But remember, my friends, a valid Unicode scalar value may span
multiple bytes. It's like a puzzle waiting to be solved.

```rust
208
151
208
180
```

Now, let's talk about grapheme clusters. If you're dealing with scripts like
Devanagari and need to handle those clusters, things get a bit more complex.
Unfortunately, the standard library doesn't provide this functionality out of
the box. But fear not! There are crates available on crates.io that can fulfill
your grapheme cluster needs. It's like having a whole arsenal of tools at your
disposal.

So, my friends, remember to choose wisely: chars for characters, bytes for raw
bytes, and explore the crates for grapheme clusters. With the right tools in
hand, you'll conquer any string that comes your way.

    Strings Are Not So Simple

Strings, my friends, are a whirlwind of complexity. Every programming language
has its own way of dealing with them, and Rust is no exception. Rust takes the
road less traveled, making sure we handle string data correctly from the get-go.
It's like having a responsible friend who reminds you to double-check your UTF-8
encoding. Sure, it exposes more of the complexity, but it saves us from
headaches down the line.

Now, here's the good news. Rust's standard library has got our backs. It offers
a plethora of functionality to handle strings like a pro. We're talking methods
like contains for searching through strings and replace for swapping parts of a
string with something new. It's like having a Swiss Army knife for all your
string-related tasks.

So, my friends, when you find yourself in the depths of string manipulation,
consult the documentation. It's like having a treasure map to guide you through
the complexities. With Rust by your side, you'll conquer those strings and
emerge victorious.

Now, let's take a breather from the intricacies of strings and delve into the
fascinating world of hash maps. It's like switching gears to something a bit
more manageable.
