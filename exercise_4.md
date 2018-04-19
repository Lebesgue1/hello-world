## Use Array Methods to Transpose a Piece of Music
In this exercise you will get to use your knowledge of array methods to write a function that transposes a song from a given key into another key.

- For the purposes of this lesson a **scale** is just a collection of 7 notes from the set `{"A", "A#/Bb", "B", "C", "C#/Dd", "D", "D#/Eb", "E", "F", "F#/Gb", "G", "G#/Ab"}` in a specific order. The first note in the collection gives the scale its name. For example, the C scale is the collection `["C", "D", "E", "F", "G", "A", "B"]`, and the G scale is the collection ["G", "A", "B", "C", "D", "E", "F#/Gb"].

- A **song** is just a collection of notes. For example, `["C", "C", "F", "F", "G", "G"]` is a song. 

- The **key** of a song is (loosely) the note that is the focal point of the song and if a song is in a certain key then song made up of only notes from the note's scale.

The song `["C", "C", "F", "F", "G", "G"]` is in the key of C, but we could sing it in any key by transposing it. To transpose a song from one key to another we need to match up each note in the song to its position in the corresponding scale. Then we change the note to the note with the same position in the scale we want to transpose to. 

For example, if we want to transpose the song `["C", "C", "F", "F", "G", "G"]` from the key of C to the key of G we first map each note to its position in the C scale. Doing so we get the array `[1, 1, 4, 4, 5, 5]` since C is the first note in the C scale, F is the fourth note in the C scale and G is the fifth. Next we find the notes in the G scale that correspond to these positions to get `[G, G, C, C, D, D]`. Note that G is the first note in the G scale, C is the fourth note in the G scale and D is the fifth.

### Instructions
___
#### 1. Complete the transpose function using by using at least one array method.
___
#### 2. Great work! Press next to move on to the next lesson.
**Initial Code:**

```javascript
var notes = ["A", "A#/Bb", "B", "C", "C#/Dd", "D", "D#/Eb", "E", "F", "F#/Gb", "G", "G#/Ab"]

//Function to return the notes in a given key
function getKeyNotes(key){
  var steps = [2,2,1,2,2,2,1] //the pattern a major scale follows
  var keyNotes = []
  
  var currentIndex = notes.indexOf(key)
  
  steps.forEach(function(step){
    keyNotes.push(notes[currentIndex]);
    currentIndex += step;
    currentIndex %= 12;
  })
  return keyNotes
}

//Complete this function.
function transpose(song, originalKey, newKey){
  var originalKeyNotes = getKeyNotes(originalKey) //an array containing the notes in the original key, in order
  var newKeyNotes = getKeyNotes(newKey) //an array containing the notes in the new key, in order
  
  return transposedSong.join("")
}
//Test your function against the provided use case
songInC = ["C", "C", "F", "F", "C", "C", "F", "F", "G", "G", "C", "C"]
console.log(transpose(song, "C", "G"))
```

**Completed Code:**

```javascript
var notes = ["A", "A#/Bb", "B", "C", "C#/Dd", "D", "D#/Eb", "E", "F", "F#/Gb", "G", "G#/Ab"]

//Function to return the notes in a given key
function getKeyNotes(key){
  var steps = [2,2,1,2,2,2,1]
  var keyNotes = []
  
  var currentIndex = notes.indexOf(key)
  
  steps.forEach(function(step){
    keyNotes.push(notes[currentIndex]);
    currentIndex += step;
    currentIndex %= 12;
  })
  return keyNotes
}

//Fill in this function.
function transpose(song, originalKey, newKey){
  var originalKeyNotes = getKeyNotes(originalKey)
  var newKeyNotes = getKeyNotes(newKey)
  
  keyMap = {}
  originalKeyNotes.forEach(function(note, index) {
    keyMap[note] = newKeyNotes[index];
  })

  var transposedSong = song.map(function(note) {
    note = keyMap[note];
    return note
  })
  return transposedSong
}

songInC = ["C", "C", "F", "F", "C", "C", "F", "F", "G", "G", "C", "C"]
console.log(transpose(song, "C", "G"))
```