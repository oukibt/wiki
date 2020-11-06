# OnDialogResponse
Этот обратный вызов был добавлен в SA-MP 0.3a и не будет работать в более ранних версиях!

### Описание
Этот обратный вызов срабатывает когда игрок отвечает на диалоговое окно, которое отображается с помощью [ShowPlayerDialog](https://wiki.open.mp/docs/scripting/functions/ShowPlayerDialog) клавишами ENTER/ESC или двойным щелчком по элементу из списка

Параметр | Описание
---------|---------
playerid | ID игрока ответевшего на диалог
dialogid | ID диалога, на который ответил игрок
response | 1 для левой кнопки (ENTER), 0 для правой кнопки (ESC)
listitem | ID элемента из списка (начинается с 0 только при использовании диалога стиля "[список](https://wiki.open.mp/docs/scripting/resources/dialogstyles)", иначе -1)
inputtext | Текст введённый игроком, или текст элемента со списка

### Возвращаемые значения
Он всегда вызывается первым в filterscript'ах и поэтому возвращает 1 блокируя при этом его просмотр другими скриптами.
### Пример использования

```c++
// Идентификатор диалога для обработки ответа
#define DIALOG_RULES 1

// При каком-нибудь действии
ShowPlayerDialog(playerid, DIALOG_RULES, DIALOG_STYLE_MSGBOX, "Правила сервера", "- Не читерить\n- Не спамить\n- Уважать администрацию\n\nВы согласны с этими правилами?", "Да", "Нет");

public OnDialogResponse(playerid, dialogid, response, listitem, inputtext[])
{
    if (dialogid == DIALOG_RULES)
    {
        if (response) // Если игрок нажал на кнопку 'Да' или на ENTER
        {
            SendClientMessage(playerid, COLOR_GREEN, "Спасибо, что вы согласились с правилами нашего сервера!");
        }
        else // Если игрок нажал на кнопку 'Нет' или на ESC
        {
            Kick(playerid); // Выгоним игрока, так как он не согласен с правилами сервера
        }
        return 1; // Мы обработали диалог, поэтому возвращаем 1
    }
}
```
---
```c++
// Идентификатор диалога для обработки ответа
#define DIALOG_LOGIN 2

// При каком-нибудь действии
ShowPlayerDialog(playerid, DIALOG_LOGIN, DIALOG_STYLE_INPUT, "Вход", "Пожалуйста, введите свой пароль", "Вход", "Отмена");

public OnDialogResponse(playerid, dialogid, response, listitem, inputtext[])
{
    if (dialogid == DIALOG_LOGIN)
    {
        if (!response) // Если игрок нажал на кнопку 'Нет' или на ESC
        {
            Kick(playerid);
        }
        else // Если игрок нажал на кнопку 'Да' или на ENTER
        {
            if (CheckPassword(playerid, inputtext))
            {
                SendClientMessage(playerid, COLOR_RED, "Вы вошли!");
            }
            else
            {
                SendClientMessage(playerid, COLOR_RED, "Авторизация не удалась!");

                // Повторно показать диалог со входом
                ShowPlayerDialog(playerid, DIALOG_LOGIN, DIALOG_STYLE_INPUT, "Вход", "Пожалуйста, введите свой пароль", "Вход", "Отмена");
            }
        }
        return 1; // Мы обработали диалог, поэтому возвращаем 1
    }
```
---
```c++
// Идентификатор диалога для обработки ответа
#define DIALOG_WEAPONS 3

// При каком-нибудь действии
ShowPlayerDialog(playerid, DIALOG_WEAPONS, DIALOG_STYLE_LIST, "Оружие",
"Оружие\tБоеприпасы\tЦена\n\
M4\t120\t500\n\
MP5\t90\t350\n\
AK-47\t120\t400",
"Выбрать", "Закрыть");

public OnDialogResponse(playerid, dialogid, response, listitem, inputtext[])
{
    if (dialogid == DIALOG_WEAPONS)
    {
        if (response) // Если игрок нажал на кнопку 'Выбрать' или на ENTER
        {
            // Даём игроку оружие
            switch(listitem)
            {
                case 0: GivePlayerWeapon(playerid, WEAPON_M4, 120); // Даём M4
                case 1: GivePlayerWeapon(playerid, WEAPON_MP5, 90); // Даём MP5
                case 2: GivePlayerWeapon(playerid, WEAPON_AK47, 120); // Даём AK-47
            }
        }
        return 1; // Мы обработали диалог, поэтому возвращаем 1
    }
}
```

### Примечание
Параменты обратного вызова могут содержать разные значения в зависимости от [стиля](https://wiki.open.mp/docs/scripting/resources/dialogstyles)

Уместно использовать switch вместо if, else или else if при большом количестве диалогов

### Предупреждение 
Диалог игрока не скрывается при перезапуске игрового режима

### Связанные функции
[ShowPlayerDialog](https://wiki.open.mp/docs/scripting/functions/ShowPlayerDialog): Показать диалог игроку


