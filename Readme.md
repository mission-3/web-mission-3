# Mission 2

## Part 0

[Link] (https://drive.google.com/file/d/1pkTwGvTLpQkPlsgu7IR3ljnmDT0W_n6a/view?usp=sharing)

## Part1

- Вопрос 1	 
> Ответ: SSH (Secure Shell) используется для защищенного удаленного доступа и управления серверами через шифрованное соединение. Это обеспечивает безопасную передачу данных и управление сервером удаленно  

- Вопрос 2	 
> Ответ: Вася должен добавить свой публичный ключ в файл ~/.ssh/authorized_keys на сервере. Этот файл содержит список ключей, которым разрешено подключаться к серверу  

- Вопрос 3	 
> Ответ: Long polling - это метод взаимодействия клиента и сервера, при котором клиент отправляет запрос на сервер и сервер задерживает ответ до тех пор, пока не будет доступна актуальная информация. Webhooks - это метод отправки данных от сервера к клиенту в режиме реального времени, когда сервер отправляет данные клиенту по мере их появления  

- Вопрос 4	 
> Ответ: Issues на GitHub - это инструмент для отслеживания ошибок, идей, задач и других проблем в проекте. Примеры issues в популярных "не знаю, на сколько они популярны" open source проектах: 
- React:
https://github.com/facebook/react/issues
- VS Code:
https://github.com/microsoft/vscode/issues  

- Вопрос 5	 
> Ответ: Чтобы git отслеживал пустые папки, можно в них добавить файл, который будет сохранять папку в репозитории, даже если она пуста  

# Mission 3

###  Ссылка на скринкаст по 0,1,2 заданиям (https://drive.google.com/file/d/1Bs012vnr2bWLcjufh9L72T-WxJ5fxASH/view?usp=sharing)

## part 3 с sql запросами
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
