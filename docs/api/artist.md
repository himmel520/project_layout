<h2>Artist страница</h2>
<h3>Создание артиста</h3>
<p>request:</p>
<pre>
POST /api/artists HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "name": "New Artist",
  "description": "Description of the new artist"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 201 Created
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "error": "Failed to create artist",
  "message": "The requested artist could not be created."
}
</pre>

<h3>Получение артиста по uid</h3>
<p>request:</p>
<pre>
GET /api/artists/1234567890 HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "uid": "1234567890",
  "name": "Artist Name",
  "songs": [
    {"uid": "123456", "name": "Song 1"},
    {"uid": "123456", "name": "Song 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Artist not found",
  "message": "The requested artist was not found."
}
</pre>

<h3>Все артисты</h3>
<p>request:</p>
<pre>
GET /api/artists HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "artists": [
    {"uid": "123456", "name": "Artist 1"},
    {"uid": "789012", "name": "Artist 2"},
    {"uid": "345678", "name": "Artist 3"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Artists not found",
  "message": "The requested resource was not found."
}
</pre>