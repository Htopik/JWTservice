# Сервис авторизации JWT

## Цель: ##


Получить опыт работы с Jwt. 

## Задачи: ##


- Реализовать сервис, предоставляющий возможность регистрироваться и логиниться пользователям, при успешном логине выдающий Jwt Токен.
Создать сервис на SpringBoot, предоставляющий 2 эндпоинта: для регистрации и логина, сохраняющий в бд логин, пароль, email. Пароль должен быть захэширован (не путать с зашифрован) при сохранении в бд.
- Сгенерировать пару ключей шифрования (keypair), положить в ресурсы проекта. использовать например keytool -genkeypair
- При успешном логине должен собираться jwt токен, подписываться приватным ключом, в ответ на правильный логин и пароль выдаваться токен. В токене в payload кладется какая-либо информация о пользователе, например email.
- Добавить эндпоинт /.well-known/jwks.json, выдающий публичный ключ. Для работы с ключами использовать библиотеку com.nimbusds:nimbus-jose-jwt. Клиент будет использовать публичный ключ для валидации токена. Ответ будет вида:
  
{

  "keys": [
  
    {

      "use": "sig",
  
      "kty": "RSA",
  
      "kid": "public:c424b67b-fe28-45d7-b015-f79da50b5b21",
  
      "alg": "RS256",
  
      "n": "sttd***6h0gdMoDfZTq9Gn5S-Aq0-_-fIfyN9qrrQ0E1Q_QDhvqXx8eQ1r9smM",
  
      "e": "AQAB"
  
    }
  
  ]
  
}

ПОКА НЕ РЕАЛИЗОВАНО:
- Создать сервис-клиент (отдельный микросервис на SpringBoot), принимающий токен в хедерах. Создать любой эндпоинт. Создать фильтр всех запросов, который берет публичный ключ с  /.well-known/jwks.json сервиса авторизации и верифицирует подпись токена. Если токен прошел верификацию, из токена извлекается email и кладется в хедер и пробрасывается фильтром дальше в контроллер. Эндпоинт выводит в консоль email.
- Создать коллекцию запросов в Postman. Первый запрос регистрирует юзера, второй запрос логинится и заносит токен в переменные коллекции, третий - отправляет запрос в сервис-клиент, токен берет из переменных коллекции, кладет в хедеры.


## Результаты: ##
- знание структуры jwt
- знание понятия «Асинхронное шифрование»
- понимание основных принципов работы механизмов авторизации в микросервисных системах

