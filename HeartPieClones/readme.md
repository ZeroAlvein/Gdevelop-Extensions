# HeartPieClones<br>  

*Allows you to display frames of animation based on some number at any position in various ways  
For example hearts based on number variable (and more)*<br>  


Check it out in my [Test game](https://gd.games/instant-builds/37b76f97-d5d7-441e-ace8-a6dc0f87da03) try picking up fish.  
That is cool trick to display how many items you gathered.  Move mouse wheel up and down to change number variable (Health)  
Hover cursor over player <('.'< )

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3ae042a9-43d1-46f7-80dd-9ad8ad512e40" />  


When you add Create and animate heart pie clones action, there will be quite few things to configure, and it only looks scary and long.  
But in reality there is not so much to configure and stuff you need to configure is not cryptic.  

<img width="1215" height="89" alt="image" src="https://github.com/user-attachments/assets/e2b1113f-f739-438a-a1d9-35103f0145ab" />  

Also if you have that action open in action window, parameters and descriptions above them will make much more sense.  
And i left some tips to help you adjust it to your needs, and you can click that ? icon in top right to find this page.  

<img width="1198" height="311" alt="image" src="https://github.com/user-attachments/assets/a013b209-6f7d-44a0-83e3-12fb3e5fd147" />


## Configuration  

All images/frames of your clones, need to be added as one animation.  
But you can have multiple animations for different purposes like boss or player 2 or enemies or some pickups (like i did with fish above).  

I have fev animations with different fram count where frames have all fill states i care about.  
Order does not matter (is it going from left empty to right filled or vice versa) cause it can be changed in action.  

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b1f24f0a-852c-4f50-8ddb-7c1328799ab6" />


Let's go with configuration of parameters 1 by 1.  

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9ce65a71-bae9-4646-a483-3cdcbbede217" />

1 - your sprite object  
2 - how many clones you want to create in tottal? And keep in mind you can have multiple lines so if you wanna have one line of 10 and in second line 2 then you type here 12  
3 - profile is like tween identifier, Since you are using same object, but can have different sets of clones, you need to identify them somehow.  
4 - X position where to start from  
5 - Y position where to start from  
6 - pick on which layer to create clones. (if you use in X and Y expression that can accept layer name then in them you put that layer also for example CameraBorderLeft("Base layer", ) where something like Player.X() does not accept layers)  
7 - scale is basically size 1 is image original size  
8 - how many pixels horizontally between each clone  
9 - how many pixels vertically between each clone  
10 - which animation (by number) to use for this set of clones  
11 - how many frames/images animation you selected in #10 have  
12 - if your frames start by empty on left and fill them up in right direction, here you can reverse that order, or do it on purpose to fake with variable 
increasing something loosing hearts or charges (for example having boomerangs and displaying how many do you still have in your possesion)  

<img width="1213" height="512" alt="image" src="https://github.com/user-attachments/assets/2d4041b0-beda-4f29-ae1e-0cdfcde334e1" />  

13 - in what orientation clones will be created
14 - in which horizontal direction create new clones from starting postion (ones in #4 #5)  
15 - in which vertical direction create new clones from starting postion (ones in #4 #5)  

> That is only confusing part of this configuration that need in depth explanation. Imagine like you wanna display two horziontal lines of clones at cursor position so at #13 set it to horizontal. Now in #14 if you set it to reight they will go from cursor position into RIGHT. But if you set it to left all clones will be created LEFT from cursor. Now in #15 if you set down then 2nd line will be BELOW 1st line, and if you set it to UP 2nd line will be created ABOVE 1st line.  

16 - flip image of each clone horizontally?  
17 - flip image of each clone vertically?
18 - this will determine after how many clones create new line in direction you set in #14 #15  
19 - here you put your health variable (can be expression for behavior for example from health behavior)


Few examples

A - created in top left corner of screen going into right direction with 2 lines of clones  
B - same as above but at top right corner going into left direction  

<img width="1333" height="216" alt="image" src="https://github.com/user-attachments/assets/3a2a957e-a6bd-4906-83df-385caae230a7" />  

C - created on left side of screen little above vertical center with two lines of vertical clones into right direction  
D - same as above just created on right side and going into right direciton  

<img width="1339" height="200" alt="image" src="https://github.com/user-attachments/assets/4bd7753e-1762-4707-9152-87dca1dcf21e" />

Here we have bottom ones (skills) from my test game  

<img width="1205" height="183" alt="image" src="https://github.com/user-attachments/assets/3dc1faee-be4e-4f25-991e-a2b1d5c3d2b2" />


And here something more advanced.  
That is how i made ones you see when you hover cursor over player.  

<img width="1889" height="574" alt="image" src="https://github.com/user-attachments/assets/db78d8ab-e205-44ef-88ff-de53991c4214" />

I am adding to scene variable (ActualNumber) when cursor is on player and subtracting when its not. Then i am setting opacity of clones with profiles i wanna target to that variable. And now they show/hide with kinda like fade in/fade out effect.<br>  

## Selecting specific clones for whatever  

If you want to do something to clones outside of extension you need to pick them this way.  

<img width="1174" height="169" alt="image" src="https://github.com/user-attachments/assets/39f0aa65-6bf7-4f5c-8ecd-fbf240c2db1d" />

This condition allows you to target ones with specific profile but you will still need to use repeat for each object.  

There is also delete clones action if you need it for whatever reason.

That's pretty much it.
Enjoy <('.'< )
