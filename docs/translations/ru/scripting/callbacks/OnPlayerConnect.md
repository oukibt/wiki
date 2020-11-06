# OnPlayerConnect

### Описание
Этот обратный вызов срабатывает, когда игрок входит на сервер

Параметр | Описание
---------|---------
playerid | ID подключившегося игрока

### Возвращаемые значения
0 - Не позволит другим filterscript'ам получать этот обратный вызов.

1 - Указывает, что этот обратный вызов будет передан в следующий filterscript.

Вызывается первым из filterscript'ов.
### Пример использования

```c++
public OnPlayerConnect(playerid)
{
    new
        string[64],
        playerName[MAX_PLAYER_NAME];

    GetPlayerName(playerid, playerName, MAX_PLAYER_NAME);
    format(string, sizeof string, "%s вошел на сервер. Добро пожаловать!", playerName);
    SendClientMessageToAll(0xFFFFFFFF, string);
    return 1;
}
```
### Примечание
Этот обратный вызов также может быть вызван NPC
