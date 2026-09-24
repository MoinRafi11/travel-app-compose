# Travel App using Docker Compose

A containerized travel application built with **PHP, Apache, PostgreSQL, and Docker Compose**.

The application allows users to explore travel destinations and submit bookings. Destination and booking data are stored in PostgreSQL.

## Technologies Used

- PHP
- Apache
- PostgreSQL
- Docker
- Docker Compose
- HTML
- CSS
- PDO

## Project Structure

```text
travel-app-compose/
├── db/
│   └── init.sql
├── src/
│   └── index.php
├── .env
├── .env.example
├── .gitignore
├── docker-compose.yml
├── Dockerfile
└── README.md
```

## Architecture

The project uses two Docker Compose services:

- **travel-app** — PHP application running on Apache
- **travel_db** — PostgreSQL database

Both services communicate through a custom Docker network, while PostgreSQL data is persisted using a named volume.

```text
Browser
   │
   ▼
PHP + Apache
   │
   │ PDO
   ▼
PostgreSQL
```

## Database

The application uses PostgreSQL with two main tables:

### `destinations`

Stores available travel destinations, including their name, location, description, price, image, and category.

### `bookings`

Stores customer booking information such as name, email, selected destination, travel date, and number of guests.

The database is initialized using:

```text
db/init.sql
```

## Environment Variables

Database credentials and connection details are stored in `.env`.

Example:

```env
POSTGRES_DB=travel_db
POSTGRES_USER=travel_user
POSTGRES_PASSWORD=your_password

DB_HOST=travel_db
DB_PORT=5432
```

The `.env` file is excluded from Git using `.gitignore`.

## Running the Application

Build and start the containers:

```bash
docker compose up -d --build
```

Check the running services:

```bash
docker compose ps
```

Open the application:

```text
http://localhost:8085
```

## Stopping the Application

```bash
docker compose down
```

To remove the containers and PostgreSQL volume:

```bash
docker compose down -v
```

## Docker Features Demonstrated

- Dockerfile
- Docker Compose
- PHP + Apache containerization
- PostgreSQL container
- Container networking
- Named volumes
- Environment variables
- PostgreSQL health checks
- Service dependencies
- PHP–PostgreSQL communication using PDO

## Author

**M. Moin**