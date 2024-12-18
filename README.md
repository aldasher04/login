<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Firebase Auth</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f7fc;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      background-color: white;
      padding: 40px;
      border-radius: 10px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      width: 300px;
      text-align: center;
    }

    h1 {
      color: #4CAF50;
      font-size: 24px;
      margin-bottom: 20px;
    }

    input[type="email"],
    input[type="password"] {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 5px;
      box-sizing: border-box;
      font-size: 16px;
    }

    button {
      width: 100%;
      padding: 10px;
      background-color: #4CAF50;
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background-color: #45a049;
    }

    .footer {
      margin-top: 20px;
      font-size: 14px;
      color: #777;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Register or Login</h1>
    <input type="email" id="email" placeholder="Enter your email" required>
    <input type="password" id="password" placeholder="Enter your password" required>
    <button onclick="register()">Submit</button>

    <div class="footer">
      <p>By registering, you agree to our <a href="#">Terms of Service</a> and <a href="#">Privacy Policy</a>.</p>
    </div>
  </div>

  <!-- Firebase SDK-ҳо -->
  <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-auth.js"></script>

  <script>
    // Firebase Config (Калидҳои Firebase-ро инҷо илова кунед)
    const firebaseConfig = {
      apiKey: "AIzaSyA3IwBi-EWmjawWPh13gHaioShKCQbE_6A",
      authDomain: "mywebcoin-bot.firebaseapp.com",
      projectId: "mywebcoin-bot",
      storageBucket: "mywebcoin-bot.appspot.com",
      messagingSenderId: "523064192512",
      appId: "1:523064192512:web:7fd246eef1aa1f1f2432e5"
    };

    // Ибтидоии Firebase
    firebase.initializeApp(firebaseConfig);

    // Функсияи бақайдгирӣ
    function register() {
      const email = document.getElementById('email').value;
      const password = document.getElementById('password').value;

      // Валидасияи имейл ва пароль
      if (email === "" || password === "") {
        alert("Please enter both email and password.");
        return;
      }

      firebase.auth().createUserWithEmailAndPassword(email, password)
        .then((userCredential) => {
          // Бақайдгирии муваффақ
          alert("User registered successfully!");
          console.log(userCredential);

          // Мутобиқ бо муваффақият равона кардан
          window.location.href = "https://www.google.com";  // Ба Google равона мекунад
        })
        .catch((error) => {
          // Хато
          alert("Error: " + error.message);
          console.error(error);
        });
    }

    // Хидмат барои санҷидани ҳолати аутентификатсия
    firebase.auth().onAuthStateChanged(function(user) {
      if (user) {
        console.log("User is logged in:", user);
      } else {
        console.log("No user is logged in.");
      }
    });
  </script>
</body>
</html>
