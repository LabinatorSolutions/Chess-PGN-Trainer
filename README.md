# Chess PGN Trainer
Online tool that opens chess PGN files and allows the user to practice the moves.  This tool is to help with drilling, ***as efficiently as possible***, a set group of puzzles/games in an appropriately configured PGN file. Once the set is complete, the player sees how many errors they made as well as how long the set took to complete.

The original design goal was to help with implementing a learning approach where a player repeatedly completes the same series of puzzles, striving to reduce both errors and time needed with each round.
The idea for this came from a recommendation by Dan Heisman (https://www.danheisman.com/recommended-books.html) on how to practice tactics puzzles.  In the article, Dan strongly recommends the idea of "repeatedly going through the book faster and faster until you can get 85%+ within 10-15 seconds". You can read about my own results following this approach using this tool [here](https://www.chess.com/forum/view/for-beginners/applying-dan-heismans-guide-to-using-chess-tactics-for-students).

Since then, the tool has grown and can now be used to:
* Practice puzzles
* Practice openings for black or white
* Practice entire games (useful for learning full games or for playing solitaire chess such as "Guess the Move")

See the sample PGN files in the /examples folder for more information.  The samples include puzzles, openings for both white and black, as well as some famous games to practice.  Also included is a PGN of a slighly modified [Aman Hambleton's reset mate](https://www.youtube.com/watch?v=XAlcDWQ6iTM) for those who want to practice that sequence along with the same sequence mirrored for black pieces.

[A live online copy of tool is available here](https://rodpolako.github.io/)

![screenshot](screenshot.png)

PGN Files need only three parts:
* FEN - The representation of the board and associated information. Only needed to set up the board in a specific position.  If practicing games/openings this is not required.
* The moves for both white and black.
* (Optional) the "Event" tag so that the puzzle has a label that shows below the progress bar.

Here is an example PGN created using the analysis board from [chess.com](https://www.chess.com) with a really basic endgame that was just saved to a file.
```
[Event "Example 1"]
[Site "?"]
[Date "????.??.??"]
[Round "?"]
[White "?"]
[Black "?"]
[Result "1-0"]
[SetUp "1"]
[FEN "7k/8/8/3Q1K2/8/8/8/8 w - - 0 1"]

1. Kf6 Kh7 2. Qf7+ Kh8 3. Qg7# 1-0
```
The same puzzle created in [Lichess](https://lichess.org) via the analysis board generates the following file and also works with this tool. 

**Note:** there is no "Event" tag generated so you would need to add this tag if you want to label the puzzle.  Otherwise it works the same.
```
[Variant "From Position"]
[FEN "7k/8/8/3Q1K2/8/8/8/8 w - - 0 1"]

1. Kf6 Kh7 2. Qf7+ Kh8 3. Qg7#
```

Use the "Open PGN file" button to open this file and you can practice this puzzle.  

The PGN file can have any number of puzzles or games so you can work through a set in one shot.

## Features
This tool has a number of features that you might find useful:
* Auto move to next puzzle - Automatically advances to the next puzzle/game upon completion of the current one
* Play both sides - Allows the player to play both sides of the puzzle/game
* Randomize - Presents the puzzles/games in the set in a random order
* Flipped - Allows you to play the puzzle/game from the other side of the board.  May help to develop sense when a given tactic is being used on you.
* Play Opposite Side - Allows the player to go second instead and makes the computer play the first move from the PGN.  Useful for when you want to practice opening defenses instead of puzzles.  For example, if you wanted to practice a defense as black, load a PGN with the move order you want to practice and this feature will play as white and play the moves in the PGN while you play the response.  Recommended that you use the Flipped option in conjunction with this one.
* Analysis board - More useful for puzzles, this option generates a link to a Lichess analysis board of the currently displayed puzzle as per the PGN. Useful when you want to analyze a specific puzzle during a run in order to analyze or troubleshoot.  This will place a link below the title of the puzzle which if clicked will open an analysis board in Lichess with the position in a new tab.
* Pause - Useful if you are doing a large number of puzzles/games and need to step away.  Click on the pause button and the board will clear and the timer will stop.  Click Resume in order to continue.  Your elapsed time will not include the paused time.
* Hints - You can press the hint button at any time during a puzzle/game to see the next expected move.  Just know that if a hint is used, it will be counted as an error in your performance.
* Restart/replay - You can repeat the current puzzle/game set upon completion with a single click. Useful if you want to try again with the same settings.  When the current set is complete, just click on "Restart" to try the current PGN file again.  If you want, you can choose different settings like random, flipped, etc. before restarting.
* Feature settings via PGN Tags - You can configure a PGN to set a default combination of features by adding the relevant tag to the top of the PGN.  Details below.
* Responsive design allows the app to be used in either portrait or landscape mode which means that it is able to be used on phones and tablets along with desktop.
* A settings menu which gives the following options:
  
   * Choice of multiple piece designs - Note this will reset the board so don't change sets while in the middle of puzzle set.
   * Ability to specify custom board colors either by manual entry or color picking 
   * Dark mode
  
* Ability to copy results to clipboard ready to paste into a spreadsheet. 
* Ability to export results to CSV file along with setting to include the headers
* Ability to add additional piece sets (either PNG for SVG) for hosted instances only.  Not available on github.io page.

Once a test group is completed, tool displays the following performance information:
* Number of errors
* Time to completion
* Average time per puzzle/game (Calculated)
* Error rate (Calculated)

![screenshot](screenshot2.png)

## Download to CSV
Upon completion of a set you will have the option to download a CSV file of your performance via the "Download to CSV" button on the results screen.  This file can then be opened up in spreadsheet programs like Excel or Google Sheets and can function as a way to keep track of your progress.  By default, the CSV file will include all the header information so you know what each column contains.  You can disable the headers for subsequent entries via the settings menu.  

The CSV file contains the following columns:
| Column Name   | Description   |
|:-------------|:-------------|
| date | The date the run was completed | 
| filename | The filename of the PGN | 
| round | The round for this file (see note below) | 
| series | The value of the first event tag in the PGN | 
| mode | Indicates if the puzzles this set were completed in random or sequential order | 
| setlength | The total number of puzzles in this set | 
| errors | The number of errors on this set | 
| totaltime | The total time spent on this set | 
| avgtime | The average time spent per puzzle | 
| errorrate | The average error rate | 

Note: The round value is the only field that will require manual entry after pasting. The idea is that you would manually increase the number for each row for a specific PGN file.  For example, if a given PGN is run for the first time, you would set the round value to 1.  On the next run of the same PGN, you would paste the second results below the first set and you would record 2 for the round.  In this way, you would be able to track your progress for a given PGN file over time.

## Copy results to clipboard
By default, when you complete a set your performance is automatically copied to the clipboard which is useful for pasting into a new row of a spreadsheet containing your prior results.  It is recommended you download the CSV on your first run through and then open in Excel or Google Sheets.  With the spreadsheet open, you can then simply paste your results to a new line.  If needed, you can always re-copy your performace back to the clipboard by clicking on the "Copy results to clipboard" button on the results screen.

You can disable the automatic copying of the data to the clipboard via the settings menu.

## Custom piece sets
If you are hosting this application on your own server, you can add additional piece sets by following the instructions in the piece-list.js file. 

## Custom board color
You can specify the exact color you would like for both the light and dark squares via the settings menu. Clicking on either value will display a color picker which you can use to select your color.  Clicking anywhere else will close the color picker.  If you have a specific RGB value in mind, you can simply type or paste it in instead.  

![screenshot](screenshot3.png)


## Default settings via PGN Tags
You can set the default options via custom tags in the PGN.  For example, if you have a set of puzzles/games that you always want to be in random order, you can add a tag to the top of the PGN and it will automatically check the Randomize box when the file is loaded.
Here is the example PGN with the randomize setting turned on.
```
[PGNTrainerRandomize "1"]
[Event "Example 1"]
[Site "?"]
[Date "????.??.??"]
[Round "?"]
[White "?"]
[Black "?"]
[Result "1-0"]
[SetUp "1"]
[FEN "7k/8/8/3Q1K2/8/8/8/8 w - - 0 1"]

1. Kf6 Kh7 2. Qf7+ Kh8 3. Qg7# 1-0
```
Or another use case could be that you want to practice defenses as black and you have a PGN that has the move sequences you want to practice.  Ideally you would want to use the "flipped" and "play opposite side" options every time so that you see the board from black's perspective and the computer makes the opening move.  You can set that with the ```[PGNTrainerFlipped "1"]``` and ```[PGNTrainerOppositeSide "1"]``` tags in the PGN and every time you load that PGN going forward, those options will automatically be selected.  You can always de-select a setting if you want something different for a particular run.

The available tags are:
* ```[PGNTrainerBothSides "1"]``` - This will check the "Play both sides" option
* ```[PGNTrainerOppositeSide "1"]``` - This will check the "Play opposite side" option
* ```[PGNTrainerRandomize "1"]``` - This will check the "Randomize" option
* ```[PGNTrainerFlipped "1"]``` - This will check the "Flipped" option
* ```[PGNTrainerAnalysisLink "1"]``` - This will check the "Analysis board" option

The value of the tag has to be 1 in order to activate.  Any other value or omission of the tag entirely will be ignored.

You can use any combination of the above tags.  Just insert the desired tag(s) at the top of the PGN.  

**Note** The only exception is selecting both "Play both sides" and "Play opposite side" at the same time (which is nonsensical). Any PGN file setting both of these options via the custom tags will have them both ignored. In this situation, update your PGN to remove one of these tags in order to set "Play both sides" **OR** "Play opposite side".

## Known limitations
* The PGN parser ignores variations in a PGN file.  Attempting to use a PGN with these will not work and will only play the "main-line".  If you want to work a line that has variations, break out each variation into its own entry in the PGN.

For example, the following PGN shows a position where the black king has two possible moves recorded after Qe5+:
```
[Event "?"]
[FEN "r1r1k3/5p2/3K4/2Q5/8/8/8/8 w - - 1 1"]

1. Qe5+ Kf8 (1... Kd8 2. Qe7#) 2. Qh8# 1-0
```
Loading this PGN as-is will result in the tool indicating that there is only 1 puzzle, the main line. To get the tool to test the main line and the variation, copy the entry and show each variation separately.  Like this:

```
[Event "?"]
[FEN "r1r1k3/5p2/3K4/2Q5/8/8/8/8 w - - 1 1"]

1. Qe5+ Kf8 2. Qh8# 1-0

[Event "?"]
[FEN "r1r1k3/5p2/3K4/2Q5/8/8/8/8 w - - 1 1"]

1. Qe5+ Kd8 2. Qe7# 1-0
```
In this way, the tool will see that there are two puzzles and test both.

Note: There is an excellent freeware tool called [PGN Extract](https://www.cs.kent.ac.uk/people/staff/djb/pgn-extract/) that can take a file with variants and split each variant into a separate game suitable for this app.  Here is example usage of this tool to take **input.pgn** which has variants and save it to a new file called **output.pgn** with the variants saved as separate games:
```
pgn-extract input.pgn --output output.pgn --splitvariants
```
## Non-standard PGNs
Some PGNs contain data that the parser does not handle well.  Examples include embedded commands (such as {[%evp]}).  If you are having difficulty opening a file, remove non-essential components and try again.  

## Error loading PGN file
If you have an issue opening a specific PGN file the app will display a pop up and indicate the issue that the parser has found.  It will also show you how many games/puzzles were successfully loaded prior to the error.  For example, if the app tells you that 5 puzzles/games were loaded successfully, then the issue is with the sixth puzzle/game in the PGN.  Use the error message to help guide you on fixing the issue with the sixth puzzle/game and then try loading it again.

## Setup Instructions
If you just want to use the trainer and and not bother hosting the page yourself, you can just use the live link [here](https://rodpolako.github.io/).  The latest version of the trainer will always be hosted there.

If you want to host a copy on your own environment and/or make changes:
1. Download & extract the zip into a folder and start a web server from there.
2. In a browser, point to ```index.html```.  On my own setup, the URL is ```localhost:8000/index.html``` but may be different for your setup.  Refer to your web server for details.

## Usage
1. Click on "Open PGN File"
2. Navigate to the desired PGN file and then click on OK
3. Place a checkmark next to any desired features (such as random, flipped, play both sides)
4. When ready, click on start and the first puzzle in the set will be displayed and you can make your first move.
5. When the puzzle/game is finished, the next puzzle/game in the set will be automatically loaded
6. When the set of puzzles/games is complete, your final stats will be displayed.
7. You can pause any time if you need to step away.
8. If you get stuck you can get a hint by clicking the hint button.

You can then start a new PGN file by repeating these steps.

## References
Built with the help of the following projects:
* [chess.js](https://github.com/jhlywa/chess.js) chess.js is a TypeScript chess library used for chess move generation/validation, piece placement/movement, and check/checkmate/stalemate detection - basically everything but the AI.
* [pgn-parser](https://github.com/mliebelt/pgn-parser): Javascript library to allow reading of a PGN (Portable Game Notation) chess game notation, and providing the result as JSON.
* [chessboardjs](https://github.com/oakmac/chessboardjs/) chessboard.js is a standalone JavaScript Chess Board. It is designed to be "just a board" and expose a powerful API so that it can be used in different ways.
* [pawn-promotion](https://github.com/siansell/pawn-promotion) Quick and dirty example showing one approach to pawn promotion with chessboard.js and chess.js.
* [lichess-org/lila](https://github.com/lichess-org/lila/tree/master) Lila (li[chess in sca]la) is a free online chess game server focused on realtime gameplay and ease of use.
* [jquery-wheelcolorpicker](https://github.com/fujaru/jquery-wheelcolorpicker/tree/master) A jQuery plugin to add color picker functionality to HTML form inputs in round color wheel style.


## Possible ideas for improvements/features/roadmap

### Visual/UI ###
* I'm looking at possibly incorporating the next major release of chessboardjs which may be better suited for use on mobile since it allows things like tapping instead of just dragging pieces.  
* Possibly adding support for more PGN tags.
* Reporting capabilities such as graphs/charts replicating what I'm currently doing in Excel.
* Sound effects when moving the pieces, capturing, etc.
* Annotation support

### Functionality ###
* User data storage to save progress and allow for resuming progress through a set if the browser is closed.
* Add a way to organize all the PGNs I want to test as part of a larger structure so that I would be able to choose from a defined list which includes the info on the PGN file to use along with the desired settings.
* Connected with the point above, maybe introduce some sort of spaced reptition capability or have the tool automatically drill you from the list based on when last drilled or performance.
* Adding text-to-speech so the app can announce moves and maybe speech recognition in order to play moves.  Not sure about this one yet.
* Fork the PGN-Parser and extend it to also read variations and load each variation as another puzzle and resolve other bugs.  Alternatively, write my own parser.

