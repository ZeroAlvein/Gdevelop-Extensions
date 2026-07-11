Formatter functionality
-


## Adding separators to numbers Formatter::AddSeparator(Number,".")

Imagine you have variable called Score with long number 1234567890 and you would wish to add some kind of separator each 3 digits from right side.  
Not a problem.  

Into action to change text of text object put Formatter::AddSeparator(Your number here,"Your separator here")  
So for example Formatter::AddSeparator(Score,".") and text object will display 1.234.567.890  
Or try Formatter::AddSeparator(Score," -X- ") and text object will display 1 -X- 234 -X- 567 -X- 890  

## Adding blinker to text Formatter::Blinker(Time("sec"),":","")
If you have some in game timer and you want to display for example 15:20 where : actually blink  
Then into change text of text object action put:  
Formatter::Blinker(Your time in seconds, "first blinker" , "second blinker")  
For example Formatter::Blinker(Time("sec"),":","")  

One blinker is visible on 0 2 4 6 8 secs where other is on 1 3 5 7 9  
So if you set one to "" it will look like it shows and disappear  
But you could make fake like spinning cross if you would go with Formatter::Blinker(Time("sec"),"+","x") 

## Displaying ingame FPS Formatter::FPS()

You literally just put that expression Formatter::FPS() into change text action of text object

## Format and add suffix to big numbers Formatter::FormatNumber(Score,".",0,"")

Imagine you have big number and you want anything above 999 to display with suffix like we have 1411 format to 1K or 1.4K or 1.411K  
Even 1.4 k  

For example put this into change text of text object Formatter::FormatNumber(Score,".",0,"")  
If score was 1234 then we gonna get 1K  
If it was 12345 then we gonna get 12K  
If it was 123456 then 123K  
If it was 1234567 then 1M  

Formatter::FormatNumber(Score,"first separator",0,"second separator") If we would display 1.23-k then period. is first separator  
And minus- would be second separator where each you can set to "" to display nothing
