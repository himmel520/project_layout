<h2>Library/Playlists страница</h2>
<h3>Библиотека/Плейлисты юзера</h3>
<p>request:</p>
<pre>
GET /api/playlists HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "genres": [
    {
      "name": "Rock",
      "userPlaylists": [
        {
          "uid": "123456",
          "name": "Classic Rock",
          "description": "The best classic rock hits."
        },
        {
          "uid": "123456",
          "name": "Alternative Rock",
          "description": "Explore the world of alternative rock music."
        }
      ]
    }
  ]
}
</pre>

<h3>Добавление плейлиста</h3>
<p>request:</p>
<pre>
POST /api/playlists HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "name": "New Playlist",
  "description": "Description of the new playlist",
  "songs": [
    {"uid": "song1_uid", "name": "Song 1", "artist": "Artist 1"},
    {"uid": "song2_uid", "name": "Song 2", "artist": "Artist 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 201 Created
Content-Type: application/json<br>
{
  "uid": "123456"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "error": "Failed to create playlist",
  "message": "The requested playlist could not be created."
}
</pre>

<h3>Получение плейлиста по uid</h3>
<p>request:</p>
<pre>
GET /api/playlists/123456 HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "uid": "123456",
  "name": "New Playlist",
  "description": "Description of the new playlist",
  "songs": [
    {"uid": "song1_uid", "name": "Song 1", "artist": "Artist 1"},
    {"uid": "song2_uid", "name": "Song 2", "artist": "Artist 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Playlist not found",
  "message": "The requested playlist was not found."
}
</pre>

<h3>Удаление добавленного плейлиста</h3>
<p>request:</p>
<pre>
DELETE /api/playlists/123456 HTTP/1.1
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
  "error": "Failed to delete playlist",
  "message": "The requested playlist could not be deleted."
}
</pre>

<h3>Получение плейлистов по жанру</h3>
<p>request:</p>
<pre>
GET /api/playlists?genre=Rock HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "userPlaylists": [
    {
      "uid": "123456",
      "name": "Classic Rock",
      "description": "The best classic rock hits."
    },
    {
      "uid": "789012",
      "name": "Alternative Rock",
      "description": "Explore the world of alternative rock music."
    }
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Genre not found",
  "message": "The requested genre was not found."
}
</pre>
