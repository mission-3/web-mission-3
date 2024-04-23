# Миссия 3
###  Ссылка на скринкаст по 0,1,2 заданиям (https://drive.google.com/file/d/1Bs012vnr2bWLcjufh9L72T-WxJ5fxASH/view?usp=sharing)
## задание 3 с sql запросами
### 1. получить список юзернеймов пользователей : 
SELECT (username) from users;
### 2. получить кол-во отправленных сообщений каждым пользователем: username - number of sent messages:
SELECT users.username, COUNT(messages.text) 
FROM users
JOIN messages ON users.id = messages.from
GROUP BY users.username;
### 3. Получить пользователя с самым большим кол-вом полученных сообщений и само количество: username - number of received messages:
SELECT users.username, COUNT(messages.text) As numberofreceivedmessages
FROM users
JOIN messages ON users.id = messages.from
GROUP BY users.username
order by numberofreceivedmessages DESC
LIMIT 1;
### 4. Получить среднее кол-во сообщений, отправленное каждым пользователем:
Я понимаю, что надо использовать функцию AVG(), но она не работает в запросе вида: 
SELECT users.username, AVG(COUNT(messages.text)) 
FROM users
JOIN messages ON users.id = messages.to
GROUP BY users.username;
