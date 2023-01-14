Copyright 2022 Silvan Teufel / Teufel-Engineering.com All Rights Reserved.

# RTS Unit Template - Readme - 2022
### Create your own RTS Units !

- CTRL + E -- Rotate Cam Right (works also when Cam is locked to Unit )
- CTRL + Q - Rotate Cam Left (works also when Cam is locked to Unit )
- CTRL + Left Mouse Click -- Move Cam to Mouse Position
- CTRL + W -- Zoom Cam In
- CTRL + S -- Zoom Cam Out
- CTRL + HOLD SPACE -- Fast Zoom Out to Position
- CTRL + SPACE + Left Mouse - Move Cam to Mouse Position
- Mouse to Screen Edges -- Move Cam to Mouse Position
- Right Click when Unit Selected -- Move Unit
- Shift + Right Click when Char. Sel. -- Move Unit through Waypoints
- CTRL + G when Unit Selected -- Lock Unit on Character
- CTRL + T when Unit Selected -- Switch to Third Person Mode
- Press A when Character Selected - toggle Attack
- Press A + Left Click when Character Selected - Move to Position and Attack
- Press A + Left Click on Enemy - Focus this Enemy
- HOLD TAB -- Show Control-Widget

Gameplay Preview: https://www.youtube.com/watch?v=ESS5PYtr9mU

For Questions you can write to info@teufel-engineering.com
If you find any Issues or Bugs i appreciate your Mail.
I will fix any Bugs as soon as i can and update the Product.

## Download the Plugin

https://www.unrealengine.com/marketplace/en-US/profile/Silvan+Teufel?count=20&sortBy=effectiveDate&sortDir=DESC&start=0

If you have downloaded the plugin it can be found in your Unreal Engine folder:
C:\Program Files\Epic Games\UE_5.0\Engine\Plugins\RTSUnitTemplate (for example).
or
C:\Program Files\Epic Games\UE_5.0\Engine\Plugins\Marketplace\RTSUnitTemplate

If you can find this folder in your enginge plugins folder the download was successful.
If the plugin is in another folder, you should copy it here.

## Install the Plugin

Open Unreal Editor. Click Edit -> Plugins to open the plugin window.
Search for SwarmSimulator and put a check mark at it.

## Import Settings

RTSUnitTemplate/Document/Description_Backup_2022-11-14_102425_RTSUnitTemplate.ini
RTSUnitTemplate/Document/Gameplay_Debugger_Backup_2022-11-14_102535_RTSUnitTemplate.ini
RTSUnitTemplate/Document/Input_Backup_2022-11-14_102458_RTSUnitTemplate.ini (Deprecated, use Enhanced Keyboard Settings)
RTSUnitTemplate/Document/Maps_&_Modes_Backup_2022-11-14_102333_RTSUnitTemplate.ini

__You can download these files also here from github by clicking on top left Code->Download Zip__

Open Unreal Editor. Go to Edit -> Project Settings -> Search for the Specific Input Section: Gameplay Debugger, Input, Maps & Modes, Settings (For Description)
and import the .ini file

You can also find the .ini files in the Plugin Folder "All\Engine\Plugins\SwarmSimulator\Document\Input

## Enhanced Keyboard Settings

You can Change Inputs at: All\Engine\Plugins\TopDownRTSCamLib\Content\Blueprints\Controls

For GameplayTags you have to set AssetMangerClass in ProjectSettings (Restart Project after change):

![image](https://user-images.githubusercontent.com/45244380/211891213-c16b45c3-25d7-4af2-bb5c-d4aeb124ceec.png)

Go to ProjectSettings->Input and set EnhancedIputComponentBase:

![image](https://user-images.githubusercontent.com/45244380/211891263-032cfbc6-120c-40f3-82f6-b1d7cff938a3.png)

YOu can set MappingContext and ControlAsset in the BP_CameraBase:

![image](https://user-images.githubusercontent.com/45244380/212332329-42eaec24-7096-4728-8c8a-ede7846c0efc.png)

![image](https://user-images.githubusercontent.com/45244380/212332385-9137f8ed-212e-4c99-bcb5-def35dd7160b.png)

## Test Example Map

Open Unreal Editor. Open folder (In Unreal Editor folder tab):
All\Engine\Plugins\RTSUnitTemplate\Content\RTSUnitTemplate\Level\levelOne

## Example Blueprints

Your can find example Blueprints in the Unreal Editor as well:
All\Engine\Plugins\RTSUnitTemplate\Content\RTSUnitTemplate\Blueprints

This Blueprints use the Parent Classes from RTSUnitTemplate Plugin, which you can use for your Blueprints.
	
## Parent Classes

If RTSUnitTemplate is installed the Classes can be used as Parent Class in Blueprint, so all functions from this Class are available.
Just use one of the following Classes as Parent Class and or just choose them in your GameMode Blueprint. Category = RTSUnitTemplate. 

Parentclasses are:

Actors:
- Projectile
- SelectedIcon
- Waypoint

Animations:
- UnitBaseAnimInstance ( Usable with Blenspaces via DataTable )

Characters:
- CameraBase ( A Small RTS Camera with cool responsive Camera-Jump)
- UnitBase (This is the Key Element of this Product)

Controller:
- ControllerBase (Should be used to Control the UnitBase)
- UnitControllerBase (This is needed for the UnitBase)

Hud:
- HUDBase

Widgets:
- UnitBaseHealthBar

---

Here is a List of the Classes and there Functions:
(All Variables and Functions are accessible via Blueprint - BlueprintReadWrite or EditAnywhere (so editable in Details Panel) or Both.)

## Create a Blueprint from Parent Classes

1. Right Click inside the Content Browser inside the Unreal Editor -> Create Blueprint
2. Go to "ALL CLASSES" Section and tipe the Name of the Parent Class inside the Search (Choose one of the ParentClasses)
3. Click on Select
4. Go in the Details Penal of you BP_Class and Type "RTSUnitTemplate" into the Search

BP_UnitBase Setup
1. For Character choose a Skeletal Mesh and a Animation Blueprint (there are Example Animation Blueprints in the Blueprint Folder All\Engine\Plugins\SwarmSimulator\Content\SwarmSimulator\Blueprints\Animations)
2. Adapt the Trigger Capsule to the Mesh
3. If you need a new Animation Blueprint for your Mesh Create it -> Right Click -> Animations -> Animation Blueprint
4. Copy the Statemachine from my Example Animations Blueprints (All\Engine\Plugins\SwarmSimulator\Content\SwarmSimulator\Blueprints\Animations)
5. Go through all States and change the Animation.
6. Check if the Transition Rules are Setup Correctly. If not you can easily choose the right state from a dropdown.
7. Check Details of the Blueprint by Typing SwarmSimulator in the Search.
8. Use Functions and Variables in EvenGraph and Construction Script. Or just use the Parent Class as it is.
9. Choose the AI Controller for the Unit

BP_UnitBaseController
1. When created the Blueprint u can just adapt the Details Panel by Typing in Search "RTSUnitTemplate"
2. Choose the BP_UnitBaseController in your BP_UnitBase under "Ai Controller"

Character Animation Statemachine
1. Right Click Create Animation -> Animation Blueprint
2. Choose Parent Class of the CharacterBase -> CharacterBaseAnimInstance / EnemyBase -> EnemyBaseAnimInstance / MouseBotBase -> MouseBotBaseAnimInstance
3. Choose Skeleton
4. Copy Statemachine from (All\Engine\Plugins\SwarmSimulator\Content\SwarmSimulator\Blueprints\Animations)
5. You can change the Time the Unit stuck in the Animation. This will also change Gameplay. To Adjust the Animation Times take a Look into the ControllerBase properties.

HUD/Actor Setup
1. Create a Blueprint like mentioned above.
2. Type "RTSUnitTemplate" in Search Details.
3. Use Functions and Variables in EvenGraph and Construction Script. Or just use the Parent Class as it is.


Widget Setup
1. Widgets have to be choosen inside the Blueprints of a Character
2. Example Widgets are at (All\Engine\Plugins\RTSUnitTemplate\Content\RTSUnitTemplate\Blueprints\Widgets)
3. Example Character with choosen Widgets can be found at (All\Engine\Plugins\RTSUnitTemplate\Content\RTSUnitTemplate\Blueprints\Character)
4. Widget hast to been set Space "Screen" and Draw at Desired Size to true. (In the Widget and in the Character BP)
5. Widget Class has to choose a Blueprint (in the Character BP). Or just use the Parent Class like it is.


# UnitBase

|UnitStates (The Statemachine is in UnitControllerBase)        	|Note                         |
|---------------------------------------------------------------|-----------------------------|
|Idle     UMETA(DisplayName = "Idle")       			| CharAnimState = Idle	      |
|Run     UMETA(DisplayName = "Run"),    			| CharAnimState = Run         |
|Patrol UMETA(DisplayName = "Patrol"),    			| CharAnimState = Patrol      |
|Jump   UMETA(DisplayName = "Jump"),      			| CharAnimState = Jump        |
|Attack UMETA(DisplayName = "Attack"),			        | CharAnimState = Attack      |
|Pause UMETA(DisplayName = "Pause"),     			| CharAnimState = Pause       |
|Chase UMETA(DisplayName = "Chase"),  				| CharAnimState = Chase       |
|IsAttacked UMETA(DisplayName = "IsAttacked") ,     		| CharAnimState = IsAttacked  |
|Dead UMETA(DisplayName = "Dead"),   				| CharAnimState = Dead        |
|None UMETA(DisplayName = "None"),    				| Should not happen	      |


|Properties (EditAnyWhere + BlueprintReadWrite)                  	|Note                         |
|-----------------------------------------------------------------------|-----------------------------|
|bool IsFriendly = true;         					| Set false for Enemys	      					|
|float Range = 300.f;           					| Choose Attack Range         					|
|float StopChaseAtDistance = 100.f;					| Switches from Chase to Attack if Distance is reached 		|
|float MaxRunSpeed = 400.f;        					| Unit Max Run Speed          					|
|float IsAttackedSpeed = 200.f;          				| Slow Down when EnemyUnit is Attacked				|
|float RunSpeedScale = 4.f;						| Choose to Scale the Speed in "Run" 4 is standard		|
|float StopRunTolerance = 100.f;       					| Stops when Position is only 100.f away	       		|
|float StopRunToleranceY = 400.f;           				| Stops if Y-Position is only 400.f away        		|
|float AttackDamage = 40.0f;          					| The Damage that the Unit Makes when attacking        		|
|class AWaypoint* NextWaypoint;       					| The Start Waypoint when Unit is in "Patrol"	        	|
|TEnumAsByte<UnitData::EState> UnitState = UnitData::Idle;		| Choose the Start UnitState. For Enemys it should be Patrol	|
|TEnumAsByte<UnitData::EState> UnitStatePlaceholder = UnitData::Patrol;	| This is used to Switch the UnitState back from other States	|
|class UWidgetComponent* HealthWidgetComp;          			| Used for Healthbar Implementation.           			|
|float MaxHealth = 120;       						| MaxHealth of the Character. Use it to change MaxHealth        |
|FVector HealthWidgetCompLocation = FVector (0.f, 0.f, 180.f);          | Location of the Healthbar realtive to the Character		|
|TSubclassOf<class AProjectile> ProjectileBaseClass;			| Choose a ProjectileBaseClass if you want to use a Projectile	|
|bool UseProjectile = false;      					| Set to true if you want to use a Projectile		        |
|FVector ProjectileSpawnOffset = FVector(0.f,0.f,0.f);          	| Offset Realtive to the Unit for the Spawn of the Projectile 	|
|float ProjectileScaleActorDirectionOffset = 50.f;			| Offset in Actor Direction (to Spawn infront of Weapon)	|
|float ProjectileSpeed = 50.f;						| Chosse the Speed of the Projectile				|
|FVector ProjectileScale = FVector(1.f,1.f,1.f);			| Choose the Size of the Projectile				|
|bool DestroyAfterDeath = true;						| True if Units should despawn after Death.			|	
	

|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|float UnitControlTimer = 0.0f;        				| Used in UnitControllerBase Statemachine            |
|bool ToggleUnitDetection = false;				| Is Used in ControllerBase to toggle unit to Attack |
|AUnitBase* UnitToChase;       					| Is set to the Unit which should be attacked        |
|TArray <AUnitBase*> UnitsToChase;          			| Array of all available Units		             |
|float Health;							| Current Health of the Unit			     |
|TArray <FVector> RunLocationArray;				| Used for MoveThroughWaypoints in the HUD	     |
|int32 RunLocationArrayIterator;				| Used for the Iteration of the Array		     |
|FVector RunLocation;						| Is the Location where the Unit should Run. Used in "Run"|
|class ASelectedIcon* SelectedIcon;				| The Icon is Hidden when Character is not selected|
|class AProjectile* Projectile;					| The Current Projectile|
	
|Functions (BlueprintCallable)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|void IsAttacked(AActor* AttackingCharacter);       		| Gets called when Unit is attacked. Called in UnitControllerBase |
|void SetWalkSpeed(float Speed);      				| Set Max Walkspeed           |
|bool SetNextUnitToChase();        				| Chooses UnitToChase from UnitsToChase (closest unit is choosen) |
|void SetWaypoint(class AWaypoint* NewNextWaypoint);        	| Sets the new Waypoint. Unit walks to Waypoint in State "Patrol" |
|void SetUnitState( TEnumAsByte<UnitData::EState> NewUnitState);| Used to Set the State of the Unit (UnitControllerBase->UnitControlStateMachine) |
|TEnumAsByte<UnitData::EState> GetUnitState();       		| Get the current Unit State          		|
|float GetHealth();       					| Get current health of the Unit          	|
|void SetHealth(float NewHealth);       			| Set current health of the Unit         	|
|float GetMaxHealth();      					| Get max health of the Unit            	|
|void SetSelected();       					| Sets the SelectedIcon selected           	|
|void SetDeselected();      					| Sets the SelectedIcon delected            	|
|void SpawnSelectedIcon();       				| Spawns the SelectedIcon         		|	
	

# CameraBase

|Properties (EditAnyWhere + BlueprintReadWrite)                  	|Note                         |
|-----------------------------------------------------------------------|-----------------------------|
|float Margin = 15;       						| Margin the ScreenSize where Camera-Mouse-Movement gets toggled	|
|int GetViewPortScreenSizesState = 1;         				| Choose 1 or 2  to set SetViewPortScreenSizes 2 uses GSystemResolution |
|float CamSpeed = 80;							| Choose the Speed of the Camera					|
|float ZoomOutPosition = 20000.f;       				| The Position the Camera should stop when Zooming out fast (Press Space)|
|float ZoomPosition = 1500.f;         					| The Position where Camera should stop when Zooming in again (Standard Position) |
|class UWidgetComponent* ControlWidgetComp;				| Used when Tab gets pressed to show Control Shortcuts			|	
|FRotator ControlWidgetRotation = FRotator(50, 180, 0);       		| Change the Rotation of the Control-Widget           |
|FVector ControlWidgetLocation = FVector(400.f, -100.0f, -250.0f);      | Change the Location of the Control-Widget           |
|FVector ControlWidgetHideLocation = FVector(400.f, -2500.0f, -250.0f); | Change the Location of the Control-Widget if it is hidden           |


|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|USceneComponent* RootScene;      				| Pointer to the RootScene     	|
|USpringArmComponent* SpringArm;				| Pointer to the SpringArm 	|
|Rotator SpringArmRotator = FRotator(-50, 0, 0);     		| Rotation of the SpringArm	|
|UCameraComponent* CameraComp;          			| Pointer to the CameraComp     |
|APlayerController* PC;						| Pointer to the PlayerController |
|int32 ScreenSizeX;						| This is set by SetViewPortScreenSizes |
|int32 ScreenSizeY;						| This is set by SetViewPortScreenSizes |
|float PitchValue = 0.f;					| Used for Rolling Cam |
|float YawValue = 0.f;						| Used for Rolling Cam |
|float RollValue = 0.f;						| Used for Rolling Cam |
|bool RollCamRight = false;					| Is set to Roll Cam in Tick|
|bool RollCamLeft = false;					| Is set to Roll Cam in Tick|
|bool ZoomCamOut = false;					| Is set to Zoom Cam in Tick|
|bool ZoomCamIn = false;					| Is set to Zoom Cam in Tick|
|bool ZoomCamOutToPosition = false;				| Is set to Zoom Cam to ZoomOutPosition in Tick|
|bool MoveCamForward = false;					| Is set to Move Cam in Tick|
|bool MoveCamBackward = false;					| Is set to Move Cam in Tick|
|bool MoveCamLeft = false;					| Is set to Move Cam in Tick|
|bool MoveCamRight = false;					| Is set to Move Cam in Tick|
|int CamAngle = 0;						| Current Cam Angle|
	
|Functions (BlueprintCallable)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|void CreateCameraComp();       				| Is Creating the Camera      |
|void SetViewPortScreenSizes(int x);     			| Sets ScreenSize X/>         |
|void SpawnControllWidget();       				| Spawns the Control Widget   |
|FVector GetCameraPanDirection();       			| Used in Tick to get Pandirection          |
|void PanMoveCamera(const FVector& PanDirection);		| Move Camera via ScreenEdges            |
|void ZoomIn();      						| Zoom In          |
|void ZoomOut();    						| Zoom Out          |
|void ZoomStop();      						| Zoom Stop            |
|void CamLeft();    						| Move Cam Left          |
|void CamRight();      						| Move Cam Right           |
|void CamStop();   						| Stop Cam Move           |
|void CamRotationTick();      					| Used in Tick to Rotate Cam            |
|void JumpCamera(FHitResult Hit);    				| Jump Camera to Hit Location          |
|FVector2D GetMousePos2D();   					| Get Mouse 2D Position          |
|void Zoom();      						| Zoom Camera           |
|void ZoomOutToPosition();      				| Zoom out to ZoomCamOutToPosition |
|void CamMoveAndZoomTick();    					| Move and Zoom used in Tick          |
|void ZoomInToPosition();     					| Zoom Back In           |
|void LockOnUnit(AUnitBase* SelectedActor);      		| Lock Camera on a Unit          |
|void HideControlWidget();      				| Sets the Control Widget Location        |
|void ShowControlWidget();     					| Sets the Control Widget Hide Location           |
	
	
# UnitControllerBase

|Properties (EditAnyWhere + BlueprintReadWrite)                  	|Note                         |
|-----------------------------------------------------------------------|-----------------------------|
|float SightRadius = 1500.0f;   					| The Sight of the Unit should be higher then the Range! |
|float SightAge = 5.0f;		         				| ---           |
|float LoseSightRadius = SightRadius + 1000.0f;				| The Unit Loses Sight when LoseSightRadius is reached |
|float FieldOfView = 360.0f;		      				| Field Of View in degre    |
|float DespawnTime = 1.0f;       					| Despawn Time after Death           |
|float PauseDuration = 0.6f;						| Time in UnitState Pause. Which is also CharAnimState (in Anim BP) |	
|float AttackDuration = 0.6f;				      		| Time in UnitState Attack. Which is also CharAnimState (in Anim BP) |
|float IsAttackedDuration = 0.3f;					| Time in UnitState IsAttacked. Which is also CharAnimState (in Anim BP)  |
|float AttackAngleTolerance = 0.f;					| Set it higher to prevent shaking of the Unit. Especially when Unit is Big |


|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|class UAISenseConfig_Sight* SightConfig;    			|---            |
|float DistanceToUnitToChase = 0.0f;				|Current Distance to Unit to Chase |
	
|Functions (BlueprintCallable)                  				|Note                         |
|-------------------------------------------------------------------------------|-----------------------------|
|void KillUnitBase(AUnitBase* UnitBase);     					| Kill the UnitBase           |
|void OnUnitDetected(const TArray<AActor*>& DetectedUnits);     		| Is called when a Unit is detected. UnitToChase is set.  |
|void RotateToAttackUnit(AUnitBase* AttackingUnit, AUnitBase* UnitToAttack);  	| Rotates the Unit to the Unit which will be Attacked.            |
|void UnitControlStateMachine(float DeltaSeconds);  				| Is called in Tick          |
	
	
# ControllerBase

|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|bool IsShiftPressed = false;		   			| Is Triggerd from ControllerBase  |
|bool AttackToggled = false;					| Is Triggerd from ControllerBase  |
|bool IsStrgPressed = false;					| Is Triggerd from ControllerBase  |
|bool IsSpacePressed = false;					| Is Triggerd from ControllerBase  |
|bool AltIsPressed = false;					| Is Triggerd from ControllerBase  |
|bool LeftClickIsPressed = false;				| Is Triggerd from ControllerBase  |
|bool LockCameraToCharacter = true;				| Is Triggerd from ControllerBase  |
|TArray <AUnitBase*> SelectedUnits;				| Is Triggerd from ControllerBase  |
	
|Functions (BlueprintCallable)                  				|Note                         |
|-------------------------------------------------------------------------------|-----------------------------|
|void ShiftPressed();			   					| Is Triggerd from ControllerBase  |
|void ShiftReleased();						     		| Is Triggerd from ControllerBase  |
|void LeftClickPressed();						 	| Is Triggerd from ControllerBase  |
|void LeftClickReleased();			 				| Is Triggerd from ControllerBase  |
|void RightClickPressed();			  				| Is Triggerd from ControllerBase  |
|void SpacePressed();				 				| Is Triggerd from ControllerBase  |
|void SpaceReleased();				 				| Is Triggerd from ControllerBase  |
|void APressed();				 				| Is Triggerd from ControllerBase  |
|void AReleased();				 				| Is Triggerd from ControllerBase  |
|void JumpCamera();				 				| Is Triggerd from ControllerBase  |
|void StrgPressed();				 				| Is Triggerd from ControllerBase  |
|void StrgReleased();				 				| Is Triggerd from ControllerBase  |
|void ZoomIn();				 					| Is Triggerd from ControllerBase  |
|void ZoomOut();				 				| Is Triggerd from ControllerBase  |
|void ZoomStop();				 				| Is Triggerd from ControllerBase  |
|void CamLeft();				 				| Is Triggerd from ControllerBase  |
|void CamRight();				 				| Is Triggerd from ControllerBase  |
|void ToggleLockCameraToCharacter();		 				| Is Triggerd from ControllerBase  |
|void TabPressed();				 				| Is Triggerd from ControllerBase  |
|void TabReleased();				 				| Is Triggerd from ControllerBase  |
|void CameraPawnForward();			 				| Is Triggerd from ControllerBase  |
|void CameraPawnBackward();			 				| Is Triggerd from ControllerBase  |
|void CameraPawnLeft();				 				| Is Triggerd from ControllerBase  |
|void CameraPawnRight();			 				| Is Triggerd from ControllerBase  |
|void CameraPawnForwardR();				 			| Is Triggerd from ControllerBase  |
|void CameraPawnBackwardR();				 			| Is Triggerd from ControllerBase  |
|bool IsShiftPressed = false;			 				| Is Triggerd from ControllerBase  |
|bool AttackToggled = false;				 			| Is Triggerd from ControllerBase  |
|bool IsStrgPressed = false;			 				| Is Triggerd from ControllerBase  |
|bool IsSpacePressed = false;				 			| Is Triggerd from ControllerBase  |
|bool AltIsPressed = false;				 			| Is Triggerd from ControllerBase  |
|bool LeftClickIsPressed = false;				 		| Is Triggerd from ControllerBase  |
|bool LockCameraToCharacter = true;			 			| Is Triggerd from ControllerBase  |
|TArray <AUnitBase*> SelectedUnits;			 			| Is Triggerd from ControllerBase  |


# HUDBase

|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|bool bSelectFriendly = false;   				| Left Click and holde it gets set to true |
|FVector2D InitialPoint;					| Used for select and Draw of Rectangle |
|FVector2D CurrentPoint;    					| Used for select and Draw of Rectangle |
|FVector IPoint = FVector(0.f,0.f, 0.f);			| Used for better sharpnes is set in ControllerBase |
|FVector CPoint = FVector(0.f,0.f, 0.f);   			| Used for better sharpnes is set in ControllerBase |
|float RectangleScaleSelectionFactor = 0.9;			| Only the inner rectangle will select |
|TArray <AUnitBase*> SelectedFriendlyUnits;			| The selected Units |
|TArray <AUnitBase*> AllFriendlyUnits;				| All Units which are selectable |
|bool CharacterIsUnSelectable = true;				| Set to false to make characters unselectable |

	
|Functions (BlueprintCallable)                  				|Note                         	|
|-------------------------------------------------------------------------------|-------------------------------|
|FVector2D GetMousePos2D();    							| ---           	|
|void SetUnitSelected(AUnitBase* Unit);    					| ---            	|
|void DeselectAllUnits();  	|'Isn't this fun?'            			| ---            	|
|void ControllDirectionToMouse(AActor* SelectedUnits, FHitResult Hit); 		| ---             	|
|bool IsActorInsideRec(FVector InPoint, FVector CuPoint, FVector ALocation);	| IPoint and CPoint for higher sharpness |
|void MoveUnitsThroughWayPoints(TArray <AUnitBase*> Units);			| Is called in Tick |
	
# Projectile

|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|AActor* Target;   						| of the Projectile from the Unit    |
|class UCapsuleComponent* TriggerCapsule;			| to Destroy the Projectile and do dmg, change size in BP!|
|UStaticMeshComponent* Mesh;					| Choose a Mesh!! |
|UMaterialInterface* Material;					| Material of the mesh is set in contructor |
|FVector TargetLocation;					| TargetLocation |
|float Damage;							| Gets Set in UnitControllerBase |
|float LifeTime = 0.f;						| Current Life Time|
|float MaxLifeTime = 2.f;					| After Current Life Time reached Max Life Time Projectile gets destroyed |
|bool IsFriendly = true;					| Is it from a Friendly or UnFriendly Character |
|float MovementSpeed = 50.f;					| MovementSpeed of the Projectile |
	
|Functions (BlueprintCallable)                  				|Note                        			|
|-------------------------------------------------------------------------------|-----------------------------------------------|
|void OnOverlapBegin(class AActor* OtherActor,);    				| Gets Triggered when Projectile hits a Target   |

	
# SelectedIcon

|Properties (BlueprintReadWrite)  		                 	|Note                         |
|-----------------------------------------------------------------------|-----------------------------|
|UStaticMeshComponent* IconMesh;  					| Is set in Constructor       |
|UMaterialInterface* BlueMaterial;	         			| Is set by Function          |
|UMaterialInterface* ActionMaterial;					| Is set by Function 	      |
|UMaterialInstanceDynamic* DynMaterial;		      			| ---           	      |

	
|Functions (BlueprintCallable)                  				|Note                         |
|-------------------------------------------------------------------------------|-----------------------------|
|void ChangeMaterialColour(FVector4d Colour);   				| ---               |
|void ChangeMaterialToAction();     						| ---               |
	
	
# Waypoint

|Properties (EditAnyWhere + BlueprintReadWrite)                  	|Note                         |
|-----------------------------------------------------------------------|-----------------------------|
|AWaypoint* NextWaypoint;	  					|Used for UnitState Patrol    |


|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|USceneComponent* Root;  					| ---             		|
|UBoxComponent* BoxComponent;					| ---  				|
	
|Functions (BlueprintCallable)                  				|Note                         |
|-------------------------------------------------------------------------------|-----------------------------|
|void OnPlayerEnter(AActor* OtherActor)						| The NextWaypoint of the Unit will be set   |
	
	
