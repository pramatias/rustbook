The match Control Flow Construct

Let's chat about Rust's badass control flow feature, match. You know when you
got your first bike or skates and were stoked to figure out how they worked so
you could use them to cruise around town? Well, matching works way cooler than
that. Picture this: you write code as an adventurous techie trying to solve life
mysteries using the magic wand called match. Suddenly, you find yourself knee
deep in battle with code constructs, comparing values against some patterns.
Like the most epic laser battle ever, the results determine which actions will
ensue.

In this grand spectacle, values flow like coins along a mesmerizing track,
seeking their perfect fit. The patterns become the keyholes, each one offering a
passage to a unique code block. It's a wild, laser-filled battle, where the
clash of logic determines the fate of our hero's code.

The shining stars of currency: Penny, Nickel, Dime, and Quarter. Each coin
possesses its own unique worth, waiting to be discovered. And fear not, for
with a simple match expression, we can bring clarity to this sea of wealth. The
beauty lies in its rhythm, its cadence. We embark on a journey of discovery,
one coin at a time, as the match expression reveals its magic.
 
```rust
enum Coin { Penny, Nickel, Dime, Quarter, }

fn value_in_cents(coin: Coin) -> u8{
    match coin {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}
```

Listing 6-3: An enum and a match expression that has the variants of the enum as
its patterns

As each coin takes center stage, it performs its designated role, capturing the
hearts of the audience—the pieces of code executed in response to their call.
Imagine the moment when Penny graces the stage, revealing its value of 1. The
crowd erupts in cheers—or rather, the code returns the cherished number. And
behold! A Nickel steps forward, exposing the secret of 5. The enchantment
intensifies as a Dime takes its turn, conjuring a value of 10. But wait, my
friend, for the grand finale is yet to come. A hush falls over the audience as
the mighty Quarter emerges, unveiling a value of 25—a climax that leaves us all
in awe.

At first glance, match statements may seem humble, focused on hunting down a
single expression or two. But don't be fooled by their simplicity; it's
precisely this laser-like focus that allows them to catch their prey.
No-nonsense questions, just straightforward matching to find that perfect fit.
And let me tell you, these bad boys aren't limited to a single type of
comparison like the if statement. Oh no, sirree! Our pals, the match
expressions, can handle anything from integers to strings, and even complex
patterns. They're versatile like that.

But here's the real kicker, my friend. Rust's match expression is like an
enigmatic diva, stealing the center stage in our value_in_cents function. It
struts its stuff like a superstar on Broadway, leaving the audience in awe. This
showstopper knows how to pack a punch and deliver jaw-dropping antics.

As the curtains rise, we set the scene with the mighty match keyword, signaling
the start of an epic performance like no other. And our star attraction? The
humble penny and nickel, dressed in a shiny new suit called an enum. We crafted
this ensemble with great care, ensuring that our actors shine bright on this
cybernetic stage.

Each match arm holds the key to a specific pattern, ready to be matched against
our value. With the => operator, the code associated with each arm awaits its
cue, like a faithful partner in a synchronized dance. The match expression
compares the value against each pattern, one by one, in the order they appear.
And just like a coin-sorting machine, if a pattern matches, the corresponding
code executes. But if a pattern doesn't find its match, the show goes on, and
execution continues to the next arm.

We can have as many arms as we need, my friend. In our grand spectacle, our
match expression boasts four arms, each with its own pattern and code, creating
a symphony of logic and creativity.

Now, here's the exciting part: the code within each arm is an expression in
itself. It's like a magic trick, where the resultant value of the matching arm
becomes the grand finale, the value that gets returned for the entire match
expression.

At first glance, match statements may seem humble, focused on hunting down a
single expression or two. But don't be fooled by their simplicity; it's
precisely this laser-like focus that allows them to catch their prey.
No-nonsense questions, just straightforward matching to find that perfect fit.
And let me tell you, these bad boys aren't limited to a single type of
comparison like the if statement. Oh no, sirree! Our pals, the match
expressions, can handle anything from integers to strings, and even complex
patterns. They're versatile like that.

Rust's match expression is like an enigmatic diva, stealing the center stage in
our value_in_cents function. It struts its stuff like a superstar on Broadway,
leaving the audience in awe. This showstopper knows how to pack a punch and
deliver jaw-dropping antics.

As the curtains rise, we set the scene with the mighty match keyword, signaling
the start of an epic performance like no other. And our star attraction? The
humble penny and nickel, dressed in a shiny new suit called an enum. We crafted
this ensemble with great care, ensuring that our actors shine bright on this
cybernetic stage.

Each match arm holds the key to a specific pattern, ready to be matched against
our value. With the => operator, the code associated with each arm awaits its
cue, like a faithful partner in a synchronized dance. The match expression
compares the value against each pattern, one by one, in the order they appear.
And just like a coin-sorting machine, if a pattern matches, the corresponding
code executes. But if a pattern doesn't find its match, the show goes on, and
execution continues to the next arm.

We can have as many arms as we need. In our grand spectacle, our match
expression boasts four arms, each with its own pattern and code, creating a
symphony of logic and creativity.

Now, here's the exciting part: the code within each arm is an expression in
itself. It's like a magic trick, where the resultant value of the matching arm
becomes the grand finale, the value that gets returned for the entire match
expression.

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
The really cool part happens when we apply some curly love around the Penny arm.
Why do this guy deserve such attention? Well, let's be honest, one cent isn't
exactly mind-boggling. This dude wants to share a secret with you. The code
inside that brace gives him a chance to express himself better than a tweet
character limit allows. So once Penny shows up, and the computer performs its
miracles behind closed doors, out comes the cherished output of one unit of
currency! To quote ol' Will Shakespeare: "One penny paid, another not."

You know how a musician might have different instruments and ways of playing a
song? Yeah well, these little buggers called Arms are like that but instead they
use numbers and letters. Each Arm plays a unique melody using the values 5, 10,
or 25 like the Dime, Nickel, or Quarter instruments respectively. Even though
every instrument looks similar and just plays notes from left to right, trust me
when I say there's more going on beneath the surface.

    Patterns That Bind to Values

Imagine a magical bond, where patterns stretch out their arms and embrace the
very essence of the values they encounter. It's a sight that will leave you
breathless, I assure you!

Now, let's focus our attention on a particular hero of our story—the one and
only Quarter. But hold on tight, because this Quarter has a secret surprise up
its sleeve! Picture this: from the years 1999 to 2008, each United States
quarter boasted a unique design representing one of the 50 states. Talk about a
rare artifact or a whimsical gift from Santa Claus himself!

But let's not get carried away. Back to our tale! The match expressions join
forces, engaging in a captivating dance. One pattern takes the lead, executing a
powerful move, and then gracefully passes the baton to the expression partner.

Now, let's turn our gaze to the noble Coin enum. At first glance, it may seem
ordinary—Penny, Nickel, Dime, and the steadfast Mighty Quarter, the heroes of
our coin collection. But wait! There's more to the Mighty Quarter than meets the
eye. Deep within its very structure, it holds a secret of epic proportions—the
legendary lineup of UsStates! Who would have thought that a humble quarter would
become the vessel for such hidden wonders?

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

Listing 6-4: A Coin enum in which the Quarter variant also holds a UsState value

As we delve into the realm of coins, a secret vault lies hidden within the
depths of the Coin enum. It's like burying a vault underground, only to discover
the shining brilliance of these state treasures. From Alabama to California, and
beyond, these coins become the golden members of the Coin family, united by a
simple and ritualistic phrase: "match."

But it is the Quarter variant that takes center stage, becoming the vessel for
these state wonders. Within the Quarter's very core, it holds the power to bind
the UsState value within its grasp. It's as if a hidden chamber exists within
the coin, safeguarding the essence of each state.

And here, my friend, is where the true magic unfolds—the enchantment of match
arms. They go beyond mere value matching; they possess the extraordinary ability
to extract the secrets held within. It's like wielding a key that unlocks a
door, revealing the hidden vault of riches. With match, we dance through the
intricate patterns, binding the values they embrace, one by one.

With each coin that crosses your path, the match expression springs to life,
seeking patterns that match their essence. And lo and behold, a new pattern
emerges—a Coin::Quarter, concealing a mystical state value within. But we won't
stop there, my friend. Oh, no! We'll take it a step further and introduce a
magical variable, known as state, which binds to the state value nestled within
the Coin::Quarter variant.

Now, brace yourself for the thrilling part! Our match expression embarks on a
heated search, like a gambler seeking that perfect card combo. And then it
happens—we hit the jackpot! A shiny Coin::Quarter appears before us, igniting a
rush of excitement. But we're not ones to leave our newfound friend stranded.
Oh, no! We bring in a companion named State, tying the knot between them in a
dance as old as time itself.

Together, we engage in an ancient ritual, delicately extracting the Quarter's
innards while whispering sweet nothings in its ear. It's a moment of connection,
my friend, where the code comes alive and secrets are revealed. The match
expression, fueled by its magical partnership with State, unlocks the hidden
wonders of the Quarter, painting a vibrant picture of its true essence.

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

The match arms begin their elegant dance, each one vying for a chance to claim a
match. With every comparison, they search for the perfect fit, but alas, none
succeed... until that magical moment arrives. Behold! The Coin::Quarter(state)
pattern emerges from the shadows, like a diamond in the rough.

And in that instant, the enchanting binding occurs, connecting the variable
state to the hidden gem within Coin::Quarter. It's as if a treasure chest has
been unlocked, revealing the marvelous UsState::Alaska—the very essence of this
Quarter coin.

Oh, the jubilation that fills the air! With the power of binding in our grasp,
we can now unveil the state's name with a triumphant flourish. Let it be known
to all who witness this spectacle: "State quarter from Alaska!"

    Matching with Option<T>

Imagine yourself clutching a magical box, its contents veiled in uncertainty.
Within this box lies the potential for a value or the abyss of emptiness. It's
as if you're caught in the paradox of Schrödinger's experiment, where the truth
of existence hangs in delicate balance. But fret not, for we are about to unlock
the secrets of this enigmatic realm.

In our quest, we encounter an Option<i32>, a container that could hold a
precious value or remain void. It's like a Pandora's box, teeming with the
possibilities of joy or emptiness. Our challenge, my friend, is to craft a
function that embraces this uncertainty. If a value resides within the
Option<i32>, we shall summon the power of addition and bestow upon it the gift
of one. However, should the option reveal its empty nature, we gracefully return
None, steering clear of perilous operations.

And how shall we accomplish this feat? Through the match expression, my friend!
Its power transcends the boundaries of mere coin comparisons or enum variants.
Whether we're traversing the realm of coins or venturing into the depths of
Option<T>, the match expression remains our trusty guide—a beacon of consistency
in a sea of possibilities.

This function is very easy to write, thanks to match, and will look like Listing
6-5.

```rust
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        None => None,
        Some(i)
            => Some(i + 1),
    }
}

let five = Some(5);
let six = plus_one(five);
let none = plus_one(None);
```

Listing 6-5: A function that uses a match expression on an Option<i32>

As our match expression takes center stage once again, Option<i32> variants step
into the spotlight, ready to amaze us with their powers. It's like a grand
spectacle, my friends, where each variant unveils its true essence.

The journey begins with None—a void, an absence of value. And in this case, we
gracefully return None, avoiding any unnecessary operations. No risks, no fuss.

```rust
None => None,
```

Now, picture this: you come across this thingie called Option<i32>. Ever heard
of it? It's a clever little entity that can hold either zero or one value. And
let me tell you, my friends, it can get quite complex. But fear not, for our
trusty match expression steps in, ready to decipher this enigma and make your
life easier.

```rust
Some(i) => Some(i + 1),
```

Here's the deal: our match expression delves into the heart of Option, searching
for that precious Some. Once it finds it, like a true hero, it returns the favor
by tossing that baby right back at ya. And not only that, it even adds a touch
of magic—by incrementing the value inside by one. Voila! The result is wrapped
up in another Option instance, ready to be embraced.

You see, the Option type can be a bit perplexing, with its zero or one value
encapsulation. But fear not, for our match expression swoops in, simplifying the
complexity by focusing solely on the presence or absence of the data inside. If
it's there (or "some"), we work our magic by adding one and wrapping it back up
in another Option; otherwise, if it's nonexistent, we gracefully return None,
saving ourselves from any unnecessary complications.

Now let’s consider the second call of plus_one in Listing 6-5, where x is None.
We enter the match and compare to the first arm:

```rust
None => None,
```

It matches! There’s no value to add to, so the program stops and returns the
None value on the right side of =>. Because the first arm matched, no other arms
are compared.

Combining match and enums is useful in many situations. You’ll see this pattern
a lot in Rust code: match against an enum, bind a variable to the data inside,
and then execute code based on it. It’s a bit tricky at first, but once you get
used to it, you’ll wish you had it in all languages. It’s consistently a user
favorite. Matches Are Exhaustive

In the next example we stumble upon a snippet of code that dances to its own
tune, refusing to compile. Oh, the audacity! Feast your eyes on this intriguing
scene:

```rust
[This code does not compile!]
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x { Some(i) => Some(i + 1),
    }
}
```

But wait! We missed something important, my dear compatriots. We neglected to
handle the None case, a fatal flaw that invites the bug to rear its ugly head.
Fear not, for Rust is no ordinary hero—it possesses a keen eye for detail and
won't let this blunder pass unnoticed.

As we attempt to compile this code, a mighty error descends upon us, casting a
shadow over our momentary lapse:

"Oh, valiant programmer! Thou hast forgotten to account for the None case! The
mighty Rust hath caught thine error and shall not suffer it to pass. Thou must
rectify thy code and make amends, for the patterns of the match must cover all
possibilities!"

```rust
$ cargo run Compiling enums v0.1.0 (file:///projects/enums) error[E0004]:
   non-exhaustive patterns: `None` not covered --> src/main.rs:3:15 | 3 | match
   x { | ^ pattern `None` not covered | note: `Option<i32>` defined here -->
   /rustc/d5a82bbd26e1ad8b7401f6a718a9c57c96905483/library/core/src/option.rs:518:1
   | = note:
   /rustc/d5a82bbd26e1ad8b7401f6a718a9c57c96905483/library/core/src/option.rs:522:5:
   not covered = note: the matched value is of type `Option<i32>` help: ensure
   that all possible cases are being handled by adding a match arm with a
   wildcard pattern or an explicit pattern as shown | 4 ~ Some(i) => Some(i +
   1), 5 ~ None => todo!(), |

For more information about this error, try `rustc --explain E0004`. error: could
not compile `enums` due to previous error
```

Oh, the genius of Rust, shining like a beacon of wisdom in the vast landscape of
programming! It knows that we haven't covered all the possibilities, and it
graciously points out the pattern we have forgotten. Rust's match expressions,
my friends, are the epitome of thoroughness. They leave no stone unturned, no
possibility unexplored, for our code to earn its validation. And when it comes
to the realm of Option<T>, Rust becomes our steadfast shield, protecting us from
the treacherous perils of assuming we possess a value when we may face the
dreaded null. It guards us against the abyss, preventing the occurrence of the
billion-dollar mistake we've discussed before.

Now, listen up, folks, 'cause here's some real advice: Forget everything you
think you know about programming, 'cause compared to the brilliance of Rust's
match expressions, you ain't got nothin'! Rust doesn't mess around with partial
solutions or half-baked workarounds. Sure, there may be times when you assume
you've covered all the possible options, only to find yourself face-to-face with
a cursed null pointer bug. Let me tell ya, that's a classic blunder you want to
steer clear of. But fear not, for Rust's match expressions won't let such
rubbish slip through the cracks. They keep things tight and secure, ensuring
that nothing gets left behind. They're your loyal companions, making damn sure
your app works its magic, no matter how the circumstances may change.

           Catch-all Patterns and the _ Placeholder

Imagine a world where rolling a die brings forth a cascade of possibilities,
each number holding a secret twist. In this particular game, the number 3 holds
a special charm. If fate gifts you with a 3, your character doesn't budge an
inch but is rewarded with a fancy, new hat. A stroke of luck, indeed!

But beware the treacherous number 7, my friend, for it brings misfortune. Should
the die tumble to a 7, your character's beloved fancy hat is cruelly snatched
away. A somber moment, no doubt.

Yet fear not, for all the other numbers hold a promise of adventure. They
dictate how far your character shall venture on the game board. Roll a 5, and
your character skips merrily five spaces ahead. Roll a 1, and they tiptoe gently
forward, embracing the thrill of progress.

Now, in this realm of Rust, we dive into the magic of the match construct. Our
trusty dice, hardcoded with the value of nine, sets the stage for our
demonstration. As we craft three remarkable functions—addFancyHat(),
removeFancyHat(), and movePlayer()—we unlock the realm of possibilities tied to
each outcome.

The addFancyHat() function, a splendid creation, adorns our character's head
with a new hat, adding a touch of elegance to their persona. removeFancyHat(),
on the other hand, unveils a cruel twist, snatching away their prized
possession, leaving them hatless and forlorn. And the movePlayer() function, ah,
it's the master of movement, propelling our character across the game board with
each step.

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

Imagine a triumvirate of functions: add_fancy_hat, remove_fancy_hat, and
move_player. Now, picture a battlefield of code where our match expression
stands tall, ready to conquer the world—well, at least to determine how the
program should act based on the roll of a dice.

In this grand spectacle, we have THREE ARMS, my friend, three arms to rule them
all! The first arm, like a knight in shining armor, handles the mighty roll of
3, simply summoning add_fancy_hat to adorn our player with elegance. Next, we
have arm number two, a guardian of the number 7, commanding the removal of the
fancy hat with a flourish. Oh, the drama!

But what happens when the dice rolls any other value? Fear not, my friend, for
the third arm steps forth—a catch-all arm! It welcomes all the other values,
guiding them to the mighty move_player function. Together, they embark on a
thrilling journey, traversing the realms of cyberspace with their own unique
space count. And here's a little secret—this extravaganza requires hardcoding
the dice value at 9, adding an extra layer of suspense to the mix.

Now, my dear comrade, let me enlighten you about the enchanting rules of Rust.
When it comes to patterns in match expressions, order matters. Thus, placing the
catch-all arm at the end ensures that no prior arms miss their chance to shine.
Rust, ever the vigilant guardian, will remind you with a resounding voice if you
accidentally switch them up. It's a gentle reminder to keep the code flowing
like a well-rehearsed symphony.

Ah, but wait, my whimsical friend, there's more to the tale! Remember when we
talked about catch-all patterns? Well, Rust has a wild card up its sleeve—a
pattern that carries the weight of absolute power. It goes by the name of "_", a
single letter that grants you dominion over anything that fails to fit into
previously defined patterns. With this pattern, my friend, you can swap cars
while wearing tutus, and Rust won't bat an eye! It's a testament to the flexible
nature of Rust, allowing you to roam the realms of creativity without
constraint.


In this new version of the game, things have taken an unexpected turn. If you
roll anything other than a 3 or a 7, it's not game over just yet. Oh no, my
friend! We're all about giving second chances here. So, when fate deals you an
unexpected roll, we spin up a reroll, giving you another shot at changing your
destiny.

But here's the real magic—meet the wildcard pattern, "_". This little rebel is
our catch-all, ready to jump in whenever the dice roll doesn't match 3 or 7.
It's like having a wildcard in your back pocket, always there to handle any
unexpected outcome that comes your way.

With the power of the wildcard pattern, we boldly declare to Rust, "Hey, we
don't care about the value, so don't bother binding it." And guess what? Rust
respects that. It won't pester you about an unused variable. It's like a nod of
understanding between you and the mighty Rust machine—a silent agreement that
you're in charge, and you know exactly what you're doing.

Imagine you're playing a thrilling board game, where every turn presents a
chance to roll the dice and unveil your destiny. But life isn't always fair, my
friend. Sometimes the dice don't roll in your favor. That's when our rebellious
companion, "Wild Card," steps in. He's like that daring maverick who defies the
rules, saying, "Screw it, I'll do my own thing!" And in the realm of Rust, Wild
Card reigns supreme.

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

No questions asked. No strings attached. Wild Card allows you to ignore the
binding and forge your own path. It's a true OG move, my friend. Just a simple
nod of understanding between you and the mighty Rust machine—a nod that says,
"Hey, we've got this under control."

And the best part? Our updated code still meets the exhaustiveness requirement.
We've covered all the possibilities, my friend, even the unexpected ones. With
the wildcard pattern by our side, we're prepared for any twist and turn the game
throws at us. It's a wild ride filled with suspense, surprises, and the thrill
of rewriting the rules.

Ah, my friend, let's embark on a thrilling journey into the depths of Rust's
match expressions, where patterns and code arms clash in a battle of wits and
creativity.

Imagine three mighty functions standing tall: add_fancy_hat, remove_fancy_hat,
and move_player. Now, picture this: the match expression steps forward, ready to
conquer the world—well, at least decide the fate of our program based on a dice
roll value.

Three arms, my friend, three arms to rule them all! The first arm, pattern #1,
takes charge when the dice rolls a triumphant 3. It calls forth the mighty
add_fancy_hat, adorning our player with a touch of elegance. Next in line,
pattern #2 claims dominion over the lucky number 7, demanding the removal of the
fancy hat—after all, no one likes an overindulgence of fanciness.

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

But what about the rest? Fear not, for the third arm emerges as a catch-all,
ready to handle any other value that dares to challenge its authority. It
courageously passes the dice roll value to the move_player function, allowing
our hero to navigate the virtual realms with precision and grace. Ah, but here's
the catch, my friend—this whole adventure hinges on hardcoding the dice value
at 9. It's a secret pact between the code and the programmer, a hidden dance
that only they can share.

Now, let's talk shop—patterns in Rust follow a certain rulebook. They march left
to right, like an orderly procession of code warriors. And to ensure no arm
misses its chance to shine, catch-all patterns must be placed last in line. Rust
has our back, my friend, it won't let us forget. If we accidentally switch
things up, it'll be quick to remind us with a friendly nudge.

But wait, there's more! Let's unleash the power of the catch-all pattern,
denoted by the illustrious underscore (_). It's the ultimate free spirit,
dancing to its own beat, not bound by any name. It's like having absolute power
over anything that doesn't fit within the previously defined patterns. You could
swap cars while wearing tutus, and Rust wouldn't bat an eye! It's a liberating
force, my friend, granting us the freedom to embrace the whimsical and
unexpected.

So, there you have it, the secrets of catch-all patterns in Rust—where code arms
and catch-alls collide, and creativity reigns supreme.
