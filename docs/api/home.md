<h2>Home страница</h2>
<h3>Главная страница</h3>
<p>request:</p>
<pre>
GET /api/home HTTP/1.1
Authorization: Bearer access_token_name<br>
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "playlistGenresUsers": [
    {
      "uid": "12345",
      "name": "rock"
    },
    {
      "uid": "67890",
      "name": "qwerty"
    }
  ],
  "popularSongs": [],
  "popularPlaylists": []
}
</pre>