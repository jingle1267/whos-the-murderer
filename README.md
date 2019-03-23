# Who's the murderer?
### A guessing game using faces

Built with Python/Django, React and Google Vision. Google Vision can analyze faces and can determine if a face falls into any of the following 7 categories. My goal is to use 5 of these classifcations to create a Guess Who style game. 
 - Joy
 - Sorrow
 - Anger
 - Surprise
 - Exposed
 - Blurred
 - Headwear/Hat

I plan to use Amazon S3 to store uploaded images for Release 2.

## Release 1 - Use already provided faces 
The database will be populated with url links to a set of 9 images, each face clearly shows one of the following:
 - Joy
 - Sorrow
 - Anger
 - Surprise
 - Headwear/Hat

#### 1. User can create an account and login
Use [oauth](https://www.npmjs.com/package/react-oauth-flow)
#### 2. User clicks to start a new game and a new murderer is generated
One face is randomly selected and Google Vision API analyzes the image. The json data provided will be parsed through and relevant data will be saved. React's state will know who the murderer is and various attributes about that face. For example:
```
state = {
  murdererData = {
    mainEmotion : "",
    headwear: false,
    mainColor : "",
    secondaryColor : ""
    }
}
```
#### 3. User is shown all 9 faces
(Stretch) Database is populated with url links to more faces and user could choose how many faces to play with to make the game harder - 9, 16 or 25 faces.
#### 4. User can click on "give me a clue", revealing some text
Based on the attributes that are saved in state, the user could be shown 1 of 5 main clues relating to the emotion of the murderer. 
 - Joy `The murderer is very joyful and pleased about their actions`
 - Sorrow `The murderer looks very sad about their actions, maybe it was self defense?!`
 - Anger  `The murderer is looks very angry, you'd better watch out!`
 - Surprise `The murderer is very surprised, are you about to catch them?`
 - Headwear/Hat  `The murderer knows your onto them, and are trying to disguise themselves - they are wearing a hat`

The text for "clues" would be stored in the database, and with each new game, the appropriate clue will be fetched from the database that matches the newly analyzed image.

Google Vision also provides other data that could be utilized for more specific clues:
 - `The main color in the murderers profile image is` (with a swatch showing the color)
 - `The murderer appears not to have hair`
 - `The murderer appears to be wearing glasses`

#### 5. The user can click on a face to make a guess
If the guess is wrong, the face is X-ed out (maybe flips over, or greys out, or a animated X is drawn across - utlize SVGs). If the guess is correct the face is animated to enlarge/glow and user is shown a message. `Well done! You have found the murderer! Have you considered a role in law enforment?` The game is over!

## Release 2 - Users can upload their own photos
Google Vision is called each time when a user uploads their photos.  If the photo does not match one of the 5 main classifications, photo is rejected and user is asked to upload a new one.  Will need to utlilize AWS S3 (or something similar) to images.

## Release 3 - Users can play against other people
 - Up to 5 people can play a game. When a new game is started, each player is randomly given one of the 5 main categories.
 - Users each upload a photo with their given category
 - Once everyone has uploaded an acceptable photo, a murderer is randomly chosen
 - Users take turns to guess
 - Users can only see incorrect guesses on their own screen
 - Whoever guesses murderer first, wins!
 
 Challenge - managing how the winner is communicated across all players. - Maybe need Redux??

## Release 4 - Implement a chatbox for players to share discoveries
Or lead others astray! 😈
