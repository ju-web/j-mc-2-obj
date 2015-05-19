# How-To defocus in Blender #

This is a little tutorial showing the method I use for applying a defocus effect in Blender. This is often use to produce a "tilt-shift" effect whose purpose is to make real-life scenes look like they are miniatures. This doesn't make a lot of sense in Minecraft, since the renders usually already look very miniaturish and lego-like, but it's still a cool thing to learn.

You can achieve the same effect using Photoshop, but there you would need to cheat by applying layer masks, etc. In Blender you can do the same thing, only there you can use the actual Z-buffer to calculate exact information for any scene without "cheating" with masks or anything.

## Step 1 - Make a scene ##

Load up Blender, import your map, set up cameras and lights, render everything. Here's what I used:

<a href='http://imgur.com/V4QHX'><img src='http://i.imgur.com/V4QHX.png' width='500' /></a>

## Step 2 - Prepare camera ##

Select your camera in the scene.

Go to the "Object data" (little camera icon) on the side tab.

Turn on "Limits" in the Display section.

Go to side view (shortcut numkey 1) and turn on orthographic view (numkey 5).

Adjust to "Distance" value in the "Depth of field" do that the yellow cross reaches the object you want in sharp focus.

Example:

<a href='http://imgur.com/HdBDW'><img src='http://i.imgur.com/HdBDW.png' width='500' /></a>

## Step 3 - Start Compositing ##

Render your scene one more time.

Increase the size of the lower half of the screen (the one with the timeline).

All the way in the lower left corner of the window is a little icon that allows you to change what is displayed in that part of the window. It says "Editor type" once you expand it and has about a dozen options.

Choose "Node editor" from that list.

On the bottom, you will have several menus: View, Select, Add, Node, and three little buttons. Choose the 3rd one that says: "Node tree type to display and edit: Compositing: Compositing nodes".

The screen will still be empty. You need to check "Use nodes". Two little boxes should appear: Render Layers (the input render) and "Composite" (final result)

Compositing lets you edit the render image similarly to Photoshop, but using the neat nodes UI. You can tweak the image by adding nodes like "Curves" or "Brightness/Contrast" in a chain and playing with them. If you don't like something, you just remove it and keep tweaking until you get an image you are happy with.

To add a node, press shift-A, just like in 3D view to add objects to the scene. Delete by selecting and pressing delete. Zoom-in/out using the mouse wheel. Move using middle-click. Drag nodes using left-click.

## Step 4 - defocus ##

Add a defocus node from the "Filter" section of the add menu.

Connect the Image from the Render Layer with input Image of defocus and connect the Z from the Render Layer with Z of defocus. Connect the output Image from Defocus with Image of Composite.

Check "Use Z-Buffer" in defocus!

Now, if you know something about camera lenses, you will know that F-stop controls the depth of field. The higher the F-stop the smaller the hole of the iris in the lens (f is the inverse of the diameter of the whole), the exposure is longer and the depth of field is greater. Smaller f-stop makes for shorter exposure times, but make smaller depth of field. You can find lots of explanations of this online, but if you have a digital camera, I suggest you test it yourself.

Adjust the fStop to something small. For example, I have a lens with fStop 1.4. 1.2 also exists. 2.0 is a bit more common.

You can play around with the settings a bit more, but the image may look a bit noisy still. Just uncheck "Preview" to get the final result:

<a href='http://imgur.com/XcLcV'><img src='http://i.imgur.com/XcLcV.png' width='500' /></a>