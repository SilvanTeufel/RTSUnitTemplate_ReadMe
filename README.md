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


