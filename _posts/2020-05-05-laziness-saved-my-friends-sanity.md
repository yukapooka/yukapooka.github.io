---

layout: post
title:  "Laziness Saved My Friend’s Sanity"
author: stephen
categories: [ Python, Word-count, Mindset ]
tags: [red, yellow]
image: https://miro.medium.com/max/1400/0*-r5QnnOSmncv08w3
description: "How I happened to write a Python word count script"

---

Like many developers, I’m lazy. I value my time, but also my relatives’.

When I see a friend repeating a tedious task over and over again, it frustrates me as if it was my burden. Since I loathe recurring tasks, I want to find a way to automate them.

---

# Embrace the laziness

Automation consists of letting the machine do all the heavy work for you by giving it a set of instructions. It’s all about **efficiency**. I’ll level with you: I’m a programmer specialized in mobile development. I have no particular knowledge of scripting languages.

Not long ago, I came across an article that inspired me about how and why we can make our lives easier.

> https://automatetheboringstuff.com/

---

# Is it worth the pain?

Remember, most developers are lazy. Writing a script sounds like a pain to me. It’s likely the same for you as well. Ask yourself these questions: do you mind repeating the same task? Do you find value doing it by hand? If you waver at those questions, consider investing some time in automating.

I wanted to share with you a story that brought me to write a tiny script for my friend. I decided to go with Python since it was an excellent opportunity to discover this language.

---

# A word count issue

One day, my girlfriend came to me with a task. She works as a professional content writer. Sometimes, she happens to do translation jobs. Once, a company sent her a scenario to translate. Here is a sample:

```
Joey and Phoebe meets in a bar
Joey(smiling): [<How're you doing?>]
Phoebe welcomes him with open arms
Phoebe(cheerful): [<Oh! I'm feeling great!>]
```

Notice the separators inside the text? The company highlighted the zones to translate. The rest serves as extra information — essential to pick the right tone from the context. Once the job was finished, she would need to send the invoice to the company. Since my friend was charging per word, she needed to count how many words she translated.
Any word processor software can count words for you. Yet, she couldn’t charge for the whole text — not that she wouldn’t mind the bill. She had to exclude first what was outside the brackets. Unfortunately, the company did not provide her with such a tool.
As she was starting to count words by hand — we’re talking about 50000 words! — I had to intervene before she lost her sanity.

---

# Analyze requirements

The task was clear: count all the words within a defined separator. I started by breaking it down in smaller steps:

1. For all input lines, extract the text between `[<` and `>]`.
2. Merge all those formatted lines into a single block of text.
3. Split this block into a list of words
4. Compute the list’s length

With that in mind, I was ready to start the next phase.

---

# Automate with a script

I ended up writing this script:

<script src="https://gist.github.com/StephenVinouze/b203141d3eaeb75dad4e742999d2ca21.js" charset="utf-8"></script>

That’s all! I’ll admit it took me about two hours to put that down. But it was two hours well spent. I was proud to see how a few lines of code could save so much time to my friend! Her sanity too!

She only needs to insert her text inside the `inputString` variable then run the script to get the word count.

```
$ python word_counter.py
7 // there are seven words in the example above
```

For non-initiated Python developers, let’s break this code down.

---

## Extract text within separators

The first step required me to use a regular expression (Regex). They allow me to extract all lines matching a specific pattern. I ended up with this:

```python
import re
list = re.findall(r'\[\<(.+?)\>\]', inputString)
// ['How're you doing?', 'Oh! I'm feeling great!']
```
First, we must import the Regex library. Then we create a `list` by finding all sentences from `inputString` that start with `[<` and end with `>]`. Finally, the parentheses state we want to exclude the separators. I displayed, as a comment, the result obtained from our example at the beginning of the article.

## Create a sentence from extracted text

We want to flatten `list` into one sentence. We need to join the previous list into an empty string.

```python
subString = " ".join(list).replace('\xc2\xa0', ' ')
// "How're you doing?, Oh! I'm feeling great!"
```

Notice the `replace` method? Due to UTF-8 encoding, some [non-breaking spaces](https://en.wikipedia.org/wiki/Non-breaking_space) can emerge when copy-pasting your text. We can replace them with a regular space to count two words instead of one. Omitting words would not please my friend when she would generate her invoice!

## Split sentence into words

For this step, a simple split will do.

```python
words = subString.split()
// ['How're', 'you', 'doing?', 'Oh!', 'I'm', 'feeling', 'great!']
```

Before moving further, I had to check the result was correct. For instance, it might surprise you that “How’re” counts as one word. I was curious too. And yet, any online tool will confirm this.

## Count and print

Finally, count and print the size of our `words` list.

```python
count = len(subStr.split())
print count
// 7
```
---

# What to make out of it?

I’m aware this script is far from exceptional. There is room for improvement. I could, for instance, extract arguments such as the separators or the input text.

But it gets the job done. And that’s all I care about!

Was it painful? Not really. I managed to write a small script in a couple of hours without knowing Python. I even had fun writing it!

Was it worth it? Ask my girlfriend. So far, she seems thankful for having this tool.
