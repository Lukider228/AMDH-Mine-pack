# AMDH-Mine

Сборка модов для сервера AMDH-Mine: Minecraft 1.21.1, NeoForge.

## Как играть

1. Поставь NeoForge 1.21.1 (удобнее всего через Prism Launcher).
2. Скачай [Паровозинг](https://lukider228.github.io/AMDH-Mine-pack/files/parovozing-1.3.0.jar) и положи его в папку `mods`.
3. Запусти игру. Паровозинг сам скачает все моды, добавит сервер в список и попросит перезапустить игру.

Дальше обновления приходят сами при каждом запуске.

## Что здесь лежит

- `manifest.txt` - список модов для Паровозинга: ссылки, хеши, настройки, сервер.
- `pack.toml`, `index.toml`, `mods/` - та же сборка в формате packwiz.
- `blacklist.txt` - запрещённые моды.
- `files/` - то, чего нет на Modrinth: сам Паровозинг и русификатор.
- `rus/` - исходники русификатора.

Остальные моды качаются прямо с Modrinth.

## Для себя

**Сборка.** Дома правится в Prism и пересобирается скриптом `scripts/pack-build.py`. Версию NeoForge он берёт с сервера.

**Русификатор.** В `rus/translations/` только дописанные строки, в `rus/src/` готовые `ru_ru.json` и `neoforge.mods.toml`. Мод грузится после переводимых модов, иначе их английские строки перебивают перевод. Ещё он поднимает кнопку Chest Tracker над окном сундука. Пересобрать:

```bash
cd rus/src && jar --create --file ../../files/amdh-rus-X.Y.Z.jar --manifest META-INF/MANIFEST.MF -C . assets -C . META-INF/neoforge.mods.toml
```

Потом поменять имя и хеш в `manifest.txt` и `mods/amdh-rus.pw.toml`.

**Новый Паровозинг.** Положить jar в `files/`, добавить в `manifest.txt` как обычный `mod`, а старую версию закрыть `ban` по началу имени (сейчас это `parovozing-1.3`). Старый скачает новый и уберёт себя сам.
