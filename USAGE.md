# Using the Rock of Ages API

This document outlines how to use the Rock of Ages API for managing your collection of rocks.

## Authentication

To use the API, you must first register a user and then use the provided token for all subsequent requests.

### Registering a User

To register a new user, make a `POST` request to `/register` with the following JSON body:

```json
{
    "email": "your_email@example.com",
    "password": "your_password",
    "first_name": "Your",
    "last_name": "Name"
}
```

The response will contain an authentication token.

### Logging In

To log in, make a `POST` request to `/login` with the following JSON body:

```json
{
    "email": "your_email@example.com",
    "password": "your_password"
}
```

The response will contain the same authentication token.

### Making Authenticated Requests

Include the token in the `Authorization` header for all API requests:

```
Authorization: Token YOUR_AUTH_TOKEN
```

## API Endpoints

### Types

The `/types` endpoint manages the different types of rocks available.

*   **`GET /types`**: Get a list of all rock types.
*   **`GET /types/{id}`**: Get a single rock type by its ID.

### Rocks

The `/rocks` endpoint manages the rocks in your collection.

*   **`GET /rocks`**: Get a list of all rocks in your collection.
*   **`GET /rocks/{id}`**: Get a single rock by its ID.
*   **`POST /rocks`**: Add a new rock to your collection.

    **Request Body:**

    ```json
    {
        "name": "Your Rock Name",
        "weight": 12.34,
        "type_id": 1
    }
    ```

*   **`PUT /rocks/{id}`**: Update an existing rock.

    **Request Body:**

    ```json
    {
        "name": "Updated Rock Name",
        "weight": 56.78,
        "type_id": 2
    }
    ```

*   **`DELETE /rocks/{id}`**: Delete a rock from your collection.

## Project Structure

```
/home/migiberto/nss-cloud-class/rock-of-ages-backend/rock-of-ages-api/
├───.gitignore
├───.pylintrc
├───.python-version
├───docker
├───Dockerfile
├───manage.py
├───Pipfile
├───Pipfile.lock
├───README.md
├───seed_database.sh
├───.git/...
├───.github/
│   └───workflows/
│       ├───deploy.yml
│       └───testBuildPush.yml
├───.vscode/
│   ├───launch.json
│   └───settings.json
├───rockapi/
│   ├───__init__.py
│   ├───admin.py
│   ├───apps.py
│   ├───test.py
│   ├───fixtures/
│   │   ├───rocks.json
│   │   ├───tokens.json
│   │   ├───types.json
│   │   └───users.json
│   ├───migrations/
│   │   ├───__init__.py
│   │   └───0001_initial.py
│   ├───models/
│   │   ├───__init__.py
│   │   ├───rock.py
│   │   └───type.py
│   └───views/
│       ├───__init__.py
│       ├───auth.py
│       ├───rock_view.py
│       ├───template.py
│       └───type_view.py
└───rockproject/
    ├───__init__.py
    ├───asgi.py
    ├───settings.py
    ├───urls.py
    └───wsgi.py
```