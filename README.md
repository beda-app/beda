# Приложение для контроля веса

## Установка
Убедитесь, что в вашей системе присутствуют
* [Docker Engine](https://docs.docker.com/engine/install/)
* [Docker Compose](https://docs.docker.com/compose/install/)

Переименуйте файлы `database.env.example` и `backend.env.example` в папке 
`config` в `database.env` и `backend.env` соответственно.
После заполните в них следующие поля:

| Файл               | Поле                   | Описание                                                                                                                     | Пример                                                                 |
| ------------------ | ---------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| backend.env        | `TORTOISE_URI`         | URI PostgreSQL базы данных для Tortoise.                                                                                     | `postgres://postgres:{POSTGRES_PASSWORD}@database:5432/{POSTGRES_DB}`  |
| backend.env        | `JWT_SECRET_KEY`       | Секретный ключ, которым будут подписываться токены пользователей, рекомендуется генерировать командой `openssl rand -hex 32` |                                                                        |
| backend.env        | `CORS_ORIGINS`         | Список доменов с которых будут доступны запросы к API. Опционально, по умолчанию отключено.                                  | ["http://localhost", "http://localhost:3000"]                          |
| database.env       | `POSTGRES_PASSWORD`    | Пароль базы данных для пользователя postgres.                                                                                |                                                                        |
| database.env       | `POSTGRES_DB`          | Название базы данных.                                                                                                        | beda                                                                   |

Запустите контейнер базы данных следующей командой:

`$ docker-compose up -d database`

И остальные контейнеры:

`$ docker-compose up -d`

Проверьте работу приложения, открыв в браузере:

`http://localhost/`