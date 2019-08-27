### The game of Battleship

The game of battleship is a well known tabletop guessing game. You can find the rules of the game here:
[https://en.wikipedia.org/wiki/Battleship_(game)](https://en.wikipedia.org/wiki/Battleship_(game)).

For the purposes of this exercise, let’s consider only one player with a 10x10 grid. On this grid, we can place the following 5 ships, either horizontally or vertically:

- **Carrier**: 5 squares long
- **Battleship**: 4 squares long
- **Cruiser**: 3 squares long
- **Submarine**: 3 squares long
- **Destroyer**: 2 squares long

We would like to have a model of this grid that supports these operations:

- **Setup**: Randomly place all the 5 ships.
- **Shoot**: Bombard a square.
- **Check**: Check if all of the ships have been destroyed. All the squares of every ship have to be bombed in order for the ship to be destroyed.

#### Requirements
Implement an object oriented model of the game, using the programming language of your preference.

Implement the 3 operations.

Write the necessary unit tests for the 3 operations.

#### Deliverables
Just the code and the unit tests, no need for executables or containers.
Do not implement any user interface, only the code is necessary.
