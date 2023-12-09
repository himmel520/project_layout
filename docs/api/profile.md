<h2>Profile страница</h2>
<h3>Профиль</h3>
<p>request:</p>
<pre>
GET /api/profiles/{user_uid} HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "uid": "user_uid",
  "email": "email_data",
  "login": "login_data",
  "name": "name",
  "surname": "surname",
  "country": "russia",
  "birthday": "27.01.2001",
  "addedSongs": [
    {"uid": "song1_uid", "name": "Song 1"},
    {"uid": "song2_uid", "name": "Song 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Profile not found",
  "message": "The requested profile was not found."
}
</pre>

<h3>Удаление профиля</h3>
<p>request:</p>
<pre>
DELETE /api/profiles/{user_uid} HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 204 No Content
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "error": "Failed to delete profile",
  "message": "The requested profile could not be deleted."
}
</pre>