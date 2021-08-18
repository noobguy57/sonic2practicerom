# sonic2practicerom
A Sonic 2 practice ROM meant for all emulators and console players. 
This ROM removes the score information normally displayed, and replaces it with 4 values: X Subpixels, Y Subpixels, X (Horizontal) Speed, and Spindash speed. This ROM also changes the level select feature of the game in multiple ways. The level select code is now 01 01 01 01, and when you pause in level select the A, B, and C buttons no longer do their respective resetting, slow-mo, or frame advance.

One downside to this rom is that it IS a fake REV02. Meaning the conveyor spindash in WF does not work. Spindashing in Sky Chase also kills you. I apologize for this and this is top priority for me to work on. I was unable to find an assembly decomp of the Sonic Classic cart which is the only REV02 that contains those glitches. In the future, I look to collaborate with others in order to convert this to a true REV02.

Below, are where the values are stored on the screen. They are currently displayed in hex. This will change, however it is still possible to use hex.

![explanation](https://user-images.githubusercontent.com/56403393/129827077-e2b74d15-c94d-4ddd-8a4e-dfd5d26bc1c6.png)

Subpixels:
X and Y Subpixels are a single byte of data, meaning they range from 0-255. Every time you input left or right on a pixel and Sonic does not visibly move a pixel, your X subpixel changes. Since they are in hex, the range is from 0-FF (displayed as FF00). Every time you jump or run up or down a slope or fall, your Y subpixel is changed and displayed in the same way as X subpixels.

Spindash Speed:
Spindash speed is determined by 2 RAM values, one of them super complex and hard to understand. The value showcased in this ROM will help determine how close your spindash is to perfect, or, if perfect. Again, the formula for spindash speed is complex and calculates each frame, so I will simplify my explanation. A max spindash will read in hex $800 (displayed as 0800) (2048 in decimal). Hex is very similar to decimal in that numbers still ascend towards 10, however, 10 is replaced with A, 11 replaced with B, and so on until the value 15. What this means is that if your spindash was 073A, your spindash was not perfect, but it was close to the max value of 800. Each "tap" (except for the first tap, which resets the value) increases the spindash speed by $0200 (512 in decimal). It then descends if no buttons are pressed in an equation I can't quite understand, so just try to go fast :).

X Speed:
X speed is also displayed in hex, however, when watching these values in RAM, your X speed goes negative if running left, which the game tries to reflect in hex by using a higher number. This is on the list to convert to decimal, so that it is easier to read, however, by experimenting, you should be able to figure out the value in hex for Sonic's max speed in certain scenarios.

The In Game Timer:
Since this ROM abuses debug mode's built in code to display RAM values, the in game timer was fixed to run properly rather than show sprite count. This does mean that you still can time over though, I tried removing time over's but Shore knows that it screws with rings and extra lives and the timer :).

This ROM should be updated in the future with some more quality of life changes, but for now, I'm content with what I've done. Please reach out to me if you have any questions.
