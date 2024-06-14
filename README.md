# Login-Autentication
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login and Registration</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 400px;
            margin: 100px auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
            color: #333;
        }
        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button[type="submit"] {
            width: 100%;
            padding: 10px;
            margin-top: 10px;
            background-color: #4caf50;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button[type="submit"]:hover {
            background-color: #45a049;
        }
        .error-message {
            color: red;
            margin-bottom: 10px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Registration</h2>
        <div id="register-error-message" class="error-message"></div>
        <form id="register-form">
            <label for="register-username">Username:</label>
            <input type="text" id="register-username" name="register-username" required>
            <label for="register-password">Password:</label>
            <input type="password" id="register-password" name="register-password" required>
            <button type="button" onclick="registerUser()">Register</button>
        </form>
        <hr>
        <h2>Login</h2>
        <div id="login-error-message" class="error-message"></div>
        <form id="login-form">
            <label for="login-username">Username:</label>
            <input type="text" id="login-username" name="login-username" required>
            <label for="login-password">Password:</label>
            <input type="password" id="login-password" name="login-password" required>
            <button type="button" onclick="validateLogin()">Login</button>
        </form>
    </div>

    <script>
        // Dummy user database (replace with a proper database in a real application)
        var users = {};

        function registerUser() {
            var registerUsername = document.getElementById("register-username").value;
            var registerPassword = document.getElementById("register-password").value;

            // Check if the username is already registered
            if (registerUsername in users) {
                document.getElementById("register-error-message").innerText = "Username already exists";
            } else {
                // Register the user
                users[registerUsername] = { username: registerUsername, password: registerPassword };
                alert("Registration successful! Please login.");
            }
        }

        function validateLogin() {
            var loginUsername = document.getElementById("login-username").value;
            var loginPassword = document.getElementById("login-password").value;

            // Check if the username exists and the password matches
            if (loginUsername in users && users[loginUsername]['password'] === loginPassword) {
                alert("Login successful!");
                // For demo purposes, redirect to a secured page
                window.location.href = "secured_page.html";
            } else {
                document.getElementById("login-error-message").innerText = "Invalid username or password";
            }
        }
    </script>
</body>
</html>
