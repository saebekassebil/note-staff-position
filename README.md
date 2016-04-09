# note-staff-position

    $ npm install note-staff-position

Calculate the staff position of a note for a staff with a given clef. 
Use this position number to render the note for sheet music or whatever else you like.

## usage

```js
var parse = require('scientific-notation');
var staffPosition = require('note-staff-position');

staffPosition(parse('C4'), staffPosition.TREBLE_CLEF)   // -> -1
staffPosition(parse('D4'), staffPosition.TREBLE_CLEF)   // -> -0.5
staffPosition(parse('E4'), staffPosition.TREBLE_CLEF)   // -> 0
staffPosition(parse('C5'), staffPosition.TREBLE_CLEF)   // -> 2.5

staffPosition(parse('A2'), staffPosition.BASS_CLEF)     // -> 0.5
staffPosition(parse('D3'), staffPosition.BASS_CLEF)     // -> 2
staffPosition(parse('C4'), staffPosition.BASS_CLEF)     // -> 5

// You can curry the staffPosition function with a clef
var getTreblePos = staffPosition(staffPosition.TREBLE_CLEF);
getTreblePos(parse('C4'))                               // -> -1
getTreblePos(parse('E4'))                               // -> 0

```

### `staffPosition(coord, clefNumber) -> position`

Calculates the position of a [notecoord](https://github.com/saebekassebil/notecoord)
in the given clef.

This module includes the three most common used clefs, but you can use whatever
clef you want:

 * `staffPosition.TREBLE_CLEF` = 31
 * `staffPosition.ALTO_CLEF`= 25
 * `staffPosition.BASS_CLEF`= 19

### `staffPosition(clefNumber) -> fn(coord)`

Given only a clef number, it returns a function calculating the position of a
note given *that* clef.
