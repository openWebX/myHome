# myHome
Homeautomation made easy

I am relatively new to the topic "home automation", but i really tried most of the tools out there, FHEM, openHAB, Homeassistant, ...
The (for me!) best matching tool is home assistant, but it lacks a lot of features i would like to have:

- Getting rid of the need to edit yaml-Files (should always be an option, but not the only one!)
- Nice interface...
- Better GUI for automations. A workflow-editor like "automate" for Android would be the "creme de la creme"... But also better "grouping" and more dsipeying options would be great.  
- A "fire and forget" system. Meaning, once set up, the system scans the local network and finds nearly all of the hardware it can handle and preconfigures it for you. 

What i have so far:

The current code consists of two base parts: 

- The "server" developed in nodejs. It does the main background work: Its running a cron-like system to spawn a crunz-taskmanager, it get mqtt-messages and raises different events based on the topics

- The "main" system. This one is developed in php >7.2x. 
- The frontend will be using the slim framework with twig templates and semantic UI... But hey... Should be no problem to build another frontend, as most "communication" will be done by mqtt!
- The crunz tasks use the main libs here, they do the main background-jobs: scanning the network for devices, scanning special devices (e.g. the fritzbox, the mediaplayers, the hue or lightify bridges for new lights, the nuki bridges for locks, ...), getting the states of those devices (and their subdevices) and publishing them by mqtt
- There is a possibility to define new "services" e.g. bulding a service that gets the current fuel-prices, your bank account saldo, ... Those will be easily integrateable in the frontend. 

The absolute base of the system is "The Thing"... Every scanned pc, every mobile phone, every bridge will be initiated (and used) as a "thing"-Object. These objects have built in persistance. That means once used they store their last states in a db when closed... Things hava some basic attributes like "name", "type", "state" and can define parents or children (think of e.g. the nuki brigde as a thing, the nuki lock as another thing and they map by parent-/children-attributes). The state is also important... States are own objects. The basic state can be 0 or 1, then there are other states that override it, e.g. "OnOff", "LockedUnlocked", "NULLorValue"... 


WHAT I NEED: a cool frontenddeveloper! I am not a designer. I can do all the jobs in the background and provide the data, but i really need someone to develop a nice, clean, easy to use frontend!
