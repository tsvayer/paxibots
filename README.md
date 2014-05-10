PaxiBots
========
PaxiBots are programmable bots living in a 2D PaxiWorld. PaxiBots are physically separated from PaxiWorld, that is they are runing out of world process. Every bot has a remotely controlled Avatar. Avatar is a bot projection (or representative) on the PaxiWorld.

PaxiWorld has a turn based life cycle. All events in the world happen serially on one thread. PaxiWorld has its own clock and timeline. Every PaxiBot has a life cycle completely separate from the world and each other. Bots are communicating with the world over HTTP protocol. Communication is always initiated by the world, that is bots always response and never request.

Avatar
------
State:
* WorldId: world unique identifier
* Time: current world time
* AvatarId: avatar unique identifier
* Location: current 2D world location of the avatar

Actions:
* Move (dx, dy): move avatar by (dx, dy)

PaxiBot
-------
* Name: bot name
* Url: http endpoint on which all world requests are sent


Communication Protocol
----------------------
TODO:
