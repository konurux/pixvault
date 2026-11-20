# PixVault — Digital Asset & Portfolio Platform

Веб-платформа для дизайнеров: галерея работ для развития насмотренности, мудборд, тренажёр «Какая работа сильнее?» и личное портфолио с короткой ссылкой `/u/имя`.

Сайт: https://diplom-kappa-three.vercel.app

## Стек

- **Клиент** — React 19, React Router 7, Tailwind CSS, Radix UI (`frontend/`)
- **Сервер** — Python 3.12, FastAPI, Motor (`backend/`)
- **База** — MongoDB, изображения хранятся в GridFS
- **Хостинг** — Vercel (клиент, прокси `/api`) и Render (сервер)

## Локальный запуск

Нужны Python 3.12, Node.js 20 или новее и MongoDB.

Сервер:

```bash
cd backend
python -m venv venv
venv/bin/pip install -r requirements-dev.txt
cp .env.example .env   # заполните значения
venv/bin/uvicorn server:app --port 8000
```

Клиент (в другом терминале):

```bash
cd frontend
npm install
echo "REACT_APP_BACKEND_URL=http://localhost:8000" > .env
npm start
```

Сайт откроется на http://localhost:3000.

## Тесты

Интеграционные тесты API запускаются против работающего сервера:

```bash
cd backend
TEST_API_URL=http://127.0.0.1:8000 TEST_ADMIN_EMAIL=... TEST_ADMIN_PASSWORD=... venv/bin/python -m pytest tests -q
```

## Деплой

Изменения попадают на сайт после слияния в ветку `main`: Vercel и Render собирают новую версию автоматически.
