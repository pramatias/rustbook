    Bringing Paths into Scope with the use Keyword

Let me tell you, nothing frustrates me more than having to spell out these
insanely lengthy paths just to reach some dumb old function. It's like following
a never-ending breadcrumb trail through the wilderness blindfolded. Who needs
the extra hassle when you could teleport right to where you need to be? Well,
good news folks, Rust provides just that magical solution via the use keyword.
Say hello to instant gratification! Instead of spelling out the whole path from
start to finish, we bring the crate::front_of_house::hosting module right into
the same room so we can call it straight away using the friendly alias hosting.
In short, the use key transforms your coding journey into a seamless zip line
ride straight to your desired destination without breaking a sweat or missing a
step. Bam, problem solved. Trust me guys, life's too damn short for endlessly
trekking through mountains of code. Make the most of the moment and get to
business faster with the power of the almighty use keyword!

Now this scenario arises - you're stuck with this ridiculously lengthy path to
call a simple function, like crate::front_of_house::hosting::add_to_waitlist.
That's like signing up for marathon training camp when you're trying to squeeze
in a quickie workout between meetings.

But then comes along the savior of them all, the precious, sacred "use" keyword.
With a single utterance, it transports you directly to the heart of the matter,
saving you from unnecessary footwork that drags on like an eternal winter.

Think about it - how often do you crave shortcuts in real life? Whether it's
taking the freeway exit closest to home or ordering takeout online mid-binge
session, streamlining is the name of the game. And now, behold Rust's offering,
the golden ticket to efficient coding heaven: use.

So why not treat yourself to a taste of the good life, eh? Use the hell outta
that use keyword and watch your coding world morph into one big lazy river
cruise. No longer shall the burden of excessive paths weigh down thy soul nor
thy keyboard. Go forth, my friends, and embrace the convenience of the mighty
"use". Amen.

Oh, by the way, if you happen to find yourself in the land of filenames seeking
enlightenment on the subject of long-winded paths vs the salvation of said
"use", well look no further than Listing 7-11 found within the sacred scriptures
of Programming Documentation Writing Bible Vol II: The Sequel. Just sayin'.

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}
```
Listing 7-11: Bringing a module into scope with use

Now you gotta type out these super loooong paths just to reach some functions
like crate::front_of_house::hosting::add_to_waitlist. Like wow, dude, are you
running a marathon or something? Give me a break already. But don't worry,
folks, because Rust has our backs covered with its trusty sidekick, that oh so
divine "use" keyword.

It's like magic beans from a fairytale. All of a sudden, we have ourselves some
sweet shortcuts that hit straight to the point, no more aimless wandering around
like lost tourists. Life ain't always meant for epic quests, thankfully with
use, we can dial things up to easy mode while still being able to keep secrets
safe and sound like a good fence. Privacy stays intact even with these quick
routes at our disposal, like hidden staircases behind bookshelves. Boom! Bang
Bang! Pizzazz! Powwoweeee! Ladies and gentlemen, witness the majestic powers of
the "use" keyword in action! Whoop whoop whoop. Yup yup yup! I rest my case.

Now, before you start conjuring images of mystical, ancient scrolls filled with
arcane knowledge, let me bring your attention to something called Listing 7-11.
Don't get scared, it won't bite ya. This bad boy holds the key to unlock the
truth behind bringing modules into scope via use. It's like getting directions
from a friendly neighborhood genie - hey, if you rub the lamp three times,
voila!, you have the answer you seek! But really, just think of it as making
sense of a map, understanding stuff better is never wrong. Anyhow, give ol'
listing 7-11 a shot, see if anything clicks...like a good old fashioned
lightbulb.

So, you thought you could just slap together some code with those fancy use
statements, huh? Well, you're in for a surprise, pal. Just 'cause you got
yourself a shortcut doesn't mean you can just use it anywhere! No sirree, Bob!
These use guys work like magical portals, and once they disappear, well, let's
just say, hope you didn't forget about em', Jack! Ha ha ha. It's like having a
special door pass that gives you access to all the best rooms in the house...
until you step outside the building and boom, it's gone! Vanished! Poof!
Sayonara! So, yeah, turns out our friend Use isn't quite the miracle worker we
hoped. Darn! Guess I shoulda read the fine print or somethin'.

Filename: src/lib.rs

```rust

mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

use crate::front_of_house::hosting;

mod customer {
    pub fn eat_at_restaurant() {
        hosting::add_to_waitlist();
    }
}
```

Listing 7-12: A use statement only applies in the scope it’s in

Oh boy, looks like we've hit a snag! The compiler is not happy with us. Thought
y'all could just casually stroll into our dear old pal Rust, arms flailing
wildly, shakin' things up with these fancy use statements wherever ye pleased?
Nah-ah, them ain't brains ya got there, folks!

```rust
$ cargo build
   Compiling restaurant v0.1.0 (file:///projects/restaurant)
warning: unused import: `crate::front_of_house::hosting`
 --> src/lib.rs:7:5
  |
7 | use crate::front_of_house::hosting;
  |     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  |
  = note: `#[warn(unused_imports)]` on by default

error[E0433]: failed to resolve: use of undeclared crate or module `hosting`
  --> src/lib.rs:11:9
   |
11 |         hosting::add_to_waitlist();
   |         ^^^^^^^ use of undeclared crate or module `hosting`

For more information about this error, try `rustc --explain E0433`.
warning: `restaurant` (lib) generated 1 warning
error: could not compile `restaurant` due to previous error; 1 warning emitted
```

Yer playin' fast n' loose, throwin' around words like "filenames,"
"directories," "symbolic links" - might as well be speakin' Klingon fer all
anyone knows over here! Don't expect yerselves ta catch much breaks neither -
Rust don't take kindly ta liars n'cheetas, always lookin' fer ways ta trip ya
up! But hey, whaddaya know? Even amidst all that tech talk, we still managed ta
make some sweet ol' fashioned funny too, so kudos fer hangin' tough through them
thorny paragraphs ya little scamps! Keep scratchin' yer coding chops,
whydontcha? Who knows, might yet turn inta sumthin' legit! Now git outta here
before Rust sees fit ta give y'all the boot.

That's how us humans can get around Rust's strict rules without making the
compiler flip its lid entirely. So, usually when we write code, we need to
specify what other functions or modules we want to use from another file via
import statements. These allow Rust to access stuff from one file while working
on something else. It's kinda like having different rooms in your brain
compartmentalized to handle different tasks - you wouldn't just waltz into a
random brain lobe demanding a coffee refill. Makes sense so far? Good, 'cause
now comes the tricky bit: filenames. Turns out, Rust also requires us humans to
tell exactly which files or directories should show up in the search path during
compilation (translation: specifying WHERE those mysterious modules might live).
That's right - those symbols aren't just for show. And guess what happens if we
forget? BAM! An obscure "failed to find crate root ..." error, which sounds like
a big deal until it means NOTHING, since Rust has absolutely no freaking clue
WHERE THE CRATE ROOTS ARE SUPPOSED TO BE LOCATED. Soooo frustratingly vague,
amirite? Next level fun times await though – we ALSO must carefully label every
symbolic link in said paths with the appropriate rustc command line flag "-Z
symlink", lest Rust gets confused AF about which module it should load next
('cause life's just a series of choices after all.) Now then, finally getting to
the gold at the end of this riddle trail...we can avoid ALL THAT, AND MORE, with
ONE SIMPLE MAJOR HACK! We can simply...move...our bloody use statements...INTO
each individual module they relate to (!!) That way we ensure Rust has easy
access to whatever shiny new function we conjured up (even if it was created in
some strange parallel universe!), without him going postal over missing info!
See, folks, sometimes being lazy pays dividends, especially if you're in no mood
to navigate Rust's labyrinthine world of errors! Just remember to put that use
statement right where it belongs, 'kay?

    Creating Idiomatic use Paths

Okay, so check this out - you know that whole thing about bringing functions
into scope with use in Rust? Well, turns out there's an idiomatic way to do it.
Listing 7-11 vs. Listing 7-13 - who does it better? Let's take a look.

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

use crate::front_of_house::hosting::add_to_waitlist;

pub fn eat_at_restaurant() {
    add_to_waitlist();
}
```
Listing 7-13: Bringing the add_to_waitlist function into scope with use, which
is unidiomatic

So in Listing 7-11, we used use to bring crate::front_of_house::hosting into
scope, and then called hosting::add_to_waitlist in the eat_at_restaurant
function. Why'd we do it that way? The answer lies in our quest for idiomatic
Rust code.

In Listing 7-11, we're telling Rust, hey, this function comes from the hosting
module, and I'm using it right here. It makes it crystal clear that the function
isn't locally defined. Plus, it keeps things concise and easy to read.

But in Listing 7-13? Womp, womp. Nope, sorry buddy, not idiomatic. Instead, it
brings the entire front_of_house module into scope just to call one function.
Like finding a key to fit the lock doesn't guarantee anything anymore than just
having a broken hearted door. Trust me, stick to Listing 7-11. You won't regret
it. Unless you decide to try both ways out. Then maybe you will. Who knows these
days. Bueller? Anyone?

So, you know that thing where you gotta bring functions into scope with "use"?
Yeah yeah, you've been doing it wrong your whole damn lives. Check it out, it
goes like this: You bring in the parents man, the module they live in. They give
birth to whatcha working on. And guess what? When someone asks where the hell
those kids are coming from, you ain't got no excuses left. You show them exactly
where each and every kid was born.

And sure, it may seem like a hassle at first, but lemme ask ya something -
wouldya rather type out the same shit over and over again? Orrrrrr...keep it
sweet n short like ice cream weather on the beach? You get what I mean, don't
cha? Keepin' it simple and clean in both your code and in real life. Be it funny
or sad or happy or whatever, it's the only recipe worth cookin'.

Now go ahead, hit that "use" button like a pro and watch your code turn into a
symphony, just like a well-kept house filled with all its favorite tunes. You
see now how you need that clear headspace to think straight? And next time you
hear that little voice inside ya whisperin', "I shoulda done this sooner," know
that it's just the universe tellin' us to step it up once in a while, 'cause it
missed us nudin' those neurons around too much.

Alright, alright. So, you know how we were talkin' earlier about how to bring
functions into scope with use and stuff? Well, hold onto yer seats 'coz there's
another level to this whole game: bringing structs and enums. Oh yeah. You
didn't know? Nah, course ya did. You knew everything already, riiight? Uh huh
huh.

Filename: src/main.rs

```rust
use std::collections::HashMap;

fn main() {
    let mut map = HashMap::new();
    map.insert(1, 2);
}
```

Listing 7-14: Bringing HashMap into scope in an idiomatic way

But anyway, so like I was sayin,' when it comes to bringin' them in, we gotta do
it differently. We gotta take the long walk home by specifyin' the FULL PATH for
'em! Yep. Can you believe it? From the top down, you gotsta spell out exactly
where these babies come from. Now, some folk call it the Rust Standard Library
or somethin' fancy like that (ain't really my kinda lingo)...but heck, if it
works, then don't fix it, amirite?

That's right, partners. Git ready fer another taste o' Listing 7-15. This one'll
git y'all feelin' like a true native speaker:

"We gonna bring in tha' powerful & majestic HashMap class from tha' stdlib!
Specify th' full path from top to bottom like a boss! Tickles ur fancy? It shore
does mine."

Hey, remember when I told you guys about bringin' in items with use? Yeah, I
did, didn't I? Oh, but wait...what if I told you now, that there's an unexpected
twist. Like a plot twist in a movie, except this time, it's not even remotely
exciting. If you try bringin' in two things with the SAME NAME using use, boom -
instant death baby! That's right, if ya catch my drift. But I'm gettin' ahead of
myself again. Lemme tell you more about this exception - you know, since
exceptions make such great stories, after all.

So listen up, 'cause here goes nothing: Rust is like a strict librarian, man.
Try to bring in two items with the exact same name, and they ain't playin'
around. It's like that classic battle between siblings "MINE" vs "MIIIIINE".
Except instead of fightin', they both lose - straight out denied entry. Now, why
did I put emphasis on the word SUPREMACY earlier? Because it turns out, there
can only be ONE winner, people.

Just imagine it like the wild west, or maybe The Walking Dead? There's a limited
number of spots available, and only the STRONGEST will survive. If two items
wanna share space under the same roof, they better be prepared for warfare.
Trust me folks, life is unpredictable sometimes.

"Two items with the same name? Ain't nobody got time fo dat! Rust's the law,
pal."

Filename: src/lib.rs

```rust
use std::fmt;
use std::io;

fn function1() -> fmt::Result {
    // --snip--
}

fn function2() -> io::Result<()> {
    // --snip--
}
```

Hey, so have you ever found yourself trying to bring two types with the same
name into the same scope, only to realize that Rust just isn't having it? Well,
let me tell you, Rust doesn't mess around when it comes to naming conflicts. But
don't fret, because in most cases, there's a way around it. Check it out:
Listing 7-15. In this example, we've got two Result types (one from fmt, another
from io) with the same damn name. Can you believe it? Talk about an awkward
family dinner. How do we differentiate between these two? Simple: we add their
parent module names to the use statement. Suddenly, the code knows exactly who's
who, like they're giving each result their own seat at the table. So really,
it's kind of like Rust is inviting us to their version of "The Dating Game",
making sure everyone gets along nicely together. You might think it's a pain,
but trust me, you'll thank me later when everything runs smoothly. Just remember
to treat others how you want to be treated: give each item their own unique
identity by adding their parents' module names to those use statements.

    Providing New Names with the as Keyword

Okay, so you ever been stuck with two types sharing the same name and you wanna
bring 'em both into the same scope? Don't worry, Rust's got your back. Enter
stage left: The Almighty As Keyword! Yeah, I said it. That lil' thing saves your
ass every time.

Check it out, Listing 7-16: Two Types sharing one name - Boom! As Keyword swoops
in, gives 'em some fancy ass new identities. Fresh aliases, all delivered
directly to your doorstep via The Great As Keyword.

Filename: src/lib.rs

```rust
use std::fmt::Result;
use std::io::Result as IoResult;

fn function1() -> Result {
    // --snip--
}

fn function2() -> IoResult<()> {
    // --snip--
}
```
Listing 7-16: Renaming a type when it’s brought into scope with the as keyword

And what happens next is like magic. First off, you take std::fmt::Result, it
sticks around like its badass self. Zero work needed here. Second act, then
boom: Hello std::io::Result, meet your new BFF - As Keyword. And just like that,
it transforms into IoResult. One moment, one line of code, total gamechanger.

Sure, you could call it a simple fix. A minor adjustment. But let me ask ya
this: if that tiny tweak prevents a full-on nervous breakdown or yet another
existential crisis? Welp, that's priceless. The Almighty As Keyword's got your
back like a true bestie.

When it comes to using types in our code, we sometimes face naming collisions.
You know what I mean right? Two types sharing the same damn name! Well, hold
onto your hats 'cause I'm gonna show you how Rust takes care of that mess.

First up, let's talk about the classic approach, Listing 7-15. Here, we simply
rename one of the Result types to distinguish between the two similar sounders.
This old school method works like a charm every time.

But listen up, things get interesting when we step into the modern era, courtesy
of the magical AS KEYWORD. In Listing 7-16, our boy IoResult gets himself a
spicy new handle thanks to his savvy partner in crime – the beloved AS. Who
needs a single name when we can have an army of cool alter egos ready to roll?

What happens next knocks us down memory lane: Result and Result. No joke, the
universe itself feels simpler just reading those words alone. And suddenly, life
makes sense again – or does it?

Fast forward and reality slaps us with a different flavor: IoResult gets a
snazzy sidekick, Renderer. It's not like IoResult's going solo anymore. He's
joined forces with some extra firepower. Why settle for one great friend when
you can have two?

Through thick and thin, Rust lets us choose our path. Whether you prefer one
name per type or embrace a world filled with fantastic aliases, it's all good.
But most importantly, we gain clarity and sanity inside our coding kingdom.

The moral here is clear: always wear your seatbelt when driving through the wild
jungle of code. Use tools like the incredible "AS" to tame naming collisions
before they turn your hard work upside down.

    Re-exporting Names with pub use

Let me tell you 'bout this nifty thing we call re-exporting. Ever feel like
hiding a name behind the scenes isn't enough? Like you wanna share your super
cool discovery with the rest of the world but don't wanna lift your skirt too
high? Enter pub use, the master of exposure management.

Listing 7-17 shows ya how we sprinkled the magic dust on our code, transformin'
somethin' once hidden into a star attraction. The pub keyphrase? A simple touch
of genius right here. If yah hear the drums beatin', yah better believe the
front office is bangin'.

Now, go back a coupla steps to Listing 7-11. There, the use keyword was our
ticket to access private goods without scarin' the neighbors. Here, though,
we're thinkin' big picture. Our name goes public baby, spreadin' joy among the
masses. One click of pub use and we got ourselves an open mic night of sorts.
So, who says privacy's everything? Sometimes exposure's the real crowdpleaser.

You wannabe code celebrities out there gotta make that critical decision. Keep
it under wraps or invite everyone to dance. Just take another peek at Listing
7-17, see that use statement...now imagine addin' pub foreplay...boom, instant
success story. Your secret weapon against isolation anxiety. Bask in the glory
of recognition and fame in the land of rustling re-exports. Pub onwards to the
future, amigos.

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

pub use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}
```

Listing 7-17: Making a name available for any code to use from a new scope with
pub use

tell ya about this magical thing called re-exportin'. You ever feel like hidin'
a name ain't good enough? Like ya wanna shout from the rooftops about your
latest discovery? Enter pub use, the savior of closed doors. Check out Listin'
7-17 man, I mean seriously. Whatcha gonna find there is gold Jerry, pure gold.
Oh, and if ye doubted the power of pub use before, well then, let me walk you
through this Rustilicious adventure.

Let's start where the magic happens - Listin' 7-11. That little use trick
allowed us to tap into private clubs with ease. But now, things get spicy
quicker than Taco Bell. Take a gander at Listin' 7-15 - it showcases a special
moment ta be reckoned wit': The birth o' hostsfilegen. This file genie provides
the exact same functionality as the original hostin' module, but separated by
class (that's some fancy talk fer ya). Hostsin' was still born within our main
namespace tho'. However, we're slowly learnin' to unleash it's full potential,
ready to rock da stage fer lessons ahead. Now, when I say "lessons", I really
mean, "how ta impress hotshot comp sci folks". Trust me fellas, they love these
kinds o' moves. Anyways, back ta what we were discussin'. With the addition of
pub before use, we're figurin' out we gotta bigger picture in mind. Why settle
fer a lil side action when ya can become the next global headliner?! By
sprinklin' a single touch of pub before use, our homely name is transformed into
the hottest ticket in town. Look again, jus' gaze deep inta dat sweet smilin'
use word. Ahh, it speaks volumes of secrets awaitin' ta come outta da darkness.
All it needs is ya to unlock it's true identity. Waltz wit' me on dis journey,
an' prepare ta have yer minds blown away, my friends. Thoughts o'exposure
eclipsin'privacy won't leave ya lonely, mark ma words brotha's an' sista's. Dis
ain't no party lyke evr seen befere! Prepare ta make da scene explode with
laughter & delight!!! As we wrap dis up, my wise advice would be ta give pub use
a whirl.

    Using External Packages

oday we'll dive into how to use external packages, specifically with the Rand
package we used earlier. It's like asking a stranger for directions on a busy
street corner...only way more reliable, I promise.

Okay, so here's what we did: we modified the Cargo.toml file (yes, rustling
sounds may or may not apply), adding the line rand = "0.8.5" to tell our
friendly neighborhood cargo guy, "I don't know this place too well, couldja grab
us some Rand?" Crates.io obliges, handing over the package along with whatever
else we needed that week. And thus, the guessing game fun began.

These external packages are like kindred spirits with extra skills, bringing
something fresh to the table while still respecting our space, unlike a messy
coworker who forgot you asked him to clean up last night's snack explosion from
his desk. (Protip: always ask twice.) Plus, Rand packages aren't cheap date
material either - they work hard or hardly work, depending on your perspective
of their punctuality. So yeah, bring 'em home whenever you please.

Filename: Cargo.toml

```rust
rand = "0.8.5"
```

today we gonna chat 'bout how to invite those rand external packages into our
own cozy little world. Like when the new guy finally shows up late to that team
dinner, but he didn't just order salads for everyone! Nope, he came prepared
with delicious options for every palette and dietary preference. And like the
perfect plus one, rand packages join forces without stealing attention from the
star players. Let's get started.

After all, who doesn't love a good guest appearance? But seriously though, after
adding the line "rand = "0.8.5" to our Cargo TomClub file, like slipping a
secret password to a bouncer, we opened a direct channel between Mr Cargosworth
and the mysterious world of external packages. Then, instead of reaching out for
help at a local gas station, Rand was fetched right alongside any dependants
needed by that wily crates.io character. Boom, just like that.

Now, remember when we met rand and became BFFs? This friendship went further
than simple small talk as we decided to extend the scope of our relationship.
The very first step took place via that special line, "use rand::Rng;",
basically, ringing the bell of a potential homeowner looking to rent out
services. Who knew a simple greeting like, "Come on in, Rand, share your Rng
trait with me now," could lead to such fruitful results?

And so, that's why the line looked like this: "let secret_number =
rand::thread_rng().gen_range(1..=100)"; a warm invitation like a grandma
offering her most comfortable spot on the couch. Just like that, it offered a
comfy nest egg for secret_number to rest easy and ride off into the sunset...or
maybe to find another thread and keep generating until that fateful day.

```rust
use rand::Rng;

fn main() {
    let secret_number = rand::thread_rng().gen_range(1..=100);
}
```

You know what makes a party great? Options, variety, stuff to choose from. And
that's exactly what crates.io brings to our Rust projects. Instead of being
stuck with only what comes with the house (std lib), we can add some fancy
flavors thanks to other generous guests.

Sure, Cargo may be hosting the festivities, but it's not the life of the party
if things are missing. That's where listing each guest at the table matters. The
more names listed, the merrier, so to speak. Bring the goods from these guests
inside with "use" lines and suddenly everything gets cozier and better equipped.

Just like having an ice cream truck show up, we don't always need changes in our
own recipes unless it's time to welcome something bigger than ourselves, like
the mighty std library. Hello, std! And sure, while we might need extra servings
here and there from others, we're still happy to make room for anyone willing to
contribute sweetness to the spread. That's why these guests become part of our
family, and suddenly everything tastes even better. Trust me on this one.

In short, it boils down to invites, arrivals, and treats galore. We gather to
enjoy all the extras provided by crates.io members in this open source universe,
so let's savor every byte of data types like HashMap and have a helluva good
time doing it. Thank you, dev squad, wherever y'all land.

```rust
use std::collections::HashMap;
```


    Using Nested Paths to Clean Up Large use Lists

So let's say we've got a big list of uses, right? Like a massive to-do list that
takes forever to scroll through and leaves us feeling overwhelmed. Well, i'm
gonna tell ya how to compress that sucker into one neat little package.

It's all about using nested paths to clean up large use lists. Basically, if
we've got items defined in the same crate or module, we can avoid taking up tons
of vertical space by grouping 'em together on one line. It's kinda like
organizing our mess into tidy piles.

Filename: src/main.rs

```rust
// --snip--
use std::cmp::Ordering;
use std::io;
// --snip--
```

For instance, check out those two use statements we used in the guessing game
earlier. They brought items from std into scope. A single use statement per
item, no shortcuts. But, oh yeah, did I mention Rust's got our backs covered
again? We can put 'em all on one line. Boom. Compressed like a sardine in a can.
All nice and streamlined.

Bottom line: Next time we get swamped by a long list of uses, remember to think
inside the box - er, I mean, use nested paths to keep it tight n' organized.
Your code will look neater AND save you precious screen real estate.

Instead of writin' each use item alone on its lonesome line, we give them a
comfy home wrapped in braces. Think of it as a wee little nest for your paths.
Two colons act as hosts welcoming your path's common parts, and those curly
braces? Oh, they're just holdin' hands with whatever differs from the rest. It's
a pretty sweet deal.

Filename: src/main.rs

```rust
// --snip--
use std::{cmp::Ordering, io};
// --snip--
```

Listing 7-18: Specifying a nested path to bring multiple items with the same
prefix into scope

Let's check out that Guessin' Game example from before. Those two use statements
were like strangers livin' next door with their lights on full blast all night.
Each line was workin' solo, without any thought for their neighbors. Not very
neighborly, now is it?

Well, we're fixin' that now, baby. One line with both items snuggled under those
cozy braces and watchin' their energy consumption. Ain't that somethin' else?
With nested paths, we're makin' them lines lean and clean. Sharp as a tack!

So meet the star player in this epic tale of organization: the "two colons" duo.
They open wide and allow a safe haven for those wanderlust paths to crash land
softly into their new digs. Like a cozy hotel lobby offering comfort and shelter
during stormy weather, these twins help set the stage for true magic. Next step,
roll out the welcome mat for those shifty characters named curly brackets { } .

Filename: src/lib.rs

```rust
use std::io;
use std::io::Write;
```

Listing 7-19: Two use statements where one is a subpath of the other

So we all know Rust gives us that little gem called nested paths, right? Well, I
just discovered something pretty nuts about its usage. Anywho, we got ourselves
two simple use statements in Listing 7-19. First, we call upon dear old friend
std::io, then we get another buddy, std::io::Write. But hold on a sec! Peep the
fine print - the latter guy is hiding his own subpath goodies under the hood.
Yes, my friends, both these bros are related, making this a match made in
heaven. They play nice together like chess champs. But don't take my word for
it, feast your eyes below. Filename: src/lib.rs

Listing 7-20: A couple of best buds (Use statements) working well together

Filename: src/lib.rs

```rust
use std::io::{self, Write};
```

Listing 7-20: Combining the paths in Listing 7-19 into one use statement

So, what happens when we have two or more use statements like in Listing 7-19?
We usually think of them as separate entities, each solving a specific need.
That's cool, but what if we could make 'em work even better together? And that's
exactly where the "magical" keyword "self" comes in.

Here's how it works: Instead of having individual use statements, we put 'em
both under one roof. Boom! Suddenly, they become roommates who share everything.
I mean, every subpath under std::io becomes available via a self keyword.

And just like that, folks, you see how nested paths lead to simplified code
using the wonderful concept of combining subpaths via a keyword like "self".
This ain't no regular path, nor is it a beaten path. This is an elegant, sleek
roadmap that leads us to the promised land of beautiful Rust coding, where
clarity reigns supreme.

    The Glob Operator

we're gonna talk about that funky little character, the glob operator (*), which
basically means "hey rust give me everything ya got in this path." Picture this
scenario, say you wanna import everything from a crate but you don't feel like
listing each item individually. Well, let me tell you, that's where the glob
operator steps in, acting as the wild card of code. Take a peep at this
statement:

```rust
use std::collections::*;
```

It's saying "Hey Rust, I want everything inside collections!" Now the full force
of the entire contents gets pulled into the current file's scope. Imagine being
able to import everything you need in just one line - sweet as candy corn! But
hey, before you run off and slap that glob everywhere, remember: use sparingly
cause too much of anything isn't good for anyone (or your code). Use wisely
grasshopper.

Whoopdee-doo, it pulls all public items from std::collections into our precious
scope. But here's the catch, my dear friends - overusing the globby guy can make
things confusing. When the whole gang's invited, it's easy to get lost amongst
the crowd. Can we get too comfortable with excess imports? (Heck yeah!) So tread
lightly when giving the globster free rein. Let's keep it lean and clean,
y'know? Know thy scopes, respect their borders, and stay focused on what matters
most - crystal clear code vibes! With Rust, wildcard operators and all, we stand
strong against chaos.

