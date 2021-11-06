# Xmas 2021
This is a tile-sliding gme written in VueJS. The objective of the game is to rearrange the square tiles to assemble the correct picture.

## HTML
For this, we need the following elements.
- A div with id *xmasApp*. This is what VueJS will be referencing.
- A div with id *puzzleContainer*. This will consist of 16 individual divs in a 4 x 4 grid.
  - Styling wil be provided by the *isComplete()* method.
- Each of these divs will hold another div which will have the background image of the puzzle picture, but offset according to their position in the grid.
  - Class will be *pieceContainer*.
- The third div will be blank. Thus it will be styled using the CSS class *blank*.
  - Class will be provided by the *getClass()* method.
  - Style will be provided by the *getStyle()* method.
  - Click event is the *moveTile()* method.

## JavaScript
