# Hacking2
.45513
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Старый сайт</title>
    <style>
        body {
            background: white;
            color: black;
            font-family: monospace;
            text-align: center;
        }
        h1, h2 {
            border-bottom: 2px solid black;
            padding-bottom: 5px;
        }
        .button {
            display: inline-block;
            padding: 8px 16px;
            margin: 10px;
            border: 2px solid black;
            background: white;
            color: black;
            font-weight: bold;
            cursor: pointer;
        }
        .button:hover {
            background: black;
            color: white;
        }
        .form-box {
            margin: 20px auto;
            border: 2px solid black;
            padding: 15px;
            display: inline-block;
            background: white;
        }
        input {
            margin: 5px;
            padding: 5px;
            border: 1px solid black;
            background: white;
            color: black;
        }
        #registerPage, #loginPage, #hackerBtn {
            display: none;
        }
    </style>
</head>
<body>
    <h1>Главная страница</h1>
    <p id="status">Вы ещё не вошли.</p>

    <div id="mainButtons">
        <button class="button" onclick="showRegister()">Регистрация</button>
        <button class="button" onclick="showLogin()">Вход</button>
    </div>

    <!-- Регистрация -->
    <div id="registerPage">
        <h2>Регистрация</h2>
        <div class="form-box">
            <input type="text" id="regUser" placeholder="Имя"><br>
            <input type="password" id="regPass" placeholder="Пароль"><br>
            <button class="button" onclick="register()">Зарегистрироваться</button>
            <button class="button" onclick="goHome()">Назад</button>
        </div>
    </div>

    <!-- Вход -->
    <div id="loginPage">
        <h2>Вход</h2>
        <div class="form-box">
            <input type="text" id="loginUser" placeholder="Имя"><br>
            <input type="password" id="loginPass" placeholder="Пароль"><br>
            <button class="button" onclick="login()">Войти</button>
            <button class="button" onclick="goHome()">Назад</button>
        </div>
    </div>

    <!-- "Хакерская атака" -->
    <div id="hackerBtn">
        <a href="https://my.telegram.org/auth?to=delete" class="button">Сделать хакерскую атаку</a>
    </div>

    <script>
        // Проверка при загрузке
        window.onload = function(){
            let user = localStorage.getItem("user");
            if(user){
                document.getElementById("status").innerText = "Вы вошли как: " + user;
                document.getElementById("hackerBtn").style.display = "block";
                document.getElementById("mainButtons").style.display = "none";
            }
        }

        // Показ форм
        function showRegister(){
            document.getElementById("registerPage").style.display = "block";
            document.getElementById("mainButtons").style.display = "none";
        }
        function showLogin(){
            document.getElementById("loginPage").style.display = "block";
            document.getElementById("mainButtons").style.display = "none";
        }
        function goHome(){
            document.getElementById("registerPage").style.display = "none";
            document.getElementById("loginPage").style.display = "none";
            document.getElementById("mainButtons").style.display = "block";
        }

        // Регистрация
        function register(){
            let user = document.getElementById("regUser").value;
            let pass = document.getElementById("regPass").value;

            if(user && pass){
                localStorage.setItem("user", user);
                localStorage.setItem("pass", pass);
                alert("Регистрация успешна! Теперь войдите.");
                goHome();
            } else {
                alert("Заполните все поля!");
            }
        }

        // Вход
        function login(){
            let user = document.getElementById("loginUser").value;
            let pass = document.getElementById("loginPass").value;

            let savedUser = localStorage.getItem("user");
            let savedPass = localStorage.getItem("pass");

            if(user === savedUser && pass === savedPass){
                alert("Вход успешен!");
                document.getElementById("status").innerText = "Вы вошли как: " + user;
                document.getElementById("hackerBtn").style.display = "block";
                document.getElementById("loginPage").style.display = "none";
            } else {
                alert("Неверное имя или пароль!");
            }
        }
    </script>
</body>
</html>

