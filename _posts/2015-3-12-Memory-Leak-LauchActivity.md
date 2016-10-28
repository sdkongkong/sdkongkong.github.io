---
layout: post
title: Found a memory leak at LaunchActivity
---
* Occasional,i found LaunchActivity when i was using MAT, you can see LaunchActivity on the screenshot

 <br  />
<img  src="https://raw.githubusercontent.com/sdkongkong/sdkongkong.github.io/master/images/20150312/matbeforechange.png">
<br  />
I also found the memory usage is really hign in Heap

 <br  />
<img  src="https://raw.githubusercontent.com/sdkongkong/sdkongkong.github.io/master/images/20150312/heapbeforechange.png">
<br  />
* Check the code，carefully focoused on  Handler , Thread,  then i found a line of code is suspicious
<br  />
*   apply  the  appid for a thrid library which is for speech recognize
<br  />
SpeechUtility.createUtility(this, "appid="+getString(R.string.voice_app_id));
<br  />
* this line of code was in  custom Application class，it should be ok with this there， but someone moved it to LaunchActiviy, and still using "this",that would make the application always keep the Activity's reference.
<br  />
then i change it to
<br  />
SpeechUtility.createUtility(this.getApplicationContext(), "appid="+getString(R.string.voice_app_id));
<br  />
*then check the Heap ad MAT
<br  />
the MAT after fixing
<br  />
 
<img  src="https://raw.githubusercontent.com/sdkongkong/sdkongkong.github.io/master/images/20150312/matafterchange.png">
<br  />
*the heap after fixing
<br  />

 

![Screenshot](https://raw.githubusercontent.com/sdkongkong/sdkongkong.github.io/master/images/20150312/heapafterchange.png)
