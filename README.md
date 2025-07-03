<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        @import url('https://fonts.googleapis.com/css2family=Montserrat:wqht@200;500@display=swap');
        * {
           margin: 0;
           padding: 0;
           box-sizing: border-box; 
        }

        body {
            font-family: 'Montserrat', sans-serif;
            font-weight: 200;
            color: var(--tg--there-text-color);
            background: var(--tg--there-bg-color)

        }

        #main {
            width: 100%;
            padding: 20px;
            text-align: center;

        }

        h1 {
            margin-top: 50px;
            margin-bottom: 10px;

        }

        img {
            width: 70px;
            margin: 30px auto;

        }

        p {
            width: 358px;
            margin: 0 auto;
        }

        button {
            border: 0;
            border-radius: 5px;
            margin-top: 50px;
            height: 68px;
            width: 200px;
            font-size: 20px;
            font-weight: 500;
            cursor: pointer;
            transition: all 500ms ease;
            color: var(--tg--there-button-color);
            background: var(--tg--there-button-text-color);
        }

        #form {
            display: none;
            text-align: center;
        }

        input {
            width: 90%;
            outline: none;
            margin: 18px 5%;
            padding: 15px 13px;
            font-size: 14px;
            border: 2px solid silver;
            border-radius: 5px;
        }

        input:focus {
            border-color: #db5ddb;
        }
    </style>
</head>
<body>
    <div id="main">
        <h1>Онлайн магазин</h1>
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRyFdfmgKT0PII076Ge9lVLdRWKJLWuaLUa-A&s">
        <p>textTEXTtExTTexT</p>
        <button id="buy">Купить</button>

    </div>
    <form id="form">
        <h1>Оформление покупки</h1>
        <input type="text" placeholder="Имя" id="user_name">
        <input type="text" placeholder="Email" id="user_name">
        <input type="text" placeholder="Телефон" id="user_name">
        <button id="order">Оформить</button>
    </form>
    <script src="https://telegram.org/js/telegram-web-app.js?57"></script>
    <script>
        let tg = window.Telegram.WebApp;
        let buy = document.getElementById('buy');
        let order = document.getElementById('order');
        

        buy.addEventListener("click", () =>{
            document.getElementById("main").style.display = "none";
            document.getElementById("form").style.display = "block";
            document.getElementById("user_name").value = tg.initDataUnsafe.user.first_name + " " + tg.initDataUnsafe.user.last_name
        });
        order.addEventListener("click", () => {
        
        
            document.getElementById("error").innerText = '';
            let name = document.getElementById('user_name').value;
            let email =document.getElementById('user_email').value;
            let phone =document.getElementById('user_phone').value;
            if(name.length < 5){
                document.getElementById("error").innerText = 'Ошибка в имени';
                return;
            }
            if(email.length < 5){
                document.getElementById("error").innerText = 'Ошибка в email';
                return;
            }
            if(phone.length < 5){
                document.getElementById("error").innerText = 'Ошибка в номере телефона';
                return;
            }

            let date= {
                name: name,
                email: email,
                phone: phone
            }
            tg.sendData(JSON.stringify(data));
            tg.close();
        });
    </script>
</body>
</html>
