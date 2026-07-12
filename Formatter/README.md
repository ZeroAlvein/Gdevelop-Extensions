# Formatter functionality
<br>  

*All expressions goes into change text of text object action.  
To have separators empty leave them with ""*  
<br>  

## Adding separators to numbers  
> Formatter::AddSeparator(Number,"Separator")  
<br>  

In `Number` put your number variable.  
In `Separator` put what kind of separator you want to use.  

For example we have variable called Gold with value 1234567890 and we want to turn it into 1.234.567.890   
> Formatter::AddSeparator(Gold,".")
<br> 

How about not . period as separator but , comma instead so we get 1,234,567,890  
> Formatter::AddSeparator(Gold,",")
<br> 

Maybe space for separator? So we get 1 234 567 890  
> Formatter::AddSeparator(Gold," ")
<br>  

## Display FPS
> Formatter::FPS()  
<br>   

## Format and add suffix to big numbers  
> Formatter::FormatNumber(Number,"First Separator",Decimal,"Second Separator")
<br>   

In `Number` put your number variable.  
In `First Separator` put what kind of separator you want to use. (For example "." will show 1.1)  
In `Decimal` put how many decimal digits you want to see. (For example 2 will show 1.11M and 3 will show 1.111M where 0 will show 1M)  
In `Second Separator` put how many decimal digits you want to see. (For example "" will show 1.1K but " " will show 1.1 K)  

We have variable Money with value 98765 and we want to get 98K
> Formatter::FormatNumber(Money,"",0,"")  
<br>   

Let's turn 98765 into 98.7K
> Formatter::FormatNumber(Money,".",1,"")  
<br>   

Let's turn 98765 into 98.7 K so we get space between our number and suffix (K)
> Formatter::FormatNumber(Money,".",1," ")  
<br>   

Maybe turn 98765 into 98.76-K so we get - minus between our number and suffix (K)
> Formatter::FormatNumber(Money,".",1,"-")  
<br>   

## Format your ingame time  
>Formatter::GameTime(Hour,Minutes,Seconds)  
<br>   

This expression allows you to format time.  
Useful if you made in game time flow and you want to display it in nice format. But will also format normal actual time Time("").  

You need to add action to control formatting of your game time  

<img width="1842" height="558" alt="image" src="https://github.com/user-attachments/assets/addcad15-a593-485d-a76d-a6e26737e3ad" />

`Time format` can be 12H or 24H  
`Length` allows you to choos do you wanna display only hour or hour: minutes or hour: minutes :seconds  
`Separator ON` and `Separator OFF` will show/hide each second set one to ":" and other to "" and it will fake blinking  
`AM Suffix` and `PM Suffix ` allow you to set what you want to see in 12h time on end "" would be nothing "PM" or "pm" you choose  
<br>  

## Pick random word from string of words   
>Formatter::RandomWord("Text,Text,Text","Separator")  
<br>   

Leave `Separator` as "" empty  
And it will use ,commas as separator  
> Formatter::RandomWord("Text,Text,Text","")
<br>   

Set your own separator to use it to separate words 
>Formatter::RandomWord("Text+Text+Text","+")
<br>   

We have string of words for example Cow Dog Cat Shark   
And we want to pick random one from it   
>Formatter::RandomWord("Cow,Dog,Cat,Shark","")  
<br>   

We wanna do the same but with words separated by ?  
>Formatter::RandomWord("Cow?Dog?Cat?Shark","?")
<br> 


## Display your device time in various formats
> Formatter::Time(Number1,Number2,Separator ON, Separator OFF)  
<br>  
  
In `Number1`  
0 - will display hours with extra 0 in front if its below 10, so if it's one digit  
1 - will display hours without extra 0 even if its one digit  
2 - will display hours with extra 0 in front if its below 10, and AM/PM suffix on end  
3 - will display hours without extra 0 even if its one digit, and AM/PM suffix on end  
  
In `Number2`  
0 - will display only hours  
1 - will display hours : minutes  
2 - will display hours : minutes : seconds  

In `Separator ON` and `Separator OFF` put in one ":" in other "" for it to blink each second
