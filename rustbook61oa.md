    Defining an Enum

Hey folks, let me tell ya somethin', enums are where it's at. Structs are cool
and all, but enums bring the heat. Picture this: structs are like those trusty
sidekicks who help you organize and group related data, but enums, my friends,
take things up a notch. They're like the magical gateway to a realm of
possibilities, allowing us to define values that belong to a specific set of
options. It's like saying, "Hey, these are the choices on the table, and that's
the name of the game!"

Imagine we're venturing into the intriguing domain of IP addresses. Now, there
are two main versions to reckon with: version four and version six. And you know
what? Enums are like the wondrous artist's brush that can capture these options
effortlessly. We can conjure an enum that represents all the diverse flavors of
IP addresses we might stumble upon.

Oh, but wait, let me put it in more relatable terms for you, dear adventurers!
Enums are like the choices in an ice cream shop. You walk in, and the server
tells you, "Hey, we've got chocolate and vanilla, take your pick, and no fancy
sorbet or triple-dipped flavors!" It's straightforward, no-nonsense
decision-making. Just like when you give a presentation and you say, "Here's
slide one, move along, folks." No need for elaborate theatrics. Enums keep it
simple, and they keep it real.

So, you know how structs group related fields and stuff, right? Well, enums take
it to another level. They let us define a set of possible values. Like, "hey,
this thing can only be one of these options". It's like saying, "these are the
choices, pick one".

Now, let's say we gotta deal with some IP addresses. There's version four and
version six, but never both at the same time. That's the nature of things. And
guess what? An enum is perfect for that. We can make an enum that says, "here's
all the kinds of IP addresses we might run into".

Here's the beauty part: an IP address can only be one of those versions, not
both. But get this: even though version four and version six addresses are
different, they're still fundamentally IP addresses. And that's where enums
truly rock. They let us treat all these variants as the same type when our code
handles situations that apply to any kind of IP address.

Hey folks, let's get down to business and define our own data type for IP
address kinds. We're gonna call it IpAddrKind. This enum will represent the
different flavors of IP addresses we can encounter. And lemme tell ya, we got
two delicious options on the menu: V4 and V6.

So, our enum looks like this:

```rust
enum IpAddrKind { V4, V6, }
```

IpAddrKind is a brand-new type we can use throughout our code. It's like
creating our very own data category exclusively for IP address kinds. This
allows us to be more precise and expressive when workin' with IP addresses. No
more guesswork or ambiguity. We've got our enum to keep things nice and tidy.

Hey folks, now that we've got our IpAddrKind enum all set up, it's time to play
with some enum values. To create instances of each variant, we simply use the
enum's identifier, follow it with a double colon, and then add the variant name.
It's like bringing these little enum babies to life!

Check it out:

```rust
let four = IpAddrKind::V4; 
let six = IpAddrKind::V6;
```

We've got two IP address kinds right here under the IpAddrKind namespace: V4 and
V6. These guys are ready to roll whenever we need 'em.

But check out the best part: both V4 and V6 share the same parent, IpAddrKind.
That means we can toss 'em around, stick 'em in variables, and even use 'em as
function arguments. It's like having two siblings who can do anything their big
brother (the IpAddrKind) can do.

Hey there, let me give you an example of why enums are so darn useful. Check out
this function called route that takes an IpAddrKind as its parameter.

```rust
fn route(ip_kind: IpAddrKind) {}
```

You know what happens next? You better believe we can pass in either V4 or V6 to
that bad boy.

```rust
route(IpAddrKind::V4); 
route(IpAddrKind::V6);
```

Just like choosing between pepperoni or sausage on a slice of pie, we can go for
the V4 flavor or heat things up with some V6 action. At the end of the day, our
trusty route function knows exactly how to handle both variants since they're
all related under IpAddrKind umbrella.

So don't hesitate, folks. Get cracking and start crafting killer code capable of
tackling various situations. Enum powers unleashed!

while it may be easy to fall back on the classic ways, let me show you how enums
actually pack some extra oomph in solving problems. Take a gander at this
situation where we wanna store the IP address type and the actual address
details.

We previously had our IpAddrKind enum with those V4 and V6 variations. In order
to stock the info plus connect it to the variant, we bring forth a structure
called IpAddr. It consists of two members - kind, being IpAddrKind (our enum we
fashioned before), and address, a String.

Look at how simple yet effective our new syntax looks:

```rust
enum IpAddrKind {
    V4,
    V6,
}

struct IpAddr {
    kind: IpAddrKind,
    address: String,
}

let home = IpAddr {
    kind: IpAddrKind::V4,
    address: String::from("127.0.0.1"),
};

let loopback = IpAddr {
    kind: IpAddrKind::V6,
    address: String::from("::1"),
};
```

While our IpAddrKind enum does a great job of distinguishing between IP types V4
and V6, we still need somewhere to stash the actual addresses themselves. So,
let's break down these instances we're working with...

Home sweet home and loopback represent IPv4 and IPv6 respectively, duh! The
first one's got the V4 variation of IpAddrKind and the address is "127.0.0.1",
while the second comes equipped with V6 kind and "::1" as its address. They come
bundled up into our IpAddr buddy along with their corresponding data, lockin'
em' up tight like a kid in timeout.

What if I told you there was an even easier way to group related data than using
structs? That's right, enums are here to save the day once again. Not only do
they allow us to differentiate between types of IP addresses, but they also let
us attach additional information to each variant.

Check out this new definition of the IpAddr enum. It's slim, it's sleek, and
it's got data directly attached to each variant:

```rust
enum IpAddr {
    V4(String),
    V6(String),
}
```

Our IpAddr enum just landed a fresh upgrade that makes the concept of IP
addresses sing even louder. Variants carry their own associated values directly
inside the same enum. One line item, many bells & whistles. With this baby, we
make enum instances pop outta thin air with their very own customized
stringiness. Each variant gets its unique sauce of character-based hype. It's
like loading up your favorite pie with all kinds of flair. Try not to drool over
this beautiful piece of functionality.

Here's how you'd make a friggin' awesome home IP address: V4 with the address
"127.0.0.1". And lemme tell you, it's like getting a brand spankin' new laptop
-- easy as breathing. The catch is, you don't just buy some off-the-shelf stuff;
you roll up your sleeves and build the damn thing yourself.

```rust
    enum IpAddr {
        V4(u8, u8, u8, u8),
        V6(String),
    }

    let home = IpAddr::V4(127, 0, 0, 1);

    let loopback = IpAddr::V6(String::from("::1"));
```

That V4 train rolls by with the value "127.0.0.1". And now let's twist this
sucker up with V6, like we're the cool kids on the block. Loads of fun with that
"::1" business.

We could take this stuff even furthersville with them fancy constructor
functions - IpAddr::V4(), IpAddr::V6(). These guys act like magic elves who make
the stuff appear before our very eyes, like we're conjuring pizzas from some
mystic circle. Order yours up from that big enum menu in the sky and watch the
goods arrive hotter than a volcano.

So, say goodbye to the extra struct and enjoy the simplicity and convenience of
attaching data directly to each variant.

Using enums means we get options, man! Like, instead of only carrying one type
of associated data (such as strings), we can mix it up, have multiple choices.
What's better than havin' a bunch of useful items in a single box of tricks?
Well, not much else except maybe some free ice cream coupons or a winning
lottery ticket stuck under my pillow. But hey, you get the point.

First off, we got ourselves a problem: representing IP addresses in two
different ways - v4 as u8 array and v6 as single string. But don't be
discouraged, enums bring solutions like Santa on his sleigh ride. Check out this
next level enum setup, making sure you understand exactly what the heck's going
on. Who needs structs anymore anyway, am I right? #goldenmicdropbaby

Take a look at this beautiful enum definition:

```rust
    enum IpAddr {
        V4(u8, u8, u8, u8),
        V6(String),
    }

    let home = IpAddr::V4(127, 0, 0, 1);

    let loopback = IpAddr::V6(String::from("::1"));
```

Yo, here's a little secret about enums versus structs: Enums will let you have
completely different types and amounts of associated data for each variant. You
better believe I'm bringing some fire to this comparison because enums glow
bright while structs just chill in the dark. In other words, it's like a box of
superheroes who all get their powers from different sources and can save your
code from danger.

Take a look, it's a sight to behold -- you can totally have your V4 as a u8
array or a V6 as a nice Stringy surprise. With enums, you can handle different
types and amounts of associated data effortlessly. The beauty never ends once
you go enum.

Hey there people! Wanna hear something interesting? Turns out Rust has figured
out how to store IP addresses in a pretty nifty way already. Yeah, no need to
break our heads figuring it out. The awesome peeps working on the libstd library
thought things through ahead of time. They made these cute li'l Ipv4Addr &
Ipv6Addr structures that hold the IP info.

They went ahead and whipped up these masterpiece classes called Ipv4Addr and
Ipv6Addr. Can ya feel the heat of creative genius radiating from their very
names? Truth is, they might just house a few secrets within 'em and I couldn't
possibly imagine how much brainpower must've gone into creating them. These
structs probably have some cool stuff inside, but I'll just leave that to your
imagination. Trust me, they're snazzy.

Aye there! I know I said it before, but seriously now... It seems my main man
Standard Lib has also decided to join the party! They took their sweet time
crafting not one, but TWO class acts for IP versions Four AND Six respectively,
named Ipv4Addr and Ipv6Addr. Jeez Louise, I bet they were sweating bullets
thinkin' up new-fangled ideas day and night.

Here's how it looks:

```rust
struct Ipv4Addr { // --snip-- }

struct Ipv6Addr { // --snip-- }

enum IpAddr { V4(Ipv4Addr), V6(Ipv6Addr), }
```
Spoiler alert though, brace yourself kids cuz here's where things start getting downright fancy. Their IpAddr enum packs Ipv4 and Ipv6 right smack in the middle of its own variety of variants. Don't try telling me this ain't straight up beautiful. Just take a gander at how V4 and V6 can hold something as simple as an address and you'd still think, honey, they've got something else hidden underneath those slim lil' clothes.

This whole thing here coulda turned into one wild nested-doll extravaganza if
only someone (cough cough, yours truly) would've had a better idea before. Man
oh man, you can stick anything anywhere in an enum variant: strings, ints, more
complex types, maybe even a circus animal act for all I care. This IpLib thing
brings way mo' fun than my humble experiments; so why delay?

Y'know what guys? I mean, who'da thunk that our dear friend Standard Library
wouldn't show off its ultra-cool moves once again with yet ANOTHER enum? Brace
ye selves for the motherload, 'cause it's a veritable smorgasbord o' type
variants. Hang on tight fer a wild ride, 'cuz this sucker'll keep you guessing.

Meet Message, No. 6.2. If ya thought our earlier friends was purdy cool, lemme
tell ya, this guy takes the cake. He's got FOUR variants n' each one's got a
different flavor. An' yeah, don't go thinking no ordinary vanilla or chocolate
here neither! There's gonna be action on yo plate!

```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}
```

So feast yers eyes 'pon this here Quit, Move {x, y}, Write(string),
ChangeColor(int1, int2, int3). That last one's kinda exotic innit? But what does
it matter when every single one flexes them muscles n' packs everything inside
like a righteous punch! Flexibility? Check. Versatility? Double check mate. Jump
back to Stepford? Triple quadruple check mark dat mutha *ucka! It's like the lib
was havin' a crazy sale! Take whatcha want, 'n rock out da new stuff fer hours!
Keep it comin', lib!

First up, we have Quit. It's a variant that says "I don't need any data, I'm
good on my own." No strings attached, no fields to worry about. Just a simple
Quit. Hey, sometimes you just gotta say, "I'm out!"

Then we have Move. Now, this variant is fancy. It has named fields, just like a
struct. It's like the enum version of a well-organized move. It knows exactly
where it's going with its x and y coordinates. Smooth moves, my friends.

Next in line is Write. This variant comes with a special gift—a single String.
It's like someone handing you a note, but instead of paper, it's wrapped in a
variant of an enum. How poetic.

Last but not least, we have ChangeColor. This variant brings a burst of color to
the party with not one, not two, but three i32 values. It's like a triple threat
of integers, ready to paint the town with its RGB magic. Three little numbers
just waiting ta make life a li'l more colorful. Go ahead, try me now. It's like
they couldn't resist stuffin' more awesome into that damned thing. Oh I bet they
were just rubbin' their hands together thinkin', "How much more awesome shit can
we fit in dere?" God bless 'em, amirite? They're just pourin' on the
functionality like it ain't nobody's business.

Defining enums is kind of like defining different kinds of structs, but without
all the fancy "struct" keywords cluttering up your code. It's like cutting
through the noise and getting straight to the point.

Check out these structs that could hold the same data as the enum variants we
saw earlier:

```rust
struct QuitMessage; // unit struct
struct MoveMessage {
    x: i32,
    y: i32,
}
struct WriteMessage(String); // tuple struct
struct ChangeColorMessage(i32, i32, i32); // tuple struct
```

Let me show you guys another example. Here's a list of snowflakes - I mean,
structures - which are almost identical to our friend from before. Only
difference being, each structure is an individual and needs to be handled
separately. Talk about boring sex scenes. Good Lord. Look at these guys...

That's where enums come in handy again! With enums, you can group all these
variants together under one single type. It's like having a neat little package
that can hold different kinds of messages. So, you can define a function that
takes any of these message types without breaking a sweat.

 When it comes to keeping track of all them message types, it's like trying to
keep tabs on a mob of kids. But lemme tell ya about Enum. This guy brings order
to the madness by putting all these different types under one roof. No more
dealing with individuals that need special attention, everything is taken care
of nice and tidily. You can even write functions that accept multiple types
without losing your cool. Plus, not only can you use impl on structs but also on
freaking enums themselves. Check it out here, this baby takes on more
responsibilities than a working momma. (Sorry Mom!)

```rust
impl Message { 
    fn call(&self) { 
        // We'd put the method's body here, you know, the code that does stuff
        } 
    }
let m = Message::Write(String::from("hello"));
m.call();

``` Now, what does this method do? Well, it uses "self" to get the value that we
called the method on. So, if we have a variable like "m" with the value
Message::Write(String::from("hello")), when we call "m.call()", "self" will
refer to that value inside the method body.

What if I told you guys that Rust has a built-in superpower that lets you create
flexible enums that can handle data types other than the ones they were
originally designed for? Well folks, say hello to the good old Enum. It's like
giving your enums a sidekick that helps take on more tasks than you thought
possible.

Meet the man of mystery himself, Optional. Like a great wingman always ready to
step in and help you avoid the awkward moments or unneeded errors, he lets you
take on situations where a value could either be present or absent. You see,
Option is all about handling scenarios where a value could be something or could
be nothing at all.

Alright folks, imagine you got a list and you wanna pick the first item. If that
list is empty, then boom! Nothing gonna happen. Now enter option, stage left.
Option says, "Hey, let's deal with this in a safe and sound manner". By using
Option, you got yourself an ally to handle each case that may arise - empty or
not - so that no unwanted surprises pop up. Result? Avoiding the kinda bugs that
make other languages look silly.

As for null... Naaaah, don't count on rust to fall for that trickery. The game
plan here is simple; go ahead and strip away whatever ain't needed. In other
words, null didn't pass muster in this place. From bugs to confusion to security
breaches...it's like inviting chaos itself, just sayin'. Can't stress enough the
harm it did in past years.

Okay, let me break it down real quick, back in the day, some dude named Tony Hoare went full Steve Jobs mode and declared "let there be light and add these features fast!" but little did he knew it turned into "oh crap! I blew a billion dollar hole?! What the hell did I do?" cause holy smokes! That mistake caused major headache across the globe like nobody's business. Turned out the "easy to implement" button ended up being more trouble than peace. So listen up, people! Don't mindlessly press buttons because sometimes even smart folks can act dumb (not naming names cough Tony cough).

But fret not, Rust's all about learning from past mistakes and taking precautions before diving deep sea of coding adventures. They've made sure their guardian angels like Option, are looking out for any mischief lurking around corner so stuff gets handled right without going bust.

Oh boy, null is one tricky guy. Treat it wrong and KABOOM, things blow sky high. Sure, it tries to give us a heads up when something's missing. But the execution? Less effective than a 2nd grade art project. 

Enter, Rust. Taking a swing at null's issues, it does things its own unique way, making Option<T> a star player on the team. This guy makes dealing with present OR absent info look sleek. Trust me, this kid's got mad skills to keep everything under control. So forget null's half ass attempt at fixing stuff. Go with Option.

So here's the deal. Option<T>, it's like a party invite for your code. Simple enough to understand, but packing some serious punches when it comes to handling values. It's basically saying "Hey, do I need to bring a gift or should we just grab drinks instead?" No biggie if it says "None", means nothing's coming.

```rust
enum Option<T> { None, Some(T), }
```

But oh boy, if it screams "Some<T>", then put your dancing shoes on cuz good
times are rolling. Bottom line, it might look basic, but it's really your best
buddy when you want your code to go places. And honestly, who wouldn't love a
friend that knows exactly when to hold 'em or fold 'em.

Instead of using null, why don't we go with something that actually works in our
favor? Like, Option<T> man! It's like having an insurance policy against runtime
errors. With it, you won't be caught off guard by pesky invalid data types.

Plus, Option<T> is built into Rust's core, so you don't have to import anything
extra. We're talking total support and comfort for your codebase. Don't settle
for mediocre solutions - demand more outta your tools, people! Make the switch
from null to Option<T> today (or whenever you feel like getting rid of null).

so here's the lowdown on <T>. That little bugger stands for Generic Type. In
other words, it lets us write flexible functions and methods that work across
multiple types. Think of it as a key that unlocks the door to versatility. You
see, Rust forces us to think ahead when creating code components that could
potentially serve many purposes down the road. With <T>, we're not limited to
one single functionality. It's like having a Swiss Army Knife for code - always
handy, never lonely.

In short, don't stress too much over <T> alone. As soon as we start discussing
generics proper, the fog shall clear, grasshopper. For now, take a deep breath,
relax those shoulders, and bask in the glory of code's boundless possibilities.

Oh wait, before you leave me hangin', lemme share some real-world juicy bits:
we've worked hard here to create a functional yet concise example using Option
with various types. Feast yer eyes upon these bad boys!

```rust
let some_number = Some(5); 
let some_char = Some('e');

let absent_number: Option<i32> = None;
```
First order of business: dealing with them pesky optionals. If you ain't familiar, Options are values that might either contain a valid value or none at all. Sorta like hitting up Taco Bell at midnight - sometimes you score a meal, others you walk away hungry AF. But enough about tacos, back to your Rust code! Let's take a look at our examples...

Some_number? What kind of name is that? Well, don't judge, homeschools. This guy
holds a value of 5 inside an Optional<i32>. That's right, it can contain stuff!
And what about some_char? A character in another optional, innit. The
difference? His type says chars::char rather than std::i32 since he's a special
breed.

Lastly, absent_number. He's tricky cuz he ain't got no value. So we need ta
specify his typage for Rust ta understand he's an optional w/ an undefined value
inside. We give him a lil' reminder that if ya build something around him
eventually, he'll be an Optional<i32>. Ta avoid confusion on both sides of the
screen.

ust by including <T> in our code, we get a flexible way to write options that
adapt to any data type we desire. Think about it like a restaurant menu – the
variety keeps coming until you find the best fit for every craving. Oh yeah, and
did someone say error handling? We're not gonna leave any crumbs behind because
that just messes up the kitchen (our programs).

Here's the lowdown: why should we rock Option<T> over the old pal null?

Well, first off, let's remember we don't want accidents happening when cooking
up our programs. Option<T> and T are not exactly the same recipe. Our compiler
catches when we accidentally misuse a value we think could be there ('cause it
has a chance to be), preventing us from making a mess. To summarize: by using
<T> we bring ourselves closer to a safe and sane Rust programming journey. Trust
me – your momma and gramma will thank you later.

Let me show you an example:

```rust

let x: i8 = 5; 
let y: Option<i8> = Some(5);
let sum = x + y;

``` what happens when you try mixin' apples n' oranges – i8 + Option<i8>! You
may think you can just pluck one outta either group and go nuts, but hold on one
sec. Rust's like, "I know that's tempting, but I need to make sure what you're
putting together is legit". When workin' with i8 or similar types, they're
standalone heroes ready for action. That's what Rust expects! But with <T>?
There's risk involved, bruh! So Rust demands we take the time to treat it proper
– otherwise it'd be like makin' a smoothie filled with ice cubes.Keep trustin'
that solid T to get where ya want to go with care, okay?

```rust
$ cargo run Compiling enums v0.1.0 (file:///projects/enums) error[E0277]: cannot
   add `Option<i8>` to `i8` --> src/main.rs:5:17 | 5 | let sum = x + y; | ^ no
   implementation for `i8 + Option<i8>` | = help: the trait `Add<Option<i8>>` is
   not implemented for `i8` = help: the following other types implement trait
   `Add<Rhs>`: <&'a i8 as Add<i8>> <&i8 as Add<&i8>> <i8 as Add<&i8>> <i8 as
   Add>

For more information about this error, try `rustc --explain E0277`. error: could
not compile `enums` due to previous error
```

 Yup, we're talking about those pesky situations when a variable ain't
 necessarily holding its promised value. Well, say hello to Option<T>. This
 guy's here to save the day, y'hear?

See, this little fella helps us stay organized and avoid errors related to those
oh so tricky missing values. What does this mean exactly? Simply put, it
requires us to carefully examine each situation and account for the possibility
of a missing value or "absence" altogether - it's kinda like packing for
vacation while hoping the weather holds up, only now we're looking after our
precious data too. Don't worry though, the compiler will give us gentle
reminders whenever a potential issue arises. In layman terms, this means Rust
takes good care of us and steers clear of chaos, keeping everything neatly
sorted. Options are key players in our Rust experience and once mastered,
they'll help build stronger, sturdier apps in no time.

Now let's spill the tea on convertin' them Option<T> into good olregular T. Now
lemme ask you this: Ever been stuck with some raw code that was actin' all
mysterious and unpredictable? Like maybe somethin' crashed and burned cuz ya
didn't know whether somethin' was null or not? Sounds rough, huh? Yeah,
well...it ain't pretty.

So how can we fix this mess and get some peace of mind?You guessed it, the big O
himself, Option<T>. Our mission? Convert the boring old Some, None` stuff into
actual tangible objects. Ya know, the ones you'd wanna show off to your buds and
strut around town with pride.

We've been talkin' bout those naughty nulls and how Rust keeps 'em in check.
Well, it's all thanks to one tiny yet powerful word: lift(). Now, what do ya
think happens when we take a peek behind that curtain? The answer may surprise
you. We transform a lil' thing called "Option<T>" into a proper T and suddenly
poof!, we've magically turned a maybe into a sure thing. Yep, ya heard me right.
That there's a solid gold ticket to avoid the trap of assumptionville.

When it comes to dealin' with Option<T> values, Rust gives us a helping hand
through its own set of methods. Head on over to the official docs and make
friends with these bad boys. They'll stick close by your side on your quest to
banish the nonsense of null. In return for their loyalty, ya gotta promise to
keep the lines clean and treat 'em real good. In simple terms, that means
writin' code that understands which type of Option<T> flavor it's dealing with.
The plan: separate the wheat from the chaff, baby. If ya hit pay dirt with a
Some(T), then put on yer dancin' shoes 'cause it's time to get busy with that
juicy T treasure inside. But let's not forget the poor soul who didn't quite
make the cut. Them's still important too, ya hear? So, with the help of ol'
reliable pal Match expression, let's spin a few circles and gracefully move
between both types like pros. Control flow is key, but you already knew that.

So remember, in Rust, handling Option<T> is the name of the game. It's about
being responsible, confident, and in control. Leveling up your programming
skills, one match expression at a time.
