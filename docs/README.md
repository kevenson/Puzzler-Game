# Puzzler Game

The Puzzler is a mobile VR game for Googld Cardboard that is modeled off of the old Simon electronic memory game. In this version, players begin in a dungeon on a mysterious island, and must solve memory puzzles in order to escape.

The puzzles are created with five floating orbs that the user can interact with through gaze-based raycasting--once the orbs display a pattern by lighting up in sequence, the player must match the sequence to proceed.

You can see a quick video of the game being played here:

<iframe width="560" height="315" src="https://www.youtube.com/embed/fuv_00F-f9o" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>

## Outcomes

This was a practice project for me, as I learn to design better VR experiences. The particular emphases here were scaling models in VR, creating the desired mood through lighting effects and sound, UI design and avoiding motion/simulator sickness.

With these goals in mind, the project was a success. I was able to build the game using Unity3D for Google Cardboard on Android, and my user tests (see below) suggest that the game hit all the desired notes.

## Process

The first part of the process was to create a persona for the project--an imaginary person who I thought would be interested in this particular VR app. In other words, the persona is a a way of creating a user for our app before we've even started building it. Since we want to be able to ground our design questions throughout the process on our users and use-cases this is a very important first step.

### Persona

**Bob Loblaw**
*"If you can describe it, I can build it."*

Age: 26

VR Experience: low

Bob Loblaw is a 26 year old male living in Eugene, Oregon and working as a freelance web developer. Most of Bob's clients are US-based (generally small start-ups), and he has been making a comfortable living for the last few years with this business, enough that he was able to quit his day job.

Bob loves experimenting with new technology, and is motivated by emerging trends. He likes to learn new things and to feel that he is "ahead of the curve." Recently he has begun experimenting with virtual reality, in part due to his interest in gaming, but also because he sees it playing a large role in web dev in the relatively near future. His experience is low, and he is mostly experimenting with VR games and reading up on emerging web platforms and standards like AFrame.*

### Sketches

Next in the process we start sketching the environment we're envisioning for the app. I am a terrible sketcher, so my sketches were pretty awful, but that doesn't matter here. The point is to rapidly test your general ideas for the app before you sink a lot of time into building them, in order to rapidly iterate and find the best general design. Once you have that, your sketches become a blueprint of sorts that will help you build your game or other app.

I created several sketches, but this is the one I ended up going with for the Puzzler game:

![Game Sketch](/ProjectMaterials/PuzzleMaster.jpg)

Pretty simple, right? Still, even this very basic sketch helped me make important design decisions down the road.

### Building in Unity3D

[Unity3D](https://unity3d.com/) is a powerful game engine that has become one of the most popular platforms for creating VR experiences. It's free for individuals to download and there are tons of tutorials available online so I would definitely recommend checking it out and experimenting.

For the Puzzler app, we first began with a simple model or prefab that contained the basic elements of the dungeon we wanted to build. Unity makes it very easy to start with components like this and use them to build your project--whether you're using basic models provided with Unity, downloading them, or creating them yourself.

![UnityScreenshot](/ScreenShots/ss3.png)

From here it was a relatively simple (albeit time-consuming) matter to copy and reorganize the components to build the completed structure. I also used Unity's built-in terrain editor and some materials from Unity's [Asset Store](https://www.assetstore.unity3d.com/) to build my mountainous ice-world terrain.

Next up was lighting and sound. Unity has a pretty sophisticated lighting system and it can be tricky to get the hang of (I'm definitely still learning). Going into depth here is beyond the scope of this write-up, but the basic process for mobile VR is to add the appropriate lights to your scene. For example, in this app I used two separate point lights for each of my torches to try to get the right effect:

![UnityScreenshot](/ScreenShots/ss4.jpg)

Once you have those in place, for mobile VR it is also very important to pre-render or "bake" your lighting so that it won't negatively impact performance. The alternative would be to have lighting generated in real-time, which might run fine on a desktop PC that can drive an Oculus Rift, but not so much on a mobile phone driving Google Cardboard.

Sound is incredibly easy to set up in Unity. You really just need to find the appropriate music or audio clips and add them to your scene. This app even uses spatial audio, where audio clips are bound to a particular area in the scene and so the volume will change depending on the player's position. You can read more about [spatial audio for VR here](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).

Unity also supports scripting through C# or JS. This is an incredibly important part of the process, as scripts are what really control the gameplay in your app. Like lighting, scripting is too large a topic to handle in this write-up, but you can find information about it [here](https://docs.unity3d.com/Manual/ScriptingSection.html).

My Puzzler application used scripts in C# to control the UI elements, character movement and interaction with the orbs

![Scripting](https://docs.unity3d.com/uploads/Main/ScriptingIntroPic.jpg)

Finally, the most important part of the project--iteration with the help of our user tests.

## User Testing

User tests are important because they provide you with opportunities to test your work with actual users. A common alternative is to simply use your own impressions and ideas to design your app, but that can often lead to wasted time and poor design decisions. When you user test throughout the design process, you are able to get valuable feedback--actionable information that can help you create an app that will be enjoyed by more people.

The trick is to user test frequently with different aspects of your app, ask good questions (i.e. no yes/no or leading questions), and to use the feedback you receive to help guide your design decisions.

In this project, I did four rounds of user tests, each with one user (for a non-practice project, I probably would have wanted 3-4), covering scale & mood, UI elements, movement, and sound & mechanics, and my findings from each test are summarized below.

##### User Test 1 - Scale & Mood

In my first user test, I simply wanted to determine whether I had an appropriate scale in my app, with the dungeon room not looking too big or small. I had my user try the game, which at this point was just an simple dungeon room with lights and a few objects, using Google Cardboard.

![Game Screenshot](/ScreenShots/ss2.png)

From my test, I learned that the scale seemed about right, but that my user felt a bit taller than usual. That was not surprising considering I had set the height of the camera to around my own eye-height, and my tester is about a foot shorter than me--a good reminder that for VR experiences to truly feel immersive, we need to pay attention to the little details! I also learned that I had set the mood about right--the feedback I received was that it felt dark, creepy and old, which was exactly what I was going for.

--------------------

##### User Test 2 - UI

My second user test was all about the user interface, or UI. For this test I wanted to determine whether the UI provided the necessary information for users to start and restart the game, didn't appear too large or small, and provided a generally pleasant viewing experience.

![Game Screenshot](/ScreenShots/ss1.png)

I had my user try the app again in VR using Cardboard, and asked a simple series of questions for feedback for both the start and end UI panels. Feedback from this test suggested that the UI was configured just fine--no need for revisions.

![Game Screenshot](/ScreenShots/ss5.png)

------------------

##### User Test 3 - Movement

Next up was my user test for movement within the game. This can actually be tricky in VR, since many users don't have controllers to use and certain types of movement in a VR space can trigger simulator or motion sickness in a subset of users (see [here](https://unity3d.com/learn/tutorials/topics/virtual-reality/movement-vr) for more information). There are, of course, a number of movement mechanics that can be used. My general favorite for mobile VR is ground raycasting, where you can manually teleport to locations in front of you using your line of sight.

However, for the Puzzler application, we needed a mechanic that would allow users to move seamlessly (and linearly) through the game, so I used waypoints instead. This way, users began the game at the start point, moved to the "play" position when the hit the play button, and then automatically moved to the "finished" position when they win.

To test this movement mechanic, I had my (new) user test the game and asked another series of questions while he was playing. Thankfully, my game did not cause any nausea or discomfort, and I was also able to discover that the the movements seemed appropriate--they weren't too fast and nothing felt "off".

------------------

##### User Test #4 - Sound & Mechanics

For my final user test, I was interested in getting feedback on the sound and overall game mechanics. The game was nearly complete at this point, so I had my user try it out and asked her a couple questions along the way.

This user thought the game was pretty good. She was able to make it through to the end without any confusion about the mechanics or what she was supposed to be doing, which was good. She didn't like the ambient sound I was using in the exterior of the dungeon, so I swapped this out and tried again later with a new sound that she agreed fit the mood better. She also liked the terrain I had designed, which was very nice to hear!
![Game Screenshot](/ScreenShots/ss6.png)

She also had some nice ideas to improve on the game, like adding new levels and/or new puzzles and making the world more explorable. I'll put these on the list for the next push!

## Breakdown of Puzzler



## Conclusion




Video: https://youtu.be/fuv_00F-f9o
<iframe width="560" height="315" src="https://www.youtube.com/embed/fuv_00F-f9o" frameborder="0" gesture="media" allow="encrypted-media" allowfullscreen></iframe>


My audience is mainly people who would like to learn more about developing VR experiences and are looking for "how-to" information.

Goals:
1. Write-up provides actionable information regarding how to create a simple VR experience,
from start to finish.
2. Write-up explains how to use Google VR to create experience for Cardboard.
3. Write-up provides links for further learning.

Outline:

Intro

Outcomes

Story of the process

User testing outcomes & iteration

Breakdown of final piece

Conclusion

My site: https://kevenson.github.io/UdacityPuzzler/

----DRAFT-----
https://d17h27t6h515a5.cloudfront.net/topher/2016/December/5849eff0_vrnd-course4-example-writeup-structure-000/vrnd-course4-example-writeup-structure-000.pdf
