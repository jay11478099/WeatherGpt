# WeatherGPT Setup Guide

This project contains a Flutter application and an XAMPP/PHP/MySQL admin backend.

## 1. Requirements

Install:

- Flutter SDK
- Android Studio or VS Code
- Git
- XAMPP (Apache and MySQL)
- Ollama (for local AI chat)
- A working internet connection for weather data

Check Flutter:

```bash
flutter doctor
```

## 2. Run the Flutter app

Open PowerShell in the Flutter folder:

```powershell
cd flutter_app
flutter pub get
flutter analyze
flutter run
```

For Windows desktop:

```powershell
flutter run -d windows
```

If Flutter reports missing packages, run:

```powershell
flutter clean
flutter pub get
```

## 3. Start XAMPP backend

1. Open the XAMPP Control Panel.
2. Start **Apache**.
3. Start **MySQL**.
4. Copy the `xampp_backend` folder into:

```text
C:\xampp\htdocs\WeatherGPT_XAMPP_Admin_Dashboard
```

5. Open phpMyAdmin:

```text
http://localhost/phpmyadmin
```

6. Create/select the `weathergpt` database.
7. Import:

```text
xampp_backend/database.sql
```

## 4. Open the admin dashboard

Open:

```text
http://localhost/WeatherGPT_XAMPP_Admin_Dashboard/admin/
```

Use the admin credentials supplied by your team. Change the default password before deployment.

## 5. Test backend APIs

The API files are inside:

```text
xampp_backend/api/
```

The database connection is configured in:

```text
xampp_backend/config/db.php
```

For a default XAMPP installation, the database host is usually `localhost`, the username is usually `root`, and the password is usually empty. Change these values if your MySQL setup is different.

## 6. Run Ollama AI

Install Ollama, then open a separate terminal:

```bash
ollama run llama3.2:3b
```

Keep Ollama running while testing AI chat. If your project uses another model, replace the model name with that model.

## 7. Common problems

### Missing Flutter packages

```bash
flutter clean
flutter pub get
```

### Database column error

Import the latest `database.sql`. If the error mentions a missing column, compare the existing table with the SQL file and add the missing column in phpMyAdmin.

### Apache or MySQL will not start

Check whether another program is using ports 80, 443, or 3306. Close the conflicting program or change the XAMPP port settings.

### Ollama chat does not work

Check that Ollama is installed, the model is downloaded, and the Ollama terminal is still running.

### Android device is not detected

Run:

```bash
flutter devices
```

Then enable USB debugging on the Android phone or start an emulator.

## 8. Recommended project order

1. Start XAMPP Apache and MySQL.
2. Import the database.
3. Start Ollama for AI chat.
4. Run `flutter pub get`.
5. Run the Flutter app.
6. Test login, weather, chat, and admin dashboard.

## 9. Security before public deployment

Do not commit real passwords, API keys, private user data, or production database credentials. Use environment variables or a protected server configuration for deployment.
