<h1>Изображения</h1>
<h2>Альбом/Плейлист/Профиль</h2>

<h3>Добавить изображение</h3>
<p>request:</p>
<pre>
POST /cdn/img?type=album HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW<br>
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="image"; filename="img_uuid.jpg"
Content-Type: image/jpeg<br>
[Binary data of the album image]
------WebKitFormBoundary7MA4YWxkTrZu0gW
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "status": "success",
  "message": "Image added successfully"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "status": "error",
  "message": "Invalid request."
}
</pre>

<h3>Получить изображение</h3>
<p>request:</p>
<pre>
GET /cdn/img?type=album&image=id HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW<br>
------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="image"; filename="img_uuid.jpg"
Content-Type: image/jpeg<br>
[Binary data of the album image]
------WebKitFormBoundary7MA4YWxkTrZu0gW
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/jso<,br>
{
  "status": "error",
  "message": "Image not found"
}
</pre>

<h3>Удалить изображение</h3>
<p>request:</p>
<pre>
DELETE /cdn/img?type=album&image_id=id HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "status": "success",
  "message": "Image deleted successfully"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "status": "error",
  "message": "Image not found"
}
</pre>
