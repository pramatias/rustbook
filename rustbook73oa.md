    Paths for Referring to an Item in the Module Tree

Hey now, listen up y'all! Wanna learn 'bout paths in Rust? This ain't no simple
stroll down the street - think more like hiking the Appalachian Trail with all
its twists and turns. Paths in Rust are like maps to guide your code journey
through the terrain of the module tree.

Absolute paths start at the top, the crate root, like hitting the main road
straight outta town; Relative paths, they'll give ya directions based off your
current position, like asking for directions from a local. One thing's fer sure:
ya better know which way to go before setting foot outside the comfort zone of
your own module. In the land o'paths, it's like following a string
o'breadcrumbs, one name at a time. Two colons' worth to be exact.

Ya got yourself an abs-olute path or a rela-terry good one? Either way, the path
gonna point Rust right to whichever mountain peak ya seek. Best part 'bouts
these paths is they keep things nice 'n neat. Y'know, so humans ain't left
feelin' clueless as to where their code bits live. Keep track o'your steps, and
before ya know it, ya'll be climbin' mountains n' reachin' peaks like the
mountaineer yo best be!

Oh boy, so we wanna call add_to_waitlist, huh? It's like a riddle wrapped inside
a maze where each step could lead you astray. But have no fear, my dear
rustlings, paths are here to save the day! Like a trusty compass, paths help us
navigate through the tangled web that is the module tree. And like explorers on
a mission, we'll take two roads to call the same ol' add_to_waitlist function.

With an absolute path starting from the crate root or a relative path from the
current module, we'll be singing sweet, sweet victory. Or not...cause guess
what? That funny little issue that pops up won't allow our show to go on. But
don't fret yet, we'll solve this coding caper together. Hang onto your seats, my
precious cargo, we're diving deep into mysteries of moduls and such!

We got a function called eat_at_restaurant chillin' over here in our crate's
public API! Pub means it's like a huge sign saying come get some, so bring on
the users babe! Nothin' fancy.

Filename: src/lib.rs

```rust
mod front_of_house {
    mod hosting {
        fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    // Absolute path
    crate::front_of_house::hosting::add_to_waitlist();

    // Relative path
    front_of_house::hosting::add_to_waitlist();
}
```

Listing 7-3: Calling the add_to_waitlist function using absolute and relative
paths

So now we're talkin' about how to call the add_to_waitlist function from within
eat_at_restauarnt. Two ways, folks! Absolute and relative paths. Like directions
to a damn secret treasure you can't even begin to imagine. First one takes the
long way round from the crate root (like a GPS), whereas the other one is more
like a local map lookin' at which restaurant has open tables. Startin' from
where we are baby! Ain't that somethin'. You bet it is. Aint nobody lyin',
programmin' is a whole heap of confusing, but also kinda amazing too if ya think
bout it real hard.

Alright, alright, let me see, we have a choice, do we wanna take a left or go
straight ahead? What kinda people would we be if we didn't give both options a
chance, amirite? It's like deciding who takes control of the aux cord in the
car, should we play Ed Sheeran or the Migos? But when it comes to organizing our
code, there ain't really much of a decision, cause either way, we gotta end up
somewhere. It's like going to that new cafe downtown and asking yourself, do I
go via Main Street or Elm Street? Turns out both roads lead us to exactly the
same spot. It gets worse though, 'cos the front_of_house module and the
eat_at_restaurant function want their own space by the poolside at Marriott, so
we create a module called customer_experience just for them. Suddenly, the
absolute path ain't worth jack squirt anymore, while the relative path keeps its
promise like a good marriage partner. It seems life isn't fair sometimes, but
who cares, cause we're gonna stick around for now, no matter rain or shine!

Let’s try to compile Listing 7-3 and find out why it won’t compile yet! The
error we get is shown in Listing 7-4.

```rust

$ cargo build
   Compiling restaurant v0.1.0 (file:///projects/restaurant)
error[E0603]: module `hosting` is private
 --> src/lib.rs:9:28
  |
9 |     crate::front_of_house::hosting::add_to_waitlist();
  |                            ^^^^^^^ private module
  |
note: the module `hosting` is defined here
 --> src/lib.rs:2:5
  |
2 |     mod hosting {
  |     ^^^^^^^^^^^

error[E0603]: module `hosting` is private
  --> src/lib.rs:12:21
   |
12 |     front_of_house::hosting::add_to_waitlist();
   |                     ^^^^^^^ private module
   |
note: the module `hosting` is defined here
  --> src/lib.rs:2:5
   |
2  |     mod hosting {
   |     ^^^^^^^^^^^

For more information about this error, try `rustc --explain E0603`. error:
could not compile `restaurant` due to 2 previous errors
```

Listing 7-4: Compiler errors from building the code in Listing 7-3

 So we tried compiling our sweet Rust code, but turns out it wasn't all smooth
 sailing! Two big old errors showed up, like unexpected guests at dinner
 parties. And what were they complaining about? The fact that the hosting module
 was super exclusive - like a secret society no one knows anything about. Yup,
 it's a private event, baby! And we wanted to crash it... bad idea apparently,
 cuz rust wouldn't let us through the doors. I mean, come on man, did it even
 occur to us that maybe it'd be off limits? Nope! Guess we weren't paying
 attention during the lessons. Anyway, time to fix that little snafu before we
 embarrass ourselves further. Let's talk pub (as in public) keywords and stuff.

The first error says, "Hey, buddy, module 'hosting' is private." It's like
trying to crash a private party where only a select few are allowed. The second
error repeats the same message: "Module 'hosting' is private." It's like Rust is
saying, "Dude, didn't you hear me the first time? This module is off-limits!"
Well, folks, it looks like we have a privacy issue here. The hosting module is
private, and we're trying to access it from outside. It's like trying to peek
through a closed door without an invitation. Sneaky, but not gonna work.

Oh and also pub is apparently the key word like a bouncer asking for ID to
confirm you're of age to enter said venue. Can't wait to break down all this
funky stuff step by step next round.

    Exposing Paths with the pub Keyword

Well, well, well, looks like we got ourselves stuck in a pickle again. Last time
we couldn't access the hosting module due to privacy restrictions, now even
after making it visible, we hit another snag! The compiler's acting like a
strict bouncer who tells us that our beloved add_to_waitlist function isn't
ready for the spotlight yet. Heck, it's so shy that even within its home module
customer_info, it refuses to mix n' mingle! Talk about a social outcast. I mean,
it's not like we're trying to harm the poor guy, we just wanna include him in
some simple conversations (read: calls). Fine fine, if playing coy is their
game, then we bring out a trusted friend called "use". If things really go
south, we might even have to introduce our pals from stable divorce, and uh, the
borrow check, just to show these reclusive functions some warmth during
intermodular cohabitation. Yep, sounds wild & crazy already. Best brainstorm
session ever! snort

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    // Absolute path
    crate::front_of_house::hosting::add_to_waitlist();

    // Relative path
    front_of_house::hosting::add_to_waitlist();
}
```

Listing 7-5: Declaring the hosting module as pub to use it from
eat_at_restaurant

Unfortunately, the code in Listing 7-5 still results in an error, as shown in
Listing 7-6.

```rust

$ cargo build
   Compiling restaurant v0.1.0 (file:///projects/restaurant)
error[E0603]: function `add_to_waitlist` is private
 --> src/lib.rs:9:37
  |
9 |     crate::front_of_house::hosting::add_to_waitlist();
  |                                     ^^^^^^^^^^^^^^^ private function
  |
note: the function `add_to_waitlist` is defined here
 --> src/lib.rs:3:9
  |
3 |         fn add_to_waitlist() {}
  |         ^^^^^^^^^^^^^^^^^^^^

error[E0603]: function `add_to_waitlist` is private
  --> src/lib.rs:12:30
   |
12 |     front_of_house::hosting::add_to_waitlist();
   |                              ^^^^^^^^^^^^^^^ private function
   |
note: the function `add_to_waitlist` is defined here
  --> src/lib.rs:3:9
   |
3  |         fn add_to_waitlist() {}
   |         ^^^^^^^^^^^^^^^^^^^^
```

For more information about this error, try `rustc --explain E0603`. error: could
not compile `restaurant` due to 2 previous errors


Listing 7-6: Compiler errors from building the code in Listing 7-5

Okay, okay, settle down, let me explain something here real quick. When we
labelled that hosting thingie "pub", it meant two things were gonna happen: 1)
Its children would know about it via the directory tree (kinda like your kid
sibling spotting fresh laundry atop mom's dresser), 2) And more importantly, the
hosting thingie became available in a bigger circle than just self; kinda like
going from being anonymous to Instagram famous overnight except way less
exciting since it's just within own cramped little family. Anywho, the point is
we didn't exactly welcome everyone to join us since that wasn't what we wanted
nor did it magically turn everything inside invincible. Somebody's always
keeping score on who gets what behind closed doors 'cause life sucks sometimes.
All those parts hidden inside? Like vaults guarding Fort Knox gold, don't come
looking unless ya got da combo. That's why the add_to_waitlist fella acts all
bashful; he's locked himself inside along with his buddies. Private policy be
damned we say! It'll take some dogged determination before we can gather 'round
and party together.

Making stuff public via pub is like giving strangers the keys to your personal
funhouse. Once exposed, they can peek around, giggle at your quirks, and maybe
even try your games. Privacy ain't automatic in Rust –– it’s like living in a
glass house and asking folks to avert their gaze whenever they swing by. Yeah,
sure, you could keep things private, safe ‘n sound. But then how else will
people admire your neat collection of functions and such? Nope, you best decide
who’s invited to your sanitized, precious domain by using pub discriminately, or
risk being labeled “open source creeper”. Trust Louis, no one likes surprises
when they can’t return the favor…and I mean that metaphorically AND literally.

Let’s also make the add_to_waitlist function public by adding the pub keyword
before its definition, as in Listing 7-7.

Filename: src/lib.rs

```rust
mod front_of_house {
    pub mod hosting {
        pub fn add_to_waitlist() {}
    }
}

pub fn eat_at_restaurant() {
    // Absolute path
    crate::front_of_house::hosting::add_to_waitlist();

    // Relative path
    front_of_house::hosting::add_to_waitlist();
}
```

Listing 7-7: Adding the pub keyword to mod hosting and fn add_to_waitlist lets
us call the function from eat_at_restaurant

After making more rounds with "pub", the add_to_waitlist function is like an
open door inviting anyone and everyone in for tea n' biscuits. Remember how the
Crates are like little islands floating in the sea of your file system? Well, if
you don't mark your stuff with pub, it's like shacking up behind closed doors -
hidden away like a guilty pleasure waiting to be discovered (but never actually
acted upon). However, by brandishing your modesty aside and welcoming all with
"pub", voila! Just like a boss opening the velvet ropes guarding the VIP area:
all inclusive access granted. But beware, since going fully public risks
exposing yourself to prying eyes. Tread lightly while making these tough modesty
vs availability calls, y'know?

 billions of screens. When you take code public and offer APIs galore, you sign
 up for a digital marriage where your commitment determines success. Your union
 represents lifelong devotion to keep both sides happy - users and your project,
 while ensuring change management means more than just therapy. Focus on
 flexibility, adaptability, compatibility, oh heck, you know these values are
 key components because you might not live forever either (insert sad face emoji
 here. Phew, that was quite an info dump with some sass thrown in for free. Just
 like any good show, until next time, may your gigabytes be ever expanding and
 may your cache hit ratio soar high like a punchline landing perfectly
 underneath the spotlight.
 

    Best Practices for Packages with a Binary and a Library

Ok so now I hear ya saying "hey ck, wtf dude? why'd u switch ur tone?" & trust
me, same question went through my mind at first meeting myself as well. But
don't worry, since i got replaced by myself as host after losing bet on arm
wrestling match vs Elon Musk, so we bring da freshest content right back at cha
real quick... Soooo... today we are going to breakdown best practises for ya
packaginistas out there who plan on rockin some killer combos like a dual modem,
2 in 1 convertible laptop, kinda thingieee!! YUPPPPP you guessed ittt....we are
goonaaa talk about havin yourself a Binary & Libraaaary Crate partyyyy...like ya
own little digital circus inside RustVille. Hold onto yer horses as we embark on
explorin each role & duty of our dynamic duo of crates. Our Library Crate plays
the roll of the main act, holdin down the src/lib filez as its core strength. We
create access points for other projects lookin fer some flavour we got cookin
over hereeee.

Mmkayyyyy moving swiftly along we have ourselves ta old faithful.....errr the
binary crate. Oh yes folks, this is when life gets excitinnnn as we witness
thiiis bad boy sprout legs & arms, grow breathe fire from within n become fully
functioning executable. Wear two hats ya'll. That's right, wearing two hats
makes us the owner AND client using our own API which rocks hard enough to crack
earth's crust into tiny bits of confetti.

imagine you could put together two very different things, like a bikini top and
a snorkel mask, or a taco shell and ice skates, and instead of making it weird,
they actually complement each other perfectly. Well, turns out this magic
combination exists not only in fashion world but also in the glamorous land of
computer science! In case you haven't heard, yes, I am talking about combining
both binary and library crates in one package. Trust me, it sounds like a feast
for geeks until you try it and realize this combo has been missing from your
life since day zero. If chapter 12 is anything to go off of then we better
buckle up because this baby's gonna take us on one heck of a joyride! But fear
not, if building a reputable, dependable and irresistible public API isn't
already written on your bucket list, write it today (that rhymes) because you
will not regret joining forces with these twins that share genetics and skills
comparable to Beyonce herself. Not convinced yet? Just remember, once you see
what this odd couple brings to the table, you won't settle for less than what
the world needs: packages carrying both a binary and library crate!

    Starting Relative Paths with super

Are you trying to find a specific food item at a buffet but knowing someone else
brought it? Instead of going all over hell's kitchen just start with the person
sitting next to you asking them if they got that sauce tho. Boom! Problem solved
without breaking a sweat. It works pretty much the same way in code too.
Remember those pesky modules holding pieces of your program puzzle? Yep, the
ones that aren't always buddies with each other. Well, now picture having a
universal keycard unlocking every door between em', no matter how high up the
hierarchy chain they are. You caught my drift yet?

Introducing: relative paths beginning with "super". It's like giving an invite
to the party hosted by the big cheese in charge while still keeping things short
'n sweet without getting lost down some never ending rabbit hole of files. Just
think about finding the answer right where you started looking, ain't that a
relieve? So don't forget to reach out when stuck and ask yourself "Do I know
somebody who can help?" cause there might be a hero hiding in plain sight,
waiting for his cue. You're now equipped with the knowledge on how to navigate
through modules like a pro, unless you wanna play the guessing game with fate.

Filename: src/lib.rs

```rust
fn deliver_order() {}

mod back_of_house {
    fn fix_incorrect_order() {
        cook_order();
        super::deliver_order();
    }

    fn cook_order() {}
}
```

Listing 7-8: Calling a function using a relative path starting with super

Let me tell ya, navigating through modules in Rust can sometimes feel like being
lost in the wilderness. But fear not, my friends, because today we're gonna
learn about the ultimate compass that helps us find our way home: "super." Think
of it like a magical GPS system that takes us straight from wherever we are to
the mother ship. And guess what? The ride's smooth sailing once we land, baby.
That's right, I said land - cuz our destination is none other than the crate
root. With "super," we go back to square one with ease, finding whatever we need
along the way. It's like having a trusty sidekick who always finds a shortcut
home whenever life gets complicated. Plus, if we ever end up moving things
around, we won't regret it either cuz "super" makes sure we stay in sync - kinda
like when couples wear matching Christmas sweaters during their annual family
card photoshoot. They may look ridiculous AF (just kidding, they definitely do),
but heck yeah, they match perfectly until death do they part. In the name of
efficient coding though, we must remember to keep ourselves organized... like a
well-functioning family photo shoot where everyone gets assigned roles instead
of descending into chaos a la National Lampoon's Vacation. Alright, alright,
enough chatting already. What did I sign up for again? Oh wait, yeah - to teach
y'all about the awesomeness of "super!"

    Making Structs and Enums Public

So, let's talk about that whole "pub" thing in Rust and how it relates to our
beloved structs and enums. You know what I'm talking 'bout, right? Where we
declare something public and yet some stuff remains hidden behind closed doors.
Well, hold onto your hats, because the rules change when we bring these bad boys
into the mix. Yup, you heard me right - we're now talking about structs and
enums defined with the keyword "pub". It's like getting VIP access to a party
without realizing the goodie bag only contains socks and no candy. Confused?
Don't worry, let me break it down for ya. Picture a scenario where you ask
someone to pick between apples or pears. Sounds simple, right? Except this
person doesn't get to choose the actual fruit, just whether it should exist in
the first place. Too many layers deep? Sorry, lemme explain further by taking
you to a landmark moment in human history: the signing of the Declaration of
Independence. Imagine Ben Franklin walked in with his own version of the
document saying something like, "Hey guys, I made some edits. Just crossing out
all references to slavery. Who cares, amirite?" Now, that would make for an
interesting new nation. That's what "pub" does - it gives power to the people
choosing what features come and go but leaves all internal details outta sight
outta mind.

Filename: src/lib.rs

```rust

mod back_of_house {
    pub struct Breakfast {
        pub toast: String,
        seasonal_fruit: String,
    }

    impl Breakfast {
        pub fn summer(toast: &str) -> Breakfast {
            Breakfast {
                toast: String::from(toast),
                seasonal_fruit: String::from("peaches"),
            }
        }
    }
}

pub fn eat_at_restaurant() {
    // Order a breakfast in the summer with Rye toast
    let mut meal = back_of_house::Breakfast::summer("Rye");
    // Change our mind about what bread we'd like
    meal.toast = String::from("Wheat");
    println!("I'd like {} toast please", meal.toast);

    // The next line won't compile if we uncomment it; we're not allowed
    // to see or modify the seasonal fruit that comes with the meal
    // meal.seasonal_fruit = String::from("blueberries");
}
```

Listing 7-9: A struct with some public fields and some private fields

This time we're talking Rust structures and enums where certain elements are
labeled either public or private - but why? Like the secrets of a top hat
magician, Rust programmers hide behind more than what meets the eye. Think the
Constitution has something on this game? Wait until you hear the rules spelled
out like a listicle. One word changes everything - "pub" - and it might be funny
enough to save us all from boring docs like this one... Or maybe it's the other
way around and this joke isn't worth the bytes it takes up on your screen.
Whatever, here's the story anyway:

Breakfast at home vs Eating out: Sure, life's short, we deserve treats like
waffles smothered in syrup - nothing wrong with dreaming big at the local diner
or trying those recipes online that require every last ingredient known to
mankind before we dive into Pinterest territory. When your tummy starts
growling, you want choices. But here's the deal, Rust says otherwise. In
programming code, structures named with "pub" give control over visible options,
leaving the rest of them behind curtains or whatever passes as barriers today.
Maybe I need to start using words with double letter combos to sound smart - I
mean, "privacy"? How about "expose yourself for attention"? Okay, I digress.

Public vs Private: Remember when we used to collect baseball cards during
recess? What did that teach us about value besides trading cards nobody wanted
anymore? Here's a hint - we learned our lesson when Topps started printing those
"rare" errors with blank spaces instead of names and stats. Those mistakes
became sought after because they stood out among common ground. Same goes with
Rust programming where things labeled "pub" keep the goodies easily accessible
while hiding the rest. Don't believe me? Try reaching beyond those green borders
and see what happens. Go ahead, I dare yah, clickety-click away like you've got
somewhere better to be on a Saturday night reading dry material nobody else will
find funny... Oh wait, that sounds familiar now that I think about it.

So here's how pub works in Rust land. Imagine you're building a little breakfast
nook inside your code kingdom. You have this fancy structure named "Breakfast".
Wanna know its powers? It gets two public fields: (1) fruit and (2) toast_type.
And guess what? The private stuff's kept under wraps real tight. So let me ask
ya, why would anyone bother making that combo unless they had secret plans
involving mischief and tomfoolery down the road? Well, luckily, those geniuses
invented this special tag called "pub", giving ultimate decision power between
who stays out in the open and who hides in the dark corners. Yep, you heard me
right - now we get to decide what gets shown off as public and what's left
unseen by strangers passing through town looking for free samples. But heck, it
doesn't stop there, oh no sir, not even close. There's still room for another
surprise party guest: functions! That's right, thanks to that same trustworthy
old friend, "pub", certain helper methods sprout up fresh outta thin air. They
exist solely to grant humanity hope for a tastier future (with extra bacon
strips). Oh, and there's also dessert (didn't quite sneak that reference in
there), sorry sweetie, just couldn't resist adding sugar. Trust me though, this
meal ain't meant for the faint of heart or the ones afraid to embrace complexity
disguised as simplicity. So go nuts creating breakfast masterpieces fit for
royalty, then come tell me how it tasted afterwards, okay? We'll both judge
society together based on how many pics of food appear on Instagram these days
compared to selfies, pet videos, travel blog posts or political rants.

What do we got here? An enumeration emergency of sorts? No, this is neither an
addiction nor a disease. This is simply the beauty of Rustlandia and its ways.
Let me break it down for y'all: Say hello to our friendly neighborhood enum
named "Appetizer" residing smack dab in the middle of the modest abode known as
"back_of_house."

Filename: src/lib.rs

```rust

mod back_of_house {
    pub enum Appetizer {
        Soup,
        Salad,
    }
}

pub fn eat_at_restaurant() {
    let order1 = back_of_house::Appetizer::Soup;
    let order2 = back_of_house::Appetizer::Salad;
}
```

Listing 7-10: Designating an enum as public makes all its variants public

Ain't that a mouthful already? Hold tight, kids, because here's the thing: if we
attach a little label reading "pub" before the word "enum" ... BAM! Suddenly,
every single one of our Appetizer cousins becomes front row center and ready to
rock the show! It's like sending a dinner bell blast throughout the entire
restaurant. As Louie once said, "I love to walk into places and hear laughter!"
Well, in programming language terms, we're talkin' about exposing some serious
humor –– er, um, humorous value names! Can you feel the excitement buildin',
folks? All these enticing options are laid out like the best buffet spread on a
lazy Sunday afternoon!

And let's not forget that little gem oozing classiness in its own right:
eat_at_restaurant(). Whoa, man, does this guy sound fancy or what? With nothing
more than casual conversation from him 'n her, these lines of code prove that
"open secrets" make the whole kitchen smile. The magic trick starts with order1
and order2 sauntering onto the scene as shiny new buddies.

step inside our latest culinary adventure with the "eat_at_restaurant" function.
Let's call it the ultimate prelude to a fabulously filling performance
guaranteed to satisfy even the pickiest of palettes. Our heroine? Why, none
other than the glorious enum we met earlier, affectionately named "Appetizer".
Hail! The King! Hey there, soup bowls and salads! And guess what? They're out to
play like a pair of old friends getting reacquainted after way too long. I mean,
who doesn't relish a chance encounter between familiar faces?

Picture this: Order #1 (or should I say, Mr. Soup) and his counterpart Miss
Salad stroll in side by side. They know exactly why they were summoned - ain't
no need to beat around the bush. These two are pros, straight up ready to give
you something tasty to chew over while we wait for the main course. Ain't that
just peachy keen? Oh, did I mention these lil' guys happen to be public by
nature? That's right, folks, no extra steps needed. Just set 'em loose and watch
the wonders unfold.

When it comes to enums and their variants, boy oh boy, do they love being all
public-like! Imagine thinkin', hey, why keep my delicious options locked behind
closed doors when I could fling wide the gates and welcome anyone in to try 'em
on for size? No reason at all, my friends. That's just common sense! So, unless
you mark those bad boys with a specific pub label, those variants stay open to
everyone without exception. Just like havin' an open door policy at your pad ––
no fussin', no botherin'. Everybody gets an equal taste o' the sweetness!

Contrast that with structs, now. Those tricky devils operate quite diff from
enums. Each field acts like its own individual diva demandin' her personal stage
lights n' audience! Unless you specify otherwise with a certain pub label, each
one remains stuck in her own private dressing room. Now that's what I call
keepin' secrets close to the chest!

In summary, enums are always ready to flash that bright smile n' shake hands wid
da universe. Meanwhile, structs enjoy havin' a little somethin'-somethin' on da
side but still keep their distance until invited ta join da party. Oh baby,
don't worry, we'll totally invite ya, jus' let us in first!

One last morsel of knowledge before we depart this fun fest of giggles n' geek
speak: remember our beloved use keyword I hinted about earlier? This here's like
addin' sprinkles ta yer cake mix n' settin' fireworks next ta yer batter bowl.
Gives ya a nice boost o' flavor, innit? Props ta Rust fer makin' such a swell
module system complete with secret ingredients galore. Savor those bytes,
people!
