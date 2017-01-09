# theoutcome-content

This repository contains core content for the game:
- GameFiles wraped in 'packages'
- scenario files (save files)


## What are Packages?
Package is a collection of GameFiles. Organizing the GameFiles into packages makes managing game content easier for everyone, for obvious reasons, that is improved readability and less confusion. It also makes writing new content more straightforward because of clear rules for dependencies.

## What are Scenario Files/Save Files?
You can think of them as of saved game states. Variables declared as 'savable' in the GameFiles will be stored inside these files. **Modifying the game by importing Packages into the game directory or directly modifying the GameFiles will result in the change of checksum and different requirements for Save Files (different variables need to be saved).** In the event of trying to use Save File which is not-fully-compatible with the current state of the game configuration (game files configuration) it will notify the player about the inconsistencies:
- show a list of **lacking packages** declared on creation of the Save File, if any
- show a list of **added packages** not present on creation of the Save file, if any
- in case of inconsistencies allow the player to make a copy of the Save File and proceed with conversion 

Checking for inconsistancies involves preparation of a 'checksum'. The program will go through all the Packages and check the GameFiles to generate a unique file. This file will be stored inside the Save File as evidence regarding the game configuration used when it was created.

