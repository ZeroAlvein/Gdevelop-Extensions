## AutoTile Guide

After you download AutoTile.json you need to open gdevelop click on burger icon in top left to open side panel, and hit + next to extensions.  
Now on bottom you will hit import extension and import AutoTile.  
Next you will add tilemap object and go to behaviors add new one and in search bar type Autotile and just add it.

First thing first.  
We will need some image editor i will go with Aseprite but [Libresprite](https://libresprite.github.io/#!/downloads) is its free earliler version which have all the feautres we need.  
In fact any image editor will be fine but Libre/Asesprite have grid support and that helps A LOT.

Before we go we need to establish some names  
Tileset - colection (set) of your tiles that will build your shapes ingame  
Tilemap - object in gdevelop that will use this extension and draw your tiles bsed on adjacent tiles to each tile  
Tile - part of tileset that will build unique part of your image (for example bottom right corner)  
Sub tile - 1/4 part of whole tile  
Tile atlas/atlas image - image containing all your tilesets

Ok let's go.

# Step 1.1 Creating our tileset


It's easier to understand how it works by using existing tileset with some pattern, where each tile have same exact pattern (its called bitmasking), so let's take some existing one which is this made of 9 tiles and each tile 16 pixels.  
I go to Vew > Grid > Grid Settings and in X and Y i put 16 px (Using Asperite/Librespirte).  
(I upscaled 4 times so its more visible).

<img width="192" height="192" alt="image" src="https://github.com/user-attachments/assets/e21ecfb8-8621-470c-8b59-7d78b95b6550" />

Original image if someone needs it <img width="48" height="48" alt="image" src="https://github.com/user-attachments/assets/e65c7bb1-694c-458c-b4c0-20c447a5ed19" />


And we have it on nice blue grid which show us each tile.

<img width="612" height="603" alt="image" src="https://github.com/user-attachments/assets/0af6ae2a-c41f-4920-8db5-5630078c32af" />


But if you pay attention, some parts of it actually repeats. like always white head is in bottom right corner on each tile and dark one is always in top left.  
And here is all magic behind it, we can re use these parts of each tile and build ONE tile from 1/4 chunks of other tiles (sub tiles).  
So in reality we only need unique 1/4 parts of each tile, And now we gonna reduce it to 8 tiles (which in fact will be 24 sub tiles).

1st i went back to View > Grid > Grid setting and in whatever i had in X and Y i divided by 2 so i had there 16 i divide it by 2 and we get 8.  
Now repetition is A LOT more visible.

<img width="460" height="428" alt="image" src="https://github.com/user-attachments/assets/8918f080-5140-41a2-8efd-bd95a461db6a" />


# Step 1.2 Reducing our tileset

Now magic happens.  
Both rows show what we need to do, but bottom one is color coded so we can tell where each sub tile came from.  
A - our 9 tiles with grid of tile size divided by 2  
B - we only take color codded sub tiles form A  
C - here we put them together so they use up less space  
D - we copy each corner sub tile (blue) and paste them together in top left then copy all 4 center sub tiles and paste them in top right  

Top left sub tiles are what create our SINGLE tile in game, so instead of it looking like 4 corrners put together.  
We can give it unique look by editing thse 4 sub tiles without affecting how rest of tiles will look.  
I will demostrate it later so do not worry.
Top right sub tiles are called inner corners but we gonna get into that in next step.  

**PRO TIP 1**  
In Ase/Libresprite when you have selected selection tool (top most tool in tollbox on right).  
You can either double LEFT or MIDDLE mouse button click on any tile on that blue grid to select it.  
If you hold LMB/MMB on 2nd click you can drag it to expand selection, and then when holding shift add more to selection.  

**PRO TIP 2**  
In Ase/Libresprite when you have some some selection. You can hold shift and now press arrow keys to move it on your grid.  

<img width="1296" height="726" alt="image" src="https://github.com/user-attachments/assets/4825d315-44c7-4cf5-a125-98ec0b2be1d5" />


# Step 1.3 Creating inner corners

Best to explain what inner corners are is by looking at tiles placed in cross shape  
<img width="1008" height="706" alt="image" src="https://github.com/user-attachments/assets/d6f97bc6-626d-4f1a-9313-3687e676d076" />


If you look at center tile then all sub tiles don't match.  
That is why we need to edit it ourselves so it look natural. Let's zoom that in.  
Before on left and after editing on right.  
<img width="1835" height="843" alt="image" src="https://github.com/user-attachments/assets/a200d54b-56d0-4939-9401-b41be6ebc1c2" />

Easier to spot it is on tileset that is thinner and have clear pattern. We only focus on RED/ORANGE colored tile.  

A - top right tile (4 inner corners sub tiles) is just our center tile. we need to take edge tiles and put them in shape of cross
B - after having cross shape we put inner corners tile in center it totally do not fit
C - we simply adjust it to our needs, so it looks like each corner perfectly fit each arm
D - we put back our inner corners tile into top right spot

<img width="1308" height="717" alt="image" src="https://github.com/user-attachments/assets/49e62fe4-384c-4b8f-a8c8-b653538888b2" />


And now you learn the full layout of each tileset.  
Top left tile = single tile  
Top right tile = our inner corners tile  
And what is below is our walls + corners + center tiles  


# Step 1.4 Creating tileset from only center tile

Since we grasp the concept of this system, this will help us understand how to start from actual scratch.  
We gonna go with 2 patterns. Top one is for brick wall and bottom is for wood planks bridge.

A - we make our pattern on center tile that will repeat all over other tiles  
B - then we copy that tile into all 8 adjacent tiles  
C - and we create frame (think like wall edges) in case of bricks its easy to think of it as dugeon walls, where wood planks for bridge is a bit tricky
D - finally we combine our B and C with removing anything from B if it goes beyond C
E - using method from step 1.2 we reduce our tileset


<img width="1583" height="718" alt="image" src="https://github.com/user-attachments/assets/fcfe0f17-8090-4807-a5f8-7989978c89b1" />

Now if i hide grid and zoom in a little bit, you will notice that center tile don't match our tileset.

<img width="644" height="742" alt="image" src="https://github.com/user-attachments/assets/732ded9a-4b8a-4d9c-883c-95fcb8d22ea1" />

That is expect for some tilesets, cause this way its easier to create new tilesets with method i explained above.  
Some tilesets with more even pattern will look perfectly fine.  
For example we gonna try now with trees now (same goes for mountains/spikes and stuff that will connect in that way).  

A - we create just a single tree  
B - now we copy/paste it 3 times so we have 4 trees in total  
C - we paste one tree between bottom trees and one sub tile space below them  
D - lastly we paste two tiles at very bottom, and that's it

<img width="1333" height="624" alt="image" src="https://github.com/user-attachments/assets/475a97f6-bd8f-4e1b-9af9-7244bcfbe7e6" />


And ingame it will look like this (i have green background on my trees)

<img width="545" height="545" alt="image" src="https://github.com/user-attachments/assets/1ee6c2b4-33a7-4c74-ab00-df8a3f4e9996" />

