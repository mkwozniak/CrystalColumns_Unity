# CrystalColumns_Unity
Crystal Columns is an open source 2D tetris style game built in Unity. It uses as much standard C# code as possible to avoid dependency on the Unity physics system.
This means you can translate this game code to nearly any language with a graphics library. (I will be releasing a less feature intense Python version of this later)


# The Game
Crystal Columns is a 2D puzzle game in which you must align 4 gem stones of the same type in a row. The game begins with a set amount of random gems dropped through each column. The player then has a queue of randomly prepared gems they must aim and shoot. If the board gets filled with gems all the way, it's game over. 
It's basically Puzzle Bobble : Bust-A-Move mixed with Tetris.

You can play the web build at:
https://wozware.net/crystalcolumns


# The Source Code
Crystal Columns is written with the goal of efficiency combined with generic behavior. Crystal Columns utilizes simple yet powerful structures and features in C# such as Events, Queues and Dictionaries to perform its game logic. It avoids using any dependencies for physics and behavior. The game could have been written in much less code with Unity Raycasts and Rigidbodies, but it would be much harder to translate to other languages where there is no native physics system.
In almost all its entirety, the game code can be translated to any language with a graphics library. Although Events

All source code is cleanly commented, separated and summarized.


# How its structured
The game stores each Cell and its position in a Dictionary. Each column is then subsequently put into its own Dictionary based on X Position. When a Gem is launched it only checks if its bounding box is colliding with a cell in its own column.
Each Cell has positions referring to its neighbors, and whenever a cell is filled with a new gem, it performs a simple recursive flood fill algorithm with a Queue to detect a chain of 4 identical gems. If a chain is found, each gem in the chain recursively finds any gems of the same type that are "touching" the chain; then the chain explodes.

Each column is then called upon to settle any floating gems. Settling cells is done recursively as well, from the bottom up.
After settling, the same process of recursive chain checking + settling is performed until no valid chains of identical gems were found in that configuration.
The game avoids iterating through or processing needless information when it can, but there's always improvements that can be made!


# Possible Major Improvements
Pooling! Each Gem is created/destroyed rather than pooled, which is meh. Considering the amount of Gems in play at any given time is fairly low, I don't think it's needed right now.


# How to edit the Unity Project

Using the .unitypackage
1. Download wozware-crystalcolumns.unitypackage from this page.
2. Create a new Unity Project (2018+ recommended)
3. Install / Import the Unity Package

Alternatively, you may download the full source code, create a project, then manually drag and drop all the source code and assets.



