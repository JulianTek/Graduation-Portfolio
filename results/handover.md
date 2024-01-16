# Handover

This document is to be used as a reference for whoever is continuing any of the projects

## Initial prototype

### Localization

The initial prototype uses Google Sheets Localization. I didn't get to work on localization, since I moved on to the other prototype. You will have to request access to the spreadsheet through Arien or Mieke.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

These are the spreadsheets where the localized text is present.&#x20;

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

This is what an entry looks like in the database. The key is put in the inspector and the application will use the spreadsheet to find the right text.

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

You can add a language by just adding a row in the spreadsheet.

Be sure to press the sync button in your localization sync object!

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

If you create a new sheet, you'll have to add it under the "sheets" list here, too. The ID can be found in the URL.

Currently, the game supports English and Dutch.

### Would you rather?

In order to add new statements to the Would You Rather quiz, you will have to go to the WouldYouRatherHandler.cs script, which can be found in Scripts/Minigames/Would You Rather

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Like the code comment describes, the indecies of the right and left option must match. The first string in the constructor describes what is visible in the game, whereas the second one is what appears in the summary at the end of the game

I kept in mind the following things when creating the statements:

* No clear better option. I tried to keep the statements as neutral as possible, with both options having good arguments as to why they'd be valid
* All influence the world at its core. These statements are not stuff like "Everyone likes pineapple pizza vs. pineapple pizza is banned from everywhere" because these statements should be about how the world is run and works.

### Hard/Soft quiz

This part should be removed, like I said in [Broken link](broken-reference "mention").

### Ideal world creator

In order to add more words, you can copy one of the existing GameObjects that are children of --WORDS--. Change the TextMeshPro to the word you want to add, then navigate to the "Ideal world creator" object, go to the "Floating Words Handler" and add your new object to the "Ideal world adjectives" list

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

And that's it! It's really that simple to add words

## Wrestling Game

### Disclaimer

The following asset packs are used in the wrestling game

* POLYGON City Characters by Synty Studios
* POLYGON Gang Warfare by Synty Studios
* POLYGON Office by Synty Studios
* POLYGON Pirates by Synty Studios
* POLYGON Shops by Synty Studios
* NodeCanvas by Paradox Notion

If you wish to continue this project, you must make sure TweeKracht has _legal_ access to these assets

### The dialogue tree

#### Dialogue

In order to write dialogue, and have the name appear on the dialogue box, you will need to provide characters with the "dialogue actor" class



<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

All that is important is the name. However, you can totally add portraits by adding them in the portrait field

These actors will have to be added to your dialogue tree

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

This can be found in the "Dialogue Tree Controller." You give it a name and then drag in the object.

#### The dialogue tree

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

This is the dialogue tree, a visual scripting tool. You can just drag out a line from one node for another

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

To make a character say something, select the "Say" option. This will pop up the following menu

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Name, comments, tag, audio file and metadata have been ignored in my project.

"SELF" is where you select the actor for the specific line of dialogue, and "This is a dialogue text is where your line will show up.

### Controlling cutscenes

In [implementing-the-story-flow.md](../implementation-phase-wrestling-game/implementing-the-story-flow.md "mention") I described how to utilise the code I wrote to control the cutscene. You can access this, and other methods like camera fades, by using the "Task action" setting

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Selecting that will pop up the following menu

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

"Assign action task" will allow you to select what method you want to run.

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

If you want to use one of the cutscene functions I wrote, you will have to use the "Execute Function" action. Other functions, like camera fades, waiting or loading scenes, can be done without this middleman.

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

From here you can access any method you want, including the cutscene methods.

### Blackboard variables

A dialogue tree can have variables, too. These are on the "blackboard"

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

The DialogueTreeManager Blackboard Variables are variables on this object, with Graph blackboard variables being set to this specific graph, which is loaded ON the DialogueTreeManager.

If you ever need to access one during a function call

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

You select the circle next to the object![](<../.gitbook/assets/image (22).png>)

And here you can select one.

### Using animations

I used Mixamo to find animations, and [this](https://www.youtube.com/watch?v=9H0aJhKSlEQ) video on how to use these animations on the Synty Studio characters
