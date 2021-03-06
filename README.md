# Technical Stack
- Development:  Express | Socket.io | React | Node.js

# Description
World of Walkcraft is an example of a simple MMORPG built using React, web sockets, and sprites. Basically, you control a character that walks around a mini Zelda/Pokemon-style world and send chats to other players. A few functionalities I want to highlight:

1) Real-time character movements - This is achieved by storing a central grid (for each section of the map) in the socket server. Each grid is an m x n matrix storing values that each represent an image to display on the screen (e.g., a tree, rock, or character). When a user presses an arrow key, a "moveCharacter" event is sent to the web socket, which then updates the matrix before emitting it out to every connected client. This way, there is a shared global state on the server rendering the same grid across all clients a la Flux architecture.

2) Traversal to different sections of the map - This feature (reminiscent of the original Zelda games) was implemented using Socket.io's rooms functionality, which allows you emit some data to a specific subset of clients at a time. In this case, I only send the matrix corresponding to the room a given client is currently in. When one steps into an entrance to a new map, this sends a "switchRooms" event to the web socket, which forces the client to leave their previous socket room and join the new room before sending back the new room's matrix.

3) Walking animation - This basic sprite animation was built using a sprite map (i.e., larger image containing every frame) of the character's walking animation, React state, and CSS's "overflow: hidden" property to only show one frame/snippet of that image at a time. (This pattern was found here - https://github.com/react-u/013-building-a-dungeon-crawler-game-pt-3).

# Demos
Two browser windows shown to demonstrate multiple clients
- <a href="https://s3-us-west-1.amazonaws.com/gitbuckets/chatter-party/gifs/wow_demo1.gif">Player login + real-time multiplayer movements</a>
- <a href="https://s3-us-west-1.amazonaws.com/gitbuckets/chatter-party/gifs/wow_demo2.gif">Rooms demo 1</a>
- <a href="https://s3-us-west-1.amazonaws.com/gitbuckets/chatter-party/gifs/wow_demo3.gif">Rooms demo 2</a>
- <a href="https://s3-us-west-1.amazonaws.com/gitbuckets/chatter-party/gifs/wow_demo4.gif">Chat Feature</a>

# Setup
```
npm install
npm run build:dev
npm start:dev
```
