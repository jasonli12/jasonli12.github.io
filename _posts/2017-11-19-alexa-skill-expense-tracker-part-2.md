---
layout: post
title: Alexa Skill - Expense Tracker (Part 2)
---

In my last post, I talked about the interaction model of the Alexa skill I'm building. Within the interaction model, I defined what superpowers or 'intents' that my Alexa skill will have, what information I am collecting from the user as well as what are some phrases or utterances that a user might say to invoke an intent.

In this post, I'll go through my experience coding the actual implementation of the skill.

My first intent is called the 'AddNewExpenseIntent' and the purpose of the intent is to prompt the user for the following pieces of information, also known as slots, and then store them in a database so that the user can later ask Alexa about historical expense information:

1.Date of purchase or expense

2.Description of expense

3.Cost of expense

***Dialog Interface***

Alexa has a new feature called the *Dialog Interface* that essentially allows you to delegate to Alexa to continue prompting the user to collect all the required information. Naturally then I would need to define what the prompts would be to collect that information.

For example, let's say I tell Alexa: "Alexa, tell Expense Tracker to add an expense for hamburgers."

Alexa would recognize that Expense Tracker is the name of the skill and add an expense for hamburgers maps to the 'AddNewExpenseIntent'. In addition, it would also understand that I've already provided one of the slots. The description of the expense is 'hamburgers.'

Alexa would then prompt the user for the date of purchase and the cost.
For example, the dialog may continue as follows:

Alexa: What is the date of the expense?
Me: Today
Alexa: How much did you pay for it?
Me: 5 dollars and 99 cents
Alexa: Ok, on November 19, 2017, you paid 5 dollars and 99 cents for hamburgers. Is that correct?
Me: Yes
Alexa: Great! I've added the expense.

***Persisting Data to DyanmoDB***

Notice that after retrieving all the necessary information, I asked the user for confirmation. There is a property called `confirmationStatus` that will be set to the value `CONFIRMED` when the user confirms the expense. Upon this condition being true, I will store the expense information in DyanmoDB.

The most difficult part of this process is not figuring out the code, but how to set up your table and what your primary key(s) are for querying the database.

Initially I used the `timestamp` property to be the unique identifier, but because DynamoDB is a noSQL database, `timestamp` is not a meaningful value to search by. Then, I tried using the Alexa `userId` but found that entries were overwritten when the same user tries to add a second expense. Ultimately, I settled on a setup where the `userId` is the primary key and the `timestamp` is the secondary key. This setup allows for users to only access their expenses and not have expenses overwrite each other.

***Reading Data from DynamoDB***

What use is add expenses to the database if you can't retrieve the information? The next intent I built was to read expenses by expense date.

Again, similar to writing to the database, retrieving information was not difficult. I used the Alexa `userId` as the key.

However, when Alexa read me what I spent on a certain date, none of the expenses got read out. I checked what I logged out on the console and it appears that I am successfully querying from the database. What I ultimately discovered was at work is NodeJS' asynchronous feature. Alexa was reading the prompt back to me before the query was done and passed to the prompt. And the solution I used was a callback. This way I ensure that the querying is done and formatted correctly when Alexa responds.

***Final Thoughts***

Building with *Alexa* is fun! The first time writing out all the code yourself, defining intents and sample utterances and understanding the relationships between all the pieces can seem overwhelming. I was spinning my wheels for a long time before making any progress. For the basics, I recommend this new course just launched on Codecademy that Amazon partnered with. It is very helpful for learning the different pieces of the puzzle. Afterwards, I found myself looking at how different people implemented different pieces of Alexa. I would look for 1) How to implement the Dialog Interface 2) What to write to DyanmoDB and 3) How to read from DynamoDB all separately, tackling one feature at a time. The Alexa Cookbook on Github is another extremely helpful guide with tons of examples. Another tool that's a *must* is using the Cloudwatch logs. Everything you log to the console shows up in the logs. I found myself logging out between different states to make sure everything is on track and I am getting the desired output during the development process.

Just remember to have fun! The first time around is always challenging and more difficult, but now I'm just excited to see what new ideas I have for Alexa.
