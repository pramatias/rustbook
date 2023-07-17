    Storing Keys with Associated Values in Hash Maps

Alright, folks, let's talk about hash maps. Hash maps are like those fancy
dictionaries you find in other languages, where you store a bunch of keys with
their associated values. It's like having a secret code that lets you find stuff
super quickly.

In Rust, we call them HashMaps. The HashMap<K, V> type is where the magic
happens. It uses a hashing function to figure out where to store those keys and
values in memory. Now, other languages might call them hash tables,
dictionaries, or associative arrays, but they all do the same thing: store
key-value pairs for easy lookup.

Why are hash maps useful? Well, imagine you're playing a game and you want to
keep track of each team's score. Instead of going through a long list and
searching for the team name every time, you can use a hash map. The team names
are the keys, and the scores are the values. Just give the hash map the team
name, and boom, you get the score in an instant.

Now, I'll be honest with you, folks. The basic API of hash maps is just the tip
of the iceberg. There's a whole bunch of cool stuff hidden in the standard
library's functions for HashMap<K, V>. If you want to dive deep and explore all
the goodies, check out the documentation. It's like a treasure trove of
knowledge waiting to be discovered.

    Creating a New Hash Map

Alright, folks, let's create a hash map and keep track of some scores. In this
example, we have two teams: Blue and Yellow. The Blue team starts with 10
points, and the Yellow team starts with 50 points.

```rust
    use std::collections::HashMap;

    let mut scores = HashMap::new();

    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);
```

Listing 8-20: Creating a new hash map and inserting some keys and values

To get started, we need to bring in the HashMap from the collections part of the
standard library. It's not automatically available, so we gotta do a little
extra work. But hey, it's worth it!

Now, we can create an empty hash map using the new function. We're gonna call it
scores, and it's gonna be a HashMap<String, i32>. That means the keys are gonna
be strings (representing the team names), and the values are gonna be integers
(representing the scores).

To add the scores, we use the insert method. We give it the team name as a
String and the score as an integer. For the Blue team, we insert "Blue" as the
key and 10 as the value. And for the Yellow team, we insert "Yellow" as the key
and 50 as the value.

And just like that, we've created a hash map and populated it with some data.
Easy peasy!

Now, keep in mind that hash maps store their data on the heap, just like
vectors. They're all about that dynamic memory allocation. And just like
vectors, hash maps are homogeneous, which means all the keys must be of the same
type, and all the values must be of the same type.

    Accessing Values in a Hash Map

Alright, let's access the values stored in our hash map. Here's how it goes:

We start by creating an empty hash map, just like before. We insert some data,
associating team names with their scores. Easy peasy.

Now, let's say we want to get the score for the Blue team. We use the get method
on our hash map, providing the key "Blue". This method returns an Option<&V>,
which means it might give us a reference to the value if it exists, or it might
give us None if there's no value for that key.

```rust
    use std::collections::HashMap;

    let mut scores = HashMap::new();

    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);

    let team_name = String::from("Blue");
    let score = scores.get(&team_name).copied().unwrap_or(0);
```
Listing 8-21: Accessing the score for the Blue team stored in the hash map

To handle this option, we do a little trickery. We call copied on the
Option<&V>, which gives us an Option<V> instead. This is just a way of getting
the actual value instead of a reference to it. Then, we use unwrap_or to either
get the score if it exists or set the score to zero if it doesn't.

And there you have it! We've successfully accessed the score for the Blue team.
In this case, the score is 10.

Let's talk about iterating over a hash map. It's a lot like iterating over a
vector, but with a little twist. Check it out:

We start by creating an empty hash map, just like before. We insert some
key/value pairs, associating team names with their scores. All good so far.

Now, here's where things get interesting. We use a for loop to iterate over each
key/value pair in the hash map. But wait, there's more! We use a special syntax
to destructure each pair into its key and value. It's like magic!

Inside the loop, we can do whatever we want with the key and value. In this
example, we simply print them out using println!. And voila! We get the pairs
printed in an arbitrary order.

So go ahead, iterate over your hash maps, unravel those key/value pairs, and
make the most out of your data. Who knew handling data could be so thrilling?

```rust
    use std::collections::HashMap;

    let mut scores = HashMap::new();

    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Yellow"), 50);

    for (key, value) in &scores {
        println!("{key}: {value}");
    }
```

Inside the loop, we can do whatever we want with the key and value. In this
example, we simply print them out using println!. And voila! We get the pairs
printed in an arbitrary order.

So go ahead, iterate over your hash maps, unravel those key/value pairs, and
make the most out of your data. Who knew handling data could be so thrilling?

This code will print each pair in an arbitrary order:

Yellow: 50 Blue: 10

    Hash Maps and Ownership

Let's talk about ownership when it comes to hash maps.

Here's the deal: when you insert values into a hash map, something interesting
happens. For types that implement the Copy trait, like i32, the values are
copied into the hash map. It's like making duplicates of your precious data. But
for owned values like String, it's a different story.

```rust
    use std::collections::HashMap;

    let field_name = String::from("Favorite color");
    let field_value = String::from("Blue");

    let mut map = HashMap::new();
    map.insert(field_name, field_value);
    // field_name and field_value are invalid at this point, try using them and
    // see what compiler error you get!
```

Listing 8-22: Showing that keys and values are owned by the hash map once
they’re inserted

In Listing 8-22, we have two String variables: field_name and field_value. We
insert them into the hash map using the insert method. And here's the twist: the
hash map becomes the owner of those values. They're no longer valid outside the
hash map. It's like a wild game of ownership transfer.

If you try to use the variables field_name and field_value after they've been
inserted into the hash map, you'll get a nasty compiler error. It's a way of
telling you, "Hey, those values don't belong to you anymore. The hash map owns
them now!"

But here's a little trick: if you insert references to values into the hash map,
the values won't be moved. They'll just hang out there, waiting for the hash map
to do its thing. Just remember, those values better stick around as long as the
hash map is still kicking.

So be mindful of the ownership dance when dealing with hash maps. They can be
quite possessive, but hey, they're just trying to keep your data safe.

    Updating a Hash Map

Alright, let's talk about updating a hash map. It's all about making choices, my
friend.

Here's the deal: each unique key in a hash map can only have one value
associated with it at a time. So when you want to change the data in a hash map,
you've got some decisions to make.

First option: you can replace the old value with the new value, like ripping off
a band-aid. The old value is gone, and the new value takes its place. No looking
back. To do this, you can use the insert method. It's a one-way street.

Second option: you can keep the old value and ignore the new value. It's like
saying, "Hey, I'm good with what I've got. No need for anything new." This is
useful when you only want to add a value if the key doesn't already have one.
You can use the entry API to achieve this. It's all about being picky.

Third option: you can combine the old value and the new value, like mixing two
colors to create a whole new shade. It's all about collaboration, my friend. You
can use the entry API again, but this time with the or_insert method. It's like
a collaboration dance between the old and new values.

So there you have it. When it comes to updating a hash map, you've got options.
You can replace, ignore, or combine.

    Overwriting a Value

So, here's the deal: when you insert a key and a value into a hash map, and then
you insert that same key with a different value, guess what happens? The value
associated with that key gets overwritten. It's like a game of musical chairs
where the last one standing takes the seat.

```rust
    use std::collections::HashMap;

    let mut scores = HashMap::new();

    scores.insert(String::from("Blue"), 10);
    scores.insert(String::from("Blue"), 25);

    println!("{:?}", scores);
```

Listing 8-23: Replacing a value stored with a particular key

In the code shown in Listing 8-23, we're playing this game. We insert the value
10 for the key "Blue", and then we come back and insert the value 25 for the
same key "Blue". And what do we get? Only one key/value pair in the hash map, my
friend.

So when we print the hash map, we see {"Blue": 25}. The original value of 10 has
been kicked out of the game and replaced by the new value of 25. It's like a
ruthless takeover.

So remember, when you're dealing with a hash map, be careful with your
insertions. If you insert a value with a key that already exists, you're saying,
"Hey, I've got something new for you. Take this and forget the old stuff." It's
all about survival of the fittest in the world of hash maps.

    Adding a Key and Value Only If a Key Isn’t Present

Alright, let's talk about handling those keys in a hash map. Sometimes you want
to check if a certain key already exists, and if it does, you just want to leave
it as it is. But if the key is not present, then you want to insert it along
with a value. It's like being selective about who gets to join the party.

In Rust, hash maps have a special trick up their sleeve called entry. This API
allows you to check if a key exists in the hash map and take the appropriate
action. It's like having a bouncer at the door who decides who gets in and who
doesn't.

```rust
    use std::collections::HashMap;

    let mut scores = HashMap::new();
    scores.insert(String::from("Blue"), 10);

    scores.entry(String::from("Yellow")).or_insert(50);
    scores.entry(String::from("Blue")).or_insert(50);

    println!("{:?}", scores);
```

Listing 8-24: Using the entry method to only insert if the key does not already
have a value

Let's say we have a hash map called scores and we want to check if the key for
the Yellow team exists. If it doesn't, we want to insert the value 50. The same
goes for the Blue team. With the help of the entry method, the code looks like
Listing 8-24.

So, what happens here? Well, the entry method takes the key as a parameter and
returns an enum called Entry. This enum represents a value that might or might
not exist. It's like playing a game of chance.

In our code, we call entry for the Yellow team and use the or_insert method with
the value 50. If the Yellow team doesn't have a value, it gets inserted with the
value 50. The same goes for the Blue team. It's like giving them a reserved spot
in the hash map, but only if they don't already have one.

When we print the hash map, we see {"Yellow": 50, "Blue": 10}. The first call to
entry inserts the key for the Yellow team with the value 50 because it didn't
exist before. But the second call to entry doesn't change anything because the
Blue team already has a value of 10. It's like the Blue team is already having a
blast, so we don't need to give them another ticket.

So with the entry API, we can handle the presence or absence of keys in a more
elegant way.

    Updating a Value Based on the Old Value

Now, let's talk about updating values in a hash map based on their old values.
It's like having a conversation where you listen to what someone has to say, and
then respond accordingly. In this case, we're going to count how many times each
word appears in a given text.

```rust
    use std::collections::HashMap;

    let text = "hello world wonderful world";

    let mut map = HashMap::new();

    for word in text.split_whitespace() {
        let count = map.entry(word).or_insert(0);
        *count += 1;
    }

    println!("{:?}", map);
```

Listing 8-25: Counting occurrences of words using a hash map that stores words
and counts

In the code shown in Listing 8-25, we start with a variable called text that
contains the phrase "hello world wonderful world". Our goal is to count the
occurrences of each word in this text. So we create an empty hash map called map
to keep track of the words and their counts.

We then use the split_whitespace method on the text variable to get an iterator
over the individual words in the text. It's like breaking down the text into
bite-sized pieces for further processing.

Next, we iterate over each word in the iterator using a for loop. For each word,
we use the entry method on the hash map to check if the word already exists as a
key. If it does, we retrieve a mutable reference to its value using the
or_insert method with a default value of 0. This is like checking if we've
already counted this word before. If it's the first time we've encountered the
word, we insert it into the hash map with a value of 0.

Now comes the interesting part. We have a mutable reference to the count of the
word, stored in the count variable. To update the count, we dereference the
mutable reference using the asterisk (*) and then increment the value by 1. It's
like adding another tally mark to the count.

After processing all the words in the text, we print the hash map, which will
show us the counts of each word. The output will be something like {"world": 2,
"hello": 1, "wonderful": 1}. However, keep in mind that the order of the
key/value pairs may vary because hash maps don't guarantee a specific order when
iterating over them.

So with this code, we can count the occurrences of words in a text and keep
track of them using a hash map. It's like having a tally counter for each word,
and every time we encounter the word, we increment its count.

    Hashing Functions

Let's talk about hashing functions. You know, those magical algorithms that take
some data and turn it into a unique code. In the case of HashMap, it uses a
hashing function called SipHash by default. Now, SipHash may not be the fastest
hashing algorithm out there, but it provides better security and protection
against Denial of Service (DoS) attacks involving hash tables. It's like having
a bodyguard for your hash map, making sure no one messes with it.

Of course, if you find that the default hash function is slowing you down and
you need something faster, you can switch to a different hashing algorithm. In
Rust, you can specify a different hasher by implementing the BuildHasher trait.
Don't worry if you're not familiar with traits yet; we'll dive into them in
Chapter 10. And the great thing is, you don't have to start from scratch and
build your own hasher. There are libraries available on crates.io that provide
hashers implementing various common hashing algorithms. It's like having a
buffet of hashers to choose from!

So, whether you stick with the default SipHash or opt for a different hasher,
the choice is yours. Just remember that the default option prioritizes security
over speed, but you have the power to tailor it to your specific needs. It's all
about finding that perfect balance between performance and protection.

    Summary

Alright, folks, let's recap what we've learned so far. We've covered vectors,
strings, and hash maps - the dynamic trio of data storage and manipulation. With
these bad boys, you've got all the tools you need to handle, access, and modify
your precious data.

Now, let's put your skills to the test with a couple of exercises. First up,
given a list of integers, you gotta use a vector to find the median (that's the
value right in the middle when you sort the list) and the mode (that's the value
that shows up the most). And hey, a hash map will come in handy for that mode
business!

Next, we're gonna have some fun with pig latin. You know, that language where
you move the first consonant of each word to the end and add "ay." But hold on,
we gotta be careful with those UTF-8 encoding rules. Gotta keep things legit,
you know?

And finally, let's create a text interface for managing employees in a company.
We'll use a hash map and vectors to let the user add employee names to different
departments and retrieve lists of people in a department or the whole company.
Gotta keep everything organized and sorted alphabetically, because chaos is no
good for business.

To tackle these exercises, you can dive into the standard library API
documentation. It's your trusty guide, showing you all the methods and goodies
that vectors, strings, and hash maps have to offer.

But wait, there's more! We're about to get into some tricky territory where
things can go wrong. That's right, it's time to talk about error handling.
Buckle up, my friends. We're in for a wild ride!
