<h1>Мидлвари</h1>
<h2>Авторизация</h2>
<p>request:</p>
<pre>
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 401 Unauthorized
Content-Type: application/json<br>
{
  "error": "Authentication failed",
  "message": "Invalid token"
}
</pre>
<pre>
HTTP/1.1 403 Forbidden
Content-Type: application/json
{
  "error": "Access denied",
  "message": "You do not have the necessary permissions."
}
</pre>