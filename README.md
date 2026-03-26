# BuyerForeSight — User Management API

A REST API for user management built with **Django REST Framework** and **SQLite**.

---

## Setup & Run Instructions

### Prerequisites

- Python 3.8 or higher
- pip

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/buyerforesight-user-api.git
cd buyerforesight-user-api
```

### 2. Create and Activate Virtual Environment

```bash
# macOS / Linux
python -m venv venv
source venv/bin/activate

# Windows
python -m venv venv
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install django djangorestframework
```

### 4. Apply Database Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Start the Server

```bash
python manage.py runserver
```

The API will be running at: **`http://127.0.0.1:8000`**

---

## API Endpoints

| Method   | Endpoint                      | Description           |
|----------|-------------------------------|-----------------------|
| GET      | `/users`                      | List all users        |
| GET      | `/users?search=`              | Search by name/email  |
| GET      | `/users?sort=name&order=asc`  | Sort users            |
| POST     | `/users`                      | Create a new user     |
| GET      | `/users/:id`                  | Get user by ID        |
| PUT      | `/users/:id`                  | Update a user         |
| DELETE   | `/users/:id`                  | Delete a user         |

---

## Assumptions & Notes

- **Database**: SQLite is used as the database. The `db.sqlite3` file is auto-generated when migrations are run — no manual setup required.
- **Partial Updates**: The `PUT /users/:id` endpoint supports both full and partial updates. You do not need to send all fields; only the fields you want to change are required.
- **Search**: The `?search=` filter matches against both `name` and `email` fields and is case-insensitive.
- **Sort Fields**: Supported sort fields are `name`, `email`, `age`, and `created_at`. Default sort is by `name` ascending.
- **Validation**: Field validation is handled by DRF's ModelSerializer. Email must be unique and properly formatted. Name is required. Age is optional but must be a positive integer if provided.
- **No Authentication**: This API does not include authentication or authorization as it was not part of the assessment scope.
- **No External Dependencies**: The project only requires `django` and `djangorestframework` — no additional packages or services needed.