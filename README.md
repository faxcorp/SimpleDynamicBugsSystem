# SimpleDynamicBugsSystem
Unreal Engine Marketplace product that generates dynamic bugs that snap to walls and objects and react to repulsion/attraction force (Distance Fields required)
___
[![Watch the video](https://img.youtube.com/vi/tqs-iXqbRAE/hqdefault.jpg)](https://www.youtube.com/embed/tqs-iXqbRAE)


Try packaged game on your machine (Google Drive) https://drive.google.com/file/d/1CbTHzXU_AYn1fQ2CFVrjNvotYBUpOyiB/view?usp=sharing \
This GPU Niagara System uses Distance Fields to create dynamically moving and animated (via shader vertex offsets controlled from texture map) StaticMesh bugs that snap to walls and objects with a possibility to be attracted or repulsed. \
Multiple parameters exposed that control speed, repulsion strength, randomness, number of bugs.\
The attraction/repulsion location and radius are controlled via Niagara Parameter Collection from any actor.\
Distance Fields must be enabled in the game for this effect to work!\
___
![tutorial](https://github.com/faxcorp/SimpleDynamicBugsSystem/assets/37246339/a56f6af9-51f9-43b7-9f92-56bb93852075)
___
1.1 AttractionMultiplier: Multiplies this systems attraction value. Make it negative to invert repulsion to attraction\
1.2 MaxSpeed: Limits the speed of bugs\
1.3 NewPosition: Ignore this one, its used only internally\
1.4 RandomnessInMovement: Makes the movement more random/jittery or unified/fluid\
1.5 Rate: Spawn rate - more = more bugs\
1.6 MoveStopFrequency: makes bugs stop/start moving more or less frequently (less is more with this one, inverted)\
1.7 AmountOfTimeWalking: makes bugs stop and stay for more or less time (range = -1 to 1)\
1.8 SpawnRadius: size of area that the bugs spawn in
___
2.1 Texture specifications:\
  R = In this case I used this channel to make glow mask for the bug, its unused in marketplace product, you can do whatever you want with it\
  G = This channel is used for legs gradient (top = 0, bottm = 1) used for animating leg movement front/backwards\
  B = This channel is a front/back gradient used to offset animation to bring more variation\
  A = Leg pair mask, to make legs move like a true bug and not all legs at the same time\
![bugtexture](https://github.com/faxcorp/SimpleDynamicBugsSystem/assets/37246339/70edf1ef-5111-413d-a2b8-8a03f11781f9)
___
3.1 The niagara parameter collection used for attraction/repulsion force (the names inside the collection are generic as I can't find a way to rename them, if anyone knows, please share, thanks)\
3.2 This is the main Niagara System that you just drag and drop into the level. You can adjust its parameters in the level for each system uniquely, or if you want to modify the bug behaviour globally, adjust User Parameters inside the system. See fig. 3.3\
3.3 ![niagarasystem](https://github.com/faxcorp/SimpleDynamicBugsSystem/assets/37246339/06cf8955-9fc8-40f3-b11f-7b2e58b959fd)
___
4.1 This is the blueprint responsible for setting the Niagara Parameter Collection variables for attraction/repulsion force. In this case I'm just getting the player pawn and adjust the location and size of the attraction force on tick. You might want to change it to something that suits your needs. In my game I used it to make bugs go away from the light of the flashlight that player controls.
___
Thanks!
