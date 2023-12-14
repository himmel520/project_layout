<h1>Albums</h1>

<h3>Добавить альбом(песни и картинка)</h3>
<p>request:</p>
<pre>
POST /cdn/albums?album=id HTTP/1.1
Authorization: Bearer cdn_access_token
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW<br>
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="cover_image"; filename="album_uid.jpg"
Content-Type: image/jpeg<br>
[Binary data of the album image]
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="audio_files[]"; filename="song_uid.mp3"
Content-Type: audio/mpeg<br>
[Binary data of song_uid.mp3]
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="audio_files[]"; filename="song_uid.aac"
Content-Type: audio/aac<br>
[Binary data of song_uid.aac]
------WebKitFormBoundary7MA4YWxkTrZu0gW--
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "status": "success",
  "message": "Upload successful"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "status": "error",
  "message": "Invalid request format"
}
</pre>

<h3>Удалить альбом(песни и картинка)</h3>
<p>request:</p>
<pre>
DELETE /cdn/albums?album=id HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "status": "success",
  "message": "Album content successfully deleted"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "status": "error",
  "message": "Album not found"
}
</pre>

