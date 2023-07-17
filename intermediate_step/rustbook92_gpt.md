    Recoverable Errors with Result

Alright, let's talk about errors that we can actually deal with. Not every error
is a catastrophe that requires us to abandon ship. Sometimes, it's just a little
hiccup that we can handle gracefully. That's where Result comes into play.

You see, Result is an enum that comes with two flavors: Ok and Err. It's like a
menu of possibilities. When everything goes smoothly, we get an Ok value, which
holds the result of our successful operation. But when things go awry, we get an
Err value, which tells us what went wrong.

The beauty of Result is that it's flexible. It's not limited to a specific type
of success value or error value. It can handle different situations with ease.
We just need to define the types that we want to use for the successful and
error outcomes.

Let me break it down for you:
```rust

enum Result<T, E> {
    Ok(T),
    Err(E),
}
```

In this enum, T represents the type of the value that we get when everything
goes smoothly. It's like a little reward for our successful endeavors. On the
other hand, E represents the type of the error that we encounter when things
don't go according to plan. It's like a warning sign, telling us that we need to
adjust our course.

With Result, we have the power to handle errors in a more granular way. We can
analyze the error, interpret it, and respond accordingly. It's like being able
to choose our own adventure instead of being stuck in a one-size-fits-all
situation.

So, we're going to call a function that might fail. In this case, we're trying
to open a file. Now, opening a file is not always a walk in the park. There
could be all sorts of issues: maybe the file doesn't exist, or perhaps we don't
have the necessary permissions. We need a way to handle these potential
failures.

In Rust, when a function can encounter errors, it can return a Result value.
It's like a little package that contains either the result of a successful
operation or information about what went wrong. Let me show you an example:

Filename: src/main.rs

```rust

use std::fs::File;

fn main() {
    let greeting_file_result = File::open("hello.txt");
}
```
Listing 9-3: Opening a file

In this code, we're calling the File::open function to open a file. The
interesting thing is that File::open returns a Result value. The generic
parameters of Result, T and E, have been filled in by the implementation of
File::open. T represents the type of the success value, which in this case is
std::fs::File, a file handle. E represents the type of the error value, which is
std::io::Error.

So, when we call File::open, it might succeed and give us a file handle wrapped
in an Ok variant of Result. That's the good news. But if it fails, we'll get an
Err variant of Result, which contains more information about the specific error
that occurred.

In our case, the result of File::open will be stored in the greeting_file_result
variable. It could be an Ok value if the file was successfully opened, or an Err
value if something went wrong.

So, with Result, we have a clear way to handle potential failures. We can
examine the Result and take appropriate actions based on whether it's an Ok or
an Err. It's like having a built-in safety net for our code.

We need to enhance the code in Listing 9-3 to handle the different outcomes of
the File::open function. In Listing 9-4, we're using a match expression, which
is like a fancy tool to deal with Result values. We talked about match
expressions before, so you should be familiar with them from Chapter 6.

Here's the updated code:
Filename: src/main.rs

```rust
use std::fs::File;

fn main() {
    let greeting_file_result = File::open("hello.txt");

    let greeting_file = match greeting_file_result {
        Ok(file) => file,
        Err(error) => panic!("Problem opening the file: {:?}", error),
    };
}
```
Listing 9-4: Using a match expression to handle the Result variants that might
be returned

In this code, we have a match expression that handles the Result value returned
by File::open. It has two arms: one for the Ok variant and one for the Err
variant.

In the Ok arm, we take the file handle out of the Ok variant and assign it to
the greeting_file variable. This means that if the file was successfully opened,
we can use the file handle for further operations.

On the other hand, if we get an Err value, we enter the Err arm of the match. In
this example, we're calling the panic! macro, which will cause the program to
panic and display an error message. We pass the error value to the panic! macro
so that it can show us some details about what went wrong.

For instance, if there's no file named "hello.txt" in the current directory and
we run this code, we'll see an output like this:

```rust
$ cargo run Compiling error-handling v0.1.0 (file:///projects/error-handling)
   Finished dev [unoptimized + debuginfo] target(s) in 0.73s Running
   `target/debug/error-handling` thread 'main' panicked at 'Problem opening the
   file: Os { code: 2, kind: NotFound, message: "No such file or directory" }',
   src/main.rs:8:23 note: run with `RUST_BACKTRACE=1` environment variable to
   display a backtrace
```

This output tells us exactly what went wrong and where it happened. It's like a
little detective story that Rust presents to us.

    Matching on Different Errors

The code in Listing 9-4 was too harsh. It would panic no matter what the reason
for the failure was. But we want to handle different types of failures
differently. For example, if File::open fails because the file doesn't exist, we
want to create the file and return the handle to it. But if it fails for any
other reason, we still want to panic, just like before. So, we need to refine
our code.

Here's the updated code in Listing 9-5:

Filename: src/main.rs

```rust
use std::fs::File;
use std::io::ErrorKind;

fn main() {
    let greeting_file_result = File::open("hello.txt");

    let greeting_file = match greeting_file_result {
        Ok(file) => file,
        Err(error) => match error.kind() {
            ErrorKind::NotFound => match File::create("hello.txt") {
                Ok(fc) => fc,
                Err(e) => panic!("Problem creating the file: {:?}", e),
            },
            other_error => {
                panic!("Problem opening the file: {:?}", other_error);
            }
        },
    };
}
```
Listing 9-5: Handling different kinds of errors in different ways

In this code, we have an inner match expression nested inside the Err arm of the
outer match. This inner match expression is used to handle different types of
errors.

If the error kind is NotFound, it means the file doesn't exist. In this case, we
enter the inner match expression and try to create the file using File::create.
If creating the file succeeds, we return the file handle. But if creating the
file fails, we panic! and display an error message.

If the error kind is any other kind of error, we enter the other_error arm of
the inner match expression. In this case, we panic! and display an error message
without attempting to create the file.

This way, we handle the different failure reasons in different ways.

So, we're dealing with this File::open function and the errors it can throw at
us. When an error occurs, it returns an io::Error struct. This struct has this
cool method called kind that gives us an io::ErrorKind value. And guess what?
The io::ErrorKind enum is provided by the standard library, and it has different
variants representing the different kinds of errors we might encounter when
doing I/O operations. One of those variants is ErrorKind::NotFound, which tells
us that the file we're trying to open doesn't exist. It's like telling us, "Hey,
buddy, I couldn't find the file you're looking for."

So, in our code, we match on greeting_file_result to handle the Result, but we
also have an inner match on error.kind(). This inner match checks whether the
value returned by error.kind() is the NotFound variant of the ErrorKind enum. If
it is, we know we've got a missing file situation, and we try to create the file
using File::create. But hold on, because creating the file could also fail,
right? So, we need another arm in our inner match expression to handle that
case. If creating the file fails, we panic! and display a different error
message. It's like saying, "Sorry, I tried to create the file, but something
went wrong."

The second arm of the outer match stays the same as before. So, if we encounter
any error besides the missing file error, the program will panic! just like it
did before. We're not taking any chances with those other errors. It's like
saying, "Nope, can't handle that kind of error. I'm out!"

    Alternatives to Using match with Result<T, E>

Hey, guess what? There's an alternative to using all those match expressions! I
mean, don't get me wrong, match is great and all, but sometimes it can get a bit
overwhelming, you know? So, in Chapter 13, you'll learn about these things
called closures. They're like these little self-contained blocks of code that
you can use with methods defined on Result<T, E>. And let me tell you, these
methods can make your code much more concise and easier to read.

So, let me show you how we can rewrite the code from Listing 9-5 using closures
and the unwrap_or_else method. It's like a cleaner, more streamlined version of
the same logic.

```rust
use std::fs::File;
use std::io::ErrorKind;

fn main() {
    let greeting_file = File::open("hello.txt").unwrap_or_else(|error| {
        if error.kind() == ErrorKind::NotFound {
            File::create("hello.txt").unwrap_or_else(|error| {
                panic!("Problem creating the file: {:?}", error);
            })
        } else {
            panic!("Problem opening the file: {:?}", error);
        }
    });
}
```

We start by calling File::open("hello.txt") and then we use the unwrap_or_else
method. This method takes a closure as an argument and says, "Hey, if
everything's good and we get an Ok value, just unwrap it and give me the file
handle. But if we get an Err value, instead of panicking right away, call this
closure and do something else." It's like having a backup plan, you know?

Inside the closure, we check if the error.kind() is equal to
ErrorKind::NotFound. If it is, that means we've got a missing file situation,
just like before. So, we call File::create("hello.txt") and use another
unwrap_or_else method. This time, if creating the file fails, we panic! and
display a different error message. We're still not taking any chances with those
errors!

And if the error.kind() is anything other than NotFound, well, we panic! just
like we did before. No mercy for those other errors.

The beauty of this approach is that we don't need all those match expressions
anymore. It's like a breath of fresh air, you know? It's cleaner, easier to
read, and it does the same job as before. So, if you want to learn more about
closures and dive deeper into these methods, check out Chapter 13 and take a
look at the unwrap_or_else method in the standard library documentation. It's
like a whole new world of error handling possibilities!

    Shortcuts for Panic on Error: unwrap and expect

So, we've been talking about all these different ways to handle errors, right?
But sometimes, you just want a quick and easy solution. That's where the unwrap
method comes in. It's like a shortcut, a one-liner that does the job for you.

Check out this example. We have a simple line of code that tries to open a file
using File::open("hello.txt"). And then, we just call unwrap on it. That's it.
If everything goes well and we get an Ok value, we get the file handle. But if
we get an Err value, unwrap calls the panic! macro for us. It's like a built-in
panic button!

Filename: src/main.rs

```rust
use std::fs::File;

fn main() {
    let greeting_file = File::open("hello.txt").unwrap();
}
```

Now, let me warn you. If you run this code without a hello.txt file, you're in
for a treat. You'll see an error message from the panic! call that the unwrap
method makes. It's like a loud alarm going off, saying, "Hey, something's not
right here!"

The message will tell you that you called unwrap on an Err value, and it will
even give you some details about the error, like the code, the kind of error (in
this case, NotFound), and a message saying, "No such file or directory." It's
like an error detective, trying to give you as much information as possible.

thread 'main' panicked at 'called `Result::unwrap()` on an `Err` value: Os {
code: 2, kind: NotFound, message: "No such file or directory" }',
src/main.rs:4:49

Alright, here's another handy method for handling those Result values: expect.
It's like unwrap, but with a personal touch. You can customize the panic! error
message and give it some personality.

Filename: src/main.rs

```rust
use std::fs::File;

fn main() {
    let greeting_file = File::open("hello.txt")
        .expect("hello.txt should be included in this project");
}
```

Take a look at this code. We're trying to open a file, just like before. But
this time, we call expect instead of unwrap. And guess what? We can provide our
own error message as a parameter to expect. How cool is that?

So, in this example, we're saying that the file "hello.txt" should be included
in this project. It's like a friendly reminder, a note to self. And if something
goes wrong, if that file doesn't exist, expect will call the panic! macro with
our custom message. It's like shouting, "Hey, I expected that file to be here!"

And just like unwrap, when the panic! macro kicks in, you'll get all the details
about the error: the code, the kind of error (in this case, NotFound), and a
message telling you, "No such file or directory." It's like an error message
with a personal touch, making sure you know exactly what's going on.

thread 'main' panicked at 'hello.txt should be included in this project: Os {
code: 2, kind: NotFound, message: "No such file or directory" }',
src/main.rs:5:10

In real-life projects, many Rustaceans prefer to use expect instead of unwrap.
They find it helpful to provide more context about why they expect the operation
to always succeed. It's like leaving breadcrumbs for future debugging, in case
their assumptions turn out to be wrong.

So, if you want to add a touch of personality to your error handling, give
expect a try. It's like unwrap, but with a message that speaks to you.

    Propagating Errors

Alright, let's talk about propagating errors. When a function calls something
that could potentially fail, instead of handling the error right there and then,
it can pass the error up the chain to the calling code. This gives more power to
the caller, who might have more information or specific logic to decide how to
handle the error.

Take a look at this code in Listing 9-6. We have a function that reads a
username from a file. Now, if the file doesn't exist or can't be read, instead
of handling the error within the function, we return it to the calling code.

Filename: src/main.rs

```rust
use std::fs::File;
use std::io::{self, Read};

fn read_username_from_file() -> Result<String, io::Error> {
    let username_file_result = File::open("hello.txt");

    let mut username_file = match username_file_result {
        Ok(file) => file,
        Err(e) => return Err(e),
    };

    let mut username = String::new();

    match username_file.read_to_string(&mut username) {
        Ok(_) => Ok(username),
        Err(e) => Err(e),
    }
}
```

Listing 9-6: A function that returns errors to the calling code using match

The return type of this function is Result<String, io::Error>. In plain English,
it means that the function can either return a value of type String if
everything goes well (wrapped in the Ok variant), or it can return an error of
type io::Error (wrapped in the Err variant).

Let's break down the implementation of the function. We start by trying to open
the file using File::open. The result of this operation is stored in the
variable username_file_result.

Then comes the match expression, where we check the result. If the file was
successfully opened (Ok variant), we assign it to the variable username_file.
But if there was an error (Err variant), we immediately return that error using
the Err variant. This means we're passing the error up the chain, letting the
caller handle it.

Next, we create a mutable String called username to store the contents of the
file. We use the read_to_string method on the username_file to read the file's
contents into the username string. Again, we use a match expression to handle
the result. If the read operation was successful (Ok variant), we return the
username string wrapped in the Ok variant. But if there was an error (Err
variant), we return that error using the Err variant.

So, in essence, this function is propagating any errors that occur during the
file reading process. It's saying, "Hey, if something goes wrong, I'm not going
to handle it here. I'll let the caller decide what to do with it."

Alright, let's talk about propagating errors. When you have a function that can
potentially fail, you can return the error to the calling code instead of
handling it right there. This gives more control to the caller, who might have
more information or specific logic to decide how to handle the error.

Take a look at this code in Listing 9-6. We have a function that reads a
username from a file. Now, if the file doesn't exist or can't be read, instead
of handling the error within the function, we return it to the calling code.

The return type of this function is Result<String, io::Error>. In simple terms,
it means that the function can either return a value of type String if
everything goes well (wrapped in the Ok variant), or it can return an error of
type io::Error (wrapped in the Err variant).

Now let's dive into the implementation of the function. We start by trying to
open the file using File::open. The result of this operation is stored in the
variable username_file_result.

Next, we have a match expression to handle the result. If the file was
successfully opened (Ok variant), we assign it to the variable username_file.
But if there was an error (Err variant), we immediately return that error using
the Err variant. This means we're passing the error up the chain to the calling
code.

Then, we create a mutable String called username to store the contents of the
file. We use the read_to_string method on the username_file to read the file's
contents into the username string. Again, we use a match expression to handle
the result. If the read operation was successful (Ok variant), we return the
username string wrapped in the Ok variant. But if there was an error (Err
variant), we return that error using the Err variant.

So, in essence, this function is propagating any errors that occur during the
file reading process. It's saying, "Hey, if something goes wrong, I'm not going
to handle it here. I'll let the caller decide what to do with it."

Now, the code that calls this function can handle the result and decide how to
proceed. If it receives an Ok value, it means the username was successfully read
from the file. But if it receives an Err value, it means something went wrong,
and the calling code can decide what to do with that information.

This pattern of propagating errors is quite common in Rust, and Rust provides
the question mark operator ? to make it easier. We'll explore that in more
detail later. But for now, let's continue exploring error handling techniques.

    A Shortcut for Propagating Errors: the ? Operator

Now, let's talk about a shortcut for propagating errors: the ? operator. Take a
look at this code in Listing 9-7. It's an alternative implementation of the
read_username_from_file function that achieves the same functionality as the
previous version but uses the ? operator.

Filename: src/main.rs

```rust
use std::fs::File;
use std::io::{self, Read};

fn read_username_from_file() -> Result<String, io::Error> {
    let mut username_file = File::open("hello.txt")?;
    let mut username = String::new();
    username_file.read_to_string(&mut username)?;
    Ok(username)
}
```
Listing 9-7: A function that returns errors to the calling code using the ?
operator

So, what does the ? operator do? Well, when you place the ? after a Result
value, it works in a similar way to the match expressions we used earlier. If
the Result is an Ok value, the value inside the Ok variant will be returned from
the expression, and the program will continue executing. But if the Result is an
Err value, the Err will be returned from the entire function as if we had used
the return keyword. This means the error value gets propagated up to the calling
code.

In the code snippet, we can see the ? operator being used after each operation
that can potentially return an error. First, we try to open the file using
File::open. If it succeeds, the file handle is assigned to the variable
username_file, and the program continues. But if an error occurs, the ? operator
will return that error, and the function will terminate, passing the error to
the calling code.

Next, we create a mutable String called username to hold the contents of the
file. We use the read_to_string method on the username_file to read the file's
contents into the username string. Again, the ? operator is used. If the read
operation succeeds, the contents are stored in the username string, and the
program continues. But if an error occurs, the ? operator will return that
error, and the function will terminate.

Finally, if everything goes well, we return the username string wrapped in the
Ok variant to indicate success.

By using the ? operator, we can simplify the code and remove the need for
explicit match expressions. It makes the code more concise and easier to read.


Here's the thing: there's a subtle difference between the match expression we
saw in Listing 9-6 and the ? operator. When the ? operator is used on an error
value, it goes through a conversion process using the from function defined in
the From trait of the standard library. This conversion allows the error type to
be transformed into the error type specified in the return type of the current
function. This feature is particularly handy when a function wants to return a
single error type to represent all the possible failure scenarios, even if those
failures can occur due to different reasons.

Let me give you an example to illustrate this point. In Listing 9-7, imagine
that we modify the read_username_from_file function to return a custom error
type called OurError, which we define ourselves. We can also implement the From
trait for OurError and provide an implementation that converts an io::Error into
an OurError. By doing this, the ? operator, when used in the
read_username_from_file function, will automatically call the from function to
convert the error types without us having to write any additional code.

So, in the context of Listing 9-7, when the ? operator is used at the end of the
File::open call, it will return the value inside an Ok to the variable
username_file. However, if an error occurs, the ? operator will exit the
function early and pass the Err value to the calling code. The same applies to
the ? operator used at the end of the read_to_string call.

This behavior of the ? operator, combined with the From trait, provides a
convenient way to handle error conversions and unify different error types into
a single, consistent error type within a function. It reduces the need for
explicit error handling code and allows for more expressive and concise error
propagation.

So, to sum it up, the ? operator not only simplifies error handling by
automatically propagating errors, but it also leverages the From trait to
perform error conversions when necessary.

Let me tell you something, folks. The ? operator is a game-changer. It
simplifies the heck out of error handling and makes our code cleaner and more
concise. Just take a look at Listing 9-8.

Filename: src/main.rs

```rust
use std::fs::File;
use std::io::{self, Read};

fn read_username_from_file() -> Result<String, io::Error> {
    let mut username = String::new();

    File::open("hello.txt")?.read_to_string(&mut username)?;

    Ok(username)
}
```

Listing 9-8: Chaining method calls after the ? operator

We start by creating a new empty String called username, just like before. But
here's where things get interesting. Instead of creating a separate variable for
the file handle and chaining the read_to_string method to it, we can chain it
directly after the File::open("hello.txt")? expression. And guess what? We still
have that ? at the end of the read_to_string call to handle any potential
errors.

By doing this, we eliminate unnecessary variables and make the code flow more
smoothly. It's like a well-oiled machine, folks. And at the end, we return an Ok
value containing the username, just like before. The functionality is exactly
the same as in Listing 9-6 and Listing 9-7, but this is a more ergonomic and
compact way of writing it.

Listing 9-9 shows a way to make this even shorter using fs::read_to_string.

Filename: src/main.rs

```rust
use std::fs;
use std::io;

fn read_username_from_file() -> Result<String, io::Error> {
    fs::read_to_string("hello.txt")
}
```

Listing 9-9: Using fs::read_to_string instead of opening and then reading the
file

But wait, there's more! In Listing 9-9, we take it to the next level. We say
goodbye to File::open and read_to_string and introduce fs::read_to_string. This
nifty function does it all for us. It opens the file, creates a new String,
reads the file contents, and puts it all neatly into that String. And just like
that, we're done!

Now, I know what you're thinking. Using fs::read_to_string doesn't give us the
opportunity to dive deep into error handling like we did before. But hey,
sometimes convenience is king, right? And in this case, fs::read_to_string saves
us a lot of typing and makes our code more readable.

So, folks, that's the beauty of the ? operator and these handy functions
provided by the standard library. They make error handling a breeze and let us
focus on what really matters: getting things done.

    Where The ? Operator Can Be Used

Let me tell you, folks, the ? operator is pretty powerful, but it does have its
limits. You can't just slap that ? operator anywhere you want. It has rules,
just like everything else in life.

In Listing 9-10, we have an example that shows what happens when you try to use
the ? operator in a function that has a return type that's incompatible with the
value you're using it on. Take a look at this code:

Filename: src/main.rs

```rust
[This code does not compile!] 
use std::fs::File;

fn main() {
    let greeting_file = File::open("hello.txt")?;
}
```

Listing 9-10: Attempting to use the ? in the main function that returns () won’t
compile

This code tries to open a file using File::open, and we're all excited about
using that ? operator. But hold on a second! The main function here has a return
type of (), not Result. And that's where the problem lies.

When we try to compile this code, we get hit with an error message that tells us
exactly what's wrong:

```rust
$ cargo run Compiling error-handling v0.1.0 (file:///projects/error-handling)
   error[E0277]: the `?` operator can only be used in a function that returns
   `Result` or `Option` (or another type that implements `FromResidual`) -->
   src/main.rs:4:48 | 3 | fn main() { | --------- this function should return
   `Result` or `Option` to accept `?` 4 | let greeting_file =
   File::open("hello.txt")?; | ^ cannot use the `?` operator in a function that
   returns `()` | = help: the trait `FromResidual<Result<Infallible,
   std::io::Error>>` is not implemented for `()`
```

For more information about this error, try `rustc --explain E0277`. error: could
not compile `error-handling` due to previous error

This code tries to open a file using File::open, and we're all excited about
using that ? operator. But hold on a second! The main function here has a return
type of (), not Result. And that's where the problem lies.

When we try to compile this code, we get hit with an error message that tells us
exactly what's wrong:

Wow, that's a mouthful! Basically, it's telling us that we can only use the ?
operator in a function that returns Result, Option, or another type that
implements FromResidual. And our main function, well, it returns ().

So, what can we do to fix this? We have a couple of options. One option is to
change the return type of our function to be compatible with the value we're
using the ? operator on. That's one way to go about it. The other option is to
use a match or one of the Result<T, E> methods to handle the Result<T, E> in a
different way.

It's all about finding the right tool for the job, folks. Sometimes the ?
operator is the perfect fit, and other times we need to explore alternative
approaches. The key is understanding when and where we can use it to its full
potential.

You know, folks, the ? operator is quite versatile. It's not just for Result
values; you can use it with Option values too! That's right, you heard me
correctly.

Let me show you an example in Listing 9-11. We have a nifty little function
called last_char_of_first_line. What this function does is find the last
character of the first line in the given text. And guess what? We're using the ?
operator on an Option<T> value here.

```rust
fn last_char_of_first_line(text: &str) -> Option<char> {
    text.lines().next()?.chars().last()
}
```

Listing 9-11: Using the ? operator on an Option<T> value

This function returns an Option<char> because, hey, there might be a character
there, or there might not be. It's all up in the air. So here's what the code
does:

We take the text string slice argument and call the lines method on it. That
gives us an iterator over the lines in the string. Then we call next on the
iterator to get the first value from it. Now, if the text happens to be an empty
string, that call to next will give us None. And here's the cool part: the ?
operator steps in and says, "Hey, we're done here. Return None right now." It
saves us from doing any more work. But if the text is not empty, next will
return a Some value containing a string slice of the first line.

We then use the ? operator again to extract that string slice. And now we can
call chars on that string slice to get an iterator of its characters. We're only
interested in the last character of this first line, so we call last to get the
last item in the iterator. And here's the thing: this last call returns an
Option. Why? Well, it's possible that the first line is empty, like if the text
starts with a blank line. In that case, the last character would be None. But if
there is a last character, it will be returned in the Some variant.

Now, you might be thinking, "Wow, that's a lot of logic." And you're absolutely
right! But thanks to the ? operator, we can express all of this in just one
line. It's concise and elegant. If we couldn't use the ? operator on Option,
we'd have to resort to more method calls or even a match expression. Trust me,
it wouldn't be pretty.

Now, folks, let's talk about some rules when it comes to using the ? operator.
You can use the ? operator on a Result in a function that returns Result, and
you can use it on an Option in a function that returns Option. But here's the
catch: you can't mix and match them. The ? operator won't magically convert a
Result to an Option or vice versa. If you need to do that, you gotta use methods
like ok on Result or ok_or on Option to make the conversion explicit.

Now, let's focus on the main function for a moment. The main function is special
because it's the entry and exit point of executable programs. And let me tell
you, it has some restrictions on what its return type can be to make sure
everything behaves as expected.

In most cases, the return type of main is (). Yeah, that's right, just a plain
old unit type. But guess what? Main can also return a Result<(), E>. Look at
Listing 9-12, where we changed the return type of main to Result<(), Box<dyn
Error>> and added Ok(()) as the return value at the end. And you know what? This
code compiles perfectly fine.


```rust
use std::error::Error;
use std::fs::File;

fn main() -> Result<(), Box<dyn Error>> {
    let greeting_file = File::open("hello.txt")?;

    Ok(())
}
```

Listing 9-12: Changing main to return Result<(), E> allows the use of the ?
operator on Result values

In this listing, we have the same code as in Listing 9-10, but we've changed the
return type of main to Result<(), Box<dyn Error>>. What's this Box<dyn Error>
you ask? Well, it's a trait object, which we'll dive into in Chapter 17. But for
now, just think of it as "any kind of error." By specifying Box<dyn Error> as
the error type, we're saying that this main function can return any kind of
error.

Now, here's the cool part. Using the ? operator on a Result value in a main
function with the error type Box<dyn Error> is totally allowed. It lets us
return any Err value early, and it works like a charm. Even if the body of this
main function only returns errors of type std::io::Error, this signature will
still be correct. So, we're prepared for whatever the code throws at us.

So there you have it, my friends. You now know how the ? operator behaves in
different contexts, and you're equipped to handle the main function with a
Result return type.

Alright, let's talk about how the main function works in Rust. When a main
function returns a Result<(), E>, here's what happens: if main returns Ok(()),
the executable will exit with a value of 0. But if main returns an Err value, oh
boy, things get interesting. The executable will exit with a nonzero value. You
see, in languages like C, successful programs return 0, and programs that mess
up return some other nonzero value. Rust follows this convention too because it
wants to play nice with the other kids on the block.

But here's the deal, my friends. The main function can actually return any type
that implements the std::process::Termination trait. This trait has a nifty
function called report that returns an ExitCode. If you're curious about
implementing the Termination trait for your own types, just hop over to the
standard library documentation. It's all there, waiting for you to explore.

Now, let's take a moment to reflect on the big question: when should we use
panic! and when should we return a Result? It's like making decisions in life,
you know? You gotta think about the context, the situation, and what makes the
most sense. It's not always easy, but we'll figure it out.

Panic! is great when you encounter an unrecoverable error. Something
catastrophic happens, and there's no way to continue. So you panic! and let the
whole world know that things have gone horribly wrong. It's like screaming at
the top of your lungs, just releasing all that frustration and despair. But
remember, don't abuse the panic! button. It's for those rare moments when all
hope is lost.

On the other hand, returning a Result is perfect when you're dealing with
recoverable errors. You know, those little hiccups in life that can be handled
gracefully. With a Result, you have more control. You can handle the error, take
a deep breath, and figure out a way to move forward. It's like taking a step
back, analyzing the situation, and finding a solution.

So, my friends, when you're faced with an error, think about the severity of the
situation. Is it a panic-worthy moment, or can you handle it with a Result?
