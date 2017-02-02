# Marionette VR

As the name implies, this is about playing around with marionettes in VR.

Read up about it [here](https://medium.com/p/6b596620c3ca/)

## Requirements

* Oculus Rift + Touch, or Vive
* Unreal Engine 4.14
* Visual Studio installed
* [VICO Dynamics plugin](https://www.unrealengine.com/marketplace/vico-dynamics-plugin). (It's unfortunately pretty expensive for an Unreal plugin, but the results are well worth it.)

You should be able to open the .uproject file and run it.

## Adding your own marionettes

* Open up `BP_Marionette`
* Click the skeletal mesh component and replace it with your own mesh

If your mesh uses a different skeleton than the Unreal default skeleton, you'll also have to:

* Make sure your skeletal mesh has a physics asset associated to it with constraints set up (look at `Mannequin/Character/Mesh/SK_Mannequin_PhysicsAsset` for reference)

* Inside `BP_Marionette`, take a look at the components called `LeftHandRope`, `RightHandRope`, `RightFootRope`, `LeftFootRope`, `HeadRope`. They have a property called `bone name` in them, and make sure to change that to reflect the bone structure of your own skeleton.

Optional: You can tweak things like rope width and length in the components mentioned above.

## Key files

### Hands
Unreal doesn't support the Oculus Avatar SDK yet, so I had to fake how the hands and gestures are done. You can find those in MarionetteVR/Core/Hands, with the blueprint called `BP_Hand`.

The pawn is at `MarionetteVR/Core/VR_Pawn`. It listens to trigger/grip presses from the controllers, and passes that along to `BP_Hand`.

### Maps
The default map is `Theatre`. There is also a map called `Creepy` inside `MarionetteVR/Maps`. You should check it out ;)

### Marionettes
All the marionette stuff is in `MarionetteVR/Marionette`. The `BP_Marionette` is the main blueprint for it, and `BP_Nub` represents the little tab/nub that you use to drag individual string around.


