# GameEvents

This table contains functions for game events.

* [GameEvents.StartListening](https://hake.me/docs/systems/gameevents#gameevents-startlistening-name)
* [GameEvents.SendCustomGameEventToServer](https://hake.me/docs/systems/gameevents#gameevents-sendcustomgameeventtoserver-name-table)
* [GameEvents.SendCustomGameEventToAllClients](https://hake.me/docs/systems/gameevents#gameevents-sendcustomgameeventtoallclients-name-table)
* [GameEvents.SendCustomGameEventToClient](https://hake.me/docs/systems/gameevents#gameevents-sendcustomgameeventtoclient-name-player_id-table)

---

## `GameEvents.StartListening(name)`​

### Remarks

* Sends a message to the server telling it the client wants to listen to a certain event
* Required for `OnGameEvent`​ for some events
* Possible events can be found in `resource/game.gameevents`​ and some others

  * Or you can use `OnNetMessageReceived(msg)`​ where `msg.name == "CMsgSource1LegacyGameEventList"`​

---

## `GameEvents.SendCustomGameEventToServer(name, table)`​

---

## `GameEvents.SendCustomGameEventToAllClients(name, table)`​

---

## `GameEvents.SendCustomGameEventToClient(name, player_id, table)`​
