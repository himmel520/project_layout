<h1>Song</h1>

<h3>Добавить песню --</h3>
<p>request:</p>
<pre>

</pre>
<p>response:</p>
<pre>

</pre>

<h3>Получить песню</h3>
<p>request:</p>
<pre>
GET /cdn/songs?album=id&song=id  HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW<br>
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="audio_file"; filename="song_uid.mp3"
Content-Type: audio/mpeg<br>
[Binary data of the audio file]
------WebKitFormBoundary7MA4YWxkTrZu0gW
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "status": "error",
  "message": "Song not found"
}
</pre>

<h3>Удалить песню --</h3>
<p>request:</p>
<pre>

</pre>
<p>response:</p>
<pre>

</pre>
