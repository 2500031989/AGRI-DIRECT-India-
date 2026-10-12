# AGRI-DIRECT-India-
AGRI DIRECT India - A fairer food market
```html
<!DOCTYPE html>
<html>
<head>
    <title>Login and Signup</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(120deg, #74b9ff, #a29bfe);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
        }

        .box {
            background: white;
            padding: 30px;
            width: 320px;
            border-radius: 15px;
            box-shadow: 0 5px 20px #555;
            text-align: center;
        }

        input {
            width: 90%;
            padding: 11px;
            margin: 8px 0;
            border: 1px solid #ccc;
            border-radius: 6px;
            box-sizing: border-box;
        }

        button {
            width: 98%;
            padding: 11px;
            margin-top: 10px;
            background: #34495e;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
        }

        button:hover {
            background: #2c3e50;
        }

        #message {
            font-weight: bold;
            overflow-wrap: anywhere;
        }
    </style>
</head>

<body>
    <div class="box">
        <h2>Create Account</h2>

        <input id="name" type="text" placeholder="Full Name">
        <input id="email" type="email" placeholder="Email">
        <input id="password" type="password"
               placeholder="Password">

        <button onclick="signup()">Sign Up</button>

        <hr>

        <h2>Login</h2>

        <input id="loginEmail" type="email"
               placeholder="Email">
        <input id="loginPassword" type="password"
               placeholder="Password">

        <button onclick="login()">Login</button>

        <p id="message"></p>
    </div>

    <script>
        function signup() {
            let name = document.getElementById("name").value.trim();
            let email = document.getElementById("email").value.trim().toLowerCase();
            let password = document.getElementById("password").value;
            let message = document.getElementById("message");

            if (name === "" || email === "" || password === "") {
                message.innerHTML = "Please fill all fields!";
                message.style.color = "red";
                return;
            }

            if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
                message.innerHTML = "Enter a valid email address!";
                message.style.color = "red";
                return;
            }

            let users = JSON.parse(localStorage.getItem("users")) || [];

            let existingUser = users.find(user => user.email === email);

            if (existingUser) {
                message.innerHTML = "Email already registered!";
                message.style.color = "red";
                return;
            }

            let user = {
                name: name,
                email: email,
                password: password
            };

            users.push(user);
            localStorage.setItem("users", JSON.stringify(users));

            message.innerHTML = "Signup Successful! Please Login.";
            message.style.color = "green";

            document.getElementById("name").value = "";
            document.getElementById("email").value = "";
            document.getElementById("password").value = "";
        }

        function login() {
            let email = document.getElementById("loginEmail").value.trim().toLowerCase();
            let password = document.getElementById("loginPassword").value;
            let message = document.getElementById("message");

            if (email === "" || password === "") {
                message.innerHTML = "Please enter email and password!";
                message.style.color = "red";
                return;
            }

            let users = JSON.parse(localStorage.getItem("users")) || [];

            let user = users.find(
                user => user.email === email &&
                        user.password === password
            );

            if (user) {
                message.innerHTML = "Welcome, " + user.name + "!";
                message.style.color = "green";
            } else {
                message.innerHTML = "Invalid Email or Password!";
                message.style.color = "red";
            }
        }
    </script>
</body>
</html>
```
