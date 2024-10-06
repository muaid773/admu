<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تسجيل الدخول باستخدام Firebase</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
            width: 300px;
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #ddd;
        }
        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .success-message {
            color: green;
            font-weight: bold;
            display: none;
        }
        .error-message {
            color: red;
            font-weight: bold;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>تسجيل الدخول</h2>
        <input type="email" id="email" placeholder="البريد الإلكتروني">
        <input type="password" id="password" placeholder="كلمة المرور">
        <button onclick="login()">تسجيل الدخول</button>
        <p class="success-message" id="successMessage">تم تسجيل الدخول بنجاح! مرحبًا بك.</p>
        <p class="error-message" id="errorMessage"></p>
    </div>

    <!-- Firebase JS SDK -->
    <script src="https://www.gstatic.com/firebasejs/9.1.3/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.1.3/firebase-auth.js"></script>

    <script>
        // Your Firebase configuration (استخدم بيانات Firebase التي أعطيتني إياها)
        const firebaseConfig = {
            apiKey: "AIzaSyABh9h4rmFpdP5uak3xsRAQMsqLSVl0Jqw",
            authDomain: "polarization-f81ed.firebaseapp.com",
            projectId: "polarization-f81ed",
            storageBucket: "polarization-f81ed.appspot.com",
            messagingSenderId: "952707656000",
            appId: "1:952707656000:web:dfe075c1e08055dcaf72a5"
        };

        // Initialize Firebase
        const app = firebase.initializeApp(firebaseConfig);
        const auth = firebase.auth();

        // Login function
        function login() {
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;

            auth.signInWithEmailAndPassword(email, password)
                .then((userCredential) => {
                    // Login success
                    document.getElementById('successMessage').style.display = 'block';
                    document.getElementById('errorMessage').style.display = 'none';
                })
                .catch((error) => {
                    // Handle errors
                    const errorMessage = error.message;
                    document.getElementById('errorMessage').textContent = errorMessage;
                    document.getElementById('errorMessage').style.display = 'block';
                    document.getElementById('successMessage').style.display = 'none';
                });
        }
    </script>
</body>
</html>
