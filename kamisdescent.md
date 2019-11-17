<h1>Kami's Descent</h1>

***

## About
*Kami's Descent* is a game prototype created using UE4 as part of my MSc in Games Software Development. Working as a team of five 
(me, another coder and three artists), we were given 10 weeks to design and develop the prototype using Scrum practices. The final result was shortlisted in the GameRepublic Student Showcase 2019.

The game centres around Kami and an elemental Wisp, who must work together to solve puzzles, evade traps and collect the gems to progress to the next level. Both characters have different abilities, and are controlled simultaneously by a single player.

The aim of the project was to develop a short tutorial level, to introduce the player to the main mechanics of the game. As of yet, there are no plans to take the project further, but it contains some novel techniques that could be helpful in future projects.

***

## Design
One of the core elements of Kami's Descent is the collaboration between Kami and the Wisp. Kami can activate pressure pads and collect gems, but he can be harmed by traps and cannot traverse large gaps. The Wisp, on the other hand, is immune to physical damage and can glide across gaps with ease. However, the Wisp's ethereal nature prohibits them from picking up items and interacting with physical switches. Instead, their only means of interaction is through special light pads that are activated when the Wisp is near.

One character cannot survive without the other: the player needs to use both simultaneously in order to complete the level. To further enforce this connection, the game also features a darkness mechanic, where Kami must remain within the Wisp's light to survive. If Kami is away from the light for too long, his health will deplete and he will eventually die. 

This forces the player to keep both characters close at all times, and opens the door for interesting kevel design. For example, one puzzle featured in the tutorial is a maze with rotating walls, which can block Kami from the Wisp's light. This adds tension and puts pressure on the player to solve the maze before time runs out and Kami dies.

***

## Challenges

### Unclear Design
One issue which plagued the early stages of the project was the lack of a clear design for gameplay mechanics and the goals of the project. Many of the design ideas were conceived and developed during the first few weeks, which slowed the project down and did not permit much time for designing the code prior to implementation. In light of the restricted development time and the rapid iteration of ideas, it was decided that the game would be entirely scripted using UE4 Blueprints and rewritten in C++ at a later time.

Halfway through the project, it was decided that instead of controlling one character at a time, the player should be able to control both characters simultaneously with one controller, *à la* 'Brothers: A Tale of Two Sons'. This capability is not readily provided by UE4, which required a workaround to implement, and demanded a fundamental change to the structure of the character blueprints and camera scripts, in order to keep both characters visible during play. 

In spite of these difficulties, I managed to develop a workable solution to meet these requirements and produce a working prototype, but the game remained scripted in Blueprints for the rest of the project.

### One Controller, Two Characters
Part of UE4's architecture stipulates a one-to-one relationship between characters and controllers. The <code>PlayerController</code> class is an abstraction of player input, mapping button presses to a <code>Pawn</code>'s response, such as moving, firing etc. Whilst a <code>PlayerController</code> can be assigned to a different <code>Pawn</code>
at run-time, it cannot serve multiple pawns simultaneously, which was problematic for our design.

To workaround this, I chose to give both Kami and the Wisp their own respective <code>PlayerController</code>s as components of the player's main <code>PlayerController</code>, adding a layer of indirection between player input and character actions. When the player presses a button, the main controller accepts this input and forwards it to the intended character's <code>PlayerController</code>, which processes the input and effects the desired character action.

***

## Gameplay trailer

