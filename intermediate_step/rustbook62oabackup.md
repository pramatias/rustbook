The match Control Flow Construct

Hey there, kids, I got a story for ya 'bout the greatest control flow tool in town – match. It's like a magic trick up Rust's sleeves, lettin' you take two things, see if they fit together like a glove or somethin', and light up the dance floor according to what happens next. It's like a game show, really, except nobody goes home empty-handed. All those options just slide under the spotlight until one finally clicks into place. Like puzzle pieces connectin' the big picture. Only difference here is the box got shredded long ago by Rust's unrelentin' march towards efficient software engineering. Don't worry though, you know exactly where every little detail fits perfectly.

First off, picture this: imagine walking into a busy market teeming with vendors hawking all sorts of wares. In our case, these goods are patterns vying to snatch up any passing-by values as customers. Every vendor wants its own special treasure displayed proudly for all to see—ready for inspection and evaluation! Some might showcase literal values or even variables with great flexibility from Rust's generous supply. But no need to fear; Rust's magnifying glass of smartness—i.e., match expressions—will help us pinpoint exactly which stalls attract our most prized possessions.

Now, let's dive into an example, shall we? Picture yourself standing before a
magnificent machine, coins in hand. Your task is to identify the value of each
coin, just like a magician revealing secrets. And Rust's match is your trusty
wand, ready to weave its spell.

Behold, the coins! Penny, Nickel, Dime, and Quarter—each with its distinct
worth. With a simple match expression, we can bring clarity to this sea of
currency. Oh, the elegance! The beauty lies in the patterns, dear friends. We
match each coin, one by one, and when a match is found, the corresponding code
block is activated. It's like unraveling a mystery, one coin at a time.

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

Do you see it? The match expression, like a wizard's potion, takes
the coin and dances through the patterns. If it stumbles upon a Penny, it
returns the value of 1. A Nickel, and it reveals the secret of 5. A Dime, and
the spell conjures 10. And finally, a Quarter! Ah, the culmination of this
enchantment—a value of 25, revealed for all to see.

But here's the real wonder: the compiler, that watchful guardian of
correctness, ensures that no coin is left unaccounted for. It's like having an
army of fact-checking elves, making sure that all possible cases are handled.
With Rust's match, we code with confidence, knowing that every scenario is
covered.

So embrace the power of match! Let your code flow like a
well-orchestrated symphony, where values find their rightful place, and patterns
unveil their secrets. And remember, in the realm of Rust, the match expression
is your key to unlocking the wonders of control flow. Let its magic guide you
through the realms of programming greatness!

Here's the thing about match. If you want to learn more than just "if", here's where you start exploring other options. See the thing is, Rust gives us ways to be creative within reason. So, here's match. This guy doesn't demand a Boolean condition like his buddy, if. He leaves that up to you. Match says, come at me with whatever expressions ya got! That's right - not just booleans, he takes 'em all! Like comparing apples to oranges, we're entering different realms here.

Here's the deal with match expressions in Rust programming language. Imagine a puzzling challenge where you must figure out how things fit together. With match statements, you can determine whether multiple patterns apply or not. Keep reading to explore how this works in practical scenarios. Trust me, once you get the hang of this tool, your code will become more flexible and expressive. Don't believe me? Let's take a look.

In our simple value_in_cents example, you quickly realize the power behind using match. Who would have thought a single currency could result in such an exciting performance? Our initial move kicks off with the invitation for excitement: match, followed by the mysterious guest named coin. Yes, coin may seem basic, yet don't overlook its crucial role in setting the scene. Plus, you'll soon witness how much flexibility comes into play depending on those currency choices.

The spotlight then shines on the match arm duo -- yes, two acts join forces here! These siblings consistently display their compatibility based on patterns matching the values provided. They wait patiently until someone discovers them through trial and error or careful planning. Together they open new doors for further execution opportunities. Once something fits the criteria, bam! Your program breaks free of monotony with actions specific to each choice. Wow, isn't it amazing how easily we've created so many directions from scratch? All thanks to this versatile and adaptable tool called match.

In our grand example, the first arm holds the pattern Coin::Penny. Ah, what a
humble coin, but it deserves its moment in the spotlight. As the pattern matches
the coin we possess, the => operator leads us to the promised land—the code
block that simply returns the value 1. It's like a tiny revelation, a glimpse
into the world of pennies and their worth.

The spotlight then shines on the match arm duo -- yes, two acts join forces here! These siblings consistently display their compatibility based on patterns matching the values provided. They wait patiently until someone discovers them through trial and error or careful planning. Together they open new doors for further execution opportunities.It's like a coin-sorting machine, guiding values through the patterns until the
right one is found. We can have as many arms as we please, each adding a new
layer of intrigue. In our wondrous example, we have four arms—four chances to
uncover the value of our coins.

The code associated with each arm is an expression. It's a spark
of brilliance, a burst of creativity. And that expression, my fellow
adventurers, holds the key to the kingdom. Its value, like a magnificent jewel,
becomes the final result of the match expression. It's the treasure we sought,
the ultimate reward for our coding odyssey.

So, embrace the match! Let its elegance guide you through
the intricate dance of patterns and code. Feel the thrill of discovery as you
witness your expressions come to life. And remember, in the realm of Rust, the
match expression is your companion on the journey to computational glory. 

Now for the fun stuff: enter the captivating curlies! These bad boys ensure we're able to write lengthier content within our newly found branches. No, we aren't done quite yet; you still need to balance the braces properly after closing parenthesis.You
see, when the code within an arm is short and sweet, we often forgo the curly
brackets. It's like taking a shortcut, a little trick to keep things concise and
elegant. In our example, each arm effortlessly returns a value, and no curly
brackets are needed. Simple, right?

But hold on tight, for if you desire to weave a more intricate tale with
multiple lines of code in an arm, then the curly brackets come into play. It's like opening a treasure chest, revealing the hidden depths of your
coding prowess. Oh, the possibilities!

Let me paint you a picture. Imagine a code block enclosed in those
lovely curly brackets, like a cozy home for your expressions to dwell. And
here's the secret: the comma that usually follows an arm becomes optional. It's
like a punctuation party, where rules are bent for the sake of beauty.

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
Now, imagine an old school phone with all the buttons labeled for different numbers. If caller number one dialed up "Coin", our Rust code would jump straight into action. But here's the catch - instead of giving out a single response, like our trusty old landline friend, the match expression gets us a whole range of options! From simple, bare-minimum-code replies to more complex ones with a few lines of code thrown in. You won't find this level of versatility anywhere else except in Rust's code kingdom.

In this enchanting code, our first arm, the Coin::Penny, yearns for a bit more
attention. It craves a grand entrance, and the curly brackets
provide just that. As the match finds a Penny, a delightful message is printed,
declaring the coin's luckiness. And then, the code within the brackets unfolds—a
value of 1 emerges, completing the arm's performance.

So, let's get started with our main attraction: Penny. He's lookin' for some love with his very own arm in the match expression lineup. But once he steps into that golden spotlight, suddenly it's time for more than just a quick solo act. Penny wants to give audiences a taste of what else he's capable of. So, out come the curly brackets, and boom! Our guy drops some fancy coding footwork. Before long, Penny's left us spellbound by announcing how lucky he truly is - 4 times luckier than nickel, 8 times better than quarter or half dollar coinage combined! Yep, our boy brought along some real pizzazz with that extra set of braces.

Let's take a peek at our Nickel, Dime, & Quarter arms while we chat. Like seasoned pros, they don't require all that jazz 'cos their needs are minimal compared to our flashy Penny star! Without the burden of excess braces, these less glitzy coins simply declare their inherent nature - Nickel = 5 cents, Dime = 10 cents, Quarter = 25 cents! Bada bing, bada bang, bada... well, you get the picture.

Match expression may sound humble, like a rusty ol' telephone waiting on its owner to dial up the next great idea. But this here's just a small preview, my friends. By combining a whole mix of code styles - from basic to embellished - Rust lets yah dance away with whatever creative beat moves your soul, eh folks? And that's somethin' pretty special indeed!

    Patterns That Bind to Values

What I can say, is that the match arms game takes the stage again. This time we enter the world of binding patterns to values, aka enums! Trust me when I tell ya, it's like witnessing the perfect blend between a magic trick and chemistry lab experiment gone right. Enums unlock secrets of a higher power for the programmer's heart to grasp. With a wink of an eye, hidden truths appear before us: mysterious "Quarter" holds wisdom of states past beneath its surface - treasured memories encased in copper for those who seek answers beneath appearances.

Specifically, let's focus on Quarter's ability to hold more than meets the eye (or, err, flip). In other words, Quarter gets extra love via binding.

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

Specifically, let's focus on Quarter's ability to hold more than meets the eye (or, err, flip). In other words, Quarter gets extra love via binding.

You see, the US State enum is like having a bunch of siblings vying for attention. Everyone knows them by name but not necessarily by face. Then comes our Quarter friend, equipped with the power to host any old state, creating a connection beyond mere acquaintanceship. The code itself even gives proof of its might: `(Penny, Nickel, Dime, Quarter(UsState))... voilà! Now you see why holding multiple states rocks our programming hearts? The Quarter binding arm brings both pattern matching AND the chance to link with something outside the family lineup.

you know what makes Rust tick? Match arms, baby, match arms. You see, when these babies start dancing, they're not just matching values - they're extracting juicy bits from 'em. Imagine match arms as a set of keys that open locked doors filled with hidden riches. 

So you take that key and twirl it around until it clicks. Bam! Suddenly, you got yourself some sweet state goodness trapped within your Quarter friend. Just picture match hands grabbing that elusive UsState value and tuckin' her away safe and sound into the depths o' the quarterly realm. And then it happens...you get that warm feeling of triumph when the full glory is revealed by those who tangoed with the arms of fate.

there's nothing quite like the joys of uncovering the secrets held deep within an enum's heart. Using those fancy-schmancy match expressions, your code can find connections no matter how well hidden. Think of match arms as the ultimate Nancy Drew detectives, always unearthing truths beneath the surface. Your match patterns will play fairy godmother to your code, transforming enums into Cinderellas - complete with glass slippers designed for easy access. Remember: every match arm unfurls another layer of potential for your program, so go forth and be a master magician wizard behind the keyboard. May the force of pattern matching be with you!

Hey y'all, let me tell ya about the wondrous world of quarters and that magical little number called the match expression. You know how sometimes you're flipping through your couch cushions or rummaging through your junk drawer, hoping for a spark of inspiration to strike? Well, today, we're trading pennies for possibility and embracing a quest to conquer ALL 50 STATE QUARTERS!

Now, it ain't just about finding random change; it's about discovering secret charms. Each coin hides a unique gem: a miniature map of America. We'll use that match expression though, like a magnifying glass, to help us decode the beauty in every penny piece. From Lincoln's visage to the Statue of Liberty, these quarters are more than pretty faces; they hold special powers waiting to be released by none other than the MATCH EXPRESSION! Trust me people, with this combo, no stone will stay unturned.

When it comes to exploring the richness of state quarters, who needs archaeologists? That's right, we're talking about the real heavy hitters of coin collection – you guessed it, the good ol' match expression! It's the only tool fit for cracking open the treasures locked away in those quarters' state secrets.

Think of it like peeling back layers of an onion (well... kinda). First thing you notice, after admiring the gleaming metal casing around that familiar face on the quarter's obverse side, is the appearance of some cryptic markings etched onto the reverse side of said artifact. Slightly intrigued yet? Good, because now we roll into stage two where things get interesting - that's right, the match expression swings into action. Just wait, watch as the coin starts doing impressions for ya', 'cause the next moment you see... the word "match" pops up front stage center! This guy's the ring leader, calling the shots under that big top circus tent called "Pattern Matching". The show has officially started, and we've got a whole troupe of performers ready to bring the house down – Coin::Quarter leading the pack and that tricky state value, hidden in plain sight

Without giving anything away, I'll drop this bombshell: turns out, once Coin::Quarter and that sneaky var state both make their debut appearances together, game over man – we'd best start practicing that famous American phrase: "...one nation, under God, indivisible." Game over indeed, since we've already solved the mystery and extracted the essence – nay, triumphed – over the state value, thanks entirely to the match expression's unstoppable force-field known simply as binding.

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

Hey there, so let's imagine we reach out to our old buddy value_in_cents and give him a visit, requesting his expertise on getting us closer to cracking that ever-elusive state code encrypted into US coins: "value_in_cents(Coin::Quarter(UsState::Alaska)). Go ahead, punch it in yourself. You didn't think I was gonna type it for ya', didja'?"

Follow along closely here. Suddenly, bam! Center stage lights up, as the Quarter king himself, alongside his trusty companion value_in_cents, take over. In perfect harmony, they belch forth their symphony, as the melody echoes through the chamber, and the audience gasps in anticipation while the hands begin their dance. Each note strikes a chord, attempting to create that perfect tune that aligns with destiny itself, only to fizzle out before long. 

Meanwhile, our very own coin savant remains unfazed, awaiting that final, divine moment when the crescendo approaches, and, viola!, the state variable finally reveals her true colors. All this time hiding in plain sight behind the curtain of Coin::Quarter, holding tight like a vice against the everlasting vault. A single touch, one quick tap, and the world trembles beneath the sheer force of the binding spell, and, lo and behold, with just a hint of magic dust, we'll extract every last drop of juicy secret from within the depths of that Coin realm. Now let's hear it for the victorious roar: "State quarter from Alaska", the sound echoing off walls, drowning out any remaining doubt concerning the sheer power of Rust's mastery over the humble Quarter kingdom.


buckle up tight 'cause we're divin' headfirst back into the rabbit hole of matching expressions, except this time we got a mighty companion in hand – Option<T>. Now I ain't gonna lie, this stuff can get pretty trippy. 

You see, Option<T>'s kinda like a little black box of mystery that might contain somethin', maybe nothin', or somewhere in between. Like Schrödinger's cat, y'know? Well, today we aim to make a function that takes our box o' unknowns (Option<i32>) and either gives it a 1 boost or returns nuthin'. No need to fret though, my pals in arms. Our trusty match buddy's the key to crackin' this puzzle wide open. Brace yourself for the solution right before your eyes:

"Some(i)", "None", whichever way ya swing it, our mission remains simple – add a measly ol' 1. With this gem o' code right 'ere, who needs more?:

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

When you mix 'n' match and Option<i32>, you've got some real fireworks. It's like a beautiful symphony of possibilities. But let's be honest - sometimes things are just simpler without fancy flourishes. So, in comes 'match expression'. It's like having your cake 'n eatin' it too - figuratively speakin', it gives us both values at once. If we have a 'Some', we spill a new secret sauce recipe and give ourselves a boost. On the other hand, if we're dealin' with a lonely None, well, we don't mess around; we let him lay low 'til he finds a friend. Here's a quick recap so you'll feel fully equipped to tackle the Rustian adventures ahead:

Now, let's say hello to these fine fellas we'll be workin' with tonight: Five's a cool customer; Six is the man in shades; and Zero is a true non-entity. They step onto the stage and strut their stuff in our little circus tent of possibilities. Let's hear them roar as they share their tales of triumph and tribulation under our watchful eye:

"Hey! Look at me," says Five proudly. "Ain't nobody fresher than me!" His confidence shines bright. And why wouldn't it? He's ready with his fresh cargo of 5. You see, Five's been on a wild ride lookin' for love in the arms of a 'Some'. But alas, my sweet chums, he's stuck in limerick heaven - he has five legs, but no rhyme scheme. Fear not, folks, I come packed with remedies to help transform Five from zero to hero.

Don't forget that our ol' compadre Zero knows full well where it's at: his own private corner of the universe! Sure, Zero may lack substance; but still, somehow that don't stop folks from fallin' hard for his charms.

we delve deep into that oh-so-tricky topic: implementing the match_expr method when working with Option types. This beauty of code can take on three flavors: Some, None, or Both (the latter known also as the curious Mr. None & Mrs. Some).

Picture yourself sitting down with four good buddies: Two_zeroes, Four_two_zeros, Three_none, and Six_some. Now, imagine treating each like your personal Siamese triplets joined by a common umbilical cord called "equal". Our first trio holds hands together as happy siblings sharing the same name. As for the final two, let's spin a different yarn. With Six_some, you dance a tango duet twisting into a pair o' onesies; Three_none gets a tad jealous but quickly agrees to share its barren existence. These boys and girls make life easier while handling Options of i32. But let's face facts: ain't nothing worse than a whole bunch of Nones. It feels like an eternal winter vacation trapped inside Frozen's palace... until someone drops a hot pan of latkes!


But wait, there's more! We dare to venture into the realm of None, an empty
container. We call upon plus_one once again, presenting None as our offering.
And what happens, my dear companions? The match encounters the None pattern,
recognizing the absence of value. With grace and elegance, it returns None,
allowing us to bask in the serenity of emptiness.

So embrace the power of matching with Option<T>! Let it
guide you through the twists and turns of existence and non-existence. Uncover
the values, perform the operations, and revel in the joy of Rust programming.
And remember, my friends, within the match expression lies the key to unlocking
the wonders of Option<T>. Now, go forth and conquer the vast realm of Rust with
your newfound knowledge!

You see, dealing with optional things can feel like getting a surprise gift from Auntie Ruthie: either she sent you her favorite recipe book or forgot your birthday altogether. Wouldn't it be sweet if we could just turn those zero-based relatives into full-fledged families? Well, we can, kind sir/madam! But here's where things get wonky: without guidance, turning Nones into Somethins involves a lot of guesswork. That's why the wise sages at Team Rust crafted the Match Expression, armed with three unique options.

First off, consider the case of SomePatterns. If you find yourself rockin' a Some box, treat yourself to a little extra love via PlusOne. Just hand over one token, and suddenly, voila, you'll get back a freshly minted number, thanks to the + operator. Ain't it neat?

Yeah, but let's not forget about NonePatterns. They're like super-cool introverts never wanting company. Without warmth or affection, they lurk in their corner of the universe. Can we really blame them?

First: NonePatterns. These fellas are the ultimate outcasts. Don't bother askin' 'em to play nice; their only response will be a cold shoulder and some snarky attitude. Still, we must acknowledge their presence, so we'd better learn their ways.

```rust
None => None,
```
Some patterns. Hmm, sounds intimidating.
These Some guys seem like they got it all figured out (whether they did or not is another matter entirely). They may come across as full-on experts, armed with answers ready to quash any problem under the sun. Or moon. Or stars.

```rust
Some(i) => Some(i + 1),
```

With Some patterns, prepare for a real head-scratcher. At least at first glance. It seems that for every i in existence, there exists some OtherValue(i+1). Wait – did someone say "Other Value"? Sounds fishy. Must be some shady relative hiding behind a mask. Well, hold on a sec – looks like math stepped in for backup! 

A quick calculation revealed that Some(i) do equal Something Else entirely: Some(i+1)! Who said algebra couldn't save lives? This stuff gives nerds superpowers, folks. Maybe not flying or lifting cars kinda powers, but still impressive compared to the rest of us normies.

You know, sometimes it feels like the whole world wants to drag us down, make us feel small. But I want ya to remember something important -– you don't need anyone else's approval to see your own worth, like when x takes the form of None. X marches
forward, entering the match and confronting the first arm:

```rust
None => None,
```

Perfect match indeed! None aligns perfectly with None, a void embracing
another void. And in this enchanting union we find solace.
There's no value to add to, no operations to perform. The program gracefully
comes to a halt, and we return the cherished None value on the right side of =>.
As the first arm matches, my friends, no further comparisons are made.

Match arms, by golly, will rock your little programmer hearts because it's like, well, a box full of surprises ya never knew existed. So, take a seat, grab a snack, and get ready to be amazed by the magical things called matches. You'll yearn for their presence in all languages. It is a
favorite among the users, consistently delivering joy and satisfaction.

So, embrace the magic of matching against enums, binding
values, and executing code based on their revelations. Let this enchanting
pattern guide you through the vast landscapes of Rust programming. And remember as you traverse this wondrous path, the match expression stands as a
beacon of power and elegance. Now, go forth and conquer the realms of Rust with
your newfound understanding!

"Caught in a trap, fellas and gals, gotta know how to read the signs, gotta find that missing piece. Now, I know what you may be thinkin': "What kinda trap, man?" Well folks, I refer to none other than the dark corners of Rust code that can ensnare even the most seasoned programmer -- hidden bugs, waitin' patiently to snag anyone who wanders past without lookin'. Just ask yourself: "Does my code do what it says it will?" Cue in this fine example, where we meet Mr. Plus One right here.


```rust
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        Some(i) => Some(i + 1),
    }
}
```

Now, I ain't judgin', but what happens should he run into the unknown? Heck yeah, we leave ol' None hangin', leavin' the whole party crashin'. But fear not, for Rust's there to help us spot such errors nice 'n' early. Like I said earlier, they catch the mistakes we wouldn't. Yup, one little mistake like forgetting to include Everybody Else brings down our beloved Compiler with this mighty blow:

"Oh No! (None case)"

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

```
For more information about this error, try `rustc --explain E0004`.
error: could not compile `enums` due to previous error

"Here's the thing. Your code must dance with the possibility devil, and match the many faces of life. So bite the bullet, and embrace those matches full throttle. Each step along the way will lead to clarity supreme. Those empty cases? Leave 'em behind. You heard me, I say leave 'em behind! The road to solid code means embracing the fullness of matches in the arms of our trusty pal Rust. And sure enough, our newfound knowledge will spare us the billion-dollar mistake curse. Especially in the realm of Option<T>, Rust
shields us from the perils of assuming we have a value when we might be facing
the dreaded null. Let Rust be your shield against the darkness of undefined behavior. It's time to saddle up and live your dream: code complete and free from bugs, thanks to the ever-vigilant watchdog that is Rust. Together, we can ride the range of safe code, herding those elusive bugs back into their pen.


Catch-all Patterns and the _ Placeholder

"Yo, welcome to Dice Roll Madness! Alright folks, let me break it down for ya. You know how sometimes it feels like your code goes off the rails? Like, when you've rolled that big ol' 3, you just sit still like a rock? That's a good day... unless you get a nifty new top knot... ahem hat! What about that bad luck 7? When the hats don't multiply, but multiply away poof. 

Well guess what? You don't need to worry too much anymore - thanks to Rust's handy dandy 'catch-alls' & this magical placeholder _. This guy takes care of all them cases left hangin' in the wind. With _ around, things stay neat & tidy--no more mess o' special rules for every type o' roll. So hop aboard and check out the smooth sailin' ride of matching complete: it'll knock yer socks off every time.

But
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

Today we've got ourselves a real humdinger, a veritable riddle wrapped in an enigma stuffed into a match statement. And boy oh boy, does she ever keep things interesting. Let's take a peek shall we? Here before us lies a dastardly dice roll situation, wherein our dear old pal dice_roll might roll a bona fide, honest-to-goodness 3 or a sneaky snake-like 7. Talk about excitement at its finest!

But then, lo and behold, what do we have here... Why it's an ole' fashioned wildcard tossed in for good measure, ready to catch whatever random numbers didn't fit under the scope of the other two arms! Can you believe it, friends? Our trusty move_player() function will spring into action, movin' characters hither and yon based solely on the whims of other. Ain't life exciting around these parts?

Fact #1: Got yourself an awesome match expression? Mind making that catch-all arm real pretty please? Turns out, hiding behind the curtains is a trickster waiting to trip you up. When ya put your catch-all arm at the front of the line, ya risk letting it eat up values meant for your other arms. Slippery fellow, ain't he? Might as well give him a knife too - haha! Don't stress, though - just pop that puppy at the back end and watch chaos fade away!

Fact #2: Didja know ol' reliable rust has got himself a super-secret undercover maneuver too? Allow me to introduce the dun dun daaaa UNDERSCORE PATTERN - _ for short. See, sometimes, ya may want a catch-all but ain't gonna need that captured value. Problem solved, mateys! Unlike his scoundrel counterpart above, Mr Underscore plays nice and doesn't force a binder upon you. Sure, sure, I hear some of you muttering: "Aww shucks, doc - couldn't ya lay offa the lingo?"

Now, we're talking 'bout rolling them dice and makin' some choices. Y'see, if anything outside o' 3 and 7 comes up on that die, it's time for a redo. No fancy fedoras involved either, just plain old rerollin'. Let's check out how I spruced up the code this time!

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

First thing's first: I set a fixed value for my trusty dice roller. Next, I spiced up the match statement with that oh-so-handy wild card symbol _. Swap out that tired old name "other" for a flashier mystery man, am I right?
Well, the real magic happens inside that nifty catch-all block where our boy _ gets to call the shots. Just think of him as the conductor of your fate train. He decides whether to put on that fancy chapeau or strip it right off. 

Now, here's the beauty of it—since we're using the wildcard pattern _, we're
explicitly saying, "Hey, Rust, we don't care about the value, so don't bother
binding it." And you know what? Rust respects that. It won't bug you about an
unused variable. It's like having a wildcard in your back pocket, ready to
handle any unexpected roll that comes your way.

And guess what? Our updated code still meets the exhaustiveness requirement.
We're covering all possibilities—rolling a 3, rolling a 7, or rolling anything
else that triggers a reroll. Nothing slips through the cracks. Rust's got our
back, making sure we don't forget a single scenario.

So, my friends, with the power of match and the handy-dandy wildcard pattern _,
we've revamped our game rules. It's all about adaptability and being prepared
for any outcome. So roll those dice, embrace the thrill of uncertainty, and let
the game unfold before your eyes. Enjoy the ride, folks!

So, my friends, with match and its catch-all powers, you can handle specific
cases while still covering all the possibilities. Rust keeps you on your toes,
ensuring that your code is thorough and complete. So go ahead, embrace the
catch-all, and let your code shine with its unwavering completeness. Happy
matching, folks!

Alright, folks, we're wrapping things up with one last twist to our game. Get
ready for it! Now, if you roll anything other than a 3 or a 7, we're changing
the rules so that nothing else happens on your turn. Yeah, I know, it's a bit
anticlimactic, but bear with me. We can handle this situation using the unit
value, which is basically an empty tuple. Let me show you how it's done:

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

So stay tuned, my friends, because Rust keeps on surprising us with its
pattern-matching prowess. It's like a puzzle waiting to be solved, and we're
just getting started. Until next time, happy coding!
