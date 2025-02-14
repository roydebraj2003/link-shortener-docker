🏗 Link Shortener - Docker Compose Setup
This docker-compose.yml file provides a seamless way to deploy a link shortener application with the following services:

App Service 🏠 (Node.js + Express)
PostgreSQL Database 🗄
Redis Cache ⚡
With this setup, users can quickly spin up the entire application environment using Docker Compose without manually configuring each service.

📌 Services Overview
🚀 App (Link Shortener API)
Runs the Node.js backend for URL shortening.
Listens on port 5000 (mapped to localhost:5000).
Connects to PostgreSQL (DB_HOST: postgres) and Redis (REDIS_HOST: redis).
Restarts automatically if it crashes.
🗄 PostgreSQL Database
Stores shortened URLs in a relational database.
Uses admin / somepassword as the default credentials.
Runs on port 5432.
Includes an initialization SQL file (init.sql) for setting up tables.
Has a health check to ensure the database is ready before the app starts.
⚡ Redis Cache
Speeds up URL lookups using caching.
Runs on port 6379.
Uses persistent storage (redisdata volume).
📜 How to Use
🔧 Step 1: Install Docker & Docker Compose
Ensure you have Docker and Docker Compose installed:

bash
Copy
Edit
docker --version
docker compose version
🚀 Step 2: Run the Application
To start all services in detached mode:

bash
Copy
Edit
docker compose up -d
📊 Step 3: Check Running Containers
bash
Copy
Edit
docker ps
🛑 Stop & Remove Containers
bash
Copy
Edit
docker compose down -v
📂 Volumes & Data Persistence
pgdata - Stores PostgreSQL database data.
redisdata - Stores Redis cache data.
Even if you restart the containers, data remains persistent.

🌍 Networking
All services communicate internally via the app-network.

🔗 Modifications for Other Users
If someone wants to use this setup with their own database:

Change the POSTGRES_USER, POSTGRES_PASSWORD, and POSTGRES_DB values.
Remove the ./server/init.sql line if they don't need pre-loaded tables.
