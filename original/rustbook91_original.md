    Unrecoverable Errors with panic!

Alright, folks, let's talk about the panic! macro in Rust. When things go
haywire and there's no way to recover, that's when you bring out the big guns:
panic!

Now, there are two ways to unleash a panic in your code. The first one is when
something really messed up happens, like trying to access an array way beyond
its limits. You know, it's like driving your car off a cliff. Your code just
goes "BOOM!" and everything comes crashing down. It's not pretty, but it
happens.

The second way is when you're feeling particularly adventurous and you want to
cause a panic yourself. You just call the panic! macro and watch the chaos
unfold. It's like screaming "I've had enough!" and throwing all caution to the
wind.

    Unwinding the Stack or Aborting in Response to a Panic

By default, when a panic occurs, Rust starts unwinding. It's like going back in
time and undoing everything that led to the panic. Rust cleans up the stack,
tidies things up, and gracefully exits the stage. It's a bit like a magician's
act, making things disappear one by one.

But wait, there's an alternative! If you're in a hurry, if you just want to cut
to the chase, you can choose to abort instead of unwinding. It's like saying
"Screw it! I'm outta here!" and pulling the emergency brake. The program stops
dead in its tracks, without cleaning up or looking back. It's a bold move, but
sometimes you just gotta do it.

Now, if you want to make your resulting binary as small as possible, you can
switch to aborting upon a panic. Just add panic = 'abort' to the appropriate
sections in your Cargo.toml file. It's like making a conscious decision to skip
the cleanup and leave it to the operating system. It's not for the faint of
heart, but it can save you some space.

Alright, folks, that's the lowdown on panics in Rust. Sometimes you gotta let it
all out and watch your code crumble. But remember, it's all about how you handle
those panics that truly matters.

```rust
    [profile.release]
    panic = 'abort'
```

Let’s try calling panic! in a simple program:

Filename: src/main.rs

 [This code panics!] 
fn main() {
    panic!("crash and burn");
}

Alright, folks, let's take a look at a simple program that's about to go down in
flames. It's a real "crash and burn" situation, if you know what I mean.

$ cargo run Compiling panic v0.1.0 (file:///projects/panic) Finished dev
   [unoptimized + debuginfo] target(s) in 0.25s Running `target/debug/panic`
   thread 'main' panicked at 'crash and burn', src/main.rs:2:5 note: run with
   `RUST_BACKTRACE=1` environment variable to display a backtrace

In this program, we have a humble function called main. And what does this
function do? Well, it doesn't waste any time. It just screams "panic!" at the
top of its lungs and brings everything crashing down. It's like setting off
fireworks in a library. Chaos ensues.

When you run this program, brace yourselves for what's about to happen. You'll
see some error messages pop up, letting you know that things have gone horribly
wrong. The message will tell you exactly what caused the panic and where it
happened in your code. It's like a virtual crime scene investigation,
pinpointing the exact line of code that led to the disaster.

In this case, it's pretty obvious. The error message tells us that the panic
occurred in our main.rs file, specifically on line 2, at character 5. That's
where the panic! macro was called, and that's where it all came crashing down.
It's like looking at a car crash and thinking, "Yep, that's where it all went
south."

Now, here's a pro tip: if you want to dig deeper into the chaos and see a
backtrace of all the functions involved in the panic, just run your program with
the RUST_BACKTRACE=1 environment variable. It's like turning on the floodlights
and seeing all the madness unfold. You'll get a detailed backtrace of all the
function calls that led to the panic. It's like following a trail of breadcrumbs
and trying to piece together what went wrong.

So there you have it, folks. When you want to bring your program crashing down,
just unleash the panic! macro. It's a wild ride, full of surprises and error
messages. But remember, it's all part of the debugging process. We crash, we
burn, and then we rise from the ashes and fix our code.

    Using a panic! Backtrace

We've got a situation where things are about to go completely off the rails.
It's like a roller coaster ride to hell, but hey, that's what happens when we
mess with indexes that don't exist.

In this little snippet, we have a vector called v with three elements: 1, 2,
and 3. It's all innocent and orderly at first. But then, out of nowhere, we
decide to do something crazy. We try to access the 100th element of this tiny
vector. I mean, what were we thinking? We might as well try to find Atlantis in
a kiddie pool.

Filename: src/main.rs

 [This code panics!] 
fn main() {
    let v = vec![1, 2, 3];

    v[99];
}

Listing 9-1: Attempting to access an element beyond the end of a vector, which
will cause a call to panic!

When Rust sees this madness, it panics. It's like a little voice in the code
saying, "No, no, no, you can't do that!" And just like that, chaos ensues. The
program crashes, burns, and screams, "I can't find what you're looking for!"

You see, when we use the [] operator to access an element in a vector, it's
supposed to return that element. But in this case, there is no element at
index 99. It's like asking for the meaning of life and getting a blank stare.
There's just nothing there.

So, brace yourselves for the error message. It will tell you exactly where this
disaster occurred. In this case, it happened in our main.rs file, and the panic
was caused by our attempt to access an invalid index in the vector. It's like
getting caught red-handed in the act of madness.

But fear not, my friends. This panic is here to help us. It's like a wake-up
call, reminding us to be careful with our indexes and stay within the
boundaries. It's like learning from our mistakes and becoming better
programmers. So let's embrace the panic, learn from it, and create code that's
stronger and more resilient.

Alright, folks, let's dive into the wild world of undefined behavior! In
languages like C, when you try to read beyond the end of a data structure, you
enter the realm of the unknown. It's like blindly reaching into the void and
grabbing whatever you can find. You might get lucky and stumble upon something
useful, or you might get a big, fat nothing. But hey, who needs rules anyway,
right?

But Rust is here to save the day! It takes buffer overreads seriously and puts a
stop to the madness. When you try to access an element at an index that doesn't
exist, Rust puts on the brakes and refuses to continue. It's like a protective
parent saying, "No, no, no, you can't go there!" It's all about keeping your
program safe and secure.

$ cargo run Compiling panic v0.1.0 (file:///projects/panic) Finished dev
   [unoptimized + debuginfo] target(s) in 0.27s Running `target/debug/panic`
   thread 'main' panicked at 'index out of bounds: the len is 3 but the index is
   99', src/main.rs:4:5 note: run with `RUST_BACKTRACE=1` environment variable
   to display a backtrace

So let's see what happens when we try to read an element that's way out of
bounds. We fire up our program, and bam! Rust jumps in and says, "Hold on a
second! The length of your data structure is 3, but you're trying to access
index 99. That's a big no-no!" It's like a friendly reminder to stay within the
boundaries and not go wandering off into unknown territory.

But here's the best part: Rust gives us a nice error message that tells us
exactly where this madness occurred. In this case, it happened on line 4 of our
main.rs file, right where we tried to access that pesky index. It's like shining
a spotlight on the exact spot where things went wrong.

And guess what? Rust even offers us a little bonus feature. By setting the
RUST_BACKTRACE environment variable, we can get a backtrace of the entire
journey that led to this error. It's like a detective story, where you follow
the clues from the top and work your way down. You'll see your code, code that
your code called, and maybe even some code from the Rust core or standard
library. It's like unraveling a mystery, one function at a time.

Rust is like a guardian angel, protecting us from the perils of undefined
behavior.

$ RUST_BACKTRACE=1 cargo run thread 'main' panicked at 'index out of bounds: the
len is 3 but the index is 99', src/main.rs:4:5 stack backtrace: 0:
rust_begin_unwind at
/rustc/e092d0b6b43f2de967af0887873151bb1c0b18d3/library/std/src/panicking.rs:584:5
1: core::panicking::panic_fmt at
/rustc/e092d0b6b43f2de967af0887873151bb1c0b18d3/library/core/src/panicking.rs:142:14
2: core::panicking::panic_bounds_check at
/rustc/e092d0b6b43f2de967af0887873151bb1c0b18d3/library/core/src/panicking.rs:84:5
3: <usize as core::slice::index::SliceIndex<[T]>>::index at
/rustc/e092d0b6b43f2de967af0887873151bb1c0b18d3/library/core/src/slice/index.rs:242:10
4: core::slice::index::<impl core::ops::index::Index<I> for [T]>::index at
/rustc/e092d0b6b43f2de967af0887873151bb1c0b18d3/library/core/src/slice/index.rs:18:9
5: <alloc::vec::Vec<T,A> as core::ops::index::Index<I>>::index at
/rustc/e092d0b6b43f2de967af0887873151bb1c0b18d3/library/alloc/src/vec/mod.rs:2591:9
6: panic::main at ./src/main.rs:4:5 7: core::ops::function::FnOnce::call_once at
/rustc/e092d0b6b43f2de967af0887873151bb1c0b18d3/library/core/src/ops/function.rs:248:5
note: Some details are omitted, run with `RUST_BACKTRACE=full` for a verbose
backtrace.

Listing 9-2: The backtrace generated by a call to panic! displayed when the
environment variable RUST_BACKTRACE is set

Alright, folks, let's take a look at the aftermath of a panic! It's like a crime
scene investigation, but with code. We've set the RUST_BACKTRACE environment
variable to 1, and now we're ready to unveil the backtrace, a detailed account
of what went down.

Hold on tight, because here it comes. We see a stack backtrace that takes us on
a wild journey through the inner workings of Rust. It starts with
rust_begin_unwind, a function that sets the panic in motion. Then we have
core::panicking::panic_fmt, a real heavyweight in the panic game. It's
responsible for formatting the panic message and delivering it to us in all its
glory.

But the real stars of the show are the lines that point directly to our code.
They reveal the exact location where the panic was triggered. In our case, it's
line 4 of our main.rs file, right where we tried to access that index way out of
bounds. It's like shining a spotlight on the culprit and saying, "You did this!"

Now, here's a little tip: when you're investigating a panic, start your search
from the first line that mentions a file you wrote. That's where the problem
originated. The lines above it are like a breadcrumb trail, showing you the path
that led to the panic. It's like reconstructing a puzzle, one piece at a time.

But wait, there's more! If you really want to dive deep into the nitty-gritty
details, you can set the RUST_BACKTRACE environment variable to "full". It's
like turning up the volume on the backtrace, giving you every little detail you
could ever want.

So there you have it, folks. When panic strikes, Rust is there to shed light on
the situation. It's all about understanding what went wrong, where it went
wrong, and how to fix it. So don your detective hat, follow the backtrace, and
let Rust guide you to error-free coding adventures!
