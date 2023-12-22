# CaseScript 1.0.1 Documentation

If you're wanting to write custom cases to solve here's what you're gonna want to know.

CaseScript is an Interperated Programming Language written by yours truly, I am in the process of polishing up the syntax for most of this. It is subject to change.

This should cover the custom programming language,
the folder setup, essential files for your case to run, and any bugs that may occur and how to fix them.

---------
# Contents
[Folders](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#contents)

[Vital Files](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#folders)

[Evidence Files](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#vital-files)

[Scripts](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#evidence-files)

[Custom Screens](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#custom-screens)

# [Script Tags ](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#script-tags)
[[Dialogue]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#script-tags)

[[Break]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#dialogue--dialogue-)

[[Space], [BigSpace]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#break-)

[[InsertName]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#space--bigspace-)

[[AddEvidence]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#insertname-)

[[WaitForInput]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#addevidence-)

[[Open]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#waitforinput-)

[[SystemSay]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#open-)

[[ImportantSay]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#systemsay-)

[[PlayAudio]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#playaudio-)

[[LoadScreen]](https://github.com/MrCryptoFantom/ColdCases/blob/main/CaseScript.md#loadscreen-)

------------------------
Folders
-----------------------------------------
Your case folder should reside in C:\ColdCases\Resources\Missions
You should have your Case's Root Folder, a folder for your suspects, witnesses, and scripts.

The Main Case Folder:

The folder with all your contents should contain 4 sub-folders inside it and an info file.
You'll need a folder named "witnesses", "suspects", "evidence", and "scripts". You'll also need an "info.txt" file.
You can read more about that below. These items are 100% vital for the game to read your case file, If anything 
in here is done incorrectly your case will not appear in the mission browser and could cause game-breaking issues.

-----------------------------------------
Vital Files
-----------------------------------------
The info.txt file:

It should follow this format exactly:

```
Case File Name
Author Name
Case File Description, you can leave this blank if you want to
The amount of reputation the player needs to play your case file, this should be a whole number such as 10 or 5. Decimals won't work. (This feature is not yet implemented but your case may not be read correctly with this field being null)
```
-----------------------------------------
Evidence Files
-----------------------------------------
You can store pieces of evidence in individual files, the evidence can be anything you want it to be, DNA records, Phone Records, Weapons and their characteristics,
Coroner reports, anything! You'll need attributes inside the file, they should be at the very top, first line, of the file.
you should type either "true" or "false". 

We use those attributes to tell the game whether you have access to this evidence or not. "true" for available, "false" for unavailable. You can unlock these for
the player with an ```[AddEvidence]``` tag followed by the name of your evidence file.

You also need to use the same tags as your scripts use, Anything you want the game to display should be in ``[Dialogue]`` tags. You can also use ``[Break]``, ``[Space]``,
and ``[BigSpace]`` tags in your file. The file extension should be ``.evidence``.

An evidence file should look like this:

```
false
[Dialogue]
 911 Transcript:
 "Hello! I need Help!!!"
[/Dialogue]
```

You could also give or take rep to and from the player through the evidence file using the ``[Rep+]`` and ``[Rep-]`` tags to increase and decrease the user's Reputation. 
Same goes for Sanity as well, use the ``[Sanity+]`` and ``[Sanity-]`` tags to increase and decrease the user's sanity

-----------------------------------------
Custom Screens
-----------------------------------------
You can create custom screens that you can load through code!
The screen should be in a text document openable with notepad, visual studio, etc.

To create a screen you can use the Editor, or create one manually. Every Case File you create in the Editor will generate an example 
screen that you can follow. 

It's a simple text file with the ".screen" extension. 

If you're on windows and can't see your file extensions in your File Explorer, go to the "View" yab at the top of your file explorer,
and click the box that says "File name extensions". Now you can edit your files' extensions manually.

Your screens dimensions should be 119x30 characters. 

You can check the amount of characters by opening this file in a text editor such as VS Code, and highlighting all the characters. 
It will give you the amount of characters you have highlighted in the bottom right corner.


-----------------------------------------
Scripts
-----------------------------------------
ColdCases uses a custom Programming language written by yours truly.
While I've made this as user friendly as possible, there's still some syntax that takes getting used to. This should be used as your guide until you get
comfortable with the language. There should be everything you need to learn in here, so if you run into a problem or a bug, the solution is probably in here.
It can be a bit weird at times but I'm still working out the bugs, glitches and bugs occur often right now so here's what you need to know.

Your script names should be as follows:

Introduction script aka the script that's launched when the case file is run: main.script

Interaction scripts: These should be named ``interaction_`` + ``interaction number aka 1`` + ``_interaction option aka _a``, so if it's your first interaction, and you want this script to run when the player chooses option a, your script should 
be named, ``interaction_1_a.script``. This is so each decision can directly affect the way your case is played out.

I would also recommend using spaces in place of TABs, this is just because of the way the script reader reads the scripts. You don't have to, but your spacing in game
may be a little wacky.

This section is gonna be a bit long so sorry about that! I'll try my best to organize it in a way that's easy to read and understand!

As a good rule of thumb to keep in mind, when you're dealing with opening, editing, or saving files, is to separate your tag with an "AT(@)" sign. When you're working with any sort of one line text command, separate your tag and the text with a colon (:).

-----------------------------------------
# Script Tags
-----------------------------------------



[Dialogue] & [/Dialogue] :
-------------------

Wrap any Dialogue you want "spoken" inside these two tags.

Example:

    [Dialogue]
     Hello World!!!
    [/Dialogue]

-----------------------
[Break] :
--------------
Insert the Break tag in your code for a one second pause. This can be used to have pauses in between blocks of Dialogue.
You can "stack" them on top of each other to create longer pauses. It is basically pausing the script reader on that tag for 1 second.

Such as:

``[Break]``

``[Break]``

``[Break]``


for a three second pause, and so on.

------------------------
[Space] & [BigSpace] :
---------------------
Insert the Space tag for a one line space in the game console. Insert the BigSpace tag for a two line space in the game console.

------------------------
[InsertName] :
--------------
You can reference the player's name by using this tag. It should be put in between two pairs of Dialogue tags, i.e:

    [Dialogue]
     Speaker1 : "How's it goin', 
    [/Dialogue]
    [InsertName]
    [Dialogue]
    ? Anything interesting going on?"
    [/Dialogue]
    
You will have to leave a space in your first pair of tags as the reader won't insert one before the name but it does afterwards.

So the name would appear as :

  ``TextBobText``

Without the space in the first line of Dialogue.

------------------------
[AddEvidence] :
--------------
This is used to activate an evidence file so that the player has access to it. I'll admit, it's syntax is a little weird but you should get used to it.

Example Script:

    [AddEvidence]@evidenceName

    or

    [AddEvidence]@evidenceName.evidence
    
You can write it with the file extension(which is .evidence), or you can just type the name. It'll work wither way.

------------------------
[WaitForInput] :
--------------
Use this to wait for the player to hit "ENTER" to continue with the program, This can also be used to keep the window opened.

------------------------
[Open] : 
--------------
You can use the Open tag to open a .script file or a .evidence file. If you're opening a script file, it must be in the scripts folder, interactions scripts don't work.

The syntax is a little weird but you should get used to it. It goes: [Open] Tag + @ + file name + : + file type. i.e. :

    [Open]@main:script

to open the main script file

or

    [Open]@911_Call:evidence

Your evidence file should be in the evidence folder. If it's not, the reader won't find the file and throw an error.

------------------------
[SystemSay] :
--------------
The SystemSay tag is used to stress a certain sentence by changing the text color to Cyan. This can be used for important notes such as when the player
unlocks a piece of evidence, the narrator is speaking, some sort of alert, anything you want to use it as really. 

It's syntax in not that complicated :

 [SystemSay]:Hello World!!!

As you can see, it's simply the Tag itself followed by a colon, that is then followed by your text. See, simple!

------------------------
[ImportantSay] :
--------------
The ImportantSay tag is very similar to SystemSay. It has the same syntax and works the same way as well.
When you use this tag it tells the script reader that the text is important and should be display as such. It uses custom colors that you can set in your settings.txt file.

Settings File Location: C:\ColdCases\Resources\BaseGame\settings.txt  There's also a JPEG in the same folder with all the colors and their corresponding numbers.

The syntax is as follows:

[ImportantSay]:Hello World!!!

------------------------
[PlayAudio] Tag:
--------------
The PlayAudio tag is a new addition in CaseScript 1.1.0. As you might suspect, this tag allows you to play any .wav
audio file though the console. This could be music, or sound effects. Just drag your audio file into the audio folder in your
Case File.

The syntax is as follows:
```
[PlayAudio]@gunshot.wav
```

------------------------
[LoadScreen] Tag:
--------------
The LoadScreen tag is a new addition in CaseScript 1.0.1. This tag is used to load custom screens (See "CustomScreens" above for more info).

As long as your custom screen is in your case file's "screens" folder, it will load the screen. Use this with caution as it may glitch the current dialogue in the console. I recommend waiting to use this function until I've worked out the kinks. But, don't be afraid to experiment
with it either! :)

The syntax is as follows:
```
[LoadScreen]@customScreen.screen
```
Accepted Arguments: 

SYSTEM: Access a screen or file that is in the system(Universal) files.

Example: 
```
[LoadScreen]SYSTEM@case_os.screen
```
