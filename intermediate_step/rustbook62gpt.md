    The match Control Flow Construct

Gather 'round for a tale of Rust's magnificent control flow construct known as
"match"! It's a powerhouse, a majestic mechanism that lets you compare values
against a series of patterns and execute code based on the match. The power of
match comes from the expressiveness of the patterns and the fact that the
compiler confirms that all possible cases are handled. It's like a sorting
machine for coins, but instead of shiny bits of metal, we're talking about the
very essence of programming!

Imagine this: you have a track, winding and twisting, with holes of various
sizes along its path. Now, picture coins gliding down that track, eagerly
searching for their rightful place. As each coin approaches a hole that matches
its size, it gracefully falls through, finding its destiny in the code block
waiting below.

And just like that, the match expression takes the stage! It's the conductor of
this grand symphony, guiding values through a series of patterns, determining
their fate. The patterns can be anything your heart desires—literal values,
variable names, wildcards, and a whole lot more! It's a playground of
creativity, a canvas for your wildest coding dreams.

Now, let's dive into an example, shall we? Picture yourself standing before a
magnificent machine, coins in hand. Your task is to identify the value of each
coin, just like a magician revealing secrets. And Rust's match is your trusty
wand, ready to weave its spell.

    Behold, the coins! Penny, Nickel, Dime, and Quarter—each with its distinct
worth. With a simple match expression, we can bring clarity to this sea of
currency. Oh, the elegance! The beauty lies in the . We match each coin, one by
one, and when a match is found, the corresponding code block is activated. It's
like unraveling a mystery, one coin at a time.

Let's take a peek at the magic incantation itself:

```rust
enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter,
}

fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```

Do you see it? The match expression, like a wizard's potion, takes the coin and
dances through the patterns. If it stumbles upon a Penny, it returns the value
of 1. A Nickel, and it reveals the secret of 5. A Dime, and the spell
conjures 10. And finally, a Quarter! Ah, the culmination of this enchantment—a
value of 25, revealed for all to see.

But here's the real wonder: the compiler, that watchful guardian of correctness,
ensures that no coin is left unaccounted for. It's like having an army of
fact-checking elves, making sure that all possible cases are handled. With
Rust's match, we code with confidence, knowing that every scenario is covered.

Ah, behold the match! Let's unravel its inner workings and dance through its
steps like a graceful ballerina. You see, the match is a clever beast, distinct
from its cousin, the if statement. While the if demands a Boolean condition, the
match embraces all types of expressions. It's like comparing apples to oranges,
but in the world of code!

Now, let's dissect the match in our value_in_cents function. Picture this: we
begin with the match keyword, a grand entrance that sets the stage for the
forthcoming drama. The expression that follows, in our case, is the marvelous
coin itself. It's like the protagonist of our story, the very essence of our
enchantment. Coin, is an enum we crafted with care.

Next, we encounter the match arms, a delightful duo of pattern and code. Each
arm is a treasure chest, waiting to be unlocked. The pattern, like a secret
code, tries to find a match with the value we hold dear. If it succeeds, ah,
then the magic happens! The code associated with that pattern springs to life,
like a genie from a bottle.

In our grand example, the first arm holds the pattern Coin::Penny. Ah, what a
humble coin, but it deserves its moment in the spotlight. As the pattern matches
the coin we possess, the => operator leads us to the promised land—the code
block that simply returns the value 1. It's like a tiny revelation, a glimpse
into the world of pennies and their worth.

But the show doesn't stop there! Each arm takes its turn, like a revolving door
of possibilities. If a pattern doesn't match the value we hold, fear not, for
the match continues its quest, searching for the perfect match. It's like a
coin-sorting machine, guiding values through the patterns until the right one is
found. We can have as many arms as we please, each adding a new layer of
intrigue. In our wondrous example, we have four arms—four chances to uncover the
value of our coins.

Ah, the code associated with each arm is an expression. It's a spark of
brilliance, a burst of creativity. And that expression, holds the key to the
kingdom. Its value, like a magnificent jewel, becomes the final result of the
match expression. It's the treasure we sought, the ultimate reward for our
coding odyssey.

Let's explore the curly wonders of the match arms! You see, when the code within
an arm is short and sweet, we often forgo the curly brackets. It's like taking a
shortcut, a little trick to keep things concise and elegant. In our example,
each arm effortlessly returns a value, and no curly brackets are needed. Simple,
right?

But hold on tight, for if you desire to weave a more intricate tale with
multiple lines of code in an arm, then the curly brackets come into play. It's
like opening a treasure chest, revealing the hidden depths of your coding
prowess. Oh, the possibilities!

Let me paint you a picture. Imagine a code block enclosed in those lovely curly
brackets, like a cozy home for your expressions to dwell. And here's the secret:
the comma that usually follows an arm becomes optional. It's like a punctuation
party, where rules are bent for the sake of beauty.

To illustrate, feast your eyes upon this snippet:

```rust
fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => {
            println!("Lucky penny!");
            1
        }
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```

In this enchanting code, our first arm, the Coin::Penny, yearns for a bit more
attention. It craves a grand entrance, and the curly brackets provide just that.
As the match finds a Penny, a delightful message is printed, declaring the
coin's luckiness. And then, the code within the brackets unfolds—a value of 1
emerges, completing the arm's performance.

Ah, but fear not! The other arms, with their simpler desires, continue to
enchant without the need for brackets. A Nickel yearns for the value of 5, a
Dime reveals its worth as 10, and a Quarter stands proud with a value of 25.
Each arm knows its role, whether simple or complex, and the match expression
dances through them with grace.

And here's the twist: even within the curly brackets, the last expression of the
block becomes the ultimate return value of the arm. It's like the crescendo of a
symphony, the final note that resonates in our ears. In our captivating example,
the Lucky Penny arm returns the value of 1, even after uttering its magical
incantation.

    Patterns That Bind to Values

Prepare yourselves for a twist in our tale of match arms! We're about to venture
into the realm of patterns that bind to values. It's like a magical bond, where
patterns reach out and embrace the very essence of the values they match. And
let me tell you, it's a sight to behold!

Now, picture this: we have an enum, a mystical construct that holds the key to
our programming adventures. But wait, there's a secret! One of the enum
variants, the mighty Quarter, carries an extra treasure within—a value that
represents a state of the grand United States. Yes, my friends, quarters from
1999 to 2008 boasted unique designs for each state, making them true gems among
coins.

To unlock this hidden power, we shall infuse our Quarter variant with the magic
of a UsState value. And behold, the transformation has begun, as demonstrated in
this wondrous code:

```rust
#[derive(Debug)] // so we can inspect the state in a minute
enum UsState {
    Alabama,
    Alaska,
    // --snip--
}

enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(UsState),
}
```

Ah, do you see it? Our UsState enum takes center stage, offering a multitude of
states to choose from. Alabama, Alaska, and countless others stand ready to join
the ranks of our glorious quarters. But it is the Quarter variant, that becomes
the vessel for these state treasures. Like a hidden chamber within the coin, it
holds the power to bind the UsState value within its grasp.

And here's where the match arms shine. They don't merely match values; they also
have the power to extract the secrets within. It's like a key that unlocks a
door, revealing the riches concealed inside. With the match, we can dance
through the patterns and bind the values they embrace.


Let me take you on a whimsical journey into the world of state quarters and the
mystical match expression! Picture this: you're sorting through your change,
just minding your own business, when suddenly, your friend's quest to collect
all 50 state quarters comes to mind. And there it is, my friends—the perfect
opportunity for a Rusty adventure!

So, you've got your coins laid out before you—pennies, nickels, dimes, and the
elusive quarters with their state treasures. But here's the twist, my friends:
we're not just sorting coins; we're on a mission to uncover the hidden gems
within! And to do that, we shall unleash the power of the match expression!

With each coin you encounter, the match expression leaps into action, seeking a
pattern that matches its essence. And behold, a new pattern emerges—a
Coin::Quarter with its secret state value nestled inside. But we don't stop
there, my friends. Oh, no! We go one step further and introduce a variable, a
magical entity called state, which binds to the state value within the
Coin::Quarter variant.

Now, you might wonder, why all this binding business? The answer lies in the art
of extraction! Once the match finds a Coin::Quarter and the state value is bound
to our variable, we have the key to unlock the mystery. And what do we do then?
We celebrate! We call out the name of the state with a resounding cry, as if
announcing the discovery of a hidden treasure.

Let me show you the enchantment in action:

```rust
fn value_in_cents(coin: Coin) -> u8 {
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter(state) => {
            println!("State quarter from {:?}!", state);
            25
        }
    }
}
```

Imagine this: if we were to call value_in_cents(Coin::Quarter(UsState::Alaska)),
the match expression takes center stage. Coin::Quarter(UsState::Alaska) steps
into the spotlight, and the match arms begin their dance. As each arm is
compared, they try to find a match, but none succeed until the magic moment
arrives—the Coin::Quarter(state) pattern is reached!

And there it is! The variable state binds to the value UsState::Alaska, the
hidden gem within the Coin::Quarter variant. Oh, the joy! With the power of
binding, we can now unveil the state's name with a flourish, as we exclaim,
"State quarter from Alaska!"


    Matching with Option<T>

Ah, let's dive deeper into the world of matching, this time with the magnificent
Option<T> by our side! Just like before, we're unraveling the mysteries of the
match expression, but this time our focus shifts to the intriguing variants of
Option<T>. Get ready for a wild ride!

Imagine this: you have an Option<i32>, a container that could hold a value or be
empty. It's like Schrödinger's box, housing the possibility of existence or
non-existence. And here's the challenge—we want to create a function that takes
this Option<i32> and, if there's a value inside, adds 1 to it. But if the option
is empty, we want to return None, avoiding any risky operations.

With the power of match, this task becomes a breeze! Behold, the code that holds
the answer to our quest:

```rust
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        None => None,
        Some(i) => Some(i + 1),
    }
}

let five = Some(5);
let six = plus_one(five);
let none = plus_one(None);
```

In this glorious function, plus_one, the match expression takes center stage
once again. It's like a grand performance, my friends, with Option<i32> variants
stepping into the spotlight. As we compare each variant, the magic unfolds.

First, the match encounters None—a void, an absence of value. And in this case,
my dear companions, we simply return None, gracefully avoiding any operations.
No risks, no fuss.

```rust
None => None,
```

But then, the match encounters the elusive Some variant. Oh, what joy! It means
we have a value—a glimmer of hope within the Option<i32>. And what do we do? We
embrace it, we seize the opportunity, and with a flourish, we add 1 to that
value. The Some(i) pattern allows us to bind the value to the variable i,
empowering us to perform this magnificent addition. And behold, we return the
result, wrapped within the comforting arms of Some.

```rust
Some(i) => Some(i + 1),
```

Now, let's witness this spectacle in action! We create a Some(5), a container
housing the value 5. We call upon our trusty function plus_one, passing this
container as our guide. And lo and behold, the match dances through its
patterns, finding the Some(i) that matches our container. It takes the value,
adds 1, and wraps it within the wondrous Some once again. The result? We receive
a new container, six, containing the value 6. Oh, the joy!

But wait, there's more! We dare to venture into the realm of None, an empty
container. We call upon plus_one once again, presenting None as our offering.
And what happens? The match encounters the None pattern, recognizing the absence
of value. With grace and elegance, it returns None, allowing us to bask in the
serenity of emptiness.

So, embrace the power of matching with Option<T>! Let it guide you through the
twists and turns of existence and non-existence. Uncover the values, perform the
operations, and revel in the joy of Rust programming. And remember, within the
match expression lies the key to unlocking the wonders of Option<T>. Now, go
forth and conquer the vast realm of Rust with your newfound knowledge!

Ah, the artistry of combining match and enums! This dance of comparisons and
bindings brings great power to the realm of Rust. Once you embrace its nuances,
my dear comrades, you'll yearn for its presence in all languages. It is a
favorite among the users, consistently delivering joy and satisfaction.

Imagine this version of our trusty plus_one function, my friends, but beware—it
holds a treacherous bug that will not go unnoticed by Rust's watchful eye:

```rust
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        Some(i) => Some(i + 1),
    }
}
```

Oh, but alas! We have failed to handle the None case, my comrades. This code, it
brings a bug that Rust is well-equipped to catch. When we attempt to compile
this code, a mighty error befalls us:

```rust
error[E0004]: non-exhaustive patterns: `None` not covered --> src/main.rs:3:15 |
3 |         match x { |               ^ pattern `None` not covered | note:
  `Option<i32>` defined here -->
      /rustc/d5a82bbd26e1ad8b7401f6a718a9c57c96905483/library/core/src/option.rs:518:1
      | = note:
      /rustc/d5a82bbd26e1ad8b7401f6a718a9c57c96905483/library/core/src/option.rs:522:5:
      not covered = note: the matched value is of type `Option<i32>` help:
      ensure that all possible cases are being handled by adding a match arm
      with a wildcard pattern or an explicit pattern as shown |
      4 ~             Some(i) => Some(i + 1),
      5 ~             None => todo!(), |

For more information about this error, try `rustc --explain E0004`. error:
could not compile `enums` due to previous error
```
Ah, the wisdom of Rust shines brightly! It knows that we have not
covered all the possibilities, and it even points out the pattern we have
forgotten. Matches in Rust are truly exhaustive. We must traverse
every nook and cranny, leaving no possibility unattended for our code to be
deemed valid. Especially in the realm of Option<T>, Rust
shields us from the perils of assuming we have a value when we might be facing
the dreaded null. It protects us, ensuring that we do not stumble upon the
billion-dollar mistake, for it is an abyss we must never venture into.

So, embrace the notion of
handling all possibilities within your match expressions, whether it be through
a wildcard pattern or an explicit pattern. Only then shall your code stand tall,
free from the clutches of bugs and the wrath of the compiler. 

    Catch-all Patterns and the _ Placeholder

I've got another trick up my sleeve to share with you. Picture
this: you're playing a game, and when you roll a 3 on the dice, your character
doesn't move, but instead gets a shiny new hat. Now, if you roll a 7, well,
tough luck—your character loses a fancy hat. And for any other number, your
character moves that many spaces on the game board. Got the scenario in your
mind? Great!

Now, let's see how we can bring this game to life using Rust's match. But
hold on, I'm gonna keep it simple by hardcoding the dice roll value as 9.
Here's the match that does the magic:

```rust
let dice_roll = 9;
match dice_roll {
    3 => add_fancy_hat(),
    7 => remove_fancy_hat(),
    other => move_player(other),
                                        }

fn add_fancy_hat() {}
fn remove_fancy_hat() {}
fn move_player(num_spaces: u8) {}
```

You see, we have three arms in this match. The first arm matches the pattern 3,
where we call the add_fancy_hat function. If the dice roll matches 7, the second
arm springs into action and invokes remove_fancy_hat. But what about the other
numbers? Well, that's where the last arm comes in.

The last arm has a pattern that simply uses the variable other. This pattern is
like a catch-all that matches any value that wasn't caught by the previous arms.
And what do we do with this catch-all? We pass it to the move_player function,
and our character moves the corresponding number of spaces on the game board.

But wait! There's an important rule to follow. The catch-all arm must be placed
last because the patterns are evaluated in order. If we put the catch-all arm
earlier, the other arms won't even get a chance to run. And let me tell you,
Rust doesn't take that lightly. It'll warn us if we try to add arms after a
catch-all. So, watch out for that!

Now, here's an interesting tidbit. Rust offers a special pattern for those cases
when we want a catch-all but don't actually care about the value. It's called
the underscore pattern—_ for short. This little fella matches any value but
doesn't bother binding to it. So, if you're not planning to use the value, Rust
won't nag you about an unused variable. Handy, isn't it?

Alright, let's shake things up in our game! Here's the deal: if you roll
anything other than a 3 or a 7, tough luck, you gotta roll again. No fancy hats,
no hat losses—just a good ol' reroll. Got it? Alright, let's dive into the code.

We'll start with the dice roll value hardcoded as 9. Here's the updated match
that handles our new rules:

```rust
let dice_roll = 9;
match dice_roll {
    3 => add_fancy_hat(),
    7 => remove_fancy_hat(),
    _ => reroll(),
}

fn add_fancy_hat() {}
fn remove_fancy_hat() {}
fn reroll() {}
```

See what we did there? We swapped out the variable named other with a cool new
wildcard pattern: _. This little wildcard acts as our catch-all, ready to jump
in whenever the dice roll doesn't match 3 or 7. In this case, it calls the
reroll function, giving you another shot at changing your destiny.

Now, here's the beauty of it—since we're using the wildcard pattern _, we're
explicitly saying, "Hey, Rust, we don't care about the value, so don't bother
binding it." And you know what? Rust respects that. It won't bug you about an
unused variable. It's like having a wildcard in your back pocket, ready to
handle any unexpected roll that comes your way.

And guess what? Our updated code still meets the exhaustiveness requirement.
We're covering all possibilities—rolling a 3, rolling a 7, or rolling anything
else that triggers a reroll. Nothing slips through the cracks. Rust's got our
back, making sure we don't forget a single scenario.

Alright, we're wrapping things up with one last twist to our game. Get ready for
it! Now, if you roll anything other than a 3 or a 7, we're changing the rules so
that nothing else happens on your turn. Yeah, I know, it's a bit anticlimactic,
but bear with me. We can handle this situation using the unit value, which is
basically an empty tuple. Let me show you how it's done:

```rust
let dice_roll = 9;
match dice_roll {
    3 => add_fancy_hat(),
    7 => remove_fancy_hat(),
    _ => (),
}

fn add_fancy_hat() {}
fn remove_fancy_hat() {}
```

In this updated match, we've added a catch-all arm using the underscore
pattern—_. It's like a safety net for any value that didn't match the previous
patterns. But here's the kicker: we don't want anything to happen in this case.
So, we use the unit value—yep, that empty tuple—as the code that goes with the
catch-all arm. It's like saying, "Hey, Rust, we're not interested in this value,
so just move along!"

And that's it! We've covered the basics of patterns and matching in Rust. But
hold your horses, there's more to come in Chapter 18. We'll dive deeper into
this topic and explore all the intricacies. For now, let's move on to something
else. We're about to unveil the if let syntax, a nifty tool that comes in handy
when the match expression starts getting a bit too verbose.

So stay tuned, because Rust keeps on surprising us with its pattern-matching
prowess. It's like a puzzle waiting to be solved, and we're just getting
started. Until next time, happy coding!
