# 2020 Spring - Workshop 1 - Let's Play Basketball! 
##### (RIP Kobe)

Our first workshop of the Spring 2020 semester: build a VR basketball hoop shooting game!

Open up a brand new Unity project and let's dive in!

---

## **Unity Basics**

#### The Hierarchy Window
The Hierarchy Window shows a list of all game objects in the scene, including game objects, camera, etc.

#### The Project Window
The project window displays all assets we have available to build the game with, such as meshes, scripts, materials.

#### The Inspector Window
The Inspector Window is a context sensitive window which shows us the properties of any object we want to see. It also lets us add components to individual game objects.

#### The Scene View
The Scene View is where we are going to visually build the game. It allow us to view the layout before and after running the game.

#### The Game View
The Game View allows us to preview our game in the editor. 

---
## First things first

Open up `Build Settings`, (File --> Build Settings, **Ctrl + Shift + B**) and change your Platform from Windows (or whatever it is) to Android.

Also, click on `Player Settings`, and under the Android settings (little alien guy), go to `Other Settings`

+ Uncheck Auto Graphics API
+ Remove Vulkan from the list
+ Change Package Name to com.[YourOnyen].unity
+ Minimum API Level: Android 6.0 "Marshmallow" (API Level 23)

Under `XR Settings`

+ Check Virtual Reality Supported
+ Add Oculus to the list
+ Check the V2 Signing (Quest)

Close Project Settings, go to the top menu and click on the `Oculus` menu.

Oculus --> Tools --> Remove AndroidManifest.xml
Oculus --> Tools --> Create store-compatible AndroidManifest.xml

## Adding the Oculus Package to your Project

Starting off, the first thing you should do in your Unity Project is add the Oculus Integration package to your Project.
Go to the Asset Store and search for "Oculus".

Then download and import the `Oculus Integration` into your project. Keep in mind that the Oculus Integration is a bit of a big asset, so it'll probably take some time to import.

## Adding your Player

First of all, kill the `Main Camera`. We don't need it.
Now, search in your <b>Assets</b> for "OVRCameraRig". Add it to your scene.

This already allows you to have a controllable player character in your scene!

## Editing your Player

Open up <b>OVRCameraRig</b> and create an Empty GameObject **(Right-click OVRCameraRig, Create Empty)**. Rename it to <b>GameManager</b>.

Inside `GameManager`, add a *SphereCollider* with a *5m radius* and a script called *GrabManager*.

#### GrabManager

The GrabManager allows the user to grab objects at a distance. The two changeable colors are used as described: the first to outline any objects in range you can grab. The second outlines any objects that are grabbable.

### Further Edits in your Player

Open up `TrackingSpace`, and then follow up by opening the `LeftHandAnchor` and `RightHandAnchor`. Now, go down to your *Asset* window and search for "DistanceGrabHand". You will find 2 Gameobjects, one named "DistanceGrabHandRight" and another named "DistanceGrabHandLeft".

Now, add the "DistanceGrabHandLeft" as a child of "LeftHandAnchor" and "DistanceGrabHandRight" as a child of "RightHandAnchor".

### Editing the DistanceGrabHands

Edit the following inside each of the DistanceGrabHandLeft/Right:

#### RigidBody

+ Collision Detection: Discrete --> Continuous Speculative

#### Hand (Script)

+ Animator: None (Animator) --> r_hand_skeletal_lowres (Animator) (or l_hand_skeletal_lowres, for the LeftHand)

#### Distance Grabber (Script)

+ Parent Transform: None --> RightControllerAnchor / LeftControllerAnchor
+ Player: None --> OVRCameraRig
+ Prevent Grab Through: Check --> Unchecked
+ MaxGrabDistance: 2m --> 20m
+ GrabObjectsInLayer: 8 --> 0
+ Obstruction Layer: 0 --> -50

---

Add the assets included in 'Package':

+ CARVR_Basketball Net
+ CARVR_Basketball Ball
+ CARVR_Basketball Court

# OH. MY. GOSH. LOOK AT THAT COURT.

Now, make sure your OVRPlayerRig is inside the court and hit ***PLAY***!

---

## Editing the Scripts

***Sire Shaik will do the honors.***
