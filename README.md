

# sonic2practicerom
A Sonic 2 practice ROM meant for all emulators and console players. Please reach out to me with any feedback or ideas.


This ROM removes the score information normally displayed, and replaces it with 5 values: X Subpixels, Y Subpixels, X and Y Position, and Spindash speed. This ROM also changes the level select feature of the game in multiple ways. The game automatically sends you to level select, with the A, B, and C buttons being disabled, unless you enable the C button in the options.

This ROM is what I like to call a standalone version of the Classic Compilation Cart ROM, it behaves in the exact same way as that version of the game, but without Sonic 1 and Mean Bean Machine added on.

Below are where the values are stored on the screen. They are currently displayed in hex. This may or may not change, however it is still possible to use hex.

![example3](https://user-images.githubusercontent.com/56403393/130340948-50e4ff95-de93-41ea-a700-ff7937b73fe5.png)

Subpixels:
X and Y Subpixels are a single byte of data, meaning they range from 0-255. Every time you input left or right on a pixel and Sonic does not visibly move a pixel, your X subpixel changes. Since they are in hex, the range is from 0-FF. When you jump or run up or down a slope or fall, your Y subpixel is changed and displayed in the same way as X subpixels.

Spindash Speed:
Spindash speed is determined by 2 RAM values, one of them is super complex and hard to understand. The value showcased in this ROM will help determine how close your spindash is to perfect, or if perfect. Again, the formula for spindash speed is complex and calculates each frame, so I will simplify my explanation. A max spindash will read in hex $800 (displayed as 0800) (2048 in decimal). Hex is very similar to decimal in that numbers still ascend towards 10, however, 10 is replaced with A, 11 replaced with B, and so on until the value 15. What this means is that if your spindash was 073A, your spindash was not perfect, but it was close to the max value of 800. Each "tap" (except for the first tap, which resets the value) increases the spindash speed by $0200 (512 in decimal). It then descends if no buttons are pressed in an equation I can't quite understand, so just try to go fast :).

X and Y Position:
This is pretty self explanatory, again these values are in hex. They start at 0000 at the leftmost pixel of the stage.

The In Game Timer:
Since this ROM abuses debug mode's built in code to display RAM values, the in game timer was fixed to run properly rather than show sprite count. This does mean that you still can time over though, I tried removing time over's but Shore knows that it screws with rings and extra lives and the timer :).

This ROM should be updated in the future with some more quality of life changes, but for now, I'm content with what I've done. Please reach out to me if you have any questions or if you have feedback or ideas you would like to share with me.

PS: Sorry about the mis-aligned text in game, I seriously have no clue how to align it or how it decides where to go :(.
