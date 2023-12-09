<h2>Album страница</h2>
<h3>Создание альбома</h3>
<p>request:</p>
<pre>
POST /api/albums HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "name": "New Album",
  "songs": [
    {"name": "Song 1"},
    {"name": "Song 2"}
  ],
  "artist": "123456"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 201 Created
Content-Type: application/json<br>
{
  "uid": "123456",
  "name": "New Album",
  "songs": [
    {"uid": "123456", "name": "Song 1"},
    {"uid": "123456", "name": "Song 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "error": "Failed to create album",
  "message": "The requested album could not be created."
}
</pre>

<h3>Получение альбома по uid</h3>
<p>request:</p>
<pre>
GET /api/albums/123456 HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "uid": "123456",
  "name": "New Album",
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
  "error": "Album not found",
  "message": "The requested album was not found."
}
</pre>

<h3>Получение всех альбомов</h3>
<p>request:</p>
<pre>
GET /api/albums HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "albums": [
    {
      "uid": "123456",
      "name": "Album 1",
      "songs": [
        {"uid": "123456", "name": "Song 1"},
        {"uid": "s123456", "name": "Song 2"}
      ]
    },
    {
      "uid": "123456d",
      "name": "Album 2",
      "songs": [
        {"uid": "123456", "name": "Song 3"},
        {"uid": "123456", "name": "Song 4"}
      ]
    }
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Albums not found",
  "message": "No albums were found."
}
</pre>

<h3>Удаление альбома</h3>
<p>request:</p>
<pre>
DELETE /api/albums/12345 HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 204 No Content
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Album not found",
  "message": "The requested album was not found."
}
</pre>