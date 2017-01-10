# theoutcome-content

This repository contains core content for the game:
- GameFiles wraped in 'packages'
- scenario files (save files)


### Quick guide
____
*This guide uses some seemingly generic terms for certain items. This is mainly due to poor naming on the [@artrist](https://github.com/artrist)'s part, some of the terms are a remnant of the project's very beginning; despite that it kinda really makes a lot of things easier to understand, or even self-explanatory, which is one of the main goals with this project. If you're new take a moment to get familiar with the basic terms and mechanics.*
____

## What are Packages?
Package is a collection of GameFiles. Organizing the GameFiles into packages makes managing game content easier for everyone, for obvious reasons, most notably it's about the improved readability and less confusion. It also makes writing new content more straightforward because of clear rules for dependencies.

### What is a GameFile?
GameFile is a collection of GameElements (see GameElement). GameFiles are written in OutcomeScript (see OutcomeScript), each GameFile needs a declaration of Packages it will depend on (Packages it will invoke).

### What is a GameElement?
Most generally speaking, GameElement is a set of rules used for the runtime simulation. 

## What are Scenario Files/Save Files?
You can think of them as of saved game states. Variables declared as 'savable' in the GameFiles will be stored inside these files. **Modifying the game by importing Packages into the game directory or directly modifying the GameFiles will result in the change of checksum and different requirements for Save Files (different variables need to be saved).** In the event of trying to use Save File which is not-fully-compatible with the current state of the game configuration (game files configuration) it will notify the player about the inconsistencies:
- [TODO?] check the packages against the files stored online, display possible inconsistencies
- [TODO?] show a list of **lacking packages** declared on creation of the Save File, if any
- [TODO?] show a list of **added packages** not present on creation of the Save file, if any
- in case of inconsistencies allow the player to make a copy of the Save File and proceed with conversion 

**Checking for inconsistancies** involves preparation of a 'checksum'. The program will go through all the Packages and check the GameFiles to generate a unique file. This file will be stored inside the Save File as evidence regarding the game configuration used when it was created.

**Conversion** means a Save File will be conformed to the current game configuration's needs for savable data: new variables will be added if required (using default values defined in GameFile, see GameFile), unused variables will be discarded, checksum will be overwritten.


