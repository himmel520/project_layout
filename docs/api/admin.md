<h3>Получение статистики</h3>
<p>request:</p>
<pre>
GET /api/admin/stats HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "songs_count": 1000,
  "albums_count": 50,
  "playlists_count": 20,
  "users_count": 500,
  "artists_count": 200
}
</pre>

<h3>Получение всех пользователей</h3>
<p>request:</p>
<pre>
GET /api/admin/users HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "users": [
    {"uid": 12345, "username": "user1", "email": "user1@example.com", "role": "admin", "status": "active"},
    {"uid": 22345, "username": "user2", "email": "user2@example.com", "role": "user", "status": "inactive"},
    {"uid": 36799, "username": "user3", "email": "user3@example.com", "role": "user", "status": "active"},
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Users not found",
  "message": "Users was not found."
}
</pre>

<h3>Изменение роли пользователя</h3>
<p>request:</p>
<pre>
PUT /api/admin/role/12345 HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "new_role": "admin"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "User not found",
  "message": "The requested user was not found."
}
</pre>

<h3>Изменение статуса верификации пользователя</h3>
<p>request:</p>
<pre>
PUT /api/admin/verified/12345 HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "new_status": "verified"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "User not found",
  "message": "The requested user was not found."
}
</pre>