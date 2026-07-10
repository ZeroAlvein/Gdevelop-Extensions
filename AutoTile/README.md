## AutoTile Guide

After you download AutoTile.json you need to open gdevelop click on burger icon in top left to open side panel, and hit + next to extensions.  
Now on bottom you will hit import extension and import AutoTile.  
Next you will add tilemap object and go to behaviors add new one and in search bar type Autotile and just add it.

First thing first.  
We will need some image editor i will go with Aseprite but [Libresprite](https://libresprite.github.io/#!/downloads).

Is its free earliler version which have all the feautres we need.  
In fact any image editor will be fine but Libre/Asesprite have grid support and that helps A LOT.

Before we go we need to establish some names  
Tileset - colection (set) of your tiles that will build your object  
Tilemap - object in gdevelop that will use this extension and draw your tiles based on your tilesets  
Tile - part of tileset that will be build unique part of your image (for example bottom right corner)  
Sub tile - 1/4 part of whole tile  
Tile atlas/atlas image - image containing all your tilesets

Ok let's go

## Step 1.1
# Creating our tileset

Let's take some existing one which is this made of 9 tiles and each tile size is 16. I go to Vew > Grid > Grid Settings and in X and Y i put 16.  
(Which i upscaled 4 times)

<img width="192" height="192" alt="image" src="https://github.com/user-attachments/assets/e21ecfb8-8621-470c-8b59-7d78b95b6550" />

And we have it on nice blue grid which show us each tile.

<img width="612" height="603" alt="image" src="https://github.com/user-attachments/assets/0af6ae2a-c41f-4920-8db5-5630078c32af" />


But if you pay attention, some parts of it actually repeats. like always white cat head is in bottom right corner and dark one is always in top left.  
And here is all magic behind it, we can re use these parts and build ONE tile from 1/4 parts of other tiles.  
So in reality we only need unique 1/4 parts of each tile, And now we gonna reduce it to 8 tiles (which in fact will be 24).

1st i went back to Vewi > Grid > Gid setting and in whatever i put in X and Y i divided by 2 so i had there 16 i divide it by 2 and we get 8.  
Now repetition is A LOT more visible.

<img width="460" height="428" alt="image" src="https://github.com/user-attachments/assets/8918f080-5140-41a2-8efd-bd95a461db6a" />

Now magic happens.  
Both rows show what you need to do, but bottom one is color coded so you know where each sub tile goes.  
A - your 9 tiles with grid of tile size divided by 2
B - you only take color codded sub tiles form A  
C - here you put them together so they use up less space  
D - copy each corner sub tile (blue) and paste them together in top left then copy all 4 center sub tiles and paste them in top right  
Top left sub tiles are what create your SINGLE tile in game, so instead of it looking like 4 corrners put together.  
You can give it unique look by editing thse 4 sub tiles.  
I will demostrate it later
Top right sub tiles are called inner corners but we gonna get into that in next step.  

<img width="1296" height="726" alt="image" src="https://github.com/user-attachments/assets/4825d315-44c7-4cf5-a125-98ec0b2be1d5" />


## Step 1.2
# Creating inner corners

