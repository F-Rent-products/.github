<p align="center">
  <img src="f-rent-icon.png" alt="F-Rent" width="120" height="120">
</p>

<h1 align="center">F-Rent</h1>

<p align="center">
  Аренда вещей напрямую между людьми
</p>

**F-Rent** — платформа P2P-аренды: люди сдают вещи, которыми редко пользуются, и берут нужное
рядом с собой на удобный срок — инструменты, техника, электроника, спортивный инвентарь и многое
другое. Внутри приложения — поиск, чат с владельцем, оплата аренды и фотофиксация вещи до передачи
и после возврата.

Продукт живёт в мобильных приложениях для Android и iOS, за ними — бэкенд на FastAPI с MySQL,
админка для модерации, боты поддержки и модерации в VK и Telegram и сайт f-rent.ru. Всё это лежит
в репозиториях ниже.

## Репозитории

| Репозиторий                                                                       | Назначение                                                                       | Стек                                          |
| --------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | --------------------------------------------- |
| [F-Rent-Server](https://github.com/F-Rent-products/F-Rent-Server)                 | Бэкенд и API платформы: пользователи, товары, аренды, чаты, платежи, модерация   | Python, FastAPI, SQLAlchemy, MySQL, Docker    |
| [F-Rent-Mobile-Android](https://github.com/F-Rent-products/F-Rent-Mobile-Android) | Мобильное приложение для Android                                                 | Kotlin, Retrofit/OkHttp                       |
| [F-Rent-Mobile-iOS](https://github.com/F-Rent-products/F-Rent-Mobile-iOS)         | Мобильное приложение для iOS                                                     | Swift                                         |
| [F-Rent-Admin-Panel](https://github.com/F-Rent-products/F-Rent-Admin-Panel)       | Админка: модерация товаров, пользователи, работа с заявками                      | React, TypeScript, Vite, Tailwind CSS         |
| [F-Rent-Web-Version](https://github.com/F-Rent-products/F-Rent-Web-Version)       | Задел под веб-версию приложения, кода пока нет                                   | не выбран                                     |
| [F-Rent-VK-Bot](https://github.com/F-Rent-products/F-Rent-VK-Bot)                 | Бот поддержки: обращения пользователей из VK, заявки для админов в VK и Telegram | Python, vk_api, aiogram, MySQL, Redis, Docker |
| [F-Rent-Telegram-Bot](https://github.com/F-Rent-products/F-Rent-Telegram-Bot)     | Бот набора бета-тестеров: регистрация, рассылки, выгрузка списка                 | Python, python-telegram-bot, SQLite           |
| [F-Rent-Product-Bot](https://github.com/F-Rent-products/F-Rent-Product-Bot)       | Бот модерации: уведомления в Telegram о новых товарах, ждущих проверки           | Python, PyMySQL, Telegram Bot API             |
| [F-Rent-Site](https://github.com/F-Rent-products/F-Rent-Site)                     | Сайт f-rent.ru: лендинг и юридические страницы                                   | HTML, Tailwind CSS                            |

## Как мы работаем

Процесс во всех репозиториях одинаковый:

- разработка идёт в ветке `develop`;
- в `main` изменения попадают только через pull request;
- при merge PR в `main` релиз создаётся автоматически: заголовок релиза = заголовок PR, описание =
  тело PR, архивы с исходниками прикладывает GitHub;
- исключение — `F-Rent-Admin-Panel`: там исторически коммитят прямо в `main`;
- у каждого репозитория свой README со структурой, быстрым стартом, конфигурацией и линтерами.

**Сайт:** [f-rent.ru](https://f-rent.ru)
