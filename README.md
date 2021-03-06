# DEVELOPING FOR MAFIA IN JS

Hey all. This is a brief explainer on how to get to a usable JS development environment for KOLMafia. Ideally, this will cover everything you need to make a sample JavaScript mafia script. This was written by a JS novice, so hopefully it properly enumerates everything you need to do to get an environment up and running!

- **STEP 1:** Download Node.js / NPM. This will allow you to install babel/webpack and set up a compiler. To download, visit [the latest node.js build](https://nodejs.org/en/). (You can also use homebrew or any other package manager, depending on your preferences, and you probably should. But I don't really want to go into homebrew etc right now. Just use your particular package manager for this, or just install as instructed in the above link.)
- **STEP 2:** Let's set up a sample repository. You can do that using this starter repository right here! I would recommend starting by forking the repository, which you can do up top using the "fork" button. Once you have forked this repository, clone it to your machine with `git clone` & the .git URL that is accessible via the green 'CODE' button above the file tree in the GitHub page you'll see before you.
- **STEP 3:** You should now have a copy of this repository on your machine, with a package.json file you can use to help ensure your dependencies are installed. Run `npm install` while in your new directory to ensure your local copy of npm has correctly installed necessary dependencies, like the Loathing Scripting Society's JS toolkit (LIBRAM) & other KoLMafia JS toolkits. 
- **STEP 4:** Let's modify the code a little bit. At build, all this code does is tell you how much MP you have relative to the number 200; let's change the print statement to add your name in here. Modify "main.ts" to include the following, changing "\[NAME\]" to your name.:
```js
import {
  myMp,
  print,
} from 'kolmafia';

export function checkMP() {
  if( myMp() < 200 ){
    return "Your MP is less than 200, buddy."
  } else {
    return "Your MP is greater than or equal to 200. Congratulations, [NAME]"
  }
}

export function main() {
  print(checkMP());
}
```
- **STEP 5:** Now, let's update package.json; run `npm init` to revamp the package.json file to reflect whatever you want your script to be named. The new name will propagate down into the final build. 
- **STEP 6:** Let's build your code! Run `npm run build` to build out a new output main.js file.
- **STEP 7:** Now, you want to symlink your code into your KoLMafia directory. This will involve using a linking command. Keep in mind that you cannot do ./ completion with symlinks; you need to explicitly list out the entire file path. My symlink command involved first running `mkdir test` in my KoLmafia/scripts folder and then running the following: `ln -s ~/Documents/PERSONAL/KOL/kol-js-starter/KoLmafia/scripts/ ~/Library/Application\ Support/KoLmafia/scripts/test/` -- this may be different for you.
- **STEP 8:** From the KoLMafia GCLI, run "main.js" -- this should generate your MP statement. Congrats, you made something!