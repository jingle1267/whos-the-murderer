### Solo Project - Guess the murderer!

===================

Built with Python and React

#### 1. User can create an account and login
Initial release use React login? Or consider setting up oauth??
#### 2. User clicks to start a new game
Could have the user choose how many faces to play with
#### 3. User clicks "choose a murderer"
Backend randomly selects a murderer and Google Vision is implemented to analyze that image. The json data provided will be parsed through and saved in state.
#### 4. User is shown a set of faces (with names)
Initial release, users would only be shown 2 or 3 faces. The database will be populated with a set of images, each face clearly shows one of the following:
 - Joy
 - Sorrow
 - Anger
 - Surprise
 - Headwear/Hat
#### 5. User can make guess via text input OR user just clicks on faces to make guesses.
Similar to hangman, already guessed letters are shown, correct letters are displayed on the word.
#### 6. User can click on give me a clue, revealing some text
The Google Vision provides data about each image. Main clues would be related to the 5 main categories that images will be split into - 
 - Joy `The murderer is very joyful and pleased about their actions`
 - Sorrow `The murderer looks very sad about their actions, maybe it was self defense?!`
 - Anger  `The murderer is looks very angry, you'd better watch out!`
 - Surprise `The murderer is very surprised, are you about to catch them?`
 - Headwear/Hat  `The murderer knows your onto them, they are wearing a hat`

These main "clues" would be stored in the database, and depending on the classification of the murderer is each new game the appropriate clue will be fetched fomr the database.
Google Vision also provides other data that could be utilized for more specific clues:
 - `The main color in the murderers profile image is` (With a swatch showing the color)
 - `The murderer appears not to have hair`

#### 7. The user can click on a face to make a guess
If the guess is wrong the face is X-ed out (maybe flips over, or greys out, or a animated X is drawn across). If the guess is correct the face is animated to enlarge/glow or something and user is shown a message. `Well done! You have found the murderer! Have you considered a role in law enforment?`



