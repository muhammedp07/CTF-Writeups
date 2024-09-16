# Black Letter by Avillia (ijctf)
So without wasting anytime, we will be on work :)

**i already uplaoded the png image provided by a chall**

![bl](https://user-images.githubusercontent.com/83280644/126889408-f40b8f55-d301-41d0-9a27-5dc229b8cb02.png)

Here is the chall description, no doubt the chall is good and pretty handy...but, well we will be movin on ^^

well, after downloading the message.png file we saw that the png is corrupted

so i decided to start Bless hex editor (you can simply install it using "sudo apt-get install bless"

now i see, everything is okey with png header, IHDR and IDAT chunks.

later on, i see if we try to open the message.png image it will show us that IHDR length is invalid .

i checked it with pngcheck

![pg](https://user-images.githubusercontent.com/83280644/126889606-15eddad5-a458-4db8-834d-6178154bb022.png)

well IHDR lenght is invalid 

after researching  on google, i come up with some tools which can help us in correcting the lenghts

there are many available tools, But here i will be specifically mentioning about pchunk_info by hanasuru ^^

you can download it by pasting this command on your terminal xD

```git clone https://github.com/hanasuru/pchunk_info.git```

aftewr downloading it we can simple run it with ```python2 pchunk_info.py -h``` '-h' will provide you a better help ^^

![pgm](https://user-images.githubusercontent.com/83280644/126890225-f6f405a8-b6c1-4ae0-a918-e8e607e88a5e.png)

running the command with ```python2 pchunk_info.py message.png --fix-crc```
will fix the chunk CRC's

pretty simple right? xD (thanks to hanasuru for the tool ^^)

will be getting a fixed.png image in which crc are already fixed. better!

now if we try to open the fixed image what will see is 

![fix](https://user-images.githubusercontent.com/83280644/126890318-cb673bb5-7bff-4d24-83c9-229c1230803f.png)

**the order of fctal and fdat are not in sequence***

if you have read the chall description than you better know it...
the description says that monochrome images are **scrambled**

what we have to do is now we will be putting the fctal and fdat chunks in proper sequence ^^ (yes i know it sounds simple but, it isn't :') )

for that we will be using tweakPNG tool

after opening the fixed image in tweakPNG 

![tweak1](https://user-images.githubusercontent.com/83280644/126890423-57781c03-0a28-4b80-8e56-f4584f223ebd.png)

we see the sequence number is scrambled 

![scra](https://user-images.githubusercontent.com/83280644/126890462-23300ba2-f60a-4d89-a6be-ae087a04e5e7.png)

well we can arrange them in proper sequence by alt+up and alt+down but unfortunately it won't work, i wasted a great ammount of time in this :(

what will do is, we will arrange it by cut/paste. yes you heared it right with cut/paste

will find the seq_no 1 cut it and paste it after seq_no 0
like that we will be doing for all 0 to 80 xD

yes, it is annoying and time taking but, worth doing it :D

done arranging? yes i guess ^^

better, almost done

now after saving it we can see the flag but wait...its an apng image like an animated png image
we can seperate it with some online tools or you can use 'apngdis'

for apngdis ```apngdis fixed.png``` command will work.
However, we can use ezgif online tool 

here is the link ^^
https://ezgif.com/split

upload the fixed image we saved from tweakPNG

and split it to frames xD

BOOM YEAH!

![ij](https://user-images.githubusercontent.com/83280644/126891444-621fa4d5-27d7-47ab-9274-ed16279bd211.jpg)


i know pretty tough in arranging the seq but isn't is worthy?

well you have your flag now...^^

__________________________________________________________________________________________________________________________________________________________________

*Thank you for spending your precious time in reading my Writeup xD*

**NOTE:** do ignore the mistakes of mine i havent wrote much writeup's before :)

For Further issues or questions you are more than welcome to contact me :D
https://github.com/7evnZer0

will meet soon with a new Bang!👊

till than, Have a great days ahead! :D

### FAREWELL ✍️
 
**Regards**











