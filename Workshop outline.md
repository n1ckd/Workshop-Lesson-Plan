# workshop outline
## Process overview 
	1. Desiging for different situations / materials / manufacturing methods
		- conception, modeling, prototype, testing, revisions
	2. research can affect your designs pretty heavily so designing with the intention of making revisions or iterations is important.
	3. showing sketch file, open fusion lets jump in!
## Fusion Menus and controls
	1. rough breakdown of fusions interface - the components we will need for todays lesson are :
	2. The toolbar at the top from left to right:
		- workspaces - today we will be staying in the design workspace but if you ever do any kind of machining or rendering in fusion that is where you'd go to access those tools. There are different tools available under each tab in each workspace 
		- show workpace change when starting a sketch to show 
	1. run through components, sketches, bodies, joints etc in the browser or outliner on the left - its an overview of everything in this project and it allows you to organize and select / hide aspects of the file while you work - this shouldnt be super surprising to see if anyone heres used photoshop or any adobe software its pretty similar. 
	2. Run through origin & View cube
		1. itll let you change your view point to see your workspace from different angles its convienet and can be faster than like shift + middle mouse especially if you dont have a proper mouse.
	3. Right click menu - something I dont actually use a whole lot but as you get more comfortable with it im sure its really useful.
	4. the timeline will list the design history as long as your capturing design history and working parametrically - this is one of fusions biggest strengths in my opinion, it will let you go back and change aspects of your design after you test a prototype - the parametric design features in fusion are some of its biggest strengths. 
	5. Anothe big strength of fusion its its access to libraries - you can leverage mcmaster carrs inventory to your advantage or you can access online libraries to get accurate recreations of common components to then work off.
## Setting up our reference 
---
Insert your reference image or just start from measurements, whatever you prefer - This is gonna be pretty hard to get exact if you are working on something more complicated than this you will likely be able to mind some more robust data sheets or drawing files that you can work off of. So just get it close and work with it off to the side. 
	1. At the top of the toolbar, towards the right side you'll see a little blue picture that says insert under it. Opening that dropdown or pressing the picture will let you use the **place canvas** tool.![[Pasted image 20240416182428.png]]
	2. You will be prompted find the file go to **insert from my computer** and find the "servoSplines.png" file you downloaded with the rest of the repository. 
	3. You should now see the canvas tool on the right side of your screen - this is where most tool windows will appear and it will allow you to have a much more granular control over a tool. We now need to select the face we want our canvas to be on - for this project this won't matter a whole lot but I'll be selecting the XZ plane (the bottom one between the red and blue axes). 
	4. After selecting the plane your canvas should appear - this is where you now will scale and position your image to your liking to work off of. the changes I made to mine are as follows:
		1. rotate the image by **90°** on the **Z axis** 
		2. change the **XY scale** to **5.25**
		Once we finish moving the canvas we can select OK. and your screen should look something like this:
		![[Pasted image 20240416212504.png]]
## Drawing Basics
---
After placing our reference we can now start sketching!
1. We are gonna start our design by recreating this A15T Servo Spline so we can mount are pincer onto the end of the servo and use its rotational force to drive an additional pincer. Lets begin by pressing **Create Sketch** in the top left of the screen. 
2. You'll notice the tools in the toolbar have changed - this is fusion giving you access to tools relevant to the workspace your currently in - the same would happen if we were working on a surfaces or mesh. While in this sketch we can only make changes and use reference from things that exist when we press the new sketch button. This is where the timeline comes in handy - you can move things around or revisit steps to make changes to models later down the line.
3. The main tools we are gonna use in the sketch workspace live under **Create & Modify** - right now another tool that's good to know is **inspect** it'll allow you to take measurements from point to point in your design if somethings not clear- we don't need to worry about the other tools for today. 
  ![[Pasted image 20240416220727.png]]
## Starting our first Sketch
---
The main tools we are gonna use in the sketch workspace live under **Create & Modify** - right now another tool that's good to know is **inspect** it'll allow you to take measurements from point to point in your design if somethings not clear- we don't need to worry about the other tools for today. 
  ![[Pasted image 20240416220727.png]]

 My overall idea was to have one driving pincer that will take the rotational force from a small hobby servo to open and close. So we need a way to attach our driving pincer to the servo.
1. To start I'm going to take the measurement we have from our reference image (**3.9mm**) and make a circle with that as its diameter, to do this we're gonna go to **Create -> Circle -> Center point circle**. We are going to click on the center of the origin to start the circle and then we can type 3.9mm into our measurement box, clicking again to lock it in. 
- We can do the same to make another circle for the inside of the teeth- its roughly **3.2mm** in diameter. After this you should have something that looks like this: 
  ![[Pasted image 20240416214730.png]]
- Next we are gonna make an **Offset** on our exterior circle to make the outer wall of our mount - we are using an offset so that if we change the exterior circles diameter the thickness of our mount will remain the same and just scale off the changes we make. To do this we can either go to **Modify -> Offset** or **press O** then clicking the exterior circle will prompt us to enter a offset number - we can just go with the default **1 mm.** 
- Next up we have the teeth of our mount to make - we are gonna do this by making one tooth and then making a circular pattern of them to round out our mount. To make our one tooth we are gonna need to **make two lines going from the center of our circles to the outside** - **the first of which can be a strait 90 degrees** and the second can be anywhere for now. To make our lines we can go to **Create -> Line** or **press L**.
- After we've placed our two lines we are going to do some math to figure out how far apart these teeth need to be spaced - its a 15 tooth gear meaning our **360°/15 = 24** so one tooth will take up **24°** tip to tip - we are going to cut that in half because we only need to model half of the spike so **24°/2 = 12°**.
- Our second line we placed randomly needs to be 12° off of our straight 90° line so we can use the **Dimension Tool** to constrain the two lines together. we can go to **Create -> Sketch Dimension** or **Press D** then click the 90° line and our second line type 12 and press enter. We should be left with this:
  ![[Pasted image 20240416220039.png]]
- This looks correct so we can connect our two lines to create the profile of the tooth, to do this **add another line from the corner of our intersecting lines to the other corner following the reference image.** This is all we really need to make our mount - but to make our lives easier I'm going to tell you about a different type of line in Fusion - **Construction Lines**. Construction lines are basically lines that do not interfere with profiles of sketches and only exist to be used as reference or measurements. We are going to make some of our lines construction lines to make extruding this profile easier. 
- We are going to **make everything except the circle that makes the outside of our mount, the diagonal tooth line we drew, and the line at 12° a construction line**. You can make lines construction lines by clicking them in the sketch and **pressing X** or by using the menu on the right. You should now have something like this:
  ![[Pasted image 20240416221903.png]]
- This will let us mirror our diagonal line to make the other half of our tooth profile. Go to **Create -> Mirror** then select our diagonal line and our 12° line , these are the lines we want mirrored. After we have those selected we need to tell fusion what we want it mirrored over - select the 90° line. You should end up with this:
  ![[Pasted image 20240416222602.png]]
- This is technically all we need to make our mount but to make our design a bit more future proof we can **trim** some lines out and create **fillets** to round our teeth out. We can use the **Trim tool** by **pressing T** or going to **Modify -> Trim** I would trim four lines - the two 12 lines and the interior arc lines of our tooth. You should now have this:   ![[Pasted image 20240416223112.png]]
- We now have the profile of our tooth! We can get ready to extrude the profile by pressing the **Finish Sketch** button in the top right, this will take us out of the sketching tool menu and bring us back to the default design workspace. You should now see a Sketch named 'Sketch 1' under the 'Sketches' menu on the left.
  ![[Pasted image 20240417001514.png]]
## Extrusions and Making Bodies
---
- We can now **Extrude** the profile we made in that sketch by **pressing E** or by going to **Create -> Extrude**. After we are in the extrude tool we can select our tooth, this will highlight it blue - then under the distance option in the menu on the right we can enter how long we want the extrusion to be - I'm going with **5mm**. You should now have something like this:
  ![[Pasted image 20240417003255.png]]
  - This is one piece of our mount - to make the rest we are going to **make a circular pattern** with our new object. Patterns can be drawn in sketches or performed as a operation on a object (the benefit of doing it this way is we can always revert it with our timeline tool). We are going to go to **Create -> Pattern -> Make Circular Pattern**, then we are going to select our body for the "object" field and our Y axis for our axis of rotation. We are going to need 15 copies of this tooth to make our mount. You should have this on your screen:    ![[Pasted image 20240417004445.png]]
  - After we have our extrusions we need to join them together to make one object - we are going to do that with the **Combine** Tool this is going to be under **Modify -> Combine** and we are just going to select all of the bodies in the menu on the left then press ok to join them together. It should now look like this:    ![[Pasted image 20240417004545.png]]
  - Because we are still testing the fit of our teeth out we can round our edges with **Fillets** we can **Press F** or go to **Modify -> Fillet**. We can then select the points of our edges of our teeth and set a radius that we think looks good, I'm going with .**1mm** for my edges. 
![[Pasted image 20240416211600.png]]
This is a stopping point I want to make sure everyone's up to speed here and take some time to answer any questions people have before starting the next piece of our model.

## Adding our pincer or actuator
- Now that we have our mounting method finished we can start creating the rest of our gripper, we are gonna need to make a actuator that transfers the rotational force of our mount to the rest of our gripper - this sounds more complicated that it really is. We are gonna start by opening up our sketch 1 again and adjusting the offset we made to give us some more space to work with. I'm changing the **1mm offset to 10.55mm** giving our base a diameter of **25mm** which should give us some more space to work with