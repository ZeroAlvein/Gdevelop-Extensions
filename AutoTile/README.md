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
Tile data - ID's and position of all your tiles on your tilemap object  

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

Also there is no way at this moment to give each tile different Zorder so all tiles of each tilemap object will have its Z order.  

Then there comes animated tiles. Which are possible, but not in this extension since it aims for having multiple tilesets.  
And adding additional tiles with animations would generate ultra huge atlas image.  
But then we would face the isuse of checking each tile each frame and updating them, which we could narrow down to tiles that are on screen.  
Still it would be very performance unfriendly.  

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
In 95% of cases you want to have it set to NO  
6 - simply removing tile from current position  
7 - is the same as #5, but as you see instead of setting it in events you can put there boolean variable to switch it on the fly ingame  

<img width="1678" height="506" alt="image" src="https://github.com/user-attachments/assets/d8492a93-c0a5-48c6-b837-b7701e9782af" />


# Section 4.3 Switching tilesets ingame

Missing sets variable is how many sets i am missing (like i told you earlier that was made on purpose and this way we combat it).  
With:  
Q - we subtract 1 from NumberVar so we switch to previous tileset
E - we add 1 to NumberVar so we switch to next tileset
You see in ther actions expression that returns number of sets your tileset have TilemapName.AutoTile::SetsCount()  
And it will loop around your tilesets perfectly fin on its own  
C - we toggle boolean variable to control do tilesets should connect to other tilesets or not  
In section 4.2 point 7 i explained that  

<img width="1774" height="307" alt="image" src="https://github.com/user-attachments/assets/e6e5ded4-f653-4df3-bd74-86df026e682d" />


And that is pretty much it. You are ready to use AutoTile as you please.  
You can even try it in my [Test Game](https://gd.games/instant-builds/e127d524-9f91-4d49-b5dc-986cae7f1e09)


# Section 5.1 Saving/Loading our tilemap tiles to and from JSON file

One of best feeature this extension have is to save/load all your tiles.  
But we are not talking as custom level editor for your players.  
Nah we are talking here about YOU as game creator creating your levels/maps/backgrounds/platforms/decoratiions and whatever else INGAME.  
Then you export all that to a file and put it inside your project folder and now all your users will play level you made.  
Did you click my Test Game link above? You see all these trees water mountains and stuff?  You think i did it in scene editor? You would be wrong.  
I did it in game and exported my tiles to .json file then simply imported it in game and loaded at beginning of scene.  
Exact same way as you would import audio file.  

## BUT SAVING (exporting file) ONLY WORKS ON DESKTOP  
Unfortunately for any other version saving will not work. Where loading will.  

There is alternative since my extension have built in saving/loading to and from storage.  
So you could use firebase to export your tiles and then load them when needed but that will make game require internet connectivity.  
Other half way solution is to open your cloud project on desktop app and import all json files you need so they are stored on cloud.  
And then you could continue to work on whatever version you have.  

BUT you can import json file into your cloud project via google drive or one drive. So you could have many dummy/empty json files in your project.  
Name them properly and save to tile data to them this way.  
YET do not ask me how exactly i never dealt with cloud stuff and i try to stay away from it.  

Ok let's go.  

This is actually pretty straight forward there are 2 actions one to save to json and one to load from json.  

<img width="1444" height="275" alt="image" src="https://github.com/user-attachments/assets/710fea6f-e309-4c93-8830-bcce643c3447" />

JSON files save with this naming YourSceneName + YourTilemapObjectName + "Text you input manually can be empty if you leave it with just "" " + .json.  
So if i have scene called Castle and tileset called Decorations and i leave text empty then i gonna get on my desktop file named CastleDecorations.json.  
Text is there in case you have many extenral layouts but only one game scene and you side load them to change level.  
Then you could put in that text for example ToNumber(GameSave.CurrentLevel) and now your file would be named GameSceneDecorations1.json.  
And now all we do is take our newly created json file and put it in some folder in our project folder, then just select it in load action.  

<img width="719" height="386" alt="image" src="https://github.com/user-attachments/assets/55f85529-a096-4fad-a070-2c0fb0fde603" />

# Section 5.2 Saving/Loading our tilemap tiles to and from storage

This open doors for any1 who is not using desktop app to saving tile data into json file that is in your project resources.  
But i lack the knowledge how to even manage google or one drive. IDK how file loading works into project from them.  

Anyway saving/loading to and from storage is also straight forward. You just provide name of Storage and Group.  
Think like this:  
Storage = main folder
Group = sub folder of main folder

<img width="1490" height="220" alt="image" src="https://github.com/user-attachments/assets/ecd6be38-848b-4024-8b84-e2c0f2583d17" />

At this can be also used as custom level editor for your players so they can design their own levels.

# Section 6.1 Connecting tilesets paramter in create tile action

Imagine we are making topdown game then it would most sense to have 2 tilemaps or 3 but let's go with 2.  
For example one for ground/dirt paht/water/lava/mountain walls and whatever else you can think off.  
But then having 2nd tilemap object with tilesets for trees/flowers/mountains/buildings/town walls/houses and whatever else.  
We would create kinda like 2 layer system so tiles from one tilemap do not affect tiles form other tilemap.  
BUT if you have huge tilemap you start to look for ways to fake it having more than it looks like.  
Again link to my [Test Game](https://gd.games/instant-builds/e127d524-9f91-4d49-b5dc-986cae7f1e09)  

I used there ONE tilemap object and only these tilesets  

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/65e0a440-8c75-472a-a12c-c2e32a2f502b" />

Now look i will press Q to switch to tileset #58 and draw rectangle worth of 2 tile size.  

<img width="1083" height="668" alt="image" src="https://github.com/user-attachments/assets/da0731bc-e551-4e66-b233-246311819605" />

Then i switch to tileset #55 and i will draw solid green tiles inside inner part of that rectangle  

<img width="976" height="679" alt="image" src="https://github.com/user-attachments/assets/c3356ea1-537a-4cbd-964c-7be7c45c4ceb" />

And now i press C to enable tiles connecting to tiles from different tilesets and draw lines on inner walls we gonna get.  

<img width="979" height="832" alt="image" src="https://github.com/user-attachments/assets/b934a08a-ff4e-4e3d-be97-ed9a85bd34a4" />

And that is exaclty how i created that whole layout/leve whatever you name it. That you see when you launch my test game. 

<img width="1918" height="1024" alt="image" src="https://github.com/user-attachments/assets/01215b70-13f3-4a3a-8ea0-462657a717e8" />  

I want to point out here again that using 2 tilemaps and splitting tilesets between them would make much more sense.  
Cause as you see i needed to paint green backgroudn on my sets for everything to match, but if i would have there transparent color and two tilemaps.  
I could put for example trees on any sufrace would it be grass or dirt path or whatever even on water.

There are plenty of creative ways to achieve cool looking levles.  

# Section 6.1 using two tilesets to fake height

I simplified meaning of it, but due lower count of unique tiles in tilesets you will need to use multiple tilesets to create some shapes.  

For example we want mountain walls that indicate higher elevation or building walls that looks like actual walls with something on top.  

<img width="1545" height="768" alt="image" src="https://github.com/user-attachments/assets/d726d00a-257f-42d1-a347-cb9721a62cb1" />

What you see here are 4 tilesets actually. On left these 2 sets where right one is top and bottom one is one from the left painted two lines below 1st one.  

<img width="612" height="441" alt="image" src="https://github.com/user-attachments/assets/532611a8-98e8-41fb-9c65-a428a0702b8c" />

Where shape on right are last two tilests from tile atlas image following same logic.  
You could even fake shadows this way.  

<img width="735" height="544" alt="image" src="https://github.com/user-attachments/assets/24b9de73-9c8e-4676-9982-d025b49ba536" />

That is all you need to know to use this extension and AutoTile yoursef.

Enjoy <('.'< )  
De Ent
- 
