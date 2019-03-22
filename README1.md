# Who's the murderer?
### A guessing game using faces

Built with Python, React and Google Vision. Google Vision can analyze faces and can determine if a face falls into any of the following 7 categories. My goal is to use 5 of these classifcations to create a Guess Who style game. 
 - Joy
 - Sorrow
 - Anger
 - Surprise
 - Exposed
 - Blurred
 - Headwear/Hat

I plan to use Amazon S3 to store uploaded images for Release 2.

## Release 1 - Use already provided faces 
The database will be populated with a set (10?) of images (with names), each face clearly shows one of the following:
 - Joy
 - Sorrow
 - Anger
 - Surprise
 - Headwear/Hat

#### 1. User can create an account and login
Use oauth.
#### 2. User clicks to start a new game and a new murderer is generated
One face is randomly selected and Google Vision analyzes the image. The json data provided will be parsed through and saved. State will know who the murderer is and their main attribute. 
#### 3. User is shown a set of faces (with names)
Users would only be shown some faces - MVP 2 or 3 images. (Stretch) User could choose how many faces to play with.  
#### 4. User can click on "give me a clue", revealing some text
Based on the attribute that is saved in state, the user could be shown 1 of 5 main clues. Main clues are be related to the 5 main categories that faces belong to - 
 - Joy `The murderer is very joyful and pleased about their actions`
 - Sorrow `The murderer looks very sad about their actions, maybe it was self defense?!`
 - Anger  `The murderer is looks very angry, you'd better watch out!`
 - Surprise `The murderer is very surprised, are you about to catch them?`
 - Headwear/Hat  `The murderer knows your onto them, and are trying to disguise themselves - they are wearing a hat`

These main "clues" would be stored in the database, and with each new game, the appropriate clue will be fetched from the database.

Google Vision also provides other data that could be utilized for more specific clues:
 - `The main color in the murderers profile image is` (with a swatch showing the color)
 - `The murderer appears not to have hair`

#### 5. The user can click on a face to make a guess
If the guess is wrong, the face is X-ed out (maybe flips over, or greys out, or a animated X is drawn across). If the guess is correct the face is animated to enlarge/glow or something and user is shown a message. `Well done! You have found the murderer! Have you considered a role in law enforment?`

## Release 2 - Users upload their own photos
Google Vision is called each time when a user uploads their photos.  If the photo does not match one of the 5 classifications, photo is rejected and user is asked to upload a new one.

## Release 3 - Users can play against other people
 - Up to 5 people can play a game. When a new game is started, each player is given one of the 5 categories.
 - Users each upload a photo with their given category
 - Once everyone has uploaded an acceptable photo, a murderer is randomly chosen
 - Users take turns to guess
 - Users can only see incorrect guesses on their own screen (similar to Clue)
 - Whoever guesses murderer first, wins!
 
 Challenge - managing how the winner is communicated across all players. - Maybe need Redux??

## Release 4 - Implement a chatbox for players to share discoveries
Or lead others astray! 😈
