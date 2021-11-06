# Xmas 2021
This is a tile-sliding gme written in VueJS. The objective of the game is to rearrange the square tiles to assemble the correct picture.

## HTML
For this, we need the following elements.
- A div with id `xmasApp`. This is what VueJS will be referencing.
  - There is a button that runs the `reset()` method.
- A div with id `puzzleContainer`. This will consist of 16 individual divs in a 4 x 4 grid.
  - Styling wil be provided by the `isComplete()` method.
- Each of these divs will hold another div which will have the background image of the puzzle picture, but offset according to their position in the grid.
  - Class will be `pieceContainer`.
- The third div will be blank. Thus it will be styled using the CSS class `blank`.
  - Class will be provided by the `getClass()` method.
  - Style will be provided by the `getStyle()` method.
  - Click event is the `moveTile()` method.

## JavaScript
Data and configuration are in the `data` object.
- `btnText` is the text that the reset button in `xmasApp` uses. By default it is "RESET", but if the game is completed, it will be "RESTART".
- `pieces` is an array used to hold all the pieces in the image.
- `arrangement` is the array used to keep track of the grid squares and what pieces are in them.
- `blankIndex` is an integer, used to reference `arrangement`, to determne which square is currently the blank one.
- `images` is the total number of images used in this app.
- `imageNo` is an integer used to determine which image is currently being used.

Methods are in the `methods` property.
- `reset()` 
  - resets all data to their default values.
  - selects a random image to be used.
  - randomly scrambles he grid.
- `isComplete()`
  - checks if all the pieces in `arrangement` are in the correct order.
  - returns `true` if so, `false` otherwise. 
- `isClickable()`
  - checks if the square in question is right next to the tile indicated by `blankIndex`.
  - returns `false` by default.
  - if the tile is next to the blank tile, this means that is is possible to switch the position of the current tile with the blank tile. The direction to move would be "n", "s", "e" or "w". This value will be accordingly returned.
- `getStyle()`
  - uses `imageNo` t get the current image.
  - uses the id of the current tile to determine the offset.
  - returns a CSS string that provides both the image and the offset.
- `getClass`
  - uses `isClickable()` to determine cursor appearance.
  - uses the id of the current tile to determine if it is blank.
  - returns a combination of CSS classes.
- `moveTile()`
  - uses `isClickable()` to determine wat directon the tile should move in.
  - using a callback in the `setTimeout()` function, it adjusts the `margin` property of the current piece.
  - the `arrangement` array is updated at the end of the transformation.
