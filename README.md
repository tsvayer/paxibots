PaxiBots
========
PaxiBots are programmable bots living in a 2D PaxiWorld. PaxiBots are physically separated from PaxiWorld, that is they are runing out of world process. Every bot has a remotely controlled Avatar. Avatar is a bot projection (or representative) on the PaxiWorld.

PaxiWorld has a turn based life cycle. All events in the world happen serially on one thread. PaxiWorld has its own clock and timeline. Every PaxiBot has a life cycle completely separate from the world and each other. Bots are communicating with the world over HTTP protocol. Communication is always initiated by the world, that is bots always response and never request. (Another alternative is for bots to push commands to the world in the Avatar "inbox" with some limited capacity. Commands will be queued and processed FIFO one by one at every world clock tick).

Avatar
------
State:
* WorldId: world unique identifier
* Time: current world time
* AvatarId: avatar unique identifier
* Location: current 2D world location of the avatar

Actions:
* MoveBy (dx, dy): move avatar by (dx, dy)

PaxiBot
-------
* BotId: unique bot identifier
* Name: bot name
* Url: http endpoint on which all world requests are sent


Communication Protocol
----------------------
Request:
```javascript
{
  world: {
    id: "6c6def3e-b1a1-4da4-b181-6abac993627e",
    time: 12345,
  },
  avatar: {
    id: "4acad603-018e-46f1-8b0e-d39b50921c16",
    location: [123, -3123123]
  },
  radar: [
    {
      location: [124, 321],
      item: { //TODO: think of  extendable cell information format
        type: 1 // 1: wall, 2: other bot
      }
    },
    {
      location: [125, 321],
      item: {
        type: 2,
        botId: "56bbcb1e-13bb-4225-b996-48ab2662aaa8"
      }
    }
  ]
}
```

Response:
```javascript
{
  moveBy: [1,-1]
}
```
