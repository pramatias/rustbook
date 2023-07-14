    Packages and Crates

We gotta get into Rust's package game - packages and crates are where it's at.

It sounds snazzy, but really it just means breaking things down into chunks, ok?
Like teeny tiny universes the compiler cares about. Throw a lone source file its
way, and boom, it treats that sucker as a crate. It's like a miniverse o'code
that deserves attention. But wait, there's more - inside every crate lies
modules like superhero squads eager to save the day. Assembling these teams
means compiling code from different sources into one sweet spot. So yeah, crates
ain't nuthin' special, but still kinda rad once ya wrap yer head around the
whole shebang. Now go forth and multiply your code crates like rabbits. That was
an accidental Bible reference... Sorry, God?

So I hear you want to learn about binary and library crates? Well, lemme break
it down for ya real quick. Binaries are the cool kids on the block, my friend.
They're like executive types, managers if you will. They handle running commands
and servers. Gotta love those bad boys!

And then there's the humble library crates. Not quite as flashy as binaries, but
damn they're important too. Library crates aren't running anything themselves;
rather, they're generously offering their goods to anyone who needs em'. Like a
communal kitchen, library crates share recipes for delicious functionality
across projects near and far. In fact, the Rand crate we met back in Chap 2 was
one such shining example. Think of library crates as the awesome bookshelf your
buddy loaned ya from his house next door. Brings a smile to your face and makes
ya wanna repay the favor! So now ya see why Rustaceans rave about libs left and
right?

Ever heard about crate roots? What do you call a single source file that acts as
a starting point for the rust compiler? A flippin' crate root that's what! Yeah,
think of it like the founding father of your code empire. Modules? We'll git
into dem' later. But just imagine, if ya will, code sections with distinct
purposes and sets of rules. Now ask yourself, have you gotten hip yet to the
modular vibes floatin' through Rustacespace? Don't worry, you won't feel outta
place for long, cuz it's high time you started exploring dat dere code universe.
Git ready fer some wild module adventures comin' round da corner soon enough...
maybe.

Hey, check this out, amigos - you know all about those gifts called "packages"
already? Great! Well let me tell you something, these little bundles of joy
ain't just your run-off-the-mill presents, no sirree! They're actual treasure
chests bursting with coding riches, just begging to be plundered by intrepid
code pirates like yers truly. (I mean come on guys, when was the last time you
saw an empty box sitting around Xmas morning saying "Please wrap me in festive
paper decorated with ribbon"? Exactly.) The catch though? Like most good things
in life, there's rules governing their construction - it's not some free-for-all
smorgasbord.

These packs need plans - namely a fancy document known as the Cargo.toml file,
kinda like the architectural blueprint guiding builders. Plus didya notice our
dear old pal Cargo herself happens to be, surprise surprise, another package
gemstone inside this necklace of wonders? It's almost like a paradoxical Russian
nesting doll or something, innit? One fine day while pondering the intricacies
behind her very existence I bet ol'Louis himself would've cracked up at this
meta laff riot too... Anyways, back to serious business - although packages can
bring on board countless hungry guests ooh-ing & ahh-ing over tasty new
functionalities, sadly only room remains for ONE honcho libra-server. Sorry,
rules are rules (and someone's gotta keep order around here)... As they say
though, a party isn't complete until after at least ONE crate shows up to work
its magic - don't be bashful, that guy could be you! Admit it, doesn't it make
ya proud knowing even the lowliest programmer holds keys to unlockin' these
magical coded chambers?

So we gots ourselves a project in need of some love, eh? Don't worry fam', we'll
whip it into shape quicker than a bake sale at fat camp. All aboard the "cargo
new" train (tickets required), destination: a whole new galaxy of possibilities.
Our mission objective? Simple as pie really, just give it the old "cargo new"
treatment followed promptly by our project name - now hear this - and we'll get
a shiny new baby package deal named "my-project", nice and easy.

```rust
$ cargo new my-project
     Created binary (application) `my-project` package
$ ls my-project
Cargo.toml
src
$ ls my-project/src
main.rs
```

 What else might you ask is needed besides a keyboard that works and fingers
 willing to dance with the clickity click click method? Why, nothing more than a
 sprinkle of your own unique code dust - add a dash o' creativity and voila (!)
 we've conjured up our very own microcosm of potential software power! (Bonus
 points awarded for the wordplay.) With cargo loaded up we're transported
 immediately via techno teleportation to a land of dreams called "my-project",
 with a veritable smorgasbord of files including two real showstoppers : A
 Cargo.toml file + a "src" directory with a "main.rs" file chillin' inside. It's
 like the perfect recipe for a delicious code sandwich, served piping hot from
 the mind kitchen of yours truly. Ah, but wait for it folks ... we've still
 gotta figure out how best to organize the files since each one does indeed
 possess an individual function. Wanna guess which two files will become crate
 roots depending on their location? Bet I fooled ya, both files play critical
 roles because Cargo.toml is the central nervous system (ahem, sorry code
 center), while src/main.rs serves double duty as the resident brainiac
 bookworm. It's all organized chaos at its finest, but heck, why should this
 crew stand alone under such pressure?

Take our dear ol' Rust programmery thing here - packages are big deals, almost
like they've got their own personalities or something (snorts). Anywho, say you
wanna make a simple li'l project called MyProject - yeah, that's right, not
exactly aiming high tonight are we? Heyohhhh... But alright, back ta bidness,
cargo then invites us ta come along fer the ride. Next step? Oh, simply drop da
source code folder down, no muss no fuss (just kiddin, don't actually drop
anything - unless ya want a brand new laptop smirks) Then, the cargo commander
guides our baby creation towards success, navigating through a whole slewta
files… Whoa, now hold on! I mean, yeez, these files ain't just ordinary pieces
o' digital fluff either, oh no siree. They each bring distinct skillsets ta the
table, like a specialized team of coding superstars.

First up, ya got da Cargo.toml file, layin' down da law o' da game. This sucker
contains vital info essential ta the survival o' da entire crater package cough,
erhm, package… The second star in dis here epic lineup? Ta boot, got yerself a
'src/main.rs'. Not sure bout da first impression, sounds kinda fancy schmancy,
eh? Fear not, this guy means serious business, actin' as anchor & nerve center
'round which all da funky dancin' happens. Finally, when life hands ya lemons,
grab 'n' throw em straight inta da bin, cause whatcha got now are multiples o'
BINARY CRATES!!!

if all you’ve got in your package is one big ol’ “src/main.rs” file, life’s
simple. One package = one binary crate. Easy peasy. But – oh snap – check this
out: toss in both “src/main.rs” AND “src/lib.rs”, and now suddenly two separate
crates exist. Suddenly, life ain’t so simple no more. Those twins aren’t
identical either – each packs an entirely different purpose! Binary crates share
the same name as the overall package whereas lib crates rock names based on the
"mod/" prefix plus the original package name. Like some kinda superpower twist.
You know what makes it even better though? Chuck whatever source files ye desire
into “src/bin/” or anywhere in your heart desires, and presto change-o,
instantaneous mutant offspring populate en masse. Bang, boom, crash course on
packaged crates in action.
