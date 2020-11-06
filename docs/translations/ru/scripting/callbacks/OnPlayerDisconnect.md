# OnPlayerDisconnect

### Описание
Этот обратный вызов срабатывает, когда игрок отключается от сервера.

Параметр | Описание
---------|---------
playerid | ID отключившегося игрока.
reason | Причина отключения.

### Возвращаемые значения
0 - Не позволит другим filterscript'ам получать этот обратный вызов.

1 - Указывает, что этот обратный вызов будет передан в следующий filterscript.

Вызывается первым из filterscript'ов.
### Пример использования

```c++
public OnPlayerDisconnect(playerid, reason)
{
    new
        szString[64],
        playerName[MAX_PLAYER_NAME];

    GetPlayerName(playerid, playerName, MAX_PLAYER_NAME);

    new szDisconnectReason[3][] =
    {
        "Таймаут/Краш",
        "Выход",
        "Кик/Бан"
    };

    format(szString, sizeof szString, "%s покинул сервер (%s).", playerName, szDisconnectReason[reason]);

    SendClientMessageToAll(0xC4C4C4FF, szString);
    return 1;
}
```
