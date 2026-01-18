<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MiniSocial — Вход</title>
  <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-auth-compat.js"></script>
  <style>
    body {
      font-family: Arial, Helvetica, sans-serif;
      background: #f3f4f6;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .card {
      background: white;
      padding: 30px;
      border-radius: 12px;
      width: 320px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
    }
    input {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border-radius: 8px;
      border: 1px solid #d1d5db;
    }
    button {
      width: 100%;
      padding: 10px;
      border: none;
      border-radius: 8px;
      background: #2563eb;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background: #1d4ed8;
    }
    p {
      text-align: center;
      cursor: pointer;
      color: #2563eb;
    }
  </style>
</head>
<body>

<div class="card">
  <h2 id="title">Регистрация</h2>
  <input id="email" type="email" placeholder="Email" />
  <input id="password" type="password" placeholder="Пароль" />
  <button onclick="submit()">Продолжить</button>
  <p onclick="toggle()">У меня уже есть аккаунт</p>
</div>

<script>
  // 🔹 Firebase config (ЗАМЕНИ на свой)
  const firebaseConfig = {
    apiKey: "AIzaSyDVsU9T7IMMfyaTUxx94ldcyPlrZ89nUZA",
    authDomain: "ss61-c04fe.firebaseapp.com",
    projectId: "ss61-c04fe"
  };

  firebase.initializeApp(firebaseConfig);
  const auth = firebase.auth();

  let isLogin = false;

  function toggle() {
    isLogin = !isLogin;
    document.getElementById('title').innerText = isLogin ? 'Вход' : 'Регистрация';
  }

  function submit() {
    const email = document.getElementById('email').value;
    const password = document.getElementById('password').value;

    if (isLogin) {
      auth.signInWithEmailAndPassword(email, password)
        .then(() => alert('Успешный вход'))
        .catch(err => alert(err.message));
    } else {
      auth.createUserWithEmailAndPassword(email, password)
        .then(() => alert('Аккаунт создан'))
        .catch(err => alert(err.message));
    }
  }
</script>

</body>
</html>

