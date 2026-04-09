# Tax Calculator

A simple full-stack application with Docker Compose, featuring:

- **Frontend:** React (Vite)
- **Backend:** Node.js (service-a and service-b)
- All services run in containers for easy development.

## Project Structure

```
app2-tax-calculator/
├── docker-compose.yml
├── node/
│   ├── service-a/   # Main API service
│   └── service-b/   # Tax calculation service
└── tax-calculator-frontend/  # React frontend
```

## How It Works

- **Frontend**: Users enter an amount and country. The app calls service-a.
- **service-a**: Receives the request, fetches tax info from service-b, and returns the total.
- **service-b**: Returns the tax rate for a given country.

## Prerequisites

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/)

## Running the App

1. Open a terminal in the `app2-tax-calculator` folder.
2. Build and start all services:
   ```
   docker compose up --build
   ```
3. Access the frontend at: [http://localhost:5173](http://localhost:5173)

## API Endpoints

- **service-a**
  - `GET /price?amount=100&country=IN`
    - Returns: `{ amount, tax, total, ... }`
- **service-b**
  - `GET /tax?country=IN`
    - Returns: `{ country, tax, ... }`

## Stopping the App

Press `Ctrl+C` in the terminal, then run:

```
docker compose down
```

## Troubleshooting

- If you see CORS errors, make sure you have the latest code and restart the containers.
- If ports are busy, stop other apps using those ports.
