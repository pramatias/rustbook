    To panic! or Not to panic!

Alright, let's dive into the art of decision-making. When it comes to calling
panic! or returning a Result, it's all about assessing the situation and making
the right choice. It's like playing chess, you know? You gotta think ahead and
consider the consequences of your moves.

So, here's the deal. When you call panic!, you're basically saying, "This is it,
game over, there's no coming back from this." It's like slamming the door shut
and admitting defeat. But hold on, my friends. Before you go all-in with panic!,
ask yourself this: Is there any possible way to recover from this error? If the
answer is yes, then returning a Result is the way to go. By returning a Result,
you're giving the calling code the power to decide how to handle the error. It's
like passing the torch and letting someone else take charge.

But hey, there are situations where panic! is the right move. Take examples,
prototype code, and tests, for instance. In those scenarios, you want to focus
on the big picture and quickly identify any issues. Panicking allows you to
highlight those problems and get a clear signal that something's not right. It's
like putting a big red flag on the issue and saying, "Hey, we need to fix this
before moving forward!"

Now, my friends, there are times when you, as a human, can see what the compiler
can't. You have that extra level of insight, that sixth sense, if you will.
Sometimes, the compiler might not be able to determine that failure is
impossible, but you know it in your gut. In those cases, it's okay to panic! and
trust your instincts. Just make sure you have a good reason for it, like when
failure would defy the laws of physics or the logic of your code.

To wrap it up, let me leave you with some general guidelines. In library code,
it's best to lean towards returning a Result. That gives the calling code the
flexibility to handle errors in the way that suits its specific needs. But in
examples, prototypes, and tests, don't be afraid to let panic! shine. It helps
you quickly identify and address issues, keeping your code on the right track.

So, remember to choose wisely. Panic! when there's no way back, and return a
Result when there's hope for recovery. It's all about making the right move and
keeping the codebase strong.

    Examples, Prototype Code, and Tests

Ah, examples, prototypes, and tests. These are the wild territories where rules
can be bent. You see, when you're crafting an example to showcase a concept,
adding extensive error-handling code can muddy the waters. We want our examples
to shine, to be crystal clear in their purpose. So, in the realm of examples,
it's understood that calls to methods like unwrap are just placeholders. They're
placeholders for the error-handling strategies you'd implement in your
real-world application, where things get serious.

Now, let's talk prototypes. When you're in the early stages of prototyping, you
want to move fast, my friends. You're exploring, experimenting, and error
handling might not be your top priority. That's where unwrap and expect come to
the rescue. They're like temporary safety nets, marking the spots where you'll
eventually beef up your code to handle errors like a pro.

And let's not forget about tests, my friends. Tests are the guardians of code
quality. When something goes wrong in a test, we want the whole thing to fail.
It's like a referee blowing the whistle and saying, "Nope, that's not right!"
So, in the realm of tests, using unwrap or expect is the way to go. They boldly
declare that if anything unexpected happens, the test should go down in flames.

So, my friends, when you're in the realm of examples, prototypes, and tests,
don't be afraid to bend the rules a little. Use unwrap and expect as temporary
crutches, knowing that they're just placeholders until you're ready to tackle
error handling with finesse.

    Cases in Which You Have More Information Than the Compiler

Ah, the cases where you, my friend, have more information than the compiler.
It's like having a secret, a nugget of knowledge that only you possess. In these
situations, you might find yourself calling unwrap or expect with confidence,
knowing deep down that failure is simply not an option.

Let me give you an example, my friends. Picture this: we're dealing with IP
addresses, and we have a hardcoded string that represents an IP address. We
know, beyond a shadow of a doubt, that this string is a valid IP address. It's
hardcoded, for crying out loud! So, we confidently parse this string into an
IpAddr instance, and we use expect to proclaim, "Hey, this hardcoded IP address
should be valid!"

```rust
    use std::net::IpAddr;

    let home: IpAddr = "127.0.0.1"
        .parse()
        .expect("Hardcoded IP address should be valid");
```

Now, here's the thing. The compiler, bless its heart, doesn't possess the same
level of understanding that we do. It still sees this as a Result value, with
the possibility of an Err variant creeping in. So, it forces us to handle the
Result as if failure is lurking around the corner. But we know better, don't we?

By using expect and documenting our assumption, we're letting the world know
that we've done our due diligence. We're acknowledging that, based on our manual
inspection of the code, an Err variant is as likely as finding a unicorn at a
coffee shop. It's a way of saying, "Hey, compiler, I got this. Trust me."

But remember, my friends, this approach is only suitable when you have concrete
evidence that failure is impossible in your specific situation. If there's even
a hint of uncertainty, if the input could come from a user or some external
source, then it's time to embrace robust error handling with open arms.

So, go forth, my friends, and wield unwrap and expect with confidence when you
hold the knowledge that the compiler lacks. But always be ready to adapt and
evolve your code if circumstances change. That's the path to code enlightenment.

    Guidelines for Error Handling

Ah, the guidelines for error handling, my friends. Let's dive into this.

First and foremost, when it comes to error handling, it's best to let your code
panic when it finds itself in a bad state. A bad state occurs when something
unexpected happens, like invalid values or contradictory values being passed to
your code. We're talking about situations where assumptions, guarantees,
contracts, or invariants have been shattered. And here's when you should
consider a panic:

The bad state is unexpected, not something that happens occasionally, like a
user entering data in the wrong format. Your code relies on not being in this
bad state. There's no point in checking for the problem at every step. There's
no good way to encode this information in the types you use. We'll explore this
further in Chapter 17, my friends.

Now, picture this scenario: someone calls your code and passes in values that
make absolutely no sense. What do you do? Well, in most cases, it's best to
return an error. This way, the user of your library can decide how they want to
handle this nonsensical situation. However, my friends, there are situations
where continuing down the rabbit hole could be unsafe or harmful. In those
cases, panic! is your friend. By calling panic!, you alert the person using your
library that there's a bug in their code, and they need to fix it pronto.

Similarly, if you're dealing with external code that is out of your control and
it returns an invalid state that you can't fix, panic! is often the appropriate
choice. It's like waving a red flag and saying, "Hey, something fishy is going
on here, and we can't proceed until it's resolved."

But my friends, when you're expecting failure, when failure is just a natural
part of the process, then it's time to embrace the Result. Imagine a parser
being fed malformed data or an HTTP request returning a rate limit status. In
these cases, it's more appropriate to return a Result, indicating that failure
is expected, and it's up to the calling code to decide how to handle it.

So, my friends, remember these guidelines. Embrace panic! when you encounter
unexpected bad states, when there's no way to recover, or when you're dealing
with external code gone wild. But when failure is part of the game, when you can
anticipate it, wrap it up in a nice Result package and let the calling code make
the decisions.

Error handling, my friends, it's a delicate dance between panic and Result.

Now, let's talk about making sure your code is safe and sound, my friends. When
your code performs an operation that could potentially put a user at risk if
it's called with invalid values, you need to verify those values first. And if
they turn out to be invalid, it's time to panic! Safety first, people!

Think about it. Operating on invalid data is like playing with fire. It exposes
your code to vulnerabilities, and we definitely don't want that. That's why the
standard library takes no chances. If you dare to attempt an out-of-bounds
memory access, guess what? Panic time! Trying to access memory that doesn't
belong to the current data structure is a recipe for disaster. It's a common
security problem that needs to be dealt with swiftly.

But wait, there's more! Functions often come with contracts, my friends. These
contracts specify the requirements for the inputs. And when those requirements
aren't met, panic is the way to go. It's a clear indication of a bug on the
caller's side, and it's not an error that the calling code should have to
explicitly handle. There's no reasonable way for the calling code to recover
from such a violation. The calling programmers need to roll up their sleeves and
fix their code, no questions asked. Remember, folks, contracts are essential,
and it's crucial to explain them in the API documentation for your function.
Transparency is key!

Now, here's the good news. You don't have to drown in a sea of error checks.
Rust's type system and the mighty compiler are here to save the day. They do the
heavy lifting for you. If your function expects a particular type as a
parameter, you can rest easy knowing that the compiler has already ensured you
have a valid value. It's like having a safety net. For example, if you're
dealing with a type instead of an Option, it means your program expects to have
something rather than nothing. You can confidently proceed with your logic,
knowing that you have a value for sure. And the best part? Code that tries to
pass nothing to your function won't even compile! The compiler will catch it and
spare you from the headache of runtime checks. It's a win-win situation.

And let's not forget about unsigned integers, like u32. These little warriors
ensure that your parameters are never negative. No negativity allowed! It's all
about maintaining the positive vibes, my friends.

So, my fellow programmers, embrace the power of the type system and the watchful
eye of the compiler. Let them handle the heavy lifting when it comes to safety
and validity. And when in doubt, remember: panic! Because we take risks
seriously, and we're not afraid to shout, "Hey, something's wrong here!"

    Creating Custom Types for Validation

Let's dive into the fascinating world of custom types for validation, my
friends. Remember the good old guessing game from Chapter 2? We asked the user
to guess a number between 1 and 100. Ah, those were the days. But you know what?
We never bothered to validate if the user's guess fell within that range. We
simply assumed that they would play by the rules and give us a positive number.
Well, sometimes life doesn't go as planned.

Now, the consequences weren't too dire in this case. Our "Too high" or "Too low"
messages would still be accurate. But wouldn't it be nice to guide the user
towards valid guesses and have different behavior for out-of-range numbers or
even when the user types something other than numbers? That would be a
game-changer, my friends.

So, here's the plan. Instead of just parsing the guess as an i32 and allowing
potentially negative numbers, let's create a custom type for validation. Are you
with me? Great!

In our loop, we'll modify the guess line like this:

```rust
    loop {
        // --snip--

        let guess: i32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        if guess < 1 || guess > 100 {
            println!("The secret number will be between 1 and 100.");
            continue;
        }

        match guess.cmp(&secret_number) {
            // --snip--
    }
```

Now, instead of blindly accepting any input, we're taking the time to parse the
guess as an i32. If the parsing succeeds, we assign the number to the guess
variable. But what about errors, you ask? Well, we simply continue the loop and
ask for another guess. We don't let those pesky errors ruin our game!

But wait, there's more! We want to make sure that the guess falls within the
range of 1 to 100, right? So, we add an if expression to check if the guess is
less than 1 or greater than 100. If it is, we kindly inform the user about the
acceptable range and continue the loop to give them another chance. We're all
about second chances here.

And guess what? After this if expression, we can proceed with the confidence
that the guess is indeed between 1 and 100. No more worries, my friends! We're
playing by the rules now.

Now, here's a little reality check. If our program has many functions with this
same requirement, checking the range in every single function would be a
nightmare. It would be tedious, time-consuming, and quite frankly, annoying. We
don't want that. It might even impact performance, and we definitely don't want
that either.

So, my fellow programmers, let's strive for elegance and efficiency. Let's
create custom types for validation when necessary, saving ourselves from the
hassle of repetitive checks.

Alright, my friends, we've reached a moment of enlightenment. We can take our
validation game to the next level by creating a new type and encapsulating our
validations in a function. No more repetitive checks and tedious code. It's time
to embrace elegance and efficiency!

```rust
pub struct Guess {
    value: i32,
}

impl Guess {
    pub fn new(value: i32) -> Guess {
        if value < 1 || value > 100 {
            panic!("Guess value must be between 1 and 100, got {}.", value);
        }

        Guess { value }
    }

    pub fn value(&self) -> i32 {
        self.value
    }
}
```

Listing 9-13: A Guess type that will only continue with values between 1 and 100

Introducing the Guess type, my friends. It's a struct that holds an i32 value,
and we're going to make sure that the only instances of Guess created are those
with values between 1 and 100. How do we do that? Well, let me show you the way
in Listing 9-13.

We start by defining our struct named Guess. It's a simple struct with a single
field named value, which will store our precious number.

But wait, there's more! We implement an associated function called new on the
Guess type. This function is responsible for creating instances of Guess values.
It takes a parameter named value of type i32 and returns a Guess. Pay attention,
my friends, because this is where the magic happens.

Inside the new function, we put our validation logic to the test. We check if
the value falls within the acceptable range of 1 to 100. If it doesn't, well,
we're not messing around here. We call panic! and let the programmer know loud
and clear that they messed up. We even provide them with a helpful error message
indicating the expected range. We're all about clarity and accountability, my
friends.

But fear not! If the value passes our rigorous test, we create a brand new Guess
instance with the value field set to the value parameter. And there you have it,
a valid Guess ready to take on the world.

Now, I must emphasize the importance of discussing these potential panics in our
API documentation. We want our fellow programmers to be fully aware of the
possible pitfalls when using our Guess type. It's all about transparency, my
friends.

So, my fellow code enthusiasts, let's embrace this new era of validation. Let's
create custom types and ensure that only valid values make it through. No more
bugs, no more headaches. It's time to build robust and reliable code. And
remember, always aim for a Guess that falls within the range of 1 to 100.
Anything less is just a shot in the dark. Good luck, my friends!

Alright, my friends, let's dig deeper into the Guess type. We've created it with
its strict validations and panic-inducing powers. But now we have a little
challenge: the value field is private. Why, you ask? Well, it's for our own
good, my friends.

By keeping the value field private, we're ensuring that no code outside the
module can directly set its value. It's like having a guard at the entrance,
making sure only the right values are allowed in. And how do we get the value
out, you ask? Well, that's where our trusty getter comes into play.

We've implemented a method called value on the Guess type. It's a public method
that takes a borrowed reference to self (that's our instance of Guess) and
returns an i32. It's a simple getter, my friends. Its purpose is to retrieve the
value from the private field and hand it over to us. It's like a reliable
messenger, bringing us the value we need.

Now, why did we go through all this trouble? It's because we want to ensure that
the only way to set the value of Guess is by going through our trusted
Guess::new function. By making the value field private, we're preventing any
code outside the module from tampering with it. It's all about maintaining
control and guaranteeing that our values have been properly validated.

Imagine, my friends, that you have a function that requires a parameter or
returns a value between 1 and 100. Instead of dealing with additional checks and
validations in the function's body, you can simply declare that it takes or
returns a Guess instead of an i32. This way, you can rest assured that the value
is already validated and falls within the acceptable range. It's like having a
seal of approval.

So, let's celebrate this moment of encapsulation and validation. Let's embrace
the power of private fields and trusted getters. With Guess, we have control
over our values, ensuring that only the right ones make it through. Let's build
code that's reliable, secure, and free from unexpected surprises.

    Summary

Let's recap what we've learned about error handling in Rust. It's all about
writing code that's robust and reliable. We have two powerful tools at our
disposal: the panic! macro and the Result enum.

When something goes terribly wrong and your code can't handle it, panic! comes
to the rescue. It's like throwing your hands up in the air and saying, "I give
up!" It's a way to signal that the program has reached a state it can't recover
from. Sometimes, it's the best way to deal with invalid or incorrect values. We
want our code to be safe, secure, and free from unexpected surprises. So, when
things go haywire, panic! is our go-to solution.

But what about situations where we can recover from errors? That's where the
Result enum steps in. It's like a safety net, my friends. It lets us handle
potential success or failure. It uses Rust's type system to indicate that
operations might fail, but it gives us the power to recover gracefully. When we
use Result, we're telling the calling code, "Hey, there's a chance this could go
wrong. You better be prepared." It's all about setting expectations and handling
errors like a pro.

Now, let's not forget about the magic of generics. We've seen how Option and
Result use generics to work with different types of values. They're like
chameleons, adapting to any situation. Generics allow us to write code that's
flexible and reusable. They give us the power to create generic types and
functions that can work with different kinds of data. It's like having a Swiss
Army knife in our coding toolbox.

So, my friends, let's embrace error handling in Rust. Let's use panic! when
things get out of control and Result when we have a chance to recover. And let's
not forget the beauty of generics, which give us the freedom to write code
that's adaptable and versatile. With these tools in our hands, we can conquer
the challenges of building reliable and robust software. Onward to the world of
generics!
