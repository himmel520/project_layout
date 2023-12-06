<h1>Мидлвари</h1>
<h2>Auth</h2>
<p>request:</p>
<pre>
{
  "headers": {
    "authorization" : "Bearer token"
  }
}
</pre>
<p>response:</p>
<pre>{
  "message": "invalid token"
}</pre>

<h1>Роуты</h1>
<h2>Регистрация</h2>
<h3>/api/register POST</h3>
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
<pre>
{
  "message": "success"
}
</pre>
<pre>
{
  "message": "email was registered"
}
</pre>

<h3>/api/login POST</h3>
<p>request:</p>
<pre>
{
  "body" : {
    "login": "email_data",
    "password": "password_data"
  }
}
</pre>
<p>response:</p>
<pre>
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
</pre>
<pre>
{
  "message": "invalid email or password"
}
</pre>

<h2>Home страница</h2>
<h3>/api/HomePage GET</h3>
<p>request:</p>
<pre>{
  "headers": {
    "Authorization": "Bearer access_token_name"
  }
}</pre>
<p>response:</p>
<pre>{
  "playlistNamesUsers" : ["rock", "qwerfr"]
}</pre>

<h2>User page</h2>
<h3>/api/user GET</h3>
<p>request:</p>
<pre>{
  "headers": {
    "Authorization": "Bearer access_token_name"
  }
}</pre>
<p>response:</p>
<pre>{
  "UserData": {
    "userId": "12",
    "username": "elleryrain",
    "lastAddedSongs": [
      {
        "nameSong": "1",
        "countListened": 0;
        (В данный момент пусть будет 0, а потом остальное согласую)
       },
       {
        "nameSong": "2",
        "countListened": 0;
        (В данный момент пусть будет 0, а потом остальное согласую)
       },
       {
        "nameSong": "3",
        "countListened": 0;
        (В данный момент пусть будет 0, а потом остальное согласую)
       }
      ]
    "countAddedTracks": 100,
    "followers": 284,
    "following": 432
    "gender": male,
    "location": "Russia",
    "Bio": "пусто",
    "years": "24"
  }
  "Posts": {
    "Не будут работать в данный момент времени"
  }
}</pre>

<h2>Follow action</h2>
<h3>/api/user/follow POST</h3>
<p>request:</p>
<pre>{
  "headers": {
    "Authorization":"Bearer access_token_name" 
  },
  "body": {
    "toFollowUserId": 10
  }
}</pre>
<p>response:</p>
<pre>{
  "message": "success"
}</pre>
<pre>{
  "message": "error"	
}</pre>
