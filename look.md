`npx create-react-app client --template typescript`

server:

`npm init -y`

`npm i express cors cookie-parser`

`npm i nodemon --save-dev` - автоперезапуск при изменениях

`npm i dotenv` - конфигурация

`npm i mongodb mongoos`

Создаем БД на mongoDB.
Настраиваем connect.

Создаем API

Создаем сервисы для контроллеров

`npm i jsonwebtoken bcrypt uuid`

через Postman отправляем POST-запрос `http://localhost:5000/api/registration`. с телом: 
<pre>
{
	"email": "user2@mail.ru",
	"password": "12345"
}
</pre>

Проверяем полученные ключи в jwt.io

В MongoDB появились записи с токенами и юзерами.

Устанавливаем библиотеку для отправки почтовых уведомлений:
`npm i nodemailer`

В настройках эл.почты включаем imap, адрес хоста почтового сервера берем из "Подробнее..." (gmail)

В userController создаем функцию `activate()`

"Middleware по обработке ошибок"

Для валидации логин/пароля установим `npm i express-validator`.

Функция логина
Функция логаута
Функция обновления токенов

Реализация getUsers для авторизованных пользователей (auth-middleware).
Здесь также выполняется валидация токена. Если токен не валидный ~ пользователь не авторизован.

~ функция next вызывает следующий по цепочке middleware.



##Client

npm i mobx mobx-react-lite
npm i axios @types/axios


`interceptor` - функция *перехватчик* на каждый запрос и ответ.
1) На __запрос__ будет вставлять перед каждой отправкой в заголовок - Authorization: "Bearer ${ACCESS_TOKEN}"

!-- access-токен(15мин), рефреш (30 мин). Есть эндпоинт, который по наличию `refresh-токена` перезаписывает `access-токен` и возвращает новую пару.

2) На __ответ__ при статусе 200 - ничего не делаем, 401 (не авторизован, протух) - interceptor отправляет рефреш токен на этот эндпоинт и повторяет запрос.
