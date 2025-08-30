## luxball
[![NPM version](https://img.shields.io/npm/v/luxball.svg?style=flat-square)](https://www.npmjs.com/package/luxball)
[![Downloads](https://img.shields.io/npm/dm/luxball.svg?style=flat-square)](https://www.npmjs.com/package/luxball)
<br />
Script for hosting Luxball Rooms

### Installation
```bash
npm i luxball
```

### Usage
```javascript
import createRoom from 'luxball';

createRoom({
    playerName: "Admin",
    roomSettings: {
        name: `Room Test`,
        joinToken: "luxball",
        password: "",
        maxPlayers: 20,
        showInRoomList: false
    }
}).then((room) => {
    room.onRoomLink = (roomLink) => {
        const roomId = roomLink.split("=")[1]
        console.log("Room URL:", `https://luxball.online/play/${roomId}`)
    }

    room.onPlayerJoin = function (player) {
        room.setPlayerTeam(player.id, 1);
        room.startGame();
    }

    room.onPlayerChat = function (player, message) {
        console.log(player.name, message)
    }
});
```