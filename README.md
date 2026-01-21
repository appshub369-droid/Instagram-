<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Login • Instagram</title>
    <!-- Google Fonts for the "Instagram" logo -->
    <link href="https://fonts.googleapis.com/css2?family=Grand+Hotel&display=swap" rel="stylesheet">
    <style>
        /* --- General Reset & Body Styles --- */
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: #fafafa;
            margin: 0;
            color: #262626;
        }
        
        * { box-sizing: border-box; }

        /* --- Login Page Styles --- */
        main {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            padding: 20px;
        }

        .login-container {
            background-color: #fff;
            border: 1px solid #dbdbdb;
            width: 100%;
            max-width: 350px;
            padding: 40px;
            text-align: center;
        }

        .login-logo {
            font-family: 'Grand Hotel', cursive;
            font-size: 3.5rem;
            margin-bottom: 30px;
        }

        .login-form input {
            width: 100%;
            padding: 10px;
            margin-bottom: 6px;
            border: 1px solid #dbdbdb;
            border-radius: 3px;
            background-color: #fafafa;
            font-size: 12px;
        }

        .login-btn {
            background-color: #0095f6;
            color: #fff;
            border: none;
            border-radius: 8px;
            padding: 8px;
            width: 100%;
            font-weight: 600;
            cursor: pointer;
            margin-top: 15px;
            opacity: 0.4; /* Button is disabled by default */
        }

        .login-btn.enabled {
            opacity: 1; /* Style for when the button is active */
        }

    </style>
</head>
<body>

    <main>
        <div class="login-container">
            <h1 class="login-logo">Instagram</h1>
            <form id="redirect-form" class="login-form">
                <input type="text" id="username" placeholder="Phone number, username, or email" required>
                <input type="password" id="password" placeholder="Password" required>
                <button type="submit" id="login-button" class="login-btn" disabled>Log In</button>
            </form>
        </div>
    </main>

    <script>
        // --- Get the elements from the page ---
        const redirectForm = document.getElementById('redirect-form');
        const usernameInput = document.getElementById('username');
        const passwordInput = document.getElementById('password');
        const loginButton = document.getElementById('login-button');

        // --- Function to check if both input fields have text ---
        function validateForm() {
            const username = usernameInput.value.trim();
            const password = passwordInput.value.trim();
            
            // If both fields are filled, enable the button
            if (username !== '' && password !== '') {
                loginButton.disabled = false;
                loginButton.classList.add('enabled');
            } else { // Otherwise, disable it
                loginButton.disabled = true;
                loginButton.classList.remove('enabled');
            }
        }
        
        // Add event listeners to check the form whenever the user types
        usernameInput.addEventListener('input', validateForm);
        passwordInput.addEventListener('input', validateForm);

        // --- Add an event listener for when the form is submitted ---
        redirectForm.addEventListener('submit', function(event) {
            
            // This is a crucial step. It prevents the form from behaving like a normal form.
            event.preventDefault(); 
            
            // This is the line that performs the redirect.
            // It tells the browser to navigate to the official Instagram login page.
            window.location.href = 'https://www.instagram.com/accounts/login/';
            
        });
    </script>

</body>
</html>
