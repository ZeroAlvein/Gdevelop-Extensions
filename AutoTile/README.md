## AutoTile Guide

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

# Section 1.1 Creating our tileset


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


# Section 1.2 Reducing our tileset

Now magic happens.  
Both rows show what we need to do, but bottom one is color coded so we can tell where each sub tile came from.  
A - our 9 tiles with grid of tile size divided by 2  
B - we only take color codded sub tiles form A  
C - here we put them together so they use up less space  
D - we copy each corner sub tile (blue) and paste them together in top left then copy all 4 center sub tiles and paste them in top right  

Top left sub tiles are what create our SINGLE tile in game, so instead of it looking like 4 corrners put together.  
We can give it unique look by editing thse 4 sub tiles without affecting how rest of tiles will look.  
I will demostrate it later so do not worry.
Top right sub tiles are called inner corners but we gonna get into that in next sectiion.  

**PRO TIP #1**  
In Ase/Libresprite when you have selected selection tool (top most tool in tollbox on right).  
You can either double LEFT or MIDDLE mouse button click on any tile on that blue grid to select it.  
If you hold LMB/MMB on 2nd click you can drag it to expand grid selection, and then when holding shift add more to selection.  

**PRO TIP #2**  
In Ase/Libresprite when you have some selection, you can hold shift and press arrow keys to move it on your grid.  

<img width="1296" height="726" alt="image" src="https://github.com/user-attachments/assets/4825d315-44c7-4cf5-a125-98ec0b2be1d5" />


# Section 1.3 Creating inner corners

Best to explain what inner corners are is by looking at tiles placed in cross shape  

<img width="1295" height="694" alt="image" src="https://github.com/user-attachments/assets/5315ef8c-b249-47be-b91a-f977ef65827d" />

If you look at center tile then all sub tiles don't match.  
That is why we need to edit it ourselves so it look natural. Let's zoom that in.  
Before on left and after editing on right.  
<img width="1340" height="590" alt="image" src="https://github.com/user-attachments/assets/4f8abbde-8c64-46e9-8330-11481fc333d3" />


Easier to spot it is on tileset that is thinner and have clear pattern. We only focus on RED/ORANGE colored tile.  

A - top right tile (4 inner corners sub tiles) is just our center tile. we need to take edge tiles and put them in shape of cross  
B - after having cross shape we put inner corners tile in center it totally do not fit  
C - we simply adjust it to our needs, so it looks like each corner perfectly fit each arm  
D - we put back our inner corners tile into top right spot  

<img width="1297" height="740" alt="image" src="https://github.com/user-attachments/assets/b89711aa-8f3d-483b-bfd4-0e4967f17886" />

And now you learn the full layout of each tileset.  
Top left tile = single tile  
Top right tile = our inner corners tile  
And what is below is our walls + corners + center tiles  


# Section 1.4 Creating tileset from only center tile

Since we grasp the concept of this system, this will help us understand how to start from actual scratch.  
We gonna go with 2 patterns. Top one is for brick wall and bottom is for wood planks bridge.

A - we make our pattern on center tile that will repeat all over other tiles  
B - then we copy that tile into all 8 adjacent tiles  
C - and we create frame (think like wall edges) in case of bricks its easy to think of it as dugeon walls, where wood planks for bridge is a bit tricky
D - finally we 1st copy/paste B onto D then C onto D and we get nice 9 tiles shape
E - using method from section 1.2 we reduce our tileset


<img width="1583" height="718" alt="image" src="https://github.com/user-attachments/assets/fcfe0f17-8090-4807-a5f8-7989978c89b1" />

Now if i hide grid and zoom in a little bit, you will notice that center tile don't match our tileset.

<img width="644" height="742" alt="image" src="https://github.com/user-attachments/assets/732ded9a-4b8a-4d9c-883c-95fcb8d22ea1" />

That is expected for some tilesets, cause this way its easier to create new tilesets with method i explained above.  
Some tilesets with more even pattern will look perfectly fine.  
For example we gonna try with trees now (same goes for mountains/spikes and stuff that will connect in that way).  

A - we create just a single tree  
B - now we copy/paste it 3 times so we have 4 trees in total  
C - we paste one tree between bottom trees and one sub tile space below them  
D - lastly we paste two tiles at very bottom, and that's it

<img width="1333" height="624" alt="image" src="https://github.com/user-attachments/assets/475a97f6-bd8f-4e1b-9af9-7244bcfbe7e6" />


And ingame it will look like this (i have green background on my trees)

<img width="545" height="545" alt="image" src="https://github.com/user-attachments/assets/1ee6c2b4-33a7-4c74-ab00-df8a3f4e9996" />

# Section 1.5 Adjusting our tileset  

Look i made this tileset.  

<img width="389" height="541" alt="image" src="https://github.com/user-attachments/assets/be760c3a-2a00-4143-8054-ec5a84fb155a" />


But i don't like how single tile looks, and the fact that if i make cross shape it goes inwards.  

<img width="980" height="677" alt="image" src="https://github.com/user-attachments/assets/94a05e30-334f-433f-b75d-1cdcc7ac190f" />

Believe or not we can fix it.  
To fix single tile, we just editing top left tile on our tileset.  
BUT for for fixing it going inwards we can do simply swap position of each wall sub tiles on their axis.  
I literaly just swapped their positions nothing more.  

<img width="539" height="769" alt="image" src="https://github.com/user-attachments/assets/928c4f95-3f87-47c1-9cab-d00ef2414ec8" />

And result is, old on top and new on bottom.  

<img width="834" height="757" alt="image" src="https://github.com/user-attachments/assets/b1f18eaa-a78d-4655-a706-3f252ffb5341" />

Be aware this trick won't work for every single tileset, and some sets will need manual adjusting.

# Section 1.6 Understand which sub tile is what part of actual tile

We gonna use 1st tileset you saw in this guide.  

<img width="342" height="508" alt="image" src="https://github.com/user-attachments/assets/c76a9405-5008-4d10-b3e9-0e4db8af6960" />

And here we go.  

<img width="1294" height="710" alt="image" src="https://github.com/user-attachments/assets/b199e62d-b7bc-4925-a780-58775a198386" />

On bottom i marked in red rectangle whole tiles built from 4 sub tiles, and we see that always yellow sub tile is in upper right corner of tile.  
Dark blue will always be in top left corner fo tile and so go on.  

<img width="850" height="685" alt="image" src="https://github.com/user-attachments/assets/472df9a8-8cf7-4103-bdbe-bc0a16f4694a" />

ONLY exception here are center sub tiles, but as i explained earlier it's cause this way it will be easier to create new tilesets.  

<img width="1126" height="554" alt="image" src="https://github.com/user-attachments/assets/892b41ca-1e24-4949-86a9-05874b24b7ca" />

# Section 1.7 Side view (platformer) tilesets  

So far we seen tilesets that fit topdown games or background. But what about platformer games for example we wanna platform?  
Have no fear papu zero is here.  
Remember our 1st tileset we used to learn how this system work?  

<img width="192" height="192" alt="image" src="https://github.com/user-attachments/assets/e21ecfb8-8621-470c-8b59-7d78b95b6550" />

We literally only need to draw platform on top sub tiles.  
Pay close attention to inner corners sub tiles. They are just extension of platform without outline.  

<img width="1011" height="610" alt="image" src="https://github.com/user-attachments/assets/c8118e67-4920-41f7-8f78-fc14f5f67bf1" />

Result ingame  

<img width="843" height="742" alt="image" src="https://github.com/user-attachments/assets/52208b2b-0331-42e8-b458-37c12486a3bf" />


# Section 1.8 Known limitations  

FENCES all kind of them, there is no way around making it proper with this minimalistic tile count.  
Here we have few fecenes tilesets.  

<img width="1026" height="382" alt="image" src="https://github.com/user-attachments/assets/0c1c2909-890b-4a4e-ab9c-c2f79db28c41" />

Nothing will fix them having that gap if you place 4 of them next to each other.  
But drawing them in straight lines will look perfectly fine.  
Where other limitation is the repetition. We cannot spread vertical pieces horizontally neither horziontal ones vertically.  

<img width="1443" height="845" alt="image" src="https://github.com/user-attachments/assets/17ce5195-a2bc-47ce-863b-2ba02098bdea" />

So in other words, you can draw fences only as hollow shapes empty inside, or you gonna get visual bug you see at bottom row.  
Last column should help you visualise what i did.  

# And that is all the logic behind creating tilesets.  
# EVERY SINGE TILESET will follow same exact logic. If your tileset look odd ingame it means you did not follow these rules.  


# Section 2.1 Multiple tilesets in atlas image

After we created our tileset we may want to have more. And my extension support multiple tilesets.  
This is my tile atlas image.  

<img width="448" height="240" alt="image" src="https://github.com/user-attachments/assets/4f0f294e-eabe-40dc-9ee9-0a261ebcfa8a" />

You simply place them next to each other.  
It does not matter will you have more vertically or horizontally, extension will auto detect it.  
You can even have just one vertical or horizontal strip of tilesets and it will still work.  

Only rule you need to follow is fill your sets from left to right then next row down.  
And as you see i am missing few tilesets and that is in purpose so you can learn you don't need to have even amount of tilesets.  
On top of that you can even skip empty tilesets ingame when switching between them but i will explain it later.  

# Section 2.2 Propper size  

Your atlas image needs to have proper size for everything to work. This whole extension is just bunch of math.  
I did use trim option in Ase/Libresprite and it cut out 1 pixel too much from right side of canvas.  
In result i was unable to select last tileset, and i wanted to report it as a bug when i realized issue is with the image itself.  

# Section 2.3 Changing size of your tile atlas image  

IDK if it is a bug or just how engine works, BUT each time i changed size of my tile atlas image i needed to:  
- go to scene editor  
- double click my tilemap object  
- and press APPLY  

Otherwise my image was not update for new size and i could not select new tilesets.  
Image itself if i draw anything on it was updated normally, but changing its size required steps i mentiond above.  
Just so you are aware what to do after you change dimensions/size of your tile atlas image.  

# Section 3.1 Setting up tilemap object

In tilemap object we need to do 3 things (4th is optional).  
A - name properly our tilemap object (later you gonna wanna have background tilesets object tilesets and stuff like that so propper naming is crucial)  
B - My tileset is made of 16 x 16 tiles and what i need to put in tile size is 8 cause 16 / 2 = 8 so we need to put there size of our sub tiles  
C - select our tile atlas image with our tilesets  
D - we can click here on our tiles and they will be marked in red to indicate which are colliders. And so they will work with seperate two object action and object is in collision with tilemap object but also work as platform if we add to it platform behavior.  

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b175ff63-42cd-4e3a-9a27-efce90a61a2b" />

# Section 3.2 Adding and setting up AutoTile extension to tilemap object

A - we click on burger icon in top left  
B - then + next to extensions  
C - import extension button  

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/45d00dac-ec4c-4cfa-a8b9-783845764abd" />

Next we double click our tilemap object and go to behaviors tab. Here we click Add a behavior and in search bar we type auto and add AutoTile.  

<img width="1004" height="359" alt="image" src="https://github.com/user-attachments/assets/0f7e2de8-cfbe-4a7e-a58d-a54328b5d309" />

Here all we need to do is put same exact number in Tile size as we put in tilemap object properties tab (we did it in section 3.2).  

<img width="1245" height="363" alt="image" src="https://github.com/user-attachments/assets/f48a022b-19b0-4c6c-88ff-89706472f178" />

This option "Enable AutoTile" needs to be checked for tiles to auto connect.
This extension have save/load functionality i will explain later, and its so it work properly with tilemap objects which you would use in normal way.  
Where each tile is one image of something for example decorations or whatever.  These most likely should not auto tile.  

# Section 4.1 Managing our tilemap via events sheet  

Tilemap object is like canvas on which you can paint your tiles, so 1st we would need to drag our tilemap object into our scene.  
But then it gives us nothing we would also need to draw any tile at top left and bottom right corners (or top right and bottom left).  
That is how we establish our canvas. But there is nothing for us to be allowed to draw tiles beyond our canvas.  
But we can change position of our tilemap object, and there is action for tilemap object to change its row and column count.  
In other words we can set our canvas in events sheet and i strongly suggest you do that.  

We have ehre bunch of my events that create and properly set up my tilemap object in my scene.  

<img width="1408" height="195" alt="image" src="https://github.com/user-attachments/assets/9678176b-a8c5-493a-8eae-6d8694da70f8" />


# Section 4.2 Painting our tiles

My events for managing tilesets via event.  
Going from top to bottom:  
1 - is for removing all tiles from selected tilemap object  
2 - when holding shift we snap SOME object to tilemap grid in case we need better indication of of where we gonna place tile, and we hide actual cursor  
3 - we do oppposite to what we did in 2 if shift is not pressed  
4 - this will update ALL tiles in selected tilemap **BE AWARE THE BIGGER TILEMAP YOU HAVE AND MORE TILES ON IT THE LONGER IT WILL TAKE SO LAG!!!**  
5 - use this action to create tile at whatever position you want. You can use X and Y pos of object you use in snap object to grid action from #2  
Additionally it have 2 parameters. One where you see NumberVar that is where you put number which determine which set you want to use so it makes more sense to have there variable which value you can change on the fly. And one on end which says NO. If its set to yes it will update only one tile, and will try to connect it to any adjacent tile even if that tile is from different set. Where if its set to NO it will update all adjacent tile from tile at position you create tile, but will connect only sets to their own sets but not to others  
6 - simply removing tile from current position  
7 -  is the same as #5, but as you see instead of setting it in events you can put there boolean variable to switch it on the fly  

<img width="1678" height="506" alt="image" src="https://github.com/user-attachments/assets/d8492a93-c0a5-48c6-b837-b7701e9782af" />

