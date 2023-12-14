<h1>Song</h1>

<h3>Добавить песню --</h3>
<p>request:</p>
<pre>
POST /cdn/songs?type=playlist&dir=playlist_id&song=id HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW<br>
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="audio_file"; filename="song_uuid.mp3"
Content-Type: audio/mpeg<br>
[Binary data of the audio file]
------WebKitFormBoundary7MA4YWxkTrZu0gW
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "status": "success",
  "message": "Song added to playlist successfully"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "status": "error",
  "message": "Invalid request"
}
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
DELETE /cdn/songs?type=playlist&dir=playlist_id&song=song_id HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "status": "success",
  "message": "Song removed successfully"
}
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
