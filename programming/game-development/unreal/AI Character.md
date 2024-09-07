'AI' directory 생성 후 그 안에
Artificial Intelligence 탭에서 Blackboard(MyBasicBlackboard), Behavior Tree(MyBasicBehaviorTree) 생성

#### Blackboard

New key(Object) 생성 - TargetActor
Key Type 에 Base Class: BP_ThirdPersonCharacter로 설정
AI는 내가 조종하는 캐릭터를 따라다닐 것임

#### Behavior Tree

Behavior Tree: 생성한 blackboard로 설정
New Task (MyBasicAITask) 생성
생성한 blueprint(MyBasicAITask) 이동
#### Blueprint(MyBasicAITask)

BLackboard Key Selector 타입인 variable(Destination) 생성 후 public으로 설정
Event Receive Execute AI, Destination, Get Player Character 생성
Set Blackboard Value as Object 연결(Event Receive.., key: Destination, value: Get Player Character)
Finish Execute 연결
Behavior Tree로 돌아감


#### Behavior Tree
Sequence 연결
blueprint(MyBasicAITask), Move To 연결
MoveTo.BlackboardKey : TargetActor로 설정

AI Controller blueprint(MyBasicAIController) 생성

#### Blueprint(MyBasicAIController)
Event BeginPlay -> Run Behavior Tree 
BTAsset: MyBasicBehavior로 설정


Character Blueprint(BP_AICharacter) 생성

#### Blueprint(BP_AICharacter)
##### Mesh
Mesh 설정
Mesh 위치, 방향 알맞게 설정
Animation - Anim CLass: ABP_Manny_C로 설정
Collision Preset: Custom
Camera: Ignore 설정
##### BP
AI Controller Class: Blueprint(MyBasicAIController)로 설정
Requested Move Use Accelerator, Use Acceleration for Paths: True
###### 자연스럽게 움직이게
Use Controller Desired Rotation: True
Use Controller Rotation Yaw: False
##### Capsule Component
Collision Preset: Custom
Camera: Ignore 설정


Nav Mesh Bounds Volume 생성 후 P를 눌러 영역 보면서 설정


##### Boom After Collision
BP_AICharacter의 Blueprint

Event Hit -> Cast To BP_ThirdPersonCharcter -> Spawn Emitter at Location(set template, scale, etc) -> Play Sound at Location -> Apply Damage(set Base Damage) -> Destroy Actor
Event Hit.Other -> Cast To BP_ThirdPersonCharcter.Object
Event Hit.HitLocation -> Spawn Emitter at Location.Location, Play Sound at Location.Location
Cast To BP_ThirdPersonCharcter.As BP Third Person Character -> Apply Damage.Damaged Actor


#### Third Person Blueprint to Apply Damage
Health variable(float) 생성
Event AnyDamage -> Health.setter -> Branch -> Quit Game
Event AnyDamage.Damage -> subtract 밑에거
Health.getter -> subtract -> Health.setter 밑에거 -> <= 위에거 -> Branch.condition