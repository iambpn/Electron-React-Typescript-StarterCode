# Electron-React with typescript 
## This repo uses electron builder to pack the electrion app
  This repo is exact clone of [Kitze Blog](https://medium.com/@kitze/%EF%B8%8F-from-react-to-an-electron-app-ready-for-production-a0468ecb1da3) this Medium blog with extra typescript configuration added into it.
  
  ## How to use this repo?
  Clone or Download this repo and open console inside of this repo and run `npm install` to install all the required dependency.
  
  ## Thing I have added:
  - created project with: `npx create-react-app my-app --template typescript` instead of `npx create-react-app my-app`
  - all the `yarn` commands are changed to `npm`
  - created `.env` file in root directory to prevent react-script from opening the browser. (inline `BROWSER=none` did not worked as instructed in blog so this approach is followed)
  - new tsconfig is created inside of public folder so that we can use that tsconfig file to watch electron's .ts code files. (note: .js file of electrons .ts code file will be generated next to the .ts file)
  - inside of `public/tsconfig` i have changed `"target":"es5"`to `"target":"es6"` . Because while writing code using electron class it require to be of es6 class.
  - added new script to package.json `"watch-tsc-public": "tsc --watch --project public",` . This typescript(ts) run script watch the public folder for any change in .ts files. 
  - modified electron-dev command to: `"electron-dev": "concurrently \"npm run watch-tsc-public\" \"npm start\" \"wait-on http://localhost:3000 && electron .\""` so that typescript(ts) start watching public folder for any changes.
  - Changed `electron.js` to `electron.ts` in public folder.
 
 Thats it, no further changes are done. You can follow [Kitze Blog](https://medium.com/@kitze/%EF%B8%8F-from-react-to-an-electron-app-ready-for-production-a0468ecb1da3) for more indepth knowledge of whats happening in this code. What I have done is just add typescript on top of it. 
 
 #### Note: When running react build `create react app` will generate the prod. code in `build` folder and the same `build` folder is used by `electron builder` to load icons for our electron app which created a conflict between `electron builder` and `create react app` so the [Kitze Blog](https://medium.com/@kitze/%EF%B8%8F-from-react-to-an-electron-app-ready-for-production-a0468ecb1da3) recomended to modify the build option of `electron builder` to accept the icons and other require files from `assets` folder rather than from `build`. The build option of electron builder is modified by adding build object in package.json. I have already done this so no need to redo this is just for just informing you.
 
 ## Usage Commands
 - `npm run electron-dev` : to run everything typescript(ts) watch public folder, start react dev server and start electron.
 - `npm run preelectron-pack` : to run react build script
 - `npm run electron-pack`: to pack the electron app with electron builder. There are many configuration to take care of if you want to pack this application for cross platform so go through the electron builder docs.

Go througth the blog if you have any confusion.
 
 Happy Electroning!!! 😉😉
