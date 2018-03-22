# DodgeballTemplate

## Description
A simple dodgeball-like game to demonstrate how to incorporate haptic feedback using the bHaptics Haptic Manager plugin into an UE4 project.
In the game, the player must dodge various balls being launched at them, scoring points for dodging, blocking, and catching the balls.
The user's body is tracked using simple IK of the head and arms, and haptic feedback is given when they are hit by any of the balls, as well as when they catch or deflect them.

## Haptic Feedback
You can find examples of how to deliver haptic feedback in the MotionControllerPawn and BP_MotionController blueprints.
The source feedback files are included in the FeedbackFiles folder in the project directory.

### Vest Feedback
The MotionControllerPawn blueprint contains the logic for collision with the balls, namely when a ball hits, the collision location is transformed into cylindrical coordinates for playing the feedback on the vest.
This feedback is further customised by storing the feedback file to be played as a variable in the blueprint for each ball.
Each ball can then have a separate effect, for example the rubber ball has a fading effect to soften the impact and give a 'bouncy' sensation, while the ice and metal balls have hard impacts of varying intensity.
The origin of the haptic effect is set as the centre of the vest, so the feedback is rotated with the centre as the impact point.

### Arm Feedback
The feedback logic for the Tactosy devices is contained in the BP_MotionController blueprint, detecting inputs from the controllers as well as collisions with the hands.
The feedback here is more simple, handling scenarios such as deflecting balls with the hand (collision), grabbing a ball (input), and deflecting with a held ball (collision).
Unlike with the vest, these are simply events which trigger the haptic feedback, with no further changes made to the feedback files.

## Disclaimer
All assets provided are derived from starter content and templates provided with Unreal Engine 4.
Feedback Files were generated from the bHaptics Designer, and imported into UE4 using the HapticsManager Plugin.
This project was built for UE4.17, and also requires the HapticsManager Plugin installed in the Engine, as well as the bHaptics Player for the haptic feedback to work.
