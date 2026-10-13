 Report: Augmented Reality Game 
1. Introduction 
Augmented Reality (AR) combines virtual objects with the real physical environment 
through a mobile device camera. Unlike traditional mobile games that are limited to a 
flat screen, AR allows players to interact with digital content using movement, camera 
direction, real surfaces, and spatial positioning. This creates a more immersive and 
interactive experience.

2. Original Game Overview: Space Shooter   
Space Shooter is a simple arcade shooting game where the player controls a 
spaceship and destroys enemy ships while avoiding attacks. Enemies appear in 
waves and the player must survive while scoring points.  
The Core Mechanics include, control a player spaceship, shoot enemy ships, avoid 
enemy bullets, destroy all enemies, protect the player ship, gain points for enemy 
kills, while shooting be careful of the dangerous space objects floating around, if you 
hit does explosion happens then game over, win by surviving and clearing enemies 
The core essence of Space Shooter is: defending against enemy attacks, shooting 
hostile ships, surviving waves of enemies, protecting the player ship, increasing 
tension during combat, and achieving a high score.

3. AR Conversion Design 
Options Considered 
Tilt Controls, Camera Aim + 
Gaze Shooting 
The player tilts the phone in 
an x and y position avoid 
the enemy’s bullets while, 
aiming at the enemy ships, 
uses the mobile camera as 
the aiming system. 
Enemies appear in AR 
space in front of the player. 
A crosshair is shown at the centre of the screen. When the player looks at an enemy 
for a short time, a circular indicator fills, then the weapon fires automatically. 
Hands-free shooting. Encourages player movement and repositioning. Clear lock-on 
feedback, Fast enemies are harder to target and requires steady camera tracking 
                                  
5. Player Interactions:  
Interaction 
5. AR Game Design. 
Environment: 
The battle area is placed on a detected real-world flat 
surface, a table. The player ship remains positioned 
near the player while enemy ships orbit and move 
around the battlefield. 
Trigger 
Tilt movement 
Feedback 
Accelerometer 
Camera aiming (gaze) 
Ship moves in real space 
Phone translation 
Lock-on & auto-fire 
Crosshair at screen  
Gaze on enemy for 1.2 sec Fill circle, colour change, 
then bullet 
Physical repositioning 
Move the phone around 
table 
Restart game 
Ui button 
Change viewing angle 
Reload scene 
7. Leveraging AR Strengths 
The AR version of Space Invaders explicitly leverages the following AR-specific strengths 
that the original 2D game could not offer: 
• 3D spatiality: The game world exists in three-dimensional AR space on a real 
surface. Players can walk around the table and view the alien formation from any 
angle, which changes the tactical situation. An alien that appears to have cover 
from one angle may be exposed from another. 
• Physical world as game environment: The table the marker is placed on becomes 
the game arena. The player's real physical position relative to the marker 
influences the gameplay. This creates genuine embodied engagement that 2D 
games cannot replicate. 
Thembalethu Nsele     225615037                                    
• Camera as weapon: The phone camera is both the AR display and the gun. The 
player aims by moving their body and the device, not by pressing a directional 
button. This collapses the separation between the player's body and the in-game 
avatar. 
• Gaze interaction: Using gaze lock-on for shooting is a uniquely AR-appropriate 
mechanic. In the real world, people aim tools with their eyes before firing. Gaze 
shooting replicates this natural behaviour digitally, which is impossible in a non
AR context. 
• Meaningful movement: In the original game, movement is a mechanic the player 
must actively slide the cannon to dodge. In the AR version, movement is 
embodied the player physically steps sideways, crouches, or move the phone 
around to gain better angles or avoid incoming fire. 
8. User Experience Considerations 
The game was designed to remain simple and intuitive. 
• Crosshair always visible, there is never ambiguity about what will be targeted. 
When the crosshair rests on an enemy, it changes color from white to red to 
confirm lock-on is active. 
• Health bar and score visible 
• Persistent HUD: Score and lives are displayed on a screen-space Canvas overlay 
that remains visible regardless of where the player moves or looks. The player is 
never without game state information. 
• Sound effects for shooting and explosions 
• Start, win, and lose panels guide the player 
• Distinct bullet colors: Player bullets are bright yellow. Enemy bullets are bright red. 
Color contrast ensures immediate recognition and allows the player to respond to 
incoming fire. 
• Start panel gate: The game does not begin until the player deliberately taps the Start 
button. This gives time to set up the marker on a surface, position the device, and 
orient before gameplay begins 
9. Technical Implementation 
The application was developed in Unity using the Vuforia Engine SDK for marker-based AR 
tracking. The complete game world is anchored as children of a Vuforia ImageTarget 
GameObject, ensuring all content remains locked to the printed marker on the physical 
surface. The prototype was developed in Unity using AR Foundation. 
Implemented systems include: 
• AR camera tracking 
• Surface placement 
• Orbiting enemy ship movement 
• Enemy ships shooting toward the player ship 
• Gaze targeting system 
• Automatic firing bullets 
Thembalethu Nsele     225615037                                    
• Score system 
• Health score system 
• Explosion particle effects 
• sound effects 
• Win / lose conditions 
• Restart functionality 
Scripts used to control the game: 
Script 
Purpose 
GazeShooter.cs 
Attached to AR Camera. Performs a raycast from screen 
center every frame. Accumulates a gaze timer when the ray 
hits an Enemy tag. Fires a bullet when timer reaches 
gazeDuration. Resets timer when gaze moves away. 
BulletController.cs 
Attached to player bullet prefab. Receives direction from 
GazeShooter via SetDirection(). Moves in that direction at 
bulletSpeed. Detects collision with Enemy and Planet tags. 
EnemyFormation.cs 
Moves the enemy group horizontally left and right, bouncing 
at moveDistance from the start position. Each individual 
enemy also wanders slightly for a scattered space particle 
effect. 
EnemyShooter.cs 
Attached to each enemy. Finds the player by tag and fires 
bullets toward the player position at randomised intervals. 
EnemyBullet.cs 
Moves enemy projectile toward player using SetDirection(). 
Destroys on collision with Player or Obstacle tags. 
GameManager.cs 
Singleton managing game state: start, score tracking, lives, 
win condition, and game over. Enables and disables all 
gameplay scripts on state transitions. 
9. Conclusion 
The AR version of Space Shooter successfully preserves the original gameplay goal of 
destroying enemy ships while protecting the player ship. However, traditional touch 
controls were redesigned into movement-based aiming and gaze-triggered shooting. 
Enemy ships orbiting the battlefield and firing toward the player ship add challenge 
while making strong use of three-dimensional AR space. The final result is a more 
immersive and interactive version of the original game that demonstrates how classic 
arcade shooters can be effectively reimagined using AR technology. 
