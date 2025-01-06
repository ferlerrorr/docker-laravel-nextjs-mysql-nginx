
# Dockerized - Laravel - NextJs - Mysql - phpMyAdmin 

The project aims to establish a self-hosted, decoupled architecture that separates the backend and frontend technologies. This approach provides flexibility, scalability, and maintainability, enabling each part to be developed and deployed independently.

## Headless Backend (Laravel)

Laravel is used as a headless backend, meaning it serves only as an API provider without any direct rendering of views. In this setup:

Purpose: Laravel handles core application logic, database interactions, user authentication, and serves RESTful or GraphQL APIs.

### Key Advantages:
Decoupling: The backend focuses solely on providing data and managing the application logic.
Flexibility: The APIs can be consumed by various frontends or other clients like mobile apps, IoT devices, or external services.
Performance: Optimized backend performance without the burden of rendering HTML or managing frontend resources.

## Frontend (Next.js)

Next.js is used as the frontend to consume the APIs provided by Laravel. In this role:

Purpose: Next.js manages the user interface, routing, and client-side interactions.

### Key Advantages:
SSR & ISR: Supports Server-Side Rendering (SSR) and Incremental Static Regeneration (ISR) for optimal performance and SEO.
React-based: Leverages React for creating dynamic, reusable components.
API Integration: Directly consumes Laravel’s APIs to render data-driven pages and handle user interactions.
Static Exporting: Capable of generating static pages for improved load times and reduced server load.

---

## Prerequisites

Ensure the following dependencies are installed on your system:

- **Composer**: For managing PHP dependencies.
- **Node.js**: For managing JavaScript dependencies.

---

## System Overview

The project uses Docker to set up its environment. Below are the services and their respective ports:

| Service       | Description                        | Port  |
|---------------|------------------------------------|-------|
| **Web Server** | Serves web content (Nginx)         | 80 (HTTP), 443 (HTTPS) |
| **Database**   | MySQL database for data handling   | 3306  |
| **phpMyAdmin** | Database management interface     | 8080  |
| **API (Laravel 10)**        | Backend logic interactions        | 8000  |
| **UI (NextJS + React)**         | Frontend of the application       | 3000  |

---

## Setup Instructions

### Step 1: Clone the Repository

```sh
git clone <repository-url>
cd Project-Directory
```

### Step 2: Create Required Directories

Create the `api` and `ui` directories inside the `src` directory:

```sh
mkdir -p src/api
mkdir -p src/ui
```

Your project structure should look like this:

```
src/
├── api/
├── ui/
```

### Step 3: Configure Environment Variables

Copy the example environment file and configure it as necessary. This is for the `.env.example` file located in the root directory:

```sh
cp .env.example .env
```

## Frontend (UI) Setup

1. Navigate to the UI source folder:

   ```sh
   cd src/ui
   ```

2. Initialize the frontend using Next.js (with TypeScript):

   ```sh
   npx create-next-app@latest . --typescript
   ```

---

## Backend (API) Setup

1. Navigate to the API source folder:

   ```sh
   cd src/api
   ```

2. Initialize the Laravel project:

   Incase here the PHP Version in Container is PHP8.1 use laravel 10 here

   ```sh
   composer create-project laravel/laravel . --prefer-dist
   ```
   or

   ```sh
   composer create-project laravel/laravel="10" .
   ```


---

## Running the Project with Docker

1. Navigate to the project directory:

   ```sh
   cd Project-Directory
   ```

2. Build and run the containers:

   ```sh
   docker-compose up --build
   ```

---

## Accessing the Application

Once the containers are running, you can access the application services:

| Component     | URL                                |
|---------------|------------------------------------|
| **UI**        | [http://127.0.0.1:80](http://127.0.0.1:80) or [http://localhost:80](http://localhost:80) |
| **API**       | [http://127.0.0.1:8000](http://127.0.0.1:8000) or [http://localhost:8000](http://localhost:8000) |
| **phpMyAdmin**| [http://127.0.0.1:8080](http://127.0.0.1:8080) or [http://localhost:8080](http://localhost:8080) |

---

### Notes

- Customize the `.env` file based on your specific environment setup.
- Ensure Docker is installed and running before executing `docker-compose` commands.

---

## License

[Specify your project's license here.]
