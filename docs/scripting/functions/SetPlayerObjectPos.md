---
title: SetPlayerObjectPos
description: Sets the position of a player-object to the specified coordinates.
tags: ["player"]
---

## Description

Sets the position of a player-object to the specified coordinates.

| Name     | Description                                                                         |
| -------- | ----------------------------------------------------------------------------------- |
| playerid | The ID of the player whose player-object to set the position of.                    |
| objectid | The ID of the player-object to set the position of. Returned by CreatePlayerObject. |
| Float:X  | The X coordinate to put the object at.                                              |
| Float:Y  | The Y coordinate to put the object at.                                              |
| Float:Z  | The Z coordinate to put the object at.                                              |

## Returns

1: The function executed successfully.

0: The function failed to execute. Player and/or object do not exist.

## Examples

```c
new obj = CreatePlayerObject(...);

// Later on

SetPlayerObjectPos(playerid, obj, 2001.195679, 1547.113892, 14.283400);
```

## Related Functions

- [CreatePlayerObject](CreatePlayerObject.md): Create an object for only one player.
- [DestroyPlayerObject](DestroyPlayerObject.md): Destroy a player object.
- [IsValidPlayerObject](IsValidPlayerObject.md): Checks if a certain player object is vaild.
- [MovePlayerObject](MovePlayerObject.md): Move a player object.
- [StopPlayerObject](StopPlayerObject.md): Stop a player object from moving.
- [SetPlayerObjectRot](SetPlayerObjectRot.md): Set the rotation of a player object.
- [GetPlayerObjectPos](GetPlayerObjectPos.md): Locate a player object.
- [GetPlayerObjectRot](GetPlayerObjectRot.md): Check the rotation of a player object.
- [AttachPlayerObjectToPlayer](AttachPlayerObjectToPlayer.md): Attach a player object to a player.
- [CreateObject](CreateObject.md): Create an object.
- [DestroyObject](DestroyObject.md): Destroy an object.
- [IsValidObject](IsValidObject.md): Checks if a certain object is vaild.
- [MoveObject](MoveObject.md): Move an object.
- [StopObject](StopObject.md): Stop an object from moving.
- [SetObjectPos](SetObjectPos.md): Set the position of an object.
- [SetObjectRot](SetObjectRot.md): Set the rotation of an object.
- [GetObjectPos](GetObjectPos.md): Locate an object.
- [GetObjectRot](GetObjectRot.md): Check the rotation of an object.
- [AttachObjectToPlayer](AttachObjectToPlayer.md): Attach an object to a player.
