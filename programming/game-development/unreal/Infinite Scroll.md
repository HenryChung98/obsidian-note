go to ThridPerson - Input - modify IMC_Default
필요한거 빼고 다 지움

Actions폴더에 Input(actionIA_Slide) 생성 후 IMC_Default에서 Mapping에 IA_Slide 키 생성

BP_ThirdPersonCharacter blueprint 이동
remove camera input
go to viewport -> set camera location, rotation
character movement -> Orient Rotation to Movement: False
카메라 움직이지 않고 캐릭터도 앞만 보고 이동함

Event graph에서
Event tick -> Add Movement Input
Get Actor Forward Vector -> Add Movement Input.World Direction
in blueprint, drag and hit C, add comment(Force character to always move forward).


Create MyBlueprint folder -> create Actor blueprint(BP_MyBlock)
Add Static Mesh(Lane1)
sidewalk01
duplicate

---x
|
y
이렇게 되있는게 좋음

Remove all components except light, playerStart

  

Modify ThirdPersonGamemode blueprint
Open full blueprint
Create numberOfBlocks(int) - default value = 10
Create AddBlock function

Add BLock -> spawnActor BP My Block
right-click spawn transform - split struct pin
make vector ->  spawnActor BP My Block.spawn transform
Create Inputs(index, int)
Add Block.index -> multiply(400.0, switch to float) -> make vector.Y
Comment spawn blocks

Move to Event Graph
Event BeginPlay -> Forloop -> Add Block
Forloop.Index -> Add Block.Index
Number Of Blocks -> subtract(1) -> Forloop.Last Index

While testing, press F8 for debugging


Go to viewport of BP_MyBlock
Add Box collision(OverlapBox)
Set box size, location
Click - On Component Begin Overlap

On Component Begin Overlap -> Cast To BP_ThirdPersonCharacter -> Cast to BP_ThirdPersonGameMode -> Delay(duration = 2.0) -> Add Block
Cast to BP_ThirdPersonGameMode.As BP Third Person GameMode -> Add Block.Target
On Component Begin Overlap.Other Actor -> Cast To BP_ThirdPersonCharacter.Object
Get Game Mode -> Cast to BP_ThirdPersonGameMode.Object