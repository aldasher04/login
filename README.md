<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Register - Firebase Auth</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f9;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .container {
      background: #fff;
      padding: 20px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
      border-radius: 8px;
      width: 300px;
      text-align: center;
    }
    .container h1 {
      font-size: 24px;
      margin-bottom: 20px;
      color: #333;
    }
    input {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      width: 100%;
      padding: 10px;
      background-color: #4caf50;
      border: none;
      color: #fff;
      border-radius: 5px;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Register</h1>
    <input type="email" id="email" placeholder="Enter your email" required>
    <input type="password" id="password" placeholder="Enter your password" required>
    <button onclick="register()">Submit</button>
  </div>

  <!-- Firebase SDK -->
  <script type="module">
    // Firebase configuration
    import { initializeApp } from "https://www.gstatic.com/firebasejs/11.1.0/firebase-app.js";
    import { getAuth, createUserWithEmailAndPassword } from "https://www.gstatic.com/firebasejs/11.1.0/firebase-auth.js";

    const firebaseConfig = {
      apiKey: "AIzaSyAdQlppXtcBYrTMwtEtiPwQjNW92yvC9IE",
      authDomain: "my-loiha.firebaseapp.com",
      projectId: "my-loiha",
      storageBucket: "my-loiha.appspot.com",
      messagingSenderId: "1078778268626",
      appId: "1:1078778268626:web:004b3d08ff3b2c6418960b",
      measurementId: "G-40KME42XEW"
    };

    // Initialize Firebase
    const app = initializeApp(firebaseConfig);
    const auth = getAuth();

    // Define the register function
    function register() {
      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;

      createUserWithEmailAndPassword(auth, email, password)
        .then((userCredential) => {
          alert("Registration successful!");
          window.location.href = "https://www.google.com"; // Redirect after success
        })
        .catch((error) => {
          alert(Error: ${error.message});
        });
    }
  </script>
</body>
</html>
