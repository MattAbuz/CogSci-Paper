# CogSci-Paper

This HTML file is one of the neural network-enabled Pong scripts that Matt Oberdorfer (my coauthor) and I developed over the summer. To get it to run, you first need to download this folder containing the HTML file. To do this, on the main page of this folder, click the green button that says "Clone or Download", click "Download ZIP", and then unzip the folder, extracting all to "Desktop". You also need to do the same process for Juan Cazala's Synaptic library at https://github.com/cazala/synaptic, also being sure to extract to "Desktop". Then (this is essential), move the unzipped folder "synaptic-master" into the unzipped folder "CogSci-Paper-master".  Doing so should allow the Pong game to play in-browser just by downloading the HTML file and then double-clicking it. 

Instructions for the Game, using keyboard controls:

"A": Switches prediction learning on and off 

"R": Switches reward learning on and off

"F": Changes speed of play between 3 different settings, useful for training quickly

"B": Switches "near-perfect player" (the non-learning AI) to manual control, where the paddle position can be moved up and down with the arrow keys.

"S": Pauses and unpauses the game

Space Bar: Resets score counters at bottom of screen

In this game, the paddle on the right is controlled by the self-learning AI, whereas the left paddle is supposed to represent the near-perfect expert human player. The smart AI starts with training mode on as a default, so hit "A" right off the bat to let the AI perform on its own (notice that it is incapable of performing at all in the beggining). The red rectangle you see on the right shows where the paddle should go if it's going to return the ball. Now hit "R" to turn on the reward-based training mode, where the AI learns how to play based on the "reward" it gets from successfully returning the ball. 

The AI needs to train for a bit before it gets really good. First, hit "A" to turn on prediction training, which allows the AI to get a basic sense of how the game works using a simple network. Hitting "F" to cycle through speeds of play, let the game run for about 50,000 epochs at the fastest speed (make sure that in the upper right corner of the display, it says "Prediction Training On"). An epoch here is one full cycle of the ball from the left to the right of the field, or one play. After 50,000 epochs (which goes fast- there's a display that says "Total Epochs Trained" in the upper left corner), hit "R" to switch the game into reward training mode (be sure it says "Reward Training On"). Train on the highest speed for about 1 million epochs. This'll take about 5 minutes at the fastest speed; this can be left running in the background, but you may need to have it open in its own window because they game only plays when its tab is currently open. 

After Total Epochs Trained reaches 1 million, turn off the reward training by pressing "R" (make sure neither Prediction Training or Reward Training says "on"), and observe how the AI now outperforms the near-perfect player. The score counters on the bottom of the screen should give a quantitative sense of this. You can alter the speed of play with "F" to see how well the AI has now learned to predict after only a few minutes, and if you want to play against the AI yourself, you can toggle manual control of the left paddle on and off by hitting "B". If you want to train the AI for longer (my paper let it run up to 5M epochs), the AI will get even better as time goes on, outscoring its opponent by a larger and larger margin. But even after just a few minutes, you can already see how well this program has learned to become the world's greatest Pong player from scratch!

Note on the technical aspects:
This script makes use of a relatively complicated reward-based neural architecture to learn how to play the game. On a basic level, the system is rewarded and "learns" how to play when it successfully retuns the ball. However, this architecture also introduces a sense of "intuition" for the AI, wherein the program will learn to estimate the certainty with which it believes its own prediction for paddle placement to be correct. If the certainty is there below a certain threshold, it will place the paddle randomly instead. This is the basic training mechanism.

