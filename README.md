UPNPAudioPlayer
===============


What is it ?
------------
It's an application that plays audio that is controlled via UPNP ("Universal Plug and Play") - designed to run on a Raspberry PI


What do I need to use it ?
--------------------------
* A UPNP Media Server to stream the content.
* A UPNP control point
* A Raspberry PI to run it on that has networking + audio configured. I've used the Debian Squeeze + Raspian distributions.


What's a UPNP Media Server and Control Point ?
----------------------------------------------
Take a look at the docs directory


How do I build and use it ?
---------------------------
It requires the GUPNP and GStreamer libraries to be installed. To do this under Debian :

sudo apt-get update
sudo apt-get -y install libgstreamer0.10-0 libgstreamer0.10-dev gstreamer0.10-tools gstreamer0.10-doc
sudo apt-get -y install gstreamer0.10-alsa gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-base-doc gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-good-doc gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-doc gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-doc gst123
sudo apt-get -y install gupnp-tools libgupnp-1.0-4 libgupnp-1.0-dev libgupnp-doc
TODO : Also needs the uuidgen utility 

To make the app
cd UPNPAudioPlayer/src
make spotless ; make

To run it :
./audio_player

TODO : To make the install package


What audio formats does it support ?
------------------------------------
UPNP Audio Player uses GStreamer to play the audio stream. So if your audio format is supported by GStreamer it should work. If not it won't.
TODO : point in the code to update formats


How do I tell if GStreamer Supports format X
--------------------------------------------
Use the "gst123" app we installed above. For example :
gst123 file:///home/pi/mytrack.mp3


I don't get any audio output from my PI. What do I do ?
-------------------------------------------------------
For the PI's audio jack try :

sudo modprobe snd-bcm2385

At the time of writing quality isn't great. I'm sure the wonderful PI folk will sort this out over time.

USB :
Have a look at the "my-setup" in the docs directory

HDMI : 
No idea. Look at the PI forums.


I can't build it - what do I do ?
---------------------------------
Check you've installed the dependencies above.
What does "gupnp-binding-tool --help" give you? make sure /usr/bin is in your path. If it is - have you installed the dependencies above ? 
Do you see a "/usr/include/gupnp-1.0" directory ?
How about "/usr/include/gstreamer-0.10" ?
What does gst123 --help do ? 
Can you build anything ?  cc -v ?


Will it run on other linux machines?
------------------------------------
I would think so, but I've not tried.


How do I find it more ?
-----------------------
There's some more information in the documents directory.



Enjoy !



Mark.

