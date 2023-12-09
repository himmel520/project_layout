<h2>Liked страница</h2>
<h3>Все добавленные песни</h3>
<p>request:</p>
<pre>
GET /api/liked HTTP/1.1
Authorization: Bearer access_token_name
</pre>
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "likedSongs": [
    {
      "uid": "123456",
      "name": "name",
      "artist": "name_artist"
    }
  ]
}
</pre>

<h3>Удаление добавленной песни</h3>
<p>request:</p>
<pre>
DELETE /api/liked/1234567890 HTTP/1.1
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
  "error": "Failed to delete song",
  "message": "The requested song could not be deleted."
}
</pre>