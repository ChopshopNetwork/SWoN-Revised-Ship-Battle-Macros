# SWoN-Revised-Ship-Battle-Macros

This code is a set of macros to be used on Roll20.com with the Stars Without Number:Revised game system.

This readme provides you with the code and the know-how to turn your Stars Without Number Revised edition spaceship battles into crisp-looking, clickable macros inside a Roll20.com game.  Follow the steps below and copy and paste the text into each macro and table entry.  Please email me at thechopshopnetwork@gmail.com if you find any bugs or typos.  Thanks! 

*****************************************************************************************************************************************

**YOU WILL NEED:**
-A Roll20 "Pro" account is needed to install the necessary API Scripts.

- 2 API Scripts must be installed in your Roll20 game:
Recursive Tables and Tokenmod, both coded by The Aaron.  You shouldn’t have to fiddle with them other than just copying and pasting them into the API Scripts section of your Roll20 game settings.

https://github.com/shdwjk/Roll20API/blob/master/RecursiveTable/RecursiveTable.js
https://wiki.roll20.net/Script:Token_Mod

- Many of the macros below are written assuming that your Roll20 game will have separate character sheets for each spaceship in battle, and that each spaceship will have a token.  Every member of a party should have permissions to control their team’s spaceship character sheet (and therefore can control it's token).  The command points will not automatically update and many commands may not work if they are used while no spaceship token is selected.

***************************************************************************************************************************************

STEP 1: Open the character sheet for the PC’s Spaceship and click the Attributes & Abilities tab, click that “Add” button above the abilities column, then scroll all the way down to find your new, blank ability.  Rename this ability “command_points”.  This allows the team's use of these macros to update the ships Command points.

STEP 1B:  You can now double click the spaceship token and set it's red bar to represen the "command_points" attribute that you created in step 1.  As long as the red bar on the token is set to 0 at the beginning of the turn (use the CP-Reset macro), all of the player's combat choices should automatically track their team's Command Points in the red bar of their ship's token.

**************************************************************************************************************************************

STEP 2: Build the Ship Crisis Table as a rollable table in your Roll20 game using the following 10 entries, all with a weight of 1.  Do not copy the "Table Title:" text or the "Entry #:" text into the table.

Table Title: ship-crisis
Entry 1: [Armor Loss](!&#13;#crisis-armor-loss)
Entry 2: [Cargo Loss](!&#13;#crisis-cargo-loss)
Entry 3: [Crew Lost](!&#13;#crisis-crew-lost)
Entry 4: [Engine Lock](!&#13;#crisis-engine-lock)
Entry 5: [Fuel Bleed](!&#13;#crisis-fuel-bleed)
Entry 6: [Haywire Systems](!&#13;#crisis-haywire-systems)
Entry 7: [Hull Breach](!&#13;#crisis-hull-breach)
Entry 8: [System Damage](!&#13;#crisis-system-damage)
Entry 9: [Target Decalibration](!&#13;#crisis-target-decalibration)
Entry 10: [VIP Imperiled](!&#13;#crisis-vip-imperiled)

************************************************************************************************************************************

STEP 3:  Copy the text of each entry below into a new macro in the collections tab of your Roll20 game.  Make sure you set the ship battle macros to be visible to all players (except for any NPC macros).  The first section of macros you will want to have set as “Token Actions” by click the token action check box when entering in a new macro.

Note:  Some of the code within the macros turns invisible after saving them and reopening the macro editor interface in Roll20.  Don’t freak out, it’s still there and it still works, just try not to touch it.

**************************************************************************************************************************************

MACROS SECTION 1:  You and your players will be using these macros for ship battles, so set them as global “token actions”.

Title: Ship-Crisis
Code: !rt &{template:spell} {{characterName=Ship Crisis}} {{spell=[Imgur](https://i.imgur.com/NuShiog.jpg)}} {{description=[[1t[ship-crisis]]]}}

_____________________________________

Title: Captain-Turn
Code:&{template:spell} {{characterName=Ship Turn Order}} {{spell=Captain's Authority}} {{description=1st Dept: ?{1st Action|Bridge|Captain|Comms|Engineering|Gunnery}
2nd Dept: ?{2nd Action|Bridge|Captain|Comms|Engineering|Gunnery}
3rd Dept: ?{3rd Action|Bridge|Captain|Comms|Engineering|Gunnery}
4th Dept: ?{4th Action|Bridge|Captain|Comms|Engineering|Gunnery}
5th Dept: ?{5th Action|Bridge|Captain|Comms|Engineering|Gunnery}
}}
_____________________________________

Title: NPC-Ship-Action
Code: &{template:spell} {{characterName=@ship_name Actions}} {{spell=NPC Ship}} {{description=**NPC Command Points** = @ship_hulltype
**Bridge** 
[Escape Combat -4](!&#13;#bridge-escape-combat) [Evasive Maneuvers -2](!&#13;#bridge-evasive-maneuvers) [Pursue Target -3](!&#13;#bridge-pursue-target)
**Comms**
[Crash Systems -2](!&#13;#comms-crash-systems) [Defeat ECM -2](!&#13;#comms-defeat-ecm) [Sensor Ghost -2](!&#13;#comms-sensor-ghost)
**Engineering**
[Boost Engines -2](!&#13;#eng-boost-engines) [Damage Control -3](!&#13;#eng-damage-control) [Emergency Repairs -3](!&#13;#eng-emergency-repairs)
**Gunnery**
[Fire All Guns -3](!&#13;#gunnery-fire-all-guns) [Fire One Weapon -2](!&#13;#gunnery-fire-one-weapon) [Target Systems -1](!&#13;#gunnery-target-systems)
**General** 
[Above and Beyond](!&#13;#ship-above-and-beyond) [Deal With Crisis](!&#13;#ship-deal-with-crisis)}}
_____________________________________

Title: Engineering-Actions
Code: &{template:spell} {{characterName=Engineering Actions}} {{spell=[Imgur](https://i.imgur.com/thTxbWD.jpg)}} {{description=**Current CP** = @{selected|command_points}

**Engineering**
[Boost Engines -2](!&#13;#eng-boost-engines) [Damage Control -3](!&#13;#eng-damage-control) [Emergency Repairs -3](!&#13;#eng-emergency-repairs)
**General** 
[Above and Beyond](!&#13;#ship-above-and-beyond) [Deal With Crisis](!&#13;#ship-deal-with-crisis) [Do Your Duty +1](!&#13;#ship-do-your-duty)}}
_____________________________________

Title: Captain-Actions
Code: &{template:spell} {{characterName=Captain Actions}} {{spell=[Imgur](https://i.imgur.com/1PaVZ3q.jpg)}} {{description=**Current CP** = @{selected|command_points}

**Captain**
[Into the Fire](!&#13;#captain-into-the-fire) [Keep It Together](!&#13;#captain-keep-it-together) [Support Department](!&#13;#captain-support-department)
**General** 
[Above and Beyond](!&#13;#ship-above-and-beyond) [Deal With Crisis](!&#13;#ship-deal-with-crisis) [Do Your Duty +1](!&#13;#ship-do-your-duty)}}
_____________________________________

Title: Comms-Actions
Code: &{template:spell} {{characterName=Comms Actions}} {{spell=[Imgur](https://i.imgur.com/pUPhCq4.jpg)}} {{description=**Current CP** = @{selected|command_points}

**Comms**
[Crash Systems -2](!&#13;#comms-crash-systems) [Defeat ECM -2](!&#13;#comms-defeat-ecm) [Sensor Ghost -2](!&#13;#comms-sensor-ghost)
**General** 
[Above and Beyond](!&#13;#ship-above-and-beyond) [Deal With Crisis](!&#13;#ship-deal-with-crisis) [Do Your Duty +1](!&#13;#ship-do-your-duty)}}
_____________________________________

Title: Gunnery-Actions
Code: &{template:spell} {{characterName=Gunnery Actions}} {{spell=[Imgur](https://i.imgur.com/9U7qdXl.jpg)}} {{description=**Current CP** = @{selected|command_points}

**Gunnery**
[Fire All Guns -3](!&#13;#gunnery-fire-all-guns) [Fire One Weapon -2](!&#13;#gunnery-fire-one-weapon) [Target Systems -1](!&#13;#gunnery-target-systems)
**General** 
[Above and Beyond](!&#13;#ship-above-and-beyond) [Deal With Crisis](!&#13;#ship-deal-with-crisis) [Do Your Duty +1](!&#13;#ship-do-your-duty)}}
_____________________________________

Title: Bridge-Actions
Code: &{template:spell} {{characterName=Bridge Actions}} {{spell=[Imgur](https://i.imgur.com/QZMjYuR.jpg)}} {{description=**Current CP** = @{selected|command_points}

**Bridge** 
[Escape Combat -4](!&#13;#bridge-escape-combat) [Evasive Maneuvers -2](!&#13;#bridge-evasive-maneuvers) [Pursue Target -3](!&#13;#bridge-pursue-target)
**General** 
[Above and Beyond](!&#13;#ship-above-and-beyond) [Deal With Crisis](!&#13;#ship-deal-with-crisis) [Do Your Duty +1](!&#13;#ship-do-your-duty)}}

_____________________________________

Title: CP-reset
Code: !token-mod --set bar3_value|0

**************************************************************************************************************************************

MACROS SECTION 2:  These are the background macros that your main “Player Actions" macros will call on.  These generally do not need to be set as "Token Action".

Title: bridge-escape-combat
Code: &{template:spell} {{characterName= Escape Combat (4CP)}} {{spell=Bridge Action}} {{description=Roll an opposed Int/Pilot or Dex/Pilot skill check plus your ship’s Speed against the fastest opponent’s skill check plus their ship’s Speed. On a win, all enemy ships gain one point of Escape. If an enemy ship gets three points, after three uses of this maneuver, your ship gets away from that ship and is no longer in combat with it.}}
!token-mod --set bar3_value|-4
_____________________________________

Title: bridge-evasive-maneuvers
Code: &{template:spell} {{characterName=Evasive Maneuvers (2CP)}} {{spell=Bridge Action}} {{description=Roll Int or Dex/Pilot against difficulty 9 to add your Pilot skill to the ship’s AC until its next turn. Usable once per round at most.}}
!token-mod --set bar3_value|-2
_____________________________________

Title: bridge-pursue-target
Code: &{template:spell} {{characterName= Pursue Target (3CP)}} {{spell=Bridge Action}} {{description=Opposed Int/Pilot or Dex/Pilot skill check plus Speed against the target ship’s skill check plus Speed. On a win, you shed one point of Escape rating the target ship may have on you.}}
!token-mod --set bar3_value|-3
_____________________________________

Title: captain-into-the-fire
Code: &{template:spell} {{characterName= Into the Fire (0CP)}} {{spell=Captain Action}} {{description=Accept a Crew Lost Crisis and gain your Lead skill plus one in Command Points. You may do this at most once per round.}}
_____________________________________

Title: captain-keep-it-together
Code: &{template:spell} {{characterName= Keep it Together (0CP)}} {{spell=Captain Action}} {{description=Nullify a successful enemy hit and roll a Crisis instead. You can use this action in Instant response to an enemy hit but you may only use it once per round.}}
_____________________________________

Title: captain-support-department
Code: &{template:spell} {{characterName= Support Department (0CP)}} {{spell=Captain Action}} {{description= One action that the **?{Department|Bridge|Comms Dept.|Engineering Dept.|Gunnery}** takes will require 2 fewer Command Points. You can do this once per round.}}
_____________________________________

Title: comms-crash-systems
Code: &{template:spell} {{characterName= Crash Systems (2CP)}} {{spell=Comms Action}} {{description=Roll an opposed Int/Program check against a targeted ship. On a success, it starts its next turn with a Command Point penalty equal to your Program skill.}}
!token-mod --set bar3_value|-2
_____________________________________

Title: comms-defeat-ecm
Code: &{template:spell} {{characterName=Defeat ECM (2CP)}} {{spell=Comms Action}} {{description=Roll an opposed Int/Program against a targeted ship. On a success, any attacks this round by your ship against the target get a hit bonus equal to twice your Program skill.}}
!token-mod --set bar3_value|-2
_____________________________________

Title: comms-sensor-ghost
Code: &{template:spell} {{characterName= Sensor Ghost (2CP)}} {{spell=Comms Action}} {{description=Succeed on a difficulty 9 Int/Program check to gain your Program as an AC bonus until the next turn. Usable once per round at most.}}
!token-mod --set bar3_value|-2
_____________________________________

Title: eng-boost-engines
Code: &{template:spell} {{characterName= Boost Engines (2CP)}} {{spell=Engineering Action}} {{description=Roll Int/Fix versus difficulty 8. On a success, the ship’s Speed is increased by 2 until the start of the ship’s next turn.}}
!token-mod --set bar3_value|-2
_____________________________________

Title: eng-damage-control
Code: &{template:spell} {{characterName= Damage Control (3CP)}} {{spell=Engineering Action}} {{description=Roll Int/Fix versus difficulty 7. On a success, repair a number of lost hit points equal to your Fix skill times 2 for fighter hulls, 3 for frigates, 4 for cruisers, and 6 for capital-class hulls. Each attempt of this action after the first in a fight increases its difficulty by a cumulative +1.}}
!token-mod --set bar3_value|-3
_____________________________________

Title: eng-emergency-repairs
Code: &{template:spell} {{characterName= Emergency Repairs (3CP)}} {{spell=Engineering Action}} {{description=Roll Int/Fix versus difficulty 8. On a success, a disabled system is repaired or a damage-degraded drive has its rating increased by 1. Destroyed systems cannot be fixed this way.}}
!token-mod --set bar3_value|-3
_____________________________________

Title: gunnery-fire-all-guns
Code: &{template:spell} {{characterName= Fire All Guns (3CP)}} {{spell=Gunnery Action}} {{description=Gunners fire all weapons mounted on the ship, designating targets as they wish.}}
!token-mod --set bar3_value|-3
_____________________________________

Title: gunnery-fire-one-weapon
Code: &{template:spell} {{characterName=Fire One Weapon (2CP)}} {{spell=Gunnery Action}} {{description=A gunner fires a single ship’s weapon of their choice.}}
!token-mod --set bar3_value|-2
_____________________________________

Title: gunnery-target-systems
Code: &{template:spell} {{characterName= Target Systems (1CP)}} {{spell=Gunnery Action}} {{description=A *Fire One Weapon* action you take this round may target a ship’s weapons, engine, or fittings the GM decides are vulnerable. Such targeted attacks take -4 to hit. On a hit, do half damage before applying Armor. If damage gets through the system is disabled or drive is degraded by 1 level. Disabled systems hit again are destroyed. You may take this action more than once to aim additional shots you may fire.}}
!token-mod --set bar3_value|-1
_____________________________________

Title: ship-above-and-beyond
Code: &{template:spell} {{characterName= Above and Beyond (0CP)}} {{spell=General Action}} {{description=Push yourself to help the ship or its crew. Pick an attribute and skill check and explain how you’re using it to help the ship. If the GM agrees, roll it against difficulty 9. On a success, gain your skill level in Command Points plus one. On a failure, take -1 Command Point.}}
_____________________________________

Title: ship-deal-with-crisis
Code: &{template:spell} {{characterName= Deal With Crisis (0CP)}} {{spell=General Action}} {{description=Explain what you are doing to solve a Crisis and roll the relevant skill check. The difficulty is usually 10, plus or minus 2 depending on the situation and the effectiveness of your action. On a success, the Crisis is resolved. You may also use this action to aid another PC in resolving a Crisis, or to take one scene’s worth of other actions around the ship.}}
_____________________________________

Title: ship-do-your-duty
Code: &{template:spell} {{characterName=Do Your Duty (+1CP)}} {{spell=General Action}} {{description=The ship gains 1 Command Point. PCs who head more than one department can act only in one of them; the rest automatically take this action. If invoked by a PC, they must name some plausible act the PC is doing to be useful, and can’t do the same act two rounds in a row.}}
!token-mod --set bar3_value|+1
_____________________________________

Title: hull-capital
Code: &{template:spell} {{characterName=Hull Breach}} {{spell=Ship Crisis}} {{description=Capital Class Hulls (ignoring armor)}}{{damage=[[4d10]]}}
_____________________________________

Title: hull-cruiser
Code: &{template:spell} {{characterName=Hull Breach}} {{spell=Ship Crisis}} {{description=Cruiser Class Hulls (ignoring armor)}}{{damage=[[3d10]]}}
_____________________________________

Title: hull-fighter
Code: &{template:spell} {{characterName=Hull Breach}} {{spell=Ship Crisis}} {{description=Fighter Class Hulls (ignoring armor)}}{{damage=[[1d10]]}}

_____________________________________

Title: hull-frigate
Code: &{template:spell} {{characterName=Hull Breach}} {{spell=Ship Crisis}} {{description=Frigate Class Hulls (ignoring armor)}}{{damage=[[2d10]]}}
_____________________________________

Title: crisis-armor-loss
Code: &{template:spell} {{characterName=Armor Loss}} {{spell=Ship Crisis}} {{description=The hit melted an important patch of ship, cracked an internal support, or exposed a sensitive system. Until resolved, the ship’s Armor rating is halved, rounded down.}}
_____________________________________

Title: crisis-cargo-loss
Code: &{template:spell} {{characterName=Cargo Loss}} {{spell=Ship Crisis}} {{description=The hit has gored open a cargo bay, threatening to dump the hold or expose delicate contents to ruinous damage. If not resolved by the end of the next round, lose d10*10% of the ship’s cargo.}}
_____________________________________

Title: crisis-crew-lost
Code: &{template:spell} {{characterName=Crew Lost}} {{spell=Ship Crisis}} {{description=Brave crew risk their lives to keep damaged systems operating. Describe the danger they face. If the Crisis is not resolved by the end of the next round, 10% of the ship’s maximum crew are incapacitated, not counting any *Extended Life Support fittings*. Half these crewmen are dead or permanently disabled, and the other half return to duty in a week. *Extended Medbay* fittings halve the number of dead and crippled. If the ship has run out of NPC crew when it takes this Crisis, a random PC must roll a Physical save; on a success, they lose half their hit points, while on a failure, they are mortally wounded. If not stabilized by the end of the ship’s turn through some PC taking a *Deal With A Crisis* action to heal them, they will die.}}
_____________________________________

Title: crisis-engine-lock
Code: &{template:spell} {{characterName=Engine Lock}} {{spell=Ship Crisis}} {{description=The ship’s engine has been jammed or control circuits have gone non-responsive. Until resolved, no bridge actions can be taken, though the pilot can still perform general actions.}}
_____________________________________

Title: crisis-fuel-bleed
Code: &{template:spell} {{characterName=Fuel Bleed}} {{spell=Ship Crisis}} {{description=The ship’s fuel tanks have been holed or emergency vents have been force-triggered by battle damage. If not resolved by the end of the next round, the ship will jettison all fuel except the minimal amount needed for in-system operation.}}
_____________________________________

Title: crisis-haywire-systems
Code: &{template:spell} {{characterName=Haywire Systems}} {{spell=Ship Crisis}} {{description=Critical command links have been damaged or disordered by the hit. Until resolved, the ship starts each round at -2 Command Points. Multiple such Crises can stack this penalty, crippling a ship until the Crises are resolved.}} {{damage=}}
_____________________________________

Title: crisis-hull-breach
Code: &{template:spell} {{characterName=Hull Breach}} {{spell=Ship Crisis}} {{description=The hull has been damaged in a way that is currently non-critical but is about to tear open an important compartment or crumple on vital systems. If not resolved by the end of the next round, the ship will take damage.
[Fighter](!&#13;#hull-fighter)
[Frigate](!&#13;#hull-frigate)
[Cruisers](!&#13;#hull-cruiser)
[Capital](!&#13;#hull-capital)}}
_____________________________________

Title: crisis-system-damage
Code: &{template:spell} {{characterName=}} {{spell=Ship Crisis}} {{description=One of the ship’s systems has been cooked by the hit. The GM randomly picks a weapon, fitting, or engine; that system is disabled as if hit with a targeted shot, with drives suffering a 1 point drive level decrease. Disabled systems hit by this Crisis or drives reduced below drive-0 are destroyed and cannot be repaired during combat.}}
_____________________________________

Title: crisis-target-decalibration
Code: &{template:spell} {{characterName=}} {{spell=Ship Crisis}} {{description=The gunnery computers are hopelessly confused and cannot lock the ship’s weaponry on a target until this Crisis is resolved.}}
_____________________________________

Title: crisis-vip-imperiled
Code: &{template:spell} {{characterName=VIP Imperiled}} {{spell=Ship Crisis}} {{description=Shipboard damage threatens a random PC or important NPC. That victim must immediately roll a Physical saving throw; on a success, they lose half their hit points, and on a failure they are mortally wounded. NPC crew can make a free attempt to stabilize the downed VIP using their usual NPC skill bonus. If the NPC fails, and no PC takes a *Deal With a Crisis* action to successfully stabilize them by the end of the ship’s turn, they die.}}





