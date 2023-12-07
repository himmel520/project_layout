<h1>Роуты</h1>
<h2>Регистрация</h2>
<h3>/db/register POST</h3>
<p>request:</p>
<pre>
{
  "body": {
    "email": "email_data",
    "login": "login_data",
    "name": "name",
    "surname": "surname",
    "country": "russia"
    "burthday": "27.01.2001"
    "password": "password_data"
  }
}
</pre>
<p>response:</p>
<p>200 OK</p>
<pre></pre>
<p>400 Bad Request</p>
<pre>
{
  "message": "invalid data"
}
</pre>

<h3>/db/login GET</h3>
<p>request:</p>
<pre>
{
  "login": "email_data",
  "password": "password_data"
}
</pre>
<p>response:</p>
<p>200 OK</p>
<pre>
{
  "user": {
    "id": 123
  }
}
</pre>
<p>401 Unauthorized</p>
<pre></pre>

<h2>Home страница</h2>
<h3>/db/homePage GET</h3>
<p>request:</p>
<pre>
{
  "user": {
    "id": 123
  }
}
</pre> 
<p>response:</p>
<p>200 OK</p>
<pre>{
  "playlistNamesUsers" : [
    "rock", 
    "qwerfr"
  ],
  "popularSongs": [
    "name1",
    "name2"
    "пока пустой список"
  ],
  "popularPlaylists": [
    "name1",
    "name2",
    "пока пустой список"
  ]
}</pre>
