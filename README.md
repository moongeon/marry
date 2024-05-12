# The Chrome Dinosaur Game
## Table of Contents
- [Introduction](#introduction)
- [How to play](#how-to-play)
- [The Images](#the-images)
- [The HTML](#the-html)
- [The CSS](#the-css)

## Introduction
Do you remember when you were a kid and the internet went out? The only thing left to do was the Dinosaur jumping game on Chrome. Does that ring a bell? Does that feel nostalgic? It did for me. _That's why I recreated it._

## How to play
1. Make an empty folder.
2. Open it in VS Code (or any other text editor).
3. Clone the repository
```git
git clone https://github.com/Lazzzer00/Dinosaur-Game
```
4. Navigate to the cloned repository.
```node
cd Dinosaur-Game
```
6. Install the Live Server VS Code extension.
5. Open the **index.html** file in the browser by right clicking and then _'Open with Live Server'_ or _Alt+L Alt+O_.

## The Images
For **all** _'animations'_ only 6 images are used.
1. The cactus image. _(Pretty straightforward)_
2. The ground image. This one makes the ilusion on a never ending map because it just repeats forver stacking on itself.
3. The stacionary dino image. The one you see before you start the game.
4. The dino lose image. The one with Xs on its eyes when you lose.
5. 2 dino run images which alternate to create the ilusion of running.

## The HTML
We select elements with data atributes rather than ids to make it faster. Also every element has a class for styling.
- There is one main with the class of _'world'_ and a **data-world**.
- Inside it there is a score card which has a class of _score_ and a **data-score**. It is set to **0** by default.
- There is also the start screen div with the class of _start-screen_ and a **data-start-screen**. It contains the well known text: _"Press any key to start"_.
- Then we have **2** ground images with the class of _ground_ and a **data-ground**.
- Lastly we have the dino image with the class of _dino_ and a **data-dino**.

## The CSS
- Firstly with this line of code we make the sizing normal (to include the border) and we make nothing on the page selectable just a precaution.
```css
* {
  box-sizing: border-box;
  user-select: none;
}
```
- The we make the body fullscreen and we make everything in it centered using flexbox.
```css
body {
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
```
- We make the world not overflow because it is repeating forever and we make it position relative.
```css
.world {
  overflow: hidden;
  position: relative;
}
```
- The score is position absolute and set with the vmin units to always be to the right.
```css
.score {
  position: absolute;
  font-size: 3vmin;
  right: 1vmin;
  top: 1vmin;
}
```
- The start screen text is also centered using position absolute.
```css
.start-screen {
  position: absolute;
  font-size: 5vmin;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```
_**P.S:**_ Use this trick to center things on position absolute. First set the **top and left to 50%**. This won't be perfect because it doesn't account for the size of the element. Because of that use the **translate(-50%, -50%)** to center it.
- Create a utility class for hiding things.
```css
.hide {
  display: none;
}
```
- Then set the ground class by making a custom propery called '**---left**' _(that we'll edit soon!)_ to make it appear as if it was moving on the X axis.
```css
.ground {
  --left: 0;
  position: absolute;
  width: 300%;
  bottom: 0;
  left: calc(var(--left) * 1%)
}
```
- We do the exact same thing except we make it for the dinosaur and we set it to '**--bottom**' because the dino jumps and changes the Y axis.
```css
.dino {
  --bottom: 0;
  position: absolute;
  left: 1%;
  height: 30%;
  bottom: calc(var(--bottom) * 1%);
}
```
- The cactus has a similar position to the ground because it has to be _**on** the ground_.
```css
.cactus {
  position: absolute;
  left: calc(var(--left) * 1%);
  height: 30%;
  bottom: 0;
}
```
