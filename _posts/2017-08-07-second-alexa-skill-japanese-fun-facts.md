---
layout: post
title: My Second Alexa Skill - Japanese Fun Facts
---

So this time around I did a fact skill instead of a trivia skill. I chose to do Japanese fun facts because I absolutely love the culture. Through the exercise, I actually uncovered a few additional gems I didn't know about. Definitely check out the Alexa skill if you're interested about Japan and Japanese culture.

Similar to my first skill, Amazon also created a boilerplate template for fact skills. Putting together the skill really just required coming up with the content and then following the instructions step-by-step. Amazon is beta-testing a new feature where a user interface is available for building intents. All you need to do is click create an intent, populate the utterances to trigger the intent and the code is filled in with your inputs.

One thing I'm not a big fan of working with Alexa is you build your skill intents and setups in the Amazon Developer Portal but the logic of how your skill works is built in Amazon Web Services (AWS). Your Alexa skill then references the ***logic*** piece through a code provided in AWS. While I'm all in favor of code reusability, it just seems the pieces of the puzzle are all scattered in different places.

***Update on Anime Quiz Time Skill***

So my first skill was fully approved, but I had the most difficult time getting it to work. I keep telling Alexa "Open Anime Quiz Time..." but it keeps telling me to enable some TV skill. Turns out the cause was because on my phone, my Amazon app is logged onto a different account from my developer account. As such, I need to enable the skill on the same account to get it to work. It would've been helpful if Alexa gave a clearer error message on what's going on.

***Playing With My New Skill On My Phone***

Now that I finally got it to work. I ran through the trivia twice and got a 5/5 perfect score each time. Yay for knowing the answers to the questions I wrote!

***Overall Impressions of Alexa***

1. Alexa is not very good at pronunciation. Granted my questions were about Japanese anime, so there were Japanese names and terms that Alexa pronounced badly.

2. Alexa needs to work on sounding more human. The places in a sentence that Alexa puts emphasis on seem out of place to the ear.

3. Of the two skills I've built so far, it seems like you have to be very prescriptive about what requests to expect from the user or Alexa would not know how to respond. I'm curious and interested to learn more about how Alexa learns and improves itself as an AI.
