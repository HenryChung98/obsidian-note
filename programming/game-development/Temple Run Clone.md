#### ThirdPerson Input

Delete all except move left, right, jump
Create an input action and name it IA_Slide, and add on mappings in IMC_Default.

des1

Set False for Orient Rotation to Movement in Character Movement so the character is always facing forward.
Set target offset of CameraBoom 0, 0, 200 and rotation of FollowCamera to face the character.

des2

#### Lane

Create Actor blueprint and name it MyBlock.
Create static mesh and name it Lane1.
Add mesh whatever you want.
Re-size, re-position it.


#### ThirdPerson GameMode
Create a number of blocks(int) variable, compile, assign 10 for default value.