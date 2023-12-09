<h1>Структура</h1>
<ol>
  <li>Мидлвари
    <ul>
      <li>Авторизация</li>
    </ul>
  </li>

  <li>Роуты
    <ul>
      <li>Регистрация</li>
      <li>Аутентификация</li>
    </ul>
  </li>

  <li>Profile страница
    <ul>
      <li>Профиль</li>
      <li>Удаление профиля</li>
    </ul>
  </li>

  <li>Home страница
    <ul>
      <li>Главная страница</li>
    </ul>
  </li>

  <li>Liked страница
    <ul>
      <li>Все добавленные песни</li>
      <li>Удаление добавленной песни</li>
    </ul>
  </li>

  <li>Library/Playlists страница
    <ul>
      <li>Библиотека/Плейлисты юзера</li>
      <li>Добавление плейлиста</li>
      <li>Получение плейлиста по uid</li>
      <li>Удаление добавленного плейлиста</li>
      <li>Получение плейлистов по жанру</li>
    </ul>
  </li>

  <li>Artist страница
    <ul>
      <li>Создание артиста</li>
      <li>Получение артиста по uid</li>
      <li>Все артисты</li>
    </ul>
  </li>

  <li>Album страница
    <ul>
      <li>Создание альбома</li>
      <li>Получение альбома по uid</li>
      <li>Получение всех альбомов</li>
      <li>Удаление альбома</li>
    </ul>
  </li>

  <li>Admin страница
    <ul>
      <li>Получение статистики(количество)</li>
      <li>Получение всех пользователей</li>
      <li>Изменение роли пользователя</li>
      <li>Изменение статуса пользователя(verifed)</li>
      <li>Удаление пользователя(профиль)</li>
    </ul>
  </li>
</ol>


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

<h1>Роуты</h1>
<h2>Регистрация</h2>
<h3>Создание пользователя</h3>
<p>request:</p>
<pre>
POST /api/profiles HTTP/1.1
Content-Type: application/json<br>
{
  "email": "email_data",
  "login": "login_data",
  "name": "name",
  "surname": "surname",
  "country": "russia"
  "burthday": "27.01.2001"
  "password": "password_data"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 201 Created
Content-Type: application/json<br>
{
  "message": "The email has been successfully registered."
}
</pre>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "error": "Failed to register user",
  "message": "Invalid data provided."
}
</pre>

<h3>Аутентификация</h3>
<p>request:</p>
<pre>
POST /api/login HTTP/1.1
Content-Type: application/json<br>
{
  "login": "email_data",
  "password": "password_data"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
</pre>
<pre>
HTTP/1.1 401 Unauthorized
Content-Type: application/json<br>
{
  "error": "Authentication failed",
  "message": "Invalid email or password"
}
</pre>

<h2>Profile страница</h2>
<h3>Профиль</h3>
<p>request:</p>
<pre>
GET /api/profiles/{user_uid} HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "uid": "user_uid",
  "email": "email_data",
  "login": "login_data",
  "name": "name",
  "surname": "surname",
  "country": "russia",
  "birthday": "27.01.2001",
  "addedSongs": [
    {"uid": "song1_uid", "name": "Song 1"},
    {"uid": "song2_uid", "name": "Song 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Profile not found",
  "message": "The requested profile was not found."
}
</pre>

<h3>Удаление профиля</h3>
<p>request:</p>
<pre>
DELETE /api/profiles/{user_uid} HTTP/1.1
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
  "error": "Failed to delete profile",
  "message": "The requested profile could not be deleted."
}
</pre>

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

<h2>Artist страница</h2>
<h3>Создание артиста</h3>
<p>request:</p>
<pre>
POST /api/artists HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "name": "New Artist",
  "description": "Description of the new artist"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 201 Created
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "error": "Failed to create artist",
  "message": "The requested artist could not be created."
}
</pre>

<h3>Получение артиста по uid</h3>
<p>request:</p>
<pre>
GET /api/artists/1234567890 HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "uid": "1234567890",
  "name": "Artist Name",
  "songs": [
    {"uid": "123456", "name": "Song 1"},
    {"uid": "123456", "name": "Song 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Artist not found",
  "message": "The requested artist was not found."
}
</pre>

<h3>Все артисты</h3>
<p>request:</p>
<pre>
GET /api/artists HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "artists": [
    {"uid": "123456", "name": "Artist 1"},
    {"uid": "789012", "name": "Artist 2"},
    {"uid": "345678", "name": "Artist 3"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Artists not found",
  "message": "The requested resource was not found."
}
</pre>

<h2>Album страница</h2>
<h3>Создание альбома</h3>
<p>request:</p>
<pre>
POST /api/albums HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "name": "New Album",
  "songs": [
    {"name": "Song 1"},
    {"name": "Song 2"}
  ],
  "artist": "123456"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 201 Created
Content-Type: application/json<br>
{
  "uid": "123456",
  "name": "New Album",
  "songs": [
    {"uid": "123456", "name": "Song 1"},
    {"uid": "123456", "name": "Song 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 400 Bad Request
Content-Type: application/json<br>
{
  "error": "Failed to create album",
  "message": "The requested album could not be created."
}
</pre>

<h3>Получение альбома по uid</h3>
<p>request:</p>
<pre>
GET /api/albums/123456 HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "uid": "123456",
  "name": "New Album",
  "songs": [
    {"uid": "123456", "name": "Song 1"},
    {"uid": "123456", "name": "Song 2"}
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Album not found",
  "message": "The requested album was not found."
}
</pre>

<h3>Получение всех альбомов</h3>
<p>request:</p>
<pre>
GET /api/albums HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "albums": [
    {
      "uid": "123456",
      "name": "Album 1",
      "songs": [
        {"uid": "123456", "name": "Song 1"},
        {"uid": "s123456", "name": "Song 2"}
      ]
    },
    {
      "uid": "123456d",
      "name": "Album 2",
      "songs": [
        {"uid": "123456", "name": "Song 3"},
        {"uid": "123456", "name": "Song 4"}
      ]
    }
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Albums not found",
  "message": "No albums were found."
}
</pre>

<h3>Удаление альбома</h3>
<p>request:</p>
<pre>
DELETE /api/albums/12345 HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 204 No Content
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Album not found",
  "message": "The requested album was not found."
}
</pre>

<h3>Получение статистики</h3>
<p>request:</p>
<pre>
GET /api/admin/stats HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "songs_count": 1000,
  "albums_count": 50,
  "playlists_count": 20,
  "users_count": 500,
  "artists_count": 200
}
</pre>

<h3>Получение всех пользователей</h3>
<p>request:</p>
<pre>
GET /api/admin/users HTTP/1.1
Authorization: Bearer access_token_name
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
Content-Type: application/json<br>
{
  "users": [
    {"uid": 12345, "username": "user1", "email": "user1@example.com", "role": "admin", "status": "active"},
    {"uid": 22345, "username": "user2", "email": "user2@example.com", "role": "user", "status": "inactive"},
    {"uid": 36799, "username": "user3", "email": "user3@example.com", "role": "user", "status": "active"},
  ]
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "Users not found",
  "message": "Users was not found."
}
</pre>


<h3>Изменение роли пользователя</h3>
<p>request:</p>
<pre>
PUT /api/admin/role/12345 HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "new_role": "admin"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "User not found",
  "message": "The requested user was not found."
}
</pre>

<h3>Изменение статуса верификации пользователя</h3>
<p>request:</p>
<pre>
PUT /api/admin/verified/12345 HTTP/1.1
Authorization: Bearer access_token_name
Content-Type: application/json<br>
{
  "new_status": "verified"
}
</pre>
<p>response:</p>
<pre>
HTTP/1.1 200 OK
</pre>
<p>response:</p>
<pre>
HTTP/1.1 404 Not Found
Content-Type: application/json<br>
{
  "error": "User not found",
  "message": "The requested user was not found."
}
</pre>
