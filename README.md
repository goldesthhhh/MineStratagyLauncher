# MineStratagyLauncher — репозиторий обновлений лаунчера

Здесь должны лежать три файла:

| Файл | Что это | Кто его берёт |
|---|---|---|
| `launcher-version.json` | манифест версии — **наличие обновления** и ссылка на новый exe | сам лаунчер (Raw URL) |
| `launcher.zip` | ZIP, внутри которого `STRATAGY Launcher <ver>.exe` | установщик 0.4.8+ и автообновление лаунчеров |
| `STRATAGY Setup <ver>.exe` | установщик для новых игроков (клади в релиз или прямо в репо) | скачивается вручную |

## Порядок выпуска новой версии (минимум телодвижений)
1. `cd launcher && npm run dist` → получишь в `dist` два файла:
   `STRATAGY Launcher <ver>.exe` и `STRATAGY Setup <ver>.exe`.
2. Собери `launcher.zip`: внутри один файл `STRATAGY Launcher <ver>.exe`.
3. Замени в репо:
   - `launcher.zip` (внутри новый Launcher exe)
   - `STRATAGY Setup <ver>.exe`
   - `launcher-version.json` — поправь `"version"` на новую и `"notes"`.

Важно: `zipUrl` в манифесте менять **не нужно** — он всегда указывает на
`.../MineStratagyLauncher/main/launcher.zip`, а сам launcher.zip ты просто перезаливаешь.

## Почему не zipUrl с версией
GitHub кэширует raw-файлы ~5 минут — после пуша обновления появятся у игроков в течение
нескольких минут автоматически. Всё, что делает игрок для обновления: клик по баннеру.

## Альтернатива без zip
Можно положить в репо голый exe (например `launcher.exe`) и в `launcher-version.json`
указать прямую ссылку на него в `zipUrl` — обработка обоих вариантов встроена
(лаунчер/установщик сами понимают zip или голый exe по сигнатуре файла).

https://drive.usercontent.google.com/download?id=1xNIMCgXePo2ZHLRpxA33qFih4YOyV3Uw&export=download&authuser=0
