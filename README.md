# 🧩 CoverageX To-Do App – Dockerized Deployment Guide

This repository provides a simple way to deploy and run the full-stack **CoverageX To-Do App** using **Docker Compose**.  
It automatically sets up the **frontend**, **backend**, and **database** containers.

---

## 🚀 Tech Stack

- **Frontend:** React (`maleeshasa/to-do-app-frontend:v1`)  
- **Backend:** Spring Boot (`maleeshasa/to-do-app-backend:v1`)  
- **Database:** PostgreSQL (`bitnamilegacy/postgresql:17.5.0`)

---

## ✅ Prerequisites

Before starting, make sure you have the following installed:

- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- Docker Compose (included with Docker Desktop)

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the Deployment Repository

Clone the GitHub repository that contains the `docker-compose.yml` and `README` files:

```bash
git clone https://github.com/pixel-mind-learning/to-do-app-readme-files.git
cd to-do-app-readme-files
```

---

### 2️⃣ Start the Application Stack

Run the following command to start all services in detached mode:

```bash
docker compose up -d
```

This will **pull**, **create**, and **run** the following containers automatically:

- `maleeshasa/to-do-app-frontend:v1`
- `maleeshasa/to-do-app-backend:v1`
- `bitnamilegacy/postgresql:17.5.0`

---

### 3️⃣ Restore the Database Dump

Once all containers are up and running, restore the PostgreSQL database using the provided `dump.sql` file in to-do-app-readme-files folder.

1. Copy the dump file into the PostgreSQL container:

   ```bash
   docker cp "<your-dump-location>/dump.sql" mypostgresqldb:/dump.dump
   ```

2. Restore the dump inside the container:

   ```bash
   docker exec -it mypostgresqldb pg_restore -U postgres -d coveragex_todo_management /dump.dump
   ```

> 💡 **Tip:**  
> - Replace `<your-dump-location>` with the actual local path to your dump file.  
> - Ensure the container name `mypostgresqldb` matches the name used in the `docker-compose.yml` file.  
> - Repository containing the dump:  
>   [https://github.com/pixel-mind-learning/to-do-app-readme-files.git](https://github.com/pixel-mind-learning/to-do-app-readme-files.git)

---

## 🌐 Access the Application

| Service | URL |
|----------|------|
| 🖥️ Frontend (React UI) | [http://localhost:8080](http://localhost:8080) |
| ⚙️ Backend (Spring Boot API) | [http://localhost:8082/api/tasks](http://localhost:8082/api/tasks) |


---

Made with ❤️ by **Maleesha Sandakalum**
