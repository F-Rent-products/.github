<p align="center">
  <img src="f-rent-icon.png" alt="F-Rent" width="120" height="120">
</p>

<h1 align="center">F-Rent</h1>

<p align="center">
  Аренда вещей напрямую между людьми
</p>

<p align="center">
  <img src="https://img.shields.io/badge/backend-FastAPI%20%2B%20MySQL-009688?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI + MySQL">
  <img src="https://img.shields.io/badge/Android-Kotlin-7F52FF?style=flat-square&logo=kotlin&logoColor=white" alt="Android · Kotlin">
  <img src="https://img.shields.io/badge/iOS-SwiftUI%20(develop)-F05138?style=flat-square&logo=swift&logoColor=white" alt="iOS · SwiftUI (develop)">
  <img src="https://img.shields.io/badge/admin-React%20%2B%20TypeScript-61DAFB?style=flat-square&logo=react&logoColor=black" alt="Admin · React + TypeScript">
  <img src="https://img.shields.io/badge/Docker-4%2F9%20repos-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker в 4 репозиториях">
  <img src="https://img.shields.io/badge/repos-private-red?style=flat-square" alt="Репозитории приватные">
</p>

**F-Rent** — платформа P2P-аренды: люди сдают вещи, которыми редко пользуются, и берут нужное
рядом с собой на удобный срок — инструменты, техника, электроника, спортивный инвентарь и многое
другое. Внутри приложения — поиск, чат с владельцем, оплата аренды и фотофиксация вещи до передачи
и после возврата.

## Состав платформы

- **Бэкенд** — FastAPI + SQLAlchemy + MySQL (Redis опционально), владелец схемы БД, платежи и
  выплаты через эквайринг Т-Банка, push через FCM.
- **Мобильное приложение для Android** — Kotlin, единственная публично раздаваемая сборка
  (RuStore).
- **iOS-клиент** — SwiftUI, код есть, но живёт в ветке `develop`; в `main` пока заглушка, сборки
  нигде не публиковались.
- **Админка** — React + TypeScript + Vite: модерация товаров, пользователи, заявки.
- **Боты** — поддержка в VK, набор бета-тестеров в Telegram и служебный бот модерации
  (товары на проверке, жалобы, чаты поддержки, баланс SMS).
- **Сайт** [f-rent.ru](https://f-rent.ru) — лендинг и юридические документы.

> **Код закрыт.** Публичен только этот репозиторий с профилем организации, все девять продуктовых
> репозиториев приватные: ссылки в таблице ниже открываются у участников организации, а всем
> остальным GitHub отдаёт 404.

## Репозитории

| Репозиторий                                                                       | Назначение                                                                          | Стек                                                 |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------- |
| [F-Rent-Server](https://github.com/F-Rent-products/F-Rent-Server)                 | Бэкенд и API платформы: пользователи, товары, аренды, чаты, платежи, модерация       | Python, FastAPI, SQLAlchemy, MySQL, Redis, Docker    |
| [F-Rent-Mobile-Android](https://github.com/F-Rent-products/F-Rent-Mobile-Android) | Мобильное приложение для Android — то, что раздаётся пользователям                   | Kotlin, Retrofit/OkHttp, Gradle                      |
| [F-Rent-Mobile-iOS](https://github.com/F-Rent-products/F-Rent-Mobile-iOS)         | iOS-клиент: код в ветке `develop`, в `main` — заглушка, публичных сборок нет         | Swift, SwiftUI, XcodeGen                             |
| [F-Rent-Admin-Panel](https://github.com/F-Rent-products/F-Rent-Admin-Panel)       | Админка: модерация товаров, пользователи, работа с заявками                          | React, TypeScript, Vite, Chakra UI, Tailwind CSS     |
| [F-Rent-Web-Version](https://github.com/F-Rent-products/F-Rent-Web-Version)       | Задел под веб-версию приложения: только README и релизный workflow, кода нет         | не выбран                                            |
| [F-Rent-VK-Bot](https://github.com/F-Rent-products/F-Rent-VK-Bot)                 | Бот поддержки: обращения пользователей из VK, заявки для админов в VK и Telegram     | Python, vk_api, aiogram, MySQL, Redis, Docker        |
| [F-Rent-Telegram-Bot](https://github.com/F-Rent-products/F-Rent-Telegram-Bot)     | Бот набора бета-тестеров: регистрация, рассылки, выгрузка списка в Excel             | Python, python-telegram-bot, SQLite, pandas, Docker  |
| [F-Rent-Product-Bot](https://github.com/F-Rent-products/F-Rent-Product-Bot)       | Бот модерации: товары на проверке (с AI-оценкой), жалобы, чаты поддержки, баланс SMS | Python, PyMySQL, Telegram Bot API, Docker            |
| [F-Rent-Site](https://github.com/F-Rent-products/F-Rent-Site)                     | Сайт f-rent.ru: лендинг и юридические страницы                                       | HTML, Tailwind CSS                                   |

## Как мы работаем

- Разработка идёт в ветке `develop`, `main` — то, что считается выпущенным.
- В восьми репозиториях из девяти есть `.github/workflows/release.yml`: при merge pull request в
  `main` релиз создаётся автоматически — тег `vГГГГ.ММ.ДД-prN`, заголовок релиза = заголовок PR,
  описание = тело PR, архивы с исходниками прикладывает GitHub. Если тело PR пустое, в описание
  попадает список последних 20 коммитов; если пустой заголовок — «Релиз &lt;тег&gt;». Тот же
  workflow можно запустить руками (`workflow_dispatch` с полями «Заголовок релиза» и «Описание
  релиза»), тогда тег будет `vГГГГ.ММ.ДД-manual.<номер запуска>`; занятый тег дополняется номером
  запуска.
- В `F-Rent-Mobile-Android` тот же workflow дополнительно собирает и подписывает release APK и AAB
  и прикладывает их к релизу.
- В `F-Rent-Server` есть ещё `deploy.yml`: прод-деплой запускается сам после успешного CI на push в
  `main`.
- CI (`ci.yml` — линтеры, типы, тесты) есть в семи репозиториях. Его нет в `F-Rent-Web-Version`
  (нет кода) и в `F-Rent-Mobile-iOS`, где вместо него свой `ios.yml`, и только в `develop`.
- У каждого репозитория свой README; общий стандарт — шапка с иконкой и бейджами и разделы
  «Структура», «Быстрый старт», «Конфигурация», «Линтеры и тесты», «Ветки и релизы». Сейчас
  стандарту соответствуют не все — см. «Известные расхождения и ограничения».

## Что лежит в этом репозитории

Только профиль организации: `profile/README.md` и `profile/f-rent-icon.png` — больше в `.github`
ничего нет, ни workflow, ни кода. Собирать, запускать и настраивать здесь нечего: структура,
быстрый старт, переменные окружения и линтеры описаны в README каждого репозитория.

## Известные расхождения и ограничения

- **Ссылки на репозитории не открываются извне.** Все девять приватные, публичен только `.github`,
  поэтому для читателя без доступа к организации каждая ссылка из таблицы — 404.
- **iOS-приложения как продукта пока нет.** В `F-Rent-Mobile-iOS` в ветке `main` лежит одна
  заглушка README, весь код (SwiftUI, Xcode-проект, CI `ios.yml`) — в `develop`. Релизного
  workflow нет ни в одной ветке, так что merge PR в `main` там не создаст ни релиза, ни тега.
  Сайт раздаёт только Android-сборку — ссылок на App Store нет.
- **Прямые пуши в `main` — обычная практика, а не исключение для `F-Rent-Admin-Panel`.** Merge PR в
  `main` реально соблюдается в `F-Rent-Server` и `F-Rent-Mobile-Android` — только у них вершина
  `main` это merge-коммит PR и только у них есть автоматические релизные теги. В `F-Rent-Site`,
  `F-Rent-Web-Version`, `F-Rent-VK-Bot` и `F-Rent-Telegram-Bot` merge-коммитов в `main` нет вообще,
  в `F-Rent-Admin-Panel` и `F-Rent-Product-Bot` свежие коммиты тоже легли в `main` напрямую.
  Следствие: `release.yml` не срабатывает и релизов в этих репозиториях не появляется.
- **README разной свежести.** Полный набор разделов в ветке `main` есть у `F-Rent-Admin-Panel`,
  `F-Rent-Site`, `F-Rent-Web-Version`, `F-Rent-VK-Bot`, `F-Rent-Telegram-Bot` и
  `F-Rent-Product-Bot`. У `F-Rent-Server` и `F-Rent-Mobile-Android` в `main` пока README прежней
  структуры — то же содержание, но под другими заголовками («Переменные окружения», «Тесты»,
  «Локальная настройка», «Проверки и качество»), а приведённые к стандарту версии лежат в
  `develop`. У `F-Rent-Mobile-iOS` в `main` README из одной строки, подробный — тоже в `develop`.
- **Безопасность.** В части репозиториев исторически закоммичены рабочие значения — статический
  API-токен в шаблоне конфигурации, токен бота прямо в коде, доступы к тестовому хосту в
  dev-каталоге. Все такие значения считаем раскрытыми: они подлежат ротации и удалению из истории,
  детали и статус описаны в README соответствующих репозиториев. Сами значения ни здесь, ни в
  других README не публикуются; секреты для CI живут в GitHub Secrets, для прода — в `.env` на
  серверах.

**Сайт:** [f-rent.ru](https://f-rent.ru)
