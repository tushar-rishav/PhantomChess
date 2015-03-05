# Phantom
Phantom is a (in development) game of Chess written in Python.  It's not very graphical but what it does have at the moment is the ability to pretty-print the board to the screen, ex:
```
  a b c d e f g h
8 r n b q k b n r 8
7 p p p p p p p p 7
6                 6
5                 5
4                 4
3                 3
2 P P P P P P P P 2
1 R N B Q K B N R 1 <
  a b c d e f g h
```
and will use Unicode characters as well.  A proper GUI is underway for the iOS app [Pythonista][].  

Please note: this project is a huge learning experience for me.  This is the 3rd revision (I've restarted from scratch twice) of my ongoing chess project, each one getting better.  Hopefully there is no 4th revision.  If you find a bug, *please* don't hesitate to let me know so I can fix it.

There's a large update on the way - but I'm developing on an iPad in a Pythonista beta build which has expired.  Until the update comes through I cannot access the files to push to GitHub. :(

## Features

- [x] Human vs. human play
- [ ] Checkmate detection  (work-in-progress)
- [x] Static board analysis (always improving)
- [ ] Move search engine (work-in-progress)
- [ ] Descriptive game notation
- [x] Move validation
- [x] En passant
- [x] Pawn promotion
- [x] Pretty printing
- [x] Save/load boards
- [x] Read/write FEN strings
- [x] Read EPD strings
- [ ] Write EPD strings
- [x] Algebraic chess notation
- [ ] Pythonista GUI
- [ ] Windows GUI
- [x] Self-test suite

## Installation
To download & extract PhantomChess, the first thing to do is download the `Phantom_installer.py` file in the master branch.  Place it in the directory to extract to and run.

## Static board analysis
How exactly does Phantom analyze a board and give it a score?  It uses a set of heuristics coded into the Phantom.ai.pos_eval.heuristics file.  This is a list of the currently active heuristics that are used to analyze a board:

- developed pieces
- advanced pawns
- separate scoring method for kings based on opening, midgame, endgame
- does player have the bishop pair
- has the player castled
- analyze pawn structure (work-in-progress)
- assess pawns, knights, bishops, rooks, queens & kings according to the Phantom.ai.pos_eval.piece_tables file
- assess bad bishops

as well as the much simpler material analysis.

### Why no mobility heuristic?
Briefly considering how chess works, one would assume a piece that could make more moves would be more valuable.  And that would be correct, although it wouldn't make the piece as valuable as you might think because most legal moves in any given chess game *are pointless*.  Also, the main reason the function isn't put to use (it does exist in the file) is that it simply takes too long to generate the list of valid moves.

### Score system
Scores are given in "centipawns", such that 100 cp = 1 pawn.  The values used are too many to list here, and can be found in the Phantom.ai.settings file.

[Pythonista]: http://omz-software.com/pythonista