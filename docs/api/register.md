<h2>Регистрация</h2>

<h3>Создание пользователя</h3>
<p>request:</p>
<pre>
POST /api/profiles HTTP/1.1
Content-Type: application/json<br>
{
  "email": "email_data",
  "login": "login_data",
  "name": "name",
  "surname": "surname",
  "country": "russia"
  "burthday": "27.01.2001"
  "password": "password_data"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 201 Created
Content-Type: application/json<br>
{
  "message": "The email has been successfully registered."
}
</pre>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "error": "Failed to register user",
  "message": "Invalid data provided."
}
</pre>

<h3>Аутентификация</h3>
<p>request:</p>
<pre>
POST /api/login HTTP/1.1
Content-Type: application/json<br>
{
  "login": "email_data",
  "password": "password_data"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
</pre>
<pre>
HTTP/1.1 401 Unauthorized
Content-Type: application/json<br>
{
  "error": "Authentication failed",
  "message": "Invalid email or password"
}
</pre>