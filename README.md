
# Authentication API

This project is an authentication API using Django REST Framework (DRF) with JWT for secure user registration, login, profile management, password change, and password reset functionalities.

## Overview
This API provides user authentication features, including:

- **User Registration**
- **User Login**
- **Profile Access**
- **Password Change**
- **Password Reset**

The API uses JWT (JSON Web Tokens) for authentication and authorization. Users must register to create an account, log in to receive access tokens, and then use those tokens to access protected endpoints.

## Endpoints Overview
Here is a list of the available endpoints in the API:


| Endpoint               | Method | Description                        | Authentication |
|------------------------|--------|------------------------------------|------------|
| `/api/user/register/`           | POST   | Register a new user | No        |
| `/api/user/login/`   | POST   | Log in a user and get JWT tokens       | No        |
| `/api/user/profile/`           | GET   | Get the authenticated user's profile | Yes (JWT)        |
| `/api/user/changepassword/`   | POST   | Change the user’s password       | Yes (JWT)        |
| `/api/user/send-reset-password/`           | POST   | Send an email to reset the password | No        |
| `/api/user/reset-password/<uid>/<token>/`   | POST   | Reset the password with a valid token       | Yes (JWT)        |

## Detailed Endpoints and Usage

### 1. User Registration
- URL: /api/user/register/
- Method: POST

- Description: Registers a new user. The user must provide an email, name, password, confirm password, and accept the terms and conditions.

### Request Example:
```bash
{
  "email": "sohail@example.com",
  "name": "Sohail Ahmad",
  "password": "password123",
  "password2": "password123",
  "terms_conditions": "True"
}
```

### Validation:
- The API will check if the passwords match (password and password2).
- It will ensure that the email is unique.
- The terms_conditions field must be true (accepted).

### Response (Success):

```bash
{
  "token": {
    "refresh": "your-refresh-token",
    "access": "your-access-token"
  },

  "msg": "Registration Successful"
}
```

### 2. User Login
- URL: /api/user/login/

- Method: POST

- Description: Authenticates the user and returns JWT tokens (access and refresh).

### Request Example:
```bash
{
  "email": "sohail@example.com",
  "password": "password123"
}
```
### Response (Success):
```bash
{
  "token": {
    "refresh": "your-refresh-token",
    "access": "your-access-token"
  },

  "msg": "Login Successful"
}
```

### 3. User Profile
- URL: /api/user/profile/

- Method: GET

- Authentication Required: Yes (JWT Token)

- Description: Fetches the profile information of the authenticated user.

**Headers:**
```bash
Authorization: Bearer <access-token>
```

### Response (Success):
```bash
{
  "id": 1,
  "email": "sohail@example.com",
  "name": "Sohail Ahmad"
}
```

### 4. Change Password
- URL: /api/user/changepassword/

- Method: POST

- Authentication Required: Yes (JWT Token)

- Description: Allows the authenticated user to change their password.

### Request Example:
```bash
{
  "password": "newpassword123",
  "password2": "newpassword123"
}
```

### Response (Success):
```bash
{
  "msg": "Password Changed Successfully"
}
```

### 5. Send Password Reset Email
- URL: /api/user/send-reset-password/

- Method: POST

- Description: Sends an email with a password reset link to the registered user. The link contains a token and user ID.

### Request Example:

```bash
{
  "email": "sidra@example.com"
}
```

### Response (Success):

```bash
{
  "msg": "Password Reset Link sent. Please check your Email"
}
```
### Email Content:
The email will contain a link in the format:
```bash
http://127.0.0.1:8000/api/user/reset-password/<uid>/<token>/
```
### 6. Password Reset
- URL: /api/user/reset-password/<uid>/<token>/

- Method: POST

- Description: Resets the password for a user using the provided token from the password reset email.

### Request Example:
```bash
{
  "password": "newpassword123",
  "password2": "newpassword123"
}
```

### Response (Success):
```bash
{
  "msg": "Password Reset Successfully"
}
```
## Installation

1. **Clone the repository:**
    ```bash
    https://github.com/Sohail342/Auth-API-with-JWT-Authentication.git

    ```

2. **Create a virtual environment:** (optional but recommended)
    ```bash
    python3 -m venv env
    source env/bin/activate  # On Windows use `env\Scripts\activate`
    ```

3. **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
    **Be sure in project directory to install requirements.txt** 

4. **Make migrations:**
    ```bash
    python manage.py makemigrations
    ```

5. **Run migrations:**
    ```bash
    python manage.py migrate
    ```

6. **Create a superuser:**
    ```bash
    python manage.py createsuperuser
    ```

7. **Run the development server:**
    ```bash
    python manage.py runserver
    ```

## Contact

If you have any questions or feedback, feel free to reach out:

<p align="left">
<a href="https://wa.me/+923431285354" target="blank"><img align="center" src="https://img.icons8.com/color/48/000000/whatsapp.png" alt="WhatsApp" height="30" width="40" /></a>
<a href="https://www.hackerrank.com/sohail_ahmad342" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/hackerrank.svg" alt="sohail_ahmad342" height="30" width="40" /></a>
<a href="https://www.linkedin.com/in/sohailahmad3428041928/" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="sohail-ahmad342" height="30" width="40" /></a>
<a href="https://instagram.com/sohail_ahmed113" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="sohail_ahmed113" height="30" width="40" /></a>
<a href="mailto:sohailahmed34280@gmail.com" target="blank"><img align="center" src="https://img.icons8.com/ios-filled/50/000000/email-open.png" alt="Email" height="30" width="40" /></a>
</p>


