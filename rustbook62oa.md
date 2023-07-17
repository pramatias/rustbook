    The match Control Flow Construct

let's chat about Rust's badass control flow feature, match. You know when you
got your first bike or skates and were stoked to figure out how they worked so
you could use them to cruise around town? Well, matching works way cooler than
that. Picture this: you write code as an adventurous techie trying to solve life
mysteries using the magic wand called match. Suddenly, you find yourself knee
deep in battle with code constructs, comparing values against some patterns.
Like the most epic laser battle ever, the results determine which actions will
ensue.

Remember that time you tried to pickle a gummy bear because you wanted to know
what would happen? That was funny stuff, wasn't it? But forget about that candy
experiment, 'cause we're here to talk about something even better: pattern
matching in Rust!

Suddenly, imagine yourself surrounded by piles of gold coins - that’s right,
we’re talking about the “golden” age of computing where our protagonist, Pattern
Matching, reigned supreme. In our story today, the main character takes center
stage in the form of the match expression - that’s right, it’s time for the star
of the show to take the stage, in all its glory: Match::Expression! Get ready
for some real entertainment folks, because tonight’s performance promises a
thrilling display of skillful sorcery as Rust’s renowned feature casts spells of
enchantment to make every programmer feel like a kid again playing games!

Let me walk you step-by-step, starting with an old friend who deserves some
respect: the good ol’ state value - that little rascal hiding behind the scenes,
waiting for his chance to steal the spotlight. Then, enter your heroes, Quarter,
Nickel, Dime, and Penny, strutting across the stage in quick succession, making
us laugh while reminding us of simpler times. But don’t settle too comfortably
into your seat just yet, because the show ain’t over until the fat lady sings
her last note. Before you know it, our beloved match expression returns to the
stage with a vengeance, taking charge, pushing state aside, and turning
Quarter’s appearance upside down to give him his biggest role yet.

What follows next might seem familiar: a game of memory meets a card trick gone
wrong. That’s right, state’s here once again. But suddenly, the unexpected
happens when the night explodes into light: Match::Expression brings Quarter,
Nickel, Dime, and Penny under his wing to share a night in Vegas, spinning tales
of wonder and delight, all while keeping state locked safely under wraps in his
bag of tricks.

 Imagine yourself on a treasure hunt, searching for answers among the scattered
 objects of different types. But don't worry, I gotcha covered with the power of
 pattern matching - a weapon so sharp it could cut through any Gordian knot. And
 yes, it's true, I did say "Gordian," and not Knott or Cable, but hey, you never
 know what mysteries may unfold along the way... maybe Medusa herself will make
 an appearance! Wait, why am I getting carried away with Greek mythology?
 
Behold, the coins! Penny, Nickel, Dime, and Quarter—each with its distinct
worth. With a simple match expression, we can bring clarity to this sea of
currency. The beauty lies in the . We match each coin, one by one, and when a
match is found, the corresponding code block is activated. It's like unraveling
a mystery, one coin at a time.

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

Do you see it? Time for the climax of the show: the match expression dance
party! Just listen closely to each beat and follow the rhythm. One coin at a
time, they appear and perform their designated roles. When a coin gets called
out to shine, the audience cheers - or rather, the code executes a certain piece
of functionality related to the chosen coin type. If it stumbles upon a Penny,
it returns the value of 1. A Nickel, and it reveals the secret of 5. A Dime, and
the spell conjures 10. And finally, a Quarter! Ah, the culmination of this
enchantment—a value of 25, revealed for all to see.

Match ain't just any old tool. Its sole purpose is to ensure that no matter what
situation pops up, the code stays afloat like a well-trained lifeguard. It's
like having an invisible safety net beneath us, catching our code whenever life
tries to pull a fast one. No need to fret over those pesky edge cases either,
because Rust's gotchya covered –– yeah, that means the compiler too, y'know,
Rust's trusty little buddy who makes sure everything's accounted for.

Match statements are like little private investigators, snooping around looking
for something specific. I mean, sure, they might seem kinda basic at first
glance, just hunting down a single expression or two - but trust me, that's
exactly how they catch 'em. No nonsense questions here, just straightforward
matching to find the perfect fit. Plus, these bad boys aren't limited to a
single type of comparison, like the if statement - oh no sirree! That's right,
our pals, the match expressions can handle anything from integers to strings to
even complex patterns. No need to fret over those pesky edge cases either,
because Rust's gotchya covered –– yeah, that means the compiler too, makes sure
in match everything's accounted for, in contrary to if.

the enigmatic match expression, stealing center stage in our value_in_cents
function like a diva strutting her stuff on Broadway. This showstopper packs
quite the punch, and boy oh boy does it know how to wow the crowds with its
jaw-dropping antics.

First off, we lay the foundation with the almighty match keyword, kickstarting
an epic performance unlike any other. Our star attraction takes the form of a
humble old penny or nickel, but don't be fooled by their simple appearance.
These guys are hiding some serious mojo up their sleeve! They come dressed up in
a shiny new suit called an enum we lovingly fashioned with great care.

Cue the drumroll, folks, 'cause next up we meet the dynamic duo behind the
scenes: the two patterns and the corresponding code awaiting their arrival. Each
arm is a ticking bomb of excitement, raring to go, ready to bust open the
secrets locked inside. Patterns act as a master key, trying to sniff out a fit
among the different possibilities, hoping to strike gold with each attempt.

Now, in this here fancy schmancy function we call value_in_cents, our
illustrious leader is a fella named coin, a dazzling display of diversity
incarnate in the form of a Penny or Nickel (or Dime, if you're feelin' frisky).
Can you believe those modest moneys contain hidden treasures beyond measure? As
the pattern matches the coin we possess, the => operator leads us to the
promised land—the code block that simply returns the value 1. Joining forces
with our intrepid explorer yields a double dose of destiny: arm number one
sports the pattern Coin::Penny right before the => operator which leads us to
the promised land—the code block that simply returns the value 1. Humble though
she may seem, she possesses inner depths worth delving into! After all, who
hasn't heard the ancient tales whispered by winds of change, legends claiming
"if only a Penny were worth a thousand bucks"?

But the show doesn't stop there! Each arm takes its turn, like a revolving door
of possibilities. If a pattern doesn't match the value we hold, fear not, for
the match continues its quest, searching for the perfect match.But alas, this
merry dance of discovery won't end with the mere mention of Pennies...oh no no
no why should mere mortals settle for less when the divine blessings of
versatility await? Four bars of possibility parade past our senses, inviting
exploration at every step.

The code associated with each arm is an expression and it's a spark of
brilliance, a burst of creativity. And that expression, holds the key to the
kingdom. Its value, like a magnificent jewel, becomes the final result of the
match expression. It's the treasure we sought, the ultimate reward for our
coding odyssey.

Let's explore the curly wonders of the match arms! You see, when the code within
an arm is short and sweet, we often forgo the curly brackets. It's like taking a
shortcut, a little trick to keep things concise and elegant. In our example,
each arm effortlessly returns a value, and no curly brackets are needed. Simple,
right?

Let me clarify this whole "match" business in terms ya peons can understand! So,
basically, it breaks down like this: when you write some code in them thar'
"arms," sometimes they're simple AF, nuff said type o' dealio'. So simple ya
don't need those pesky brackets cluttering up yer thoughts. Like, take our
coin-lovin' buddy, Coin, innit? His arsenal o' armlength boasts three babies
that need none o' dem curlicues (snicker yeah, thought you might catch my subtle
hint about curves), cuz his moves ain't complex enough ta get confused.

But lo, if ya want some next level shiznizzle, some multiple line mojo, well
THEN YA BETTER SLAP ON DEM BRACKETS and let the magic happen! Imagine them bad
boys like yerself openin' da box of tricks. Ain't dat sumthin', a secret weapon
stashed inside each arm waiting fer ya.

Now, here comes the fun part - we've saved the best for last. Ready? Those
wonderful pairs of curly braces known as match, or in other words your salvation
against boring code structures, have one important aspect setting them apart
from regular functions - guess what? They enable you to use commas instead of
semicolons after functions! Yes, indeed, feel free to forget any silly notions
regarding grammar police being unable to handle this flexibility shift since
semicolons aren't strictly necessary in certain cases involving multiple
statements. Crack out your party hats because it looks like everyone wins when
these small changes occur. Code readability shoots through the roof due to the
reduced noise caused by unnecessary symbols.

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

the really cool part happens when we apply some curly love around the Penny arm.
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

While some Arms play beautiful solos like the Lucky Penny Arm, others form
intricate harmonies complete with variables and functions – yup, just like your
favorite band trying out some fancy footwork while jamming out. And in case you
were wondering, no matter which Arm takes center stage, each musical number ends
with a satisfying finale courtesy of the returning value of the last expression.

    Patterns That Bind to Values

Prepare yourselves for a twist in our tale of match arms! We're about to venture
into the realm of patterns that bind to values. It's like a magical bond, where
patterns reach out and embrace the very essence of the values they match. And
let me tell you, it's a sight to behold!

Well, now we've hit upon another epic task involving enums – specifically a
single variant named Quarter – oh yeah, did I mention his sidekick happens to
hold a secret surprise? How's this for a teaser: that bonus treat is none other
than a special design representing each US state – imagine that, from years 1999
to 2008! I mean honestly, it's like discovering some sort of rare artifact or
prank gift straight from Santa Clause himself.

Alas, I digress; back to our story. With matching expressions joining forces,
watch in wonder as they engage each other in an intense dance. Picture the
scene: one pattern leads off with a powerful move, then passes control to the
expression partner.

This time around our attention turns toward the noble Coin enum. Yeah, it may
look basic at first glance – four heroes if you will: Penny, Nickel, Dime, and
ol' reliable... the Mighty Quarter. The catch lies deep within his chest (or
should I say data structure). Ladies and gentlemen, hold onto your hats cause
he's got something special stashed away inside: the legendary UsState lineup!
What better place to store secrets than a humble quarter, amirite?

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

It's like hiding a vault underground in that Coin enum– but seriously, these
states are golden! From Alabama to California and beyond, this eclectic bunch
gets inducted into the high society of the Coin family thanks to one simple
ritualistic phrase: "match."But it is the Quarter variant, that becomes the
vessel for these state treasures. Like a hidden chamber within the coin, it
holds the power to bind the UsState value within its grasp.

And here's where the match arms shine. They don't merely match values; they also
have the power to extract the secrets within. It's like a key that unlocks a
door. The vault opens, revealing the riches concealed inside. With the match, we
can dance through the patterns and bind the values they embrace.


Let me take you on a whimsical journey into the world of state quarters and the
mystical match expression! Picture this: you're sorting through your change,
just minding your own business, when suddenly, your friend's quest to collect
all 50 state quarters comes to mind. And there it is, my friends—the perfect
opportunity for a Rusty adventure!

So, you've got your coins laid out before you—pennies, nickels, dimes, and the
elusive quarters with their state treasures. But here's the twist: we're not
just sorting coins; we're on a mission to uncover the hidden gems within! And to
do that, we shall unleash the power of the match expression!

With each coin you encounter, the match expression leaps into action, seeking a
pattern that matches its essence. And behold, a new pattern emerges—a
Coin::Quarter with its secret state value nestled inside. But we don't stop
there, my friends. Oh, no! We go one step further and introduce a variable, a
magical entity called state, which binds to the state value within the
Coin::Quarter variant.

Our match expression will feel the heat as it starts searching for that special
card combo. Suddenly, we hit the jackpot - a shiny Coin::Quarter arrives right
under our fingertips! What a rush! Now, just because we found the guy doesn't
mean we should leave him stranded; we'll grab a buddy called State and tie the
knot between them both. Then we dance to the rhythm of an ancient ritual that
extracts the innards of the Quarter while whispering sweet nothings in its ear.

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

Now we've got something truly exciting to explore - the mysterious realm of
matching with Option<T> types! Picture yourself holding a magical box containing
either a value or nothingness itself. Sounds tricky, right? Well fear not,
'cause today we're revealing the secrets of these mystical containers through
the power of our mighty match expression.

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
, we simply return None, gracefully avoiding any operations. No risks, no fuss.

```rust
None => None,
```

Okay, so imagine you got this thingie, like an Option<32>. You guys ever hear of
those? They can store zero or one value. Zero is bad enough already, but then
they go and make it more complicated with this One stuff too. Like how am I
supposed to handle all this complexity? That's where our boy comes in, some lil'
ol' match expression dude. This dude gets stuck in your business trying to
figure out whether to give ya somethin' or nuthin'. But don't worry, once he
finds that precious Some, boom! He tosses that baby back at ya, making it easy
peasy to work with this thingummy whatever it is.

```rust
Some(i) => Some(i + 1),
```

Case in point: the Option type, which stores either zero or one value. Wrapping
up values in this thing makes them more complex than necessary. But here's the
good news: the match expression can simplify things by determining what to do
based solely on the presence or absence of the data inside. If it's there (or
"some"), we add one and wrap it back up in another Option instance; otherwise,
it's nonexistent and we simply return None without doing anything unnecessary

Now, let's witness this spectacle in action! We create a Some(5), a container
housing the value 5. We call upon our trusty function plus_one, passing this
container as our guide. And lo and behold, the match dances through its
patterns, finding the Some(i) that matches our container. It takes the value,
adds 1, and wraps it within the wondrous Some once again. The result? We receive
a new container, six, containing the value 6. Oh, the joy!


So, embrace the power of matching with Option<T>! Let it guide you through the
twists and turns of existence and non-existence. Uncover the values, perform the
operations, and revel in the joy of Rust programming. And remember, within the
match expression lies the key to unlocking the wonders of Option<T>. Now, go
forth and conquer the vast realm of Rust with your newfound knowledge!

 listen closely now 'cause I'm gonna share this insight about the beauty of
 mixin' together enum types and patterns in Rust programming language -
 specifically the match & enum combo. Y'know why it rocks harder than most
 others? Well guess what – because it gives devs access to awesome features such
 as safe code execution and even detecting bugs way before runtime errors appear
 queue drum roll. Trust me, after embracin' these tricks, you'll soon crave
 their use in other languages like clockwork cravings!
 
let's get straight to the first example now and take a look at how we could have
improved our dear old friend plus_one function while also avoiding errors thanks
to Rust's keen attention to detail..

```rust
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        Some(i) => Some(i + 1),
    }
}
```

Oh, but alas! We have failed to handle the None case. This code, it brings a bug
that Rust is well-equipped to catch. When we attempt to compile this code, a
mighty error befalls us:

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

Ah, the wisdom of Rust shines brightly! It knows that we have not covered all
the possibilities, and it even points out the pattern we have forgotten. Matches
in Rust are truly exhaustive. We must traverse every nook and cranny, leaving no
possibility unattended for our code to be deemed valid. Especially in the realm
of Option<T>, Rust shields us from the perils of assuming we have a value when
we might be facing the dreaded null. It protects us, ensuring that we do not
stumble upon the billion-dollar mistake, for it is an abyss we must never
venture into.

Here’s some advice folks: forget whatever you know about programming right now.
‘Cause you ain’t got nuthin’ compared to the brilliance of Rust’s match
expressions. They don’t play games with partial solutions or half-done
workarounds. And sure, there may be cases where you assume you’re dealing with a
complete set of options only to find yourself face-to-face with a frickin’ null
pointer bug. That’s a classic blunder you really wouldn’t want to make. But fret
not, for Rust’s match expressions won’t allow that sorta rubbish to slip through
the cracks. They keep things tight so nothing gets left behind, making damn sure
your app works wonders however circumstances change. Oh yeah, did I mention
Rust’s also pretty clever with enums too? You best believe it… chuckles Alright
folks, that’s enough banter. Just remember to stay true to covering every last
possibility via match or else risk living the nightmarish hell known as “null
reference exceptions”!

    Catch-all Patterns and the _ Placeholder

o I was messing around with Rust's match feature recently and came across this
neat idea involving catch-all patterns. Basically, think of it like rolling a
die and getting different results based on the outcome – only we manually assign
the numbers ourselves (for simplicity's sake anyway). Don't worry though, once
ya grasp how it works below, you can totally apply this concept to more complex
scenarios.

Picture this: you're playing a game, and when you roll a 3 on the dice, your
character doesn't move, but instead gets a shiny new hat. Now, if you roll a 7,
well, tough luck—your character loses a fancy hat. And for any other number,
your character moves that many spaces on the game board. Got the scenario in
your mind? Great!

Inside this Rust block o' mine, we establish our trusty ol' dice variable. By
hardcoding its value to an easy-peasy nine, we ensure smooth sailing during our
demo ride! The next step involves creating three spiffy functions named addFancy
Hat(), removeFancy Hat(), and movePlayer(). These babies represent unique
actions corresponding to each possible dice outcome.

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

Let's dissect this baby together. Say you have three functions: add_fancy_hat,
remove_fancy_hat, and move_player(..). Then, you create your match expression.
Within this epic battle of code, you place THREE ARMS TO CONQUER THE WORLD - er,
I mean, decide how the program should act given the dice roll value.

First off, pattern #1 handles a roll of 3: simply calls add_fancy_hat(). Pattern
#2 lays down the law for 7: whoop de doo, removes_fancy_hat(). What happens
otherwise? Enter the third arm: a catch-all! Other values get passed to the
move_player function alongside their own space count. Oh yeah, did I mention
this whole shindig requires hardcoding the dice value at 9?

Wrapping things up, Rust makes sure patterns go left-to-right. Thus, placin'
catch-alls LAST IN LINE prevents any prior arms from missin' their shot. But
heck, don't sweat it too much - Rust'll remind ya loud n' clear if ya
accidentally switch 'em up. And that's the scoop on catch-all patterns in Rust!

remember how we talked about having multiple arms in a match statement, right?
Yeah, well, one of these guys can be a total free spirit - no strings attached
(get it?) - the undisputed king of catch-all patterns: _ (_value)! Yup, one
single letter gives ya absolute power over anything that doesn't fit previously
defined patterns (that's legit - I'm not kidding!) Since this pattern doesn't
bind to any name, nobody cares what you do with its contents. You could swap
cars while wearing tutus; Rust wouldn't bat an eye!

Hey folks, quick question: why settle for just two options when you could have
three? Crazy talk, right? Well, hold onto your seatbelts, cuz today we're
steppin' up our game and adding a catch-all option to our game logic. Listen up,
'cause this is gonna blow your mind: we're now gonna roll the dice 3 times max
(not just twice), and if our first attempt ain't a 3 or 7, that means a reroll!

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
in whenever the dice roll doesn't match 3 or 7.For 3 or 7, it's party time,
folks! Roll anything else, though, and we spin up a reroll showcasing our
catch-all. In this case, it calls the reroll function, giving you another shot
at changing your destiny.

Now, here's the beauty of it—since we're using the wildcard pattern _, we're
explicitly saying, "Hey, Rust, we don't care about the value, so don't bother
binding it." And you know what? Rust respects that. It won't bug you about an
unused variable. It's like having a wildcard in your back pocket, ready to
handle any unexpected roll that comes your way.

And guess what? Our updated code still meets the exhaustiveness requirement.
Imagine you're playing a board game. You get one chance per turn to roll the ol'
bone box and see what destiny has in store. But sometimes life isn't always
fair, ya feel me? So what do we do when things go off the rails? That's where
our good buddy "Wild Card" steps in. He's like that rebellious dude who says,
"Screw it, I don't give AF what the rulebook said—I'm doing my own thing!" And
in Rust land, Wild Card reigns supreme. No, really, he does. You can tell him to
ignore his binding altogether, shrug shoulders, and say, "Eh, screw you too,
bruh!" Like a true OG. No questions asked. No strings attached. Just a simple
nod of understanding between man and machine.

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

Well, things might seem a little lackluster now as we roll the die once again.
This time around, if anything other than a 3 or a 7 pops up, we hit reset on the
excitement factor and let nature take its course. In this updated match, we've
added a catch-all arm using the underscore pattern—_. It's like a safety net for
any value that didn't match the previous patterns. But here's the kicker: we
don't want anything to happen in this case. So, we use the unit value—yep, that
empty tuple—as the code that goes with the catch-all arm. It's like saying,
"Hey, Rust, we're not interested in this value, so just move along!"

And that's it! We've covered the basics of patterns and matching in Rust. But
hold your horses, there's more to come in Chapter 18. We'll dive deeper into
this topic and explore all the intricacies. For now, let's move on to something
else. We're about to unveil the if let syntax, a nifty tool that comes in handy
when the match expression starts getting a bit too verbose.

So stay tuned, because Rust keeps on surprising us with its pattern-matching
prowess. It's like a puzzle waiting to be solved, and we're just getting
started. Until next time, happy coding!
