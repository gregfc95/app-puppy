# Project Puppy

A full-stack application featuring a Preact frontend, a Python Flask backend, and a MySQL database, all managed with Docker.

_Una app full-stack diseñada con un frontend de Preact, un backend de Python Flask, y una base de datos MySQL, todo manejado con Docker._

---

## 🛠️ Tech Stack

- **Frontend**: Preact, Material-UI
- **Backend**: Python, Flask, SQLAlchemy
- **Database**: MySQL
- **Containerization**: Docker

## 🚀 Getting Started | Comenzando

Follow these instructions to get the project up and running on your local machine.

_Este proyecto está diseñado para correr completamente dentro de contenedores de Docker_

### Prerequisites | Prerequisitos

Make sure you have the following installed:

_Asegurate de tener instalado:_

- [Git](https://git-scm.com/)
- [Docker & Docker Compose](https://www.docker.com/products/docker-desktop/)

### Setup

1.  **Clone the repository:** | **Clona el repositorio:**

    ```bash
    git clone <your-repository-url>
    cd <project-directory>
    ```

2.  **Create the environment file:** | **Crea el archivo de entorno:**
    Copy the example environment file. This file contains all the necessary credentials and configuration variables for the services.

    _Copia el archivo de ejemplo. Este archivo contiene todas las credenciales y variables de configuración necesarias para los servicios._

    ```bash
    cp .env.example .env
    ```

    _(Note: The default values in `.env.example` are configured to work with `docker-compose.yml` out of the box. You can modify them if needed.)_

3.  **Build and run the containers:** | **Construye y corre los contenedores:**
    This single command will build the images for the frontend and backend, pull the MySQL image, and start all the services in the background.

    _Este único comando construirá las imágenes para el frontend y el backend, descargará la imagen de MySQL y iniciará todos los servicios en segundo plano._

    ```bash
    docker-compose up --build -d
    ```

### **Accessing the Application**

Once the containers are running, the services will be available at:

_Una vez que los contenedores estén corriendo, los servicios estarán disponibles en:_

- **Frontend**: `http://localhost:8080`
- **Backend API**: `http://localhost:5001`
- **MySQL Database**: Connectable at `localhost:3306` (from your host machine)

---

## Scripts & Usage

Common commands to manage the Docker environment.

_Comandos comunes para manejar el entorno de Docker._

- **Stop all services:** | **Detener todos los servicios:**

  ```bash
  docker-compose down
  ```

- **View logs for all services:** | **Ver los logs de todos los servicios:**

  ```bash
  docker-compose logs -f
  ```

- **Access a running container's shell (e.g., the backend):** | **Acceder a la terminal de un contenedor (ej: el backend):**
  ```bash
  docker-compose exec backend /bin/bash
  ```

## Naming Conventions

To maintain a clean and consistent codebase, this project follows these strict naming conventions:

_Para mantener un código limpio y consistente, este proyecto sigue las siguientes convenciones de nombrado:_

- **Folders**: Always `kebab-case` (e.g., `user-profile`, `api-utils`).
- **Files**: Always `camelCase` (e.g., `apiServer.py`, `authController.js`).
- **Components & Classes**: Always `PascalCase` (e.g., `UserProfile.js`, `DatabaseManager`).
