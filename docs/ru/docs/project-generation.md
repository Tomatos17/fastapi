# Full Stack FastAPI Шаблон

Шаблоны обычно идут с определенной настройкой, но они разработаны гибкими и настраиваемыми. Это позволяет вам модифицировать и адаптировать их в соответствии с требованиями вашего проекта, превращая их в отличную отправную точку. 🏁

Вы можете использовать этот шаблон, чтобы начать, так как он включает множество начальных настроек, безопасности, базу данных и некоторые API эндпоинты уже готовы.

Репозиторий на GitHub: <a href="https://github.com/tiangolo/full-stack-fastapi-template" class="external-link" target="_blank">Full Stack FastAPI Template</a>

## Full Stack FastAPI Шаблон - Технологии и Особенности

- ⚡ [**FastAPI**](https://fastapi.tiangolo.com) для Python бэкенда API.
    - 🧰 [SQLModel](https://sqlmodel.tiangolo.com) для взаимодействия Python с SQL базой данных (ORM).
    - 🔍 [Pydantic](https://docs.pydantic.dev), используемый FastAPI, для валидации данных и управления настройками.
    - 💾 [PostgreSQL](https://www.postgresql.org) в качестве SQL базы данных.
- 🚀 [React](https://react.dev) для фронтенда.
    - 💃 Использование TypeScript, hooks, [Vite](https://vitejs.dev), и других компонентов современного стека фронтенда.
    - 🎨 [Chakra UI](https://chakra-ui.com) для компонентов фронтенда.
    - 🤖 Автоматически сгенерированный фронтенд клиент.
    - 🧪 [Playwright](https://playwright.dev) для End-to-End тестирования.
    - 🦇 Поддержка темного режима.
- 🐋 [Docker Compose](https://www.docker.com) для разработки и продакшна.
- 🔒 Безопасное хеширование паролей по умолчанию.
- 🔑 Аутентификация с помощью JWT токенов.
- 📫 Восстановление пароля через email.
- ✅ Тесты с использованием [Pytest](https://pytest.org).
- 📞 [Traefik](https://traefik.io) в качестве реверс-прокси / балансировщика нагрузки.
- 🚢 Инструкции по развёртыванию с Docker Compose, включая настройку фронтенд прокси Traefik для автоматического управления HTTPS сертификатами.
- 🏭 CI (непрерывная интеграция) и CD (непрерывное развёртывание) на базе GitHub Actions.
