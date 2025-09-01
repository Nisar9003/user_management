# User Management Flask Application

This is a Flask-based web application for user management, allowing users to register, log in, log out, view all users, update user details, delete users, and manage their profile. It uses Flask-SQLAlchemy with SQLite for persistent storage and Werkzeug for secure password hashing.

## Features
- **Register**: Create a new user with a unique username and email.
- **Login/Logout**: Authenticate users and manage sessions.
- **User List**: View all registered users (requires login).
- **Update/Delete Users**: Modify or remove user accounts (requires login).
- **Profile Management**: Update email and password for the logged-in user.
- **Flash Messages**: Display success or error messages for user actions.

## Prerequisites
- Python 3.8 or higher
- Virtualenv (recommended for isolated environments)

## Setup Instructions

1. **Clone or Set Up the Project**:
   - Ensure the project files are in `C:\Users\Mg\OneDrive\Desktop\file_manage\`.
   - The project structure should be:
     ```
     file_manage/
     ├── app.py
     ├── templates/
     │   ├── index.html
     │   ├── register.html
     │   ├── login.html
     │   ├── users.html
     │   ├── update.html
     │   ├── profile.html
     ├── README.md
     ├── requirements.txt
     ```

2. **Create a Virtual Environment**:
   ```bash
   cd C:\Users\Mg\OneDrive\Desktop\file_manage
   python -m venv .venv
   .venv\Scripts\activate
   ```

3. **Install Dependencies**:
   - Install required packages:
     ```bash
     pip install -r requirements.txt
     ```

4. **Set Up the Database**:
   - The SQLite database (`database.db`) is created automatically when you run `app.py` for the first time.
   - No manual database setup is required.

5. **Run the Application**:
   - Start the Flask development server:
     ```bash
     python app.py
     ```
   - The app will run on `http://127.0.0.1:5000` (or `http://0.0.0.0:5000`).

## Usage
1. **Access the Application**:
   - Open `http://127.0.0.1:5000` in your browser.
   - If not logged in, you’ll be redirected to `/login`.

2. **Register a User**:
   - Go to `/register`.
   - Enter a unique username, email, and password.
   - On success, you’ll be redirected to `/login` with a success message.

3. **Log In**:
   - Go to `/login`.
   - Enter your username and password.
   - On success, you’ll be redirected to `/` (index page).

4. **View Users**:
   - Go to `/users` (requires login).
   - See a list of all registered users.

5. **Update/Delete Users**:
   - Go to `/update/<user_id>` to modify a user’s email.
   - Go to `/delete/<user_id>` to delete a user.

6. **Manage Profile**:
   - Go to `/profile` (requires login).
   - Update your email or password.

7. **Log Out**:
   - Go to `/logout` to end the session.

## Routes
- `GET /`: Index page (shows username if logged in, else redirects to `/login`).
- `GET/POST /register`: Register a new user.
- `GET/POST /login`: Log in a user.
- `GET /logout`: Log out the current user.
- `GET /users`: List all users (requires login).
- `GET/POST /update/<user_id>`: Update a user’s email (requires login).
- `GET /delete/<user_id>`: Delete a user (requires login).
- `GET/POST /profile`: Update the current user’s email or password (requires login).

## Dependencies
See `requirements.txt` for the full list:
- Flask: Web framework
- Flask-SQLAlchemy: ORM for SQLite
- Werkzeug: Password hashing utilities

## Notes
- **Security**: The `SECRET_KEY` in `app.py` is set to `your_secret_key`. Replace it with a secure random key (e.g., generated with `os.urandom(24).hex()`) for production.
- **Production**: The Flask development server is not suitable for production. Use a WSGI server like Gunicorn:
  ```bash
  pip install gunicorn
  gunicorn --workers 4 --bind 0.0.0.0:5000 app:app
  ```
- **Database**: SQLite is used for simplicity. For production, consider PostgreSQL or MySQL.
- **Templates**: Ensure `templates/` contains `index.html`, `register.html`, `login.html`, `users.html`, `update.html`, and `profile.html`. These are not provided here but should match the routes in `app.py`.

## Troubleshooting
- **404 Errors**: Ensure all templates exist in `templates/`.
- **Database Issues**: Verify `database.db` is created in the project root after running `app.py`.
- **Login Failures**: Check username/password and ensure the user exists in the database.
- **Flash Messages**: Ensure templates render flash messages (e.g., using `get_flashed_messages()`).

For further assistance, check the Flask documentation or provide error logs for debugging.