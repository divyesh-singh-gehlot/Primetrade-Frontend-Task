# Scalable Web App with Auth & Dashboard

A full-stack web application built with the MERN stack (MongoDB, Express.js, React, Node.js) featuring JWT-based authentication, a protected dashboard, and full CRUD functionality on a sample "Notes" entity.

![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB)
![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)

---

## Features

-   ✅ **User Authentication:** Secure user registration and login flow.
-   ✅ **JWT-Based Security:** Protected API routes using JSON Web Tokens.
-   ✅ **Protected Dashboard:** A private dashboard accessible only to authenticated users.
-   ✅ **CRUD Operations:** Full Create, Read, Update, and Delete functionality for user-specific notes.
-   ✅ **Responsive Design:** A clean, mobile-first UI built with TailwindCSS.
-   ✅ **Validation:** Both client-side and server-side validation for forms.

---

## Getting Started

Follow these instructions to get the project up and running on your local machine.

### Prerequisites

-   **Node.js** and **npm** (or yarn) installed.
-   A **MongoDB Connection String**. You can get a free one from [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).

### Installation

1.  **Clone the repository:**
    ```sh
    git clone <YOUR_REPOSITORY_URL>
    cd <YOUR_REPOSITORY_FOLDER>
    ```

2.  **Setup the Backend:**
    ```sh
    # Navigate to the backend folder
    cd webapp-backend

    # Install dependencies
    npm install

    # Create a .env file in the root of the backend folder
    # and add your environment variables
    touch .env
    ```
    Your `.env` file should look like this:
    ```
    MONGO_URI=your_mongodb_connection_string
    JWT_SECRET=a_very_strong_and_long_secret_key
    ```
    ```sh
    # Run the backend server
    npm run dev
    ```
    The backend will be running on `http://localhost:5000`.

3.  **Setup the Frontend:**
    ```sh
    # Open a new terminal and navigate to the frontend folder
    cd webapp-frontend

    # Install dependencies
    npm install

    # Run the frontend development server
    npm run dev
    ```
    The frontend will be available at `http://localhost:5173` (or another port if 5173 is busy).

---

## API Documentation

All API requests are routed through the base URL: `http://localhost:5000`.

### Authentication (`/api/auth`)

All routes in this section are **public**.

| Method | Endpoint    | Description                               | Body Example                                     |
| :----- | :---------- | :---------------------------------------- | :----------------------------------------------- |
| `POST` | `/register` | Creates a new user account.               | `{ "name": "...", "email": "...", "password": "..." }` |
| `POST` | `/login`    | Logs in a user and returns a JWT token.   | `{ "email": "...", "password": "..." }`             |

### Notes (`/api/notes`)

All routes in this section are **private** and require an `Authorization: Bearer <TOKEN>` header.

| Method   | Endpoint | Description                        | Body Example                                 |
| :------- | :------- | :--------------------------------- | :------------------------------------------- |
| `GET`    | `/`      | Gets all notes for the user.       | (None)                                       |
| `POST`   | `/`      | Creates a new note.                | `{ "title": "...", "content": "..." }`      |
| `PUT`    | `/:id`   | Updates a specific note.           | `{ "title": "...", "content": "..." }`      |
| `DELETE` | `/:id`   | Deletes a specific note.           | (None)                                       |

### User (`/api/users`)

This route is **private** and requires an `Authorization: Bearer <TOKEN>` header.

| Method | Endpoint  | Description                   | Body Example |
| :----- | :-------- | :---------------------------- | :----------- |
| `GET`  | `/profile`| Gets the current user's profile. | (None)       |

---

## Note on Scaling for Production

To handle more users, we need to set our app up so it can grow. Here are three simple steps:

### 1. Separate the Parts
Think of this app like a restaurant. We want the **storefront (frontend)** to be separate from the **kitchen (backend)**.

-   **Frontend (UI):** Host our React app on a fast, global service like **Vercel** or **Netlify**. This makes the user interface load instantly for everyone.
-   **Backend (API):** Put our Node.js code on a dedicated server platform like **Heroku** or **AWS**. This keeps our app's logic and data handling in one powerful place.

### 2. Prepare for More Customers
As the app gets popular, we'll need more "cooks in the kitchen."

-   We can a server that can **auto-scale**. This means it automatically adds more power or copies of our backend when traffic is high and scales back down to save money when it's quiet. This prevents our app from crashing during busy times.

### 3. Use a Professional Database
We can use a managed service like **MongoDB Atlas**.

-   They handle all the hard parts for us: security, backups, and scaling. If our database needs more power, we can upgrade it with just a click.

---

## License

Distributed under the MIT License. See `LICENSE` for more information.
