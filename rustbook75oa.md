    Separating Modules into Different Files

Now, there might come a point when you realize your code is starting to resemble
a hobbit village - packed tight, cozy maybe, but hard to navigate. That's why
we're going to talk about splitting things up, making room for fresh air and
elbow space.

Picture this, you've written yourself a bunch of cool restaurant modules, neatly
arranged in one file like a well-organized kitchen. But then, suddenly, new
recipes arrive and stuff starts piling up faster than dirty dishes after brunch
shift. Your once tidy code is now cluttered and claustrophobic. Time to rethink
the layout and spruce things up, amigo. Enter: breaking it down into smaller
homes, each tailored for maximum efficiency and breeze flow.

Check out Exhibit A, Listing 7-17 - proof positive that separation equals
celebration! Those savvy restaurateurs got smart, recognizing that one central
office just wouldn't cut the mustard. Their solution: divvying up the
front_of_house module, tossing in a pinch of independence, and flaunting its
shiny new digs. The result? Zen harmony between organized components and
uncluttered mindspace.

Let me walk you through step-by-step, no muss, no fuss. First, grab that trusty
pen and paper or finger-dancing device - either way works sweetly. Take aim at
that original source folder containing all the restaurant modules you worked so
hard to create. Before long, you'll notice three types of files labeled by yours
truly: generic ones, module directories... oh boy, here we go again with them
fancy terms! Easy translation: regular old directory + module pairs = happy
marriage. Plus, if memory serves correctly, there's another type involving
reexports only... or some other jargon no one really needs to hear right now.

So, remember that thing I was talking about earlier, how our code might get too
crowded sometimes? Well, turns out, we're gonna fix that with this nifty trick.
Imagine we got ourselves a nice chunk of Rust code, packed full of restaurant
goodness like front_of_house module, and ya feel like you need more space to
move around without tripping over lines of code like kindergarteners on a school
trip to the museum. What do we do? Break it up, baby, make it spacious! Like
turning that cramped studio apartment into a sprawling loft pad. So, take that
front_of_house module and put it in its own file. Voila! Room to breath, man!
And all because we separated concerns and gave each part its very own space to
stretch out. Ain't life great? Check it out, guys, check it ouuuttt!!! (pumps
his fist)

Okay, okay, settle down cowboy. Let's take it easy on the exclamations. So, like
I said, we're gonna create a brand new front_of_house.rs file, which'll contain
all them juicy implementation details I'm sure you can't wait to see unfold like
a beautiful present beneath the Christmas tree! Just don't forget to import
everything from that root lib.rs first, y'know. Gotta keep order around here.
Oh, and lastly, lemme remind you we're still using Listing 7-17 as our base
example 'cause it works wonders for showin' off the latest moves in Rust coding
world!

And guess what else? We even included a sneak peek at Listing 7-21, where our
trusty friend shows us how to declare that front_of_house module goodie basket
full of methods & fields.

Filename: src/lib.rs

```rust

mod front_of_house;

pub use crate::front_of_house::hosting;

pub fn eat_at_restaurant() {
    hosting::add_to_waitlist();
}

```

Listing 7-21: Declaring the front_of_house module whose body will be in
src/front_of_house.rs

So, you wanna put all that code from the front_of_house module in its own file,
huh? Like, you know, moving furniture from one room to another, but instead of
furniture, it's code! (laughs) Alright, let's get down to business! So, we got
this new file, src/front_of_house.rs, and it's like a blank canvas, just waitin'
for us to fill it up with some good ol' code! Now, I know what you're thinkin',
"Louis, why do we gotta move this code to a new file?" Well, let me tell ya,
it's like... (pauses for dramatic effect) it's like giving this code its own
special room, you know what I mean? Like, it's not just gonna be buried inside
that big ol' front_of_house module no more, it's gonna be its own thing!
(chuckles)

Filename: src/front_of_house.rs

```rust

pub mod hosting {
    pub fn add_to_waitlist() {}
}
```

Listing 7-22: Definitions inside the front_of_house module in
src/front_of_house.rs

Now, let's talk about this hosting module. It's like, we're setting up a little
party for all these people waitin' to be seated at the restaurant, right? And
inside this party, we got this one function, add_to_waitlist. It's like, the
guest list, man! (laughs) You know, we're gonna add all these people to the
list, and then, who knows, maybe they'll get seated, maybe they won't. But hey,
that's life, right? (smirks) So, there you have it, folks! That's how we move
code from one module to another. It's like, furniture moving, but instead of
furniture, it's code! And that hosting module, it's like a party waiting to
happen!


So, you wanna know about mods and stuff? Like, you know, how to make your
codebase all neat and organized? Well, let me tell ya, it's like... have you
ever been to one of those fancy-schmancy restaurants where they got all these
little neighborhoods? Like, you know, a sushi bar, a steakhouse, a pasta joint?
Yeah, it's like that! So, you got your root module, and it's like the main
restaurant. But then you got all these little mods, and they're like the
different neighborhoods inside the restaurant. And the way you get to 'em is
like... you gotta know the secret password! Yeah, I'm talkin' 'bout the mod
statement, man! It's like the magic words that let you in to the exclusive club!
Now, once you're in, you don't gotta worry 'bout loadin' the mods again. The
compiler's like, "Yo, I got this! I know where to find the code, 'kay? It's like
it got a GPS system built-in, and it's always on the lookout for the next mod
party! And then, we're gonna take it up a notch, man! We're gonna extract the
hosting module to its own little pad, like a... like a... like a... hmm, like a
bungalow! Yeah, that's it! So, we're gonna create a new directory,
src/front_of_house/, and that's gonna be the bungalow for our hosting module.
And it's like, it's got its own little neighborhood, man! It's like, the hosting
module's all like, "Yo, I'm over here, ya hear me? I'm the king of this
bungalow, and don't you forget it!" So, that's it, man! That's how you do it!
You gotta have your mods, your secret password, and your own little
neighborhood.

So, you wanna move this hosting module to its own file, huh? Alright, let's get
this party started! *giggles* First things first, we're gonna create a new
directory called src/front_of_house/. It's like, you know, building a little
house for our hosting module. *chuckles* And inside this directory, we're gonna
create a file called hosting.rs. This is where all the magic is gonna happen,
folks! *laughs*

Filename: src/front_of_house.rs

```rust

pub mod hosting;

```

Now, we're not gonna clutter up this file with any code just yet. Nah, we're
gonna keep it simple and just say, "Hey, there's a module called hosting here."
*smirks* We're like the hosting module's real estate agent, showing off the
empty lot where our little hosting house will soon stand. *winks* So, there you
have it, folks! That's how we move our hosting module to its own file. Easy
peasy, lemon squeezy! *laughs* Now, if you'll excuse me, I gotta go work on my
hosting module's cable-knit sweater. It's gonna be a real cozy little number!

So, you got this hosting.rs file, right? And it's like, "Hey, I'm gonna add some
people to the waitlist, yo!" But then, if you put it in the wrong place, like,
directly in the src directory, the compiler's like, "What the hell, man? This
ain't no hosting module, this is like, some random file here!" And then, it gets
all confused and stuff, like a cat trying to play a piano. You know, it's like,
"Mew mew mew, I'm supposed to be playing Chopsticks, not this silly hosting
thing!"

Filename: src/front_of_house/hosting.rs

```rust

pub fn add_to_waitlist() {}

```

But, you know, if you keep it in the right place, like, in the
src/front_of_house/hosting.rs directory, then it's like, "Oh, okay, I get it
now! This is like, a little hosting party, and I'm the DJ, spinning some Rust
code!" And then, everything's cool, like a cat in a tutu, it's all good, man!
So, that's the deal, folks! Keep it organized, keep it in the right place, and
the compiler's gonna be all, "Yeah, I got this, man! This is like, the coolest
code party ever!" And then, you'll be like, "Louis C.K., you're the best
programmer ever!" And I'll be like, "Thanks, man, I'm just trying to keep it
real, like a cat trying to catch a laser pointer!"

    Alternate File Paths

So, you wanna know about file paths in Rust, huh? Well, let me tell you, it's
like having a big ol' bowl of ice cream with multiple flavors! You got your
"src/front_of_house.rs" flavor, and your "src/front_of_house/mod.rs" flavor.
Now, I know what you're thinkin', "Louis, why do I need two flavors? Can't I
just stick with one?" Well, let me tell you, my friend, having two flavors is
like having two scoops of ice cream! It's like, why choose just one when you can
have two? But, let's get real here, folks. The Rust compiler, he's like the ice
cream man, and he's got rules. He's like, "Hey, you can have two flavors, but
you gotta stick to one style per module." Now, I know what you're thinkin',
"Louis, what's the difference?" Well, let me break it down for you. It's like,
the "src/front_of_house.rs" flavor, that's like the chocolate chip cookie dough,
it's classic, it's simple, it's straightforward. But, the
"src/front_of_house/mod.rs" flavor, that's like the rocky road, it's a little
more complicated, but it's still delicious!

```rust
src/front_of_house.rs (what we covered) 
src/front_of_house/mod.rs (older style,
still supported path)
```

For a module named hosting that is a submodule of front_of_house, the compiler
will look for the module’s code in:

```rust

src/front_of_house/hosting.rs (what we covered)
src/front_of_house/hosting/mod.rs (older style, still supported path)

```

So, here's the deal, If you wanna mix and match, the compiler's gonna give you a
big ol' scoop of disappointment. He's like, "Hey, you can't have your chocolate
chip cookie dough and your rocky road too, that's just not how we roll." But, if
you stick to one style per module, the compiler's gonna be like, "Hey, you're my
kinda person, you're a rule-follower, you're gonna get two scoops of ice cream!"
So, there you have it, folks, that's the scoop on file paths in Rust.

So, you wanna organize your code like a boss, huh? Like, you wanna have all your
modules in separate files, but still keep 'em connected like they're best buds
or somethin'? Well, you're in luck 'cause I got just the thing for ya! It's
called the "older style" with files named mod.rs, and let me tell ya, it's a
real doozy! First off, you gotta know that this style is like havin' a bunch of
clones, and that can get pretty darn confusing, ya hear me? Like, you gotta keep
track of which one's which, and it's like tryin' to tell your clone army apart.
But hey, that's just part of the fun, right? Now, let's talk about the magic of
function calls. Even though we got all our module definitions in different
files, the function calls in eat_at_restaurant still work like a charm! It's
like the function calls are sayin', "Hey, I don't care that you're in a
different file, I'm gonna call you anyway!" And that, my friends, is the beauty
of this style. But wait, there's more! This technique allows us to easily move
modules to new files as they grow larger and more complex. It's like, when your
clone army gets too big, you just gotta make more files, ya know? And the best
part is, the pub use crate::front_of_house::hosting statement in src/lib.rs
hasn't changed one bit! It's still doin' its thing, makin' the hosting module
accessible to the outside world. And let me tell ya, that use statement is like
a magic wand, it just brings paths into scope and makes our lives easier. So,
use it wisely, my friends! Now, I know some of you might be thinkin', "Louis,
this all sounds like a bunch of hooey, what's the point?" Well, the point is,
this style allows us to keep our code organized, but still keep it connected.

    Summary

 So, you wanna learn about modular programming in Rust, huh? Well, let me tell
 you, it's like organizing your closet, but for code! Yeah, you heard me right,
 folks. We're gonna take all this messy, sprawling code and break it down into
 neat little packages, just like your grandma's Tupperware collection. And you
 know what the best part is? It's like magic, I'm tellin' ya! You can move these
 packages around, and the function calls still work like a charm! It's like
 those magic trick candies, you know, where you mix 'em all up, and then, voila!
 They're all in the right place!

Now, here's the thing, folks. We got this fancy-schmancy use statement that lets
us bring paths into scope. It's like a shortcut, ya see? Instead of typin' out
the whole long name of the module every time, we can just use this little
shortcut, and bam! We're good to go! It's like those little abbreviations in
text messages, you know, "lol" instead of "laugh out loud." Same idea, just a
whole lot more useful!

And you know what else is cool? We can make our code private by default, just
like your grandma's Tupperware collection. But, if we wanna share the love, we
can just add this "pub" keyword, and voila! Our code is like a big ol' picnic,
and everyone's invited! It's like openin' a window and lettin' the fresh air in,
ya know?

So, there you have it! Modular programming in Rust is like organizin' your
closet, but for code, and it's magic, I tell ya! We got these neat little
packages, and we can move 'em around like we're playin' Tetris. And with these
use statements, we can just bring the paths into scope, and boom! Our code is
all set! It's like havin' a whole toolbox of useful items at your disposal, just
like your grandma's Tupperware collection!
