Copyright 2022 Silvan Teufel / Teufel-Engineering.com All Rights Reserved.

# RTS Unit Template - Readme - 2022

Gameplay Preview:


For Questions you can write to info@teufel-engineering.com
If you find any Issues or Bugs i appreciate your Mail.

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

RTSUnitTemplate/Document/Inputs/Gameplay_Debugger_Backup_2022-11-02_080527_RTSUnitTemplate.ini
RTSUnitTemplate/Document/Inputs/Input_Backup_2022-11-01_200303_RTSUnitTemplate.ini
RTSUnitTemplate/Document/Inputs/Maps_&_Modes_Backup_2022-11-02_074806_RTSUnitTemplate.ini

__You can download Gameplay_Debugger_Backup_2022-11-02_080527_RTSUnitTemplate.ini and Input_Backup_2022-11-01_200303_RTSUnitTemplate.ini and Maps_&_Modes_Backup_2022-11-02_074806_RTSUnitTemplate.ini from here from github by clicking on top left Code->Download Zip__

Open Unreal Editor. Go to Edit -> Project Settings -> Search for the Specific Input Section: Gameplay Debugger, Input, Maps & Modes
and import the .ini file

You can also find the .ini files in the Plugin Folder "All\Engine\Plugins\SwarmSimulator\Document\Input

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
- UnitBaseAnimInstance (Only used for linking UnitState to CharAnimState)

Characters:
- CameraBase
- UnitBase (This is the Key Element of this Product)

Controller:
- ControllerBase (Should be used to Control the UnitBase)
- UnitControllerBase (This is needed for the UnitBase)

Hud:
- HUDBase

Widgets:
- UnitBaseHealthBar


For ControllerBase, if you want to use the Controller, you have to adapt your Settings (Pictures in "Document/Inputs" Folder), or "Import Keyboard Settings" (topic above).

---

Here is a List of the Classes and there Functions:
(All Variables and Functions are accessible via Blueprint - BlueprintReadWrite or EditAnywhere or Both.)

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
|USceneComponent* RootScene;      				|'Isn't this fun?'            |
|USpringArmComponent* SpringArm;				|-- is en-dash, --- is em-dash|
|Rotator SpringArmRotator = FRotator(-50, 0, 0);     		|'Isn't this fun?'            |
|UCameraComponent* CameraComp;          			|"Isn't this fun?"            |
|APlayerController* PC;						|-- is en-dash, --- is em-dash|
|int32 ScreenSizeX;						|-- is en-dash, --- is em-dash|
|int32 ScreenSizeY;						|-- is en-dash, --- is em-dash|
|float PitchValue = 0.f;					|-- is en-dash, --- is em-dash|
|float YawValue = 0.f;						|-- is en-dash, --- is em-dash|
|float RollValue = 0.f;						|-- is en-dash, --- is em-dash|
|bool RollCamRight = false;					|-- is en-dash, --- is em-dash|
|bool RollCamLeft = false;					|-- is en-dash, --- is em-dash|
|bool ZoomCamOut = false;					|-- is en-dash, --- is em-dash|
|bool ZoomCamIn = false;					|-- is en-dash, --- is em-dash|
|bool ZoomCamOutToPosition = false;				|-- is en-dash, --- is em-dash|
|bool MoveCamForward = false;					|-- is en-dash, --- is em-dash|
|bool MoveCamBackward = false;					|-- is en-dash, --- is em-dash|
|bool MoveCamLeft = false;					|-- is en-dash, --- is em-dash|
|bool MoveCamRight = false;					|-- is en-dash, --- is em-dash|
|float StartTime = 0.f;						|-- is en-dash, --- is em-dash|
|int CamAngle = 0;						|-- is en-dash, --- is em-dash|
	
|Functions (BlueprintCallable)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|void CreateCameraComp();       				|'Isn't this fun?'            |
|void SetViewPortScreenSizes(int x);     			|'Isn't this fun?'            |
|void SpawnControllWidget();       				|'Isn't this fun?'            |
|FVector GetCameraPanDirection();       			|'Isn't this fun?'            |
|void PanMoveCamera(const FVector& PanDirection);		|'Isn't this fun?'            |
|void ZoomIn();      						|'Isn't this fun?'            |
|void ZoomOut();    						|'Isn't this fun?'            |
|void ZoomStop();      						|'Isn't this fun?'            |
|void CamLeft();    						|'Isn't this fun?'            |
|void CamRight();      						|'Isn't this fun?'            |
|void CamStop();   						|'Isn't this fun?'            |
|void CamRotationTick();      					|'Isn't this fun?'            |
|void JumpCamera(FHitResult Hit);    				|'Isn't this fun?'            |
|FVector2D GetMousePos2D();   					|'Isn't this fun?'            |
|void Zoom();      						|'Isn't this fun?'            |
|void ZoomOutToPosition();      				|'Isn't this fun?'            |
|void CamMoveAndZoomTick();    					|'Isn't this fun?'            |
|void ZoomInToPosition();     					|'Isn't this fun?'            |
|void LockOnCharacter(ACharacter* SelectedActor);      		|'Isn't this fun?'            |
|void HideControlWidget();      				|'Isn't this fun?'            |
|void ShowControlWidget();     					|'Isn't this fun?'            |
|void SetUserWidget(APlayerController* PlayerController);      	|'Isn't this fun?'            |
	
	
# UnitControllerBase

|Properties (EditAnyWhere + BlueprintReadWrite)                  	|Note                         |
|-----------------------------------------------------------------------|-----------------------------|
|float SightRadius = 1500.0f;   					|'Isn't this fun?'            |
|float SightAge = 5.0f;		         				|"Isn't this fun?"            |
|float LoseSightRadius = SightRadius + 1000.0f;				|-- is en-dash, --- is em-dash|
|float FieldOfView = 360.0f;		      				|'Isn't this fun?'            |
|float DespawnTime = 1.0f;       					|"Isn't this fun?"            |
|float PauseDuration = 0.6f;						|-- is en-dash, --- is em-dash|	
|float AttackDuration = 0.6f;				      		|"Isn't this fun?"            |
|float IsAttackedDuration = 0.3f;					|"Isn't this fun?"            |
|float AttackAngleTolerance = 0.f;					|"Isn't this fun?"            |


|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|class UAISenseConfig_Sight* SightConfig;    			|'Isn't this fun?'            |
|float DistanceToUnitToChase = 0.0f;				|-- is en-dash, --- is em-dash|
	
|Functions (BlueprintCallable)                  				|Note                         |
|-------------------------------------------------------------------------------|-----------------------------|
|void KillUnitBase(AUnitBase* UnitBase);     					|'Isn't this fun?'            |
|void OnUnitDetected(const TArray<AActor*>& DetectedUnits);     		|'Isn't this fun?'            |
|void RotateToAttackUnit(AUnitBase* AttackingUnit, AUnitBase* UnitToAttack);  	|'Isn't this fun?'            |
|void UnitControlStateMachine(float DeltaSeconds);  				|'Isn't this fun?'            |
	
	
# ControllerBase

|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|bool IsShiftPressed = false;		   			|'Isn't this fun?'            |
|bool AttackToggled = false;					|-- is en-dash, --- is em-dash|
|bool IsStrgPressed = false;					|-- is en-dash, --- is em-dash|
|bool IsSpacePressed = false;					|-- is en-dash, --- is em-dash|
|bool AltIsPressed = false;					|-- is en-dash, --- is em-dash|
|bool LeftClickIsPressed = false;				|-- is en-dash, --- is em-dash|
|bool LockCameraToCharacter = true;				|-- is en-dash, --- is em-dash|
|TArray <AUnitBase*> SelectedUnits;				|-- is en-dash, --- is em-dash|
	
|Functions (BlueprintCallable)                  				|Note                         |
|-------------------------------------------------------------------------------|-----------------------------|
|void ShiftPressed();			   					|'Isn't this fun?'            |
|void ShiftReleased();						     		|'Isn't this fun?'            |
|void LeftClickPressed();						 	|'Isn't this fun?'            |
|void LeftClickReleased();			 				|'Isn't this fun?'            |
|void RightClickPressed();			  				|'Isn't this fun?'            |
|void SpacePressed();				 				|'Isn't this fun?'            |
|void SpaceReleased();				 				|'Isn't this fun?'            |
|void APressed();				 				|'Isn't this fun?'            |
|void AReleased();				 				|'Isn't this fun?'            |
|void JumpCamera();				 				|'Isn't this fun?'            |
|void StrgPressed();				 				|'Isn't this fun?'            |
|void StrgReleased();				 				|'Isn't this fun?'            |
|void ZoomIn();				 					|'Isn't this fun?'            |
|void ZoomOut();				 				|'Isn't this fun?'            |
|void ZoomStop();				 				|'Isn't this fun?'            |
|void CamLeft();				 				|'Isn't this fun?'            |
|void CamRight();				 				|'Isn't this fun?'            |
|void ToggleLockCameraToCharacter();		 				|'Isn't this fun?'            |
|void TabPressed();				 				|'Isn't this fun?'            |
|void TabReleased();				 				|'Isn't this fun?'            |
|void CameraPawnForward();			 				|'Isn't this fun?'            |
|void CameraPawnBackward();			 				|'Isn't this fun?'            |
|void CameraPawnLeft();				 				|'Isn't this fun?'            |
|void CameraPawnRight();			 				|'Isn't this fun?'            |
|void CameraPawnForwardR();				 			|'Isn't this fun?'            |
|void CameraPawnBackwardR();				 			|'Isn't this fun?'            |
|bool IsShiftPressed = false;			 				|'Isn't this fun?'            |
|bool AttackToggled = false;				 			|'Isn't this fun?'            |
|bool IsStrgPressed = false;			 				|'Isn't this fun?'            |
|bool IsSpacePressed = false;				 			|'Isn't this fun?'            |
|bool AltIsPressed = false;				 			|'Isn't this fun?'            |
|bool LeftClickIsPressed = false;				 		|'Isn't this fun?'            |
|bool LockCameraToCharacter = true;			 			|'Isn't this fun?'            |
|TArray <AUnitBase*> SelectedUnits;			 			|'Isn't this fun?'            |


# HUDBase

|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|bool bSelectFriendly = false;   				|'Isn't this fun?'            |
|FVector2D InitialPoint;					|-- is en-dash, --- is em-dash|
|FVector2D CurrentPoint;    					|'Isn't this fun?'            |
|FVector IPoint = FVector(0.f,0.f, 0.f);			|-- is en-dash, --- is em-dash|
|FVector CPoint = FVector(0.f,0.f, 0.f);   			|'Isn't this fun?'            |
|float RectangleScaleSelectionFactor = 0.9;			|-- is en-dash, --- is em-dash|
|TArray <AUnitBase*> SelectedEnemyUnits;   			|'Isn't this fun?'            |
|TArray <AUnitBase*> SelectedFriendlyUnits;			|-- is en-dash, --- is em-dash|
|TArray <AUnitBase*> AllFriendlyUnits;				|-- is en-dash, --- is em-dash|
|bool CharacterIsUnSelectable = true;				|-- is en-dash, --- is em-dash|

	
|Functions (BlueprintCallable)                  				|Note                         	|
|-------------------------------------------------------------------------------|-------------------------------|
|FVector2D GetMousePos2D();    							|'Isn't this fun?'            	|
|void SetUnitSelected(AUnitBase* Unit);    					|'Isn't this fun?'            	|
|void DeselectAllUnits();  	|'Isn't this fun?'            			|'Isn't this fun?'            	|
|void ControllDirectionToMouse(AActor* SelectedUnits, FHitResult Hit); 		|'Isn't this fun?'            	|
|bool IsActorInsideRec(FVector InPoint, FVector CuPoint, FVector ALocation);	| Is used for sharper selection |
|void MoveUnitsThroughWayPoints(TArray <AUnitBase*> Units);			| Is used for sharper selection |
	
# Projectile

|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|AActor* Target;   						|'Isn't this fun?'            |
|class UCapsuleComponent* TriggerCapsule;			|-- is en-dash, --- is em-dash|
|UStaticMeshComponent* Mesh;			|-- is en-dash, --- is em-dash|
|UMaterialInterface* Material;			|-- is en-dash, --- is em-dash|
|FVector TargetLocation;			|-- is en-dash, --- is em-dash|
|float Damage;			|-- is en-dash, --- is em-dash|
|float LifeTime = 0.f;			|-- is en-dash, --- is em-dash|
|float MaxLifeTime = 2.f;			|-- is en-dash, --- is em-dash|
|bool IsFriendly = true;			|-- is en-dash, --- is em-dash|
|float MovementSpeed = 50.f;			|-- is en-dash, --- is em-dash|
	
|Functions (BlueprintCallable)                  				|Note                        			|
|-------------------------------------------------------------------------------|-----------------------------------------------|
|void OnOverlapBegin(class AActor* OtherActor,);    				|Gets Triggered when Projectile hits a Target   |

	
# SelectedIcon

|Properties (BlueprintReadWrite)  		                 	|Note                         |
|-----------------------------------------------------------------------|-----------------------------|
|UStaticMeshComponent* IconMesh;  					|'Isn't this fun?'            |
|UMaterialInterface* BlueMaterial;	         				|"Isn't this fun?"            |
|UMaterialInterface* ActionMaterial;			|-- is en-dash, --- is em-dash|
|UMaterialInstanceDynamic* DynMaterial;		      				|'Isn't this fun?'            |

	
|Functions (BlueprintCallable)                  				|Note                         |
|-------------------------------------------------------------------------------|-----------------------------|
|void ChangeMaterialColour(FVector4d Colour);   				|'Isn't this fun?'            |
|void ChangeMaterialToAction();     						|'Isn't this fun?'            |
	
	
# Waypoint

|Properties (EditAnyWhere + BlueprintReadWrite)                  	|Note                         |
|-----------------------------------------------------------------------|-----------------------------|
|AWaypoint* NextWaypoint;	  					|'Isn't this fun?'            |


|Properties (BlueprintReadWrite)                  		|Note                         |
|---------------------------------------------------------------|-----------------------------|
|USceneComponent* Root;  					|'Isn't this fun?'            |
|UBoxComponent* BoxComponent;					|-- is en-dash, --- is em-dash|
	
|Functions (BlueprintCallable)                  				|Note                         |
|-------------------------------------------------------------------------------|-----------------------------|
|void OnPlayerEnter(AActor* OtherActor)						|'Isn't this fun?'            |
	
	
