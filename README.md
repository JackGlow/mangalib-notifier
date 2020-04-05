# MangaLib Notifier

[Switch to English version](README-EN.md)

> :warning: **Неофициальный скрипт** Этот скрипт не создан MangaLib или его администраторами, я просто сделал парсер и на его основе сделал вебхук.

Скрипт, который отправит на твой вебхук уведомление, когда на MangaLib появится перевод новой главы манги.

## Установка (Windows)

> :warning: Билды работают медленнее, чем скриптом в 2-3 раза.

1. Скачайте последний билд c вкладки Releases.
2. Запустите `mangalib.exe`
3. Настройте прослушивание, используя `setnode` (все команды и примеры ниже)
4. Запустите прослушивание, используя команду `listen`.

## Установка (Linux/MacOS)
1. Скачайте **Python 3.7+** и установите
2. Скачайте последний `source` архив с вкладки Releases (для стабильности), либо же клонируйте из `master` бранча. (для последней версии)
3. Установите зависимости используя `pip install -r requirements.txt` или `pip3 install -r requirements.txt`
4. Запустите скрипт, используя `python manga.py`, либо же `python3 manga.py`
5. Настройте прослушивание, используя `setnode` (все команды и примеры ниже)
6. Запустите прослушивание, используя команду `listen`.

## Команды
| Команда | Описание                    | Пример |
| ------------- | ----------------------- | --------------------- |
| `help`      | Отобразить ссылку на гитхаб      | `help` |
| `setnode`   | Установить настройку    | `setnode manga naruto` |
| `autonode`   | Пошагово установить настройки (более быстрый setnode)    | `autonode` |
| `save`   | Сохранить настройки в файл .ml-cfg    | `save filename` |
| `load`   | Загрузить настройки    | `load filename` |
| `exit`   | Выйти    | `exit` |

## Ноды (настройки)
| Нод  | Описание    | Возможные значения |
| ------------- | ----------------------- | --------------------- |
| `manga`      | ID Манги      | Любой ID манги |
| `chapter`      | Значение после которого стоит ждать главу      | Любое число |
| `delay`      | Задержка между проверками, в секундах      | Любое число |
| `url`      | Ссылка webhook      | Любая ссылка |
| `method`      | Протокол отправки     | `GET`, `POST`, `PUT`, `discord` маленькими буквами |
| `sendto`      | **Устаревший метод** Используйте `url`     |  |

## Настройка для Дискорда
1. `method` должен быть `discord`;
2. `url` должна быть ссылкой на Discord вебхук.

## Демонстрация Дискорд Вебхука
![Demo](https://i.imgur.com/gC4scNu.png "Demo")

## Размещение на Heroku, Now, AWS, и т.д.
Для размещения на облачном сервере нужно не много интеллекта и размышлений, с Heroku все просто:
1. Скачиваем последний стабильный `source` архив, либо же бранч разработки.
2. Запускаем `manga.py`
3. Используем `autonode` и заполняем все поля (Если хотите что бы последняя глава опредилась сама пишем `-1` в `chapter`)
4. Сохраняем под любым названием используя `save` (кроме autoload)
5. Выходим (`exit` или `Ctrl+^C`)
6. Переименовываем новосозданный файл в autoload.ml-cfg
7. Создайте новое приложение и задеплойте папку на Heroku.

### AWS и другие выделенные облачные сервера (Azure, Google Cloud, ...) на Linux
Тут еще все проще, так как мы можем использовать сервер как обычный компьютер, для того что бы вебхук работал без присутствия пользователя следует выполнить следующее:
1. По инструкции выше создать `autoload.ml-cfg` файл
2. Установить `screen` (`sudo apt install screen`)
3. Создать новый энвайрнмент `screen -S mangalibenv`
4. Запустить скрипт
5. Закрыть соеденение
Вебхук продолжит работать, пока вы отстуствуете.