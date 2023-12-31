# UsersManagingService API Reference

## Сущности API

### User

<pre class="language-json"><code class="lang-json"><strong>{
</strong>    "tgId": 123471234123789,
    "name": "Денис",
    "surname": "Войтенко",
    "role": {
        "id": 3123123,
        "name": "Regular"
    },
    "studentInfo": {
        "roomNumber": 217,
        "isMale": true,
        "groupNumber": "Б13-301"
    },
    "score": 312312,
    "email": "voitenko.da@phystech.edu"
}
</code></pre>

### StudentInfoDelta

```json
"studentInfoDelta": {
    "newRoomNumber": 217, // Изменение номера комнаты
    "newIsMale": true, // Изменение пола (-_-),
    "newGroupNumber": "Б13-302" // Изменение группы
}
```

### Role

```json
{
    "id": 313312312,
    "name": "Regular"
}
```

## Методы API

{% swagger method="post" path="/create-user" baseUrl="" summary="Создание нового пользователя" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="tgId" type="int" required="true" %}
ID пользователя в тг
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" required="true" %}
Имя пользователя
{% endswagger-parameter %}

{% swagger-parameter in="body" name="surname" type="string" required="true" %}
Фамилия пользователя
{% endswagger-parameter %}

{% swagger-parameter in="body" name="roleId" type="int" %}
ID роли&#x20;
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Все норм" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так... " %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/get-user" baseUrl="" summary="Получение пользователя" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="tgId" type="int" %}
ID пользователя в тг
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Возвращает объект User" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/get-all-users" baseUrl="" summary="Получение всех пользователей" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="Возвращает массив всех пользователей User" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так..." %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/update-user" baseUrl="" summary="Обновление информации о пользователе" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="tgId" type="int" %}
ID в тг пользователя, которого меняют
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newName" type="string" %}
Новое имя
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newSurname" type="string" %}
Новая фамилия
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newRoleId" type="int" %}
Новая роль (ее ID)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="studentInfoDelta" type="StudentInfoDelta" %}
Объект изменения доп инфы о пользователе
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newScore" type="int" %}
Ставит новый счет пользователя (deltaScore = null)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="deltaScore" type="int" %}
Изменяет счет пользователя на +deltaScore (newScore = null)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Если успешно, возвращает измененный объект User" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так..." %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="put" path="/update-role" baseUrl="" summary="Обновление роли" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="newName" type="String" %}
Название роли
{% endswagger-parameter %}

{% swagger-parameter in="query" name="id" type="Int" %}
ID роли
{% endswagger-parameter %}
{% endswagger %}

{% swagger method="delete" path="/delete-user" baseUrl="" summary="Удаление пользователя" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="tgId" type="int" %}
ID в тг пользователя, которого удаляют
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Пользователь удален" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так..." %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/get-roles" baseUrl="" summary="Получение всех ролей" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="Возвращает массив объектов Roles" %}
<pre class="language-json"><code class="lang-json">[
<strong>    {
</strong>        "id": 313312312,
        "name": "Regular"
    },
    {
        "id": 313312313,
        "name": "Admin"
    },
]
</code></pre>
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/get-role" baseUrl="" summary="Получение роли" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="id" type="int" %}
ID роли
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Если успешно, возвращает объект Role" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/get-role-by-name" baseUrl="" summary="Получение роли по имени" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="name" type="String" %}
Имя роли
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Если успешно, возвращает объект Role" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/ban-user" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="tg_id" type="int" %}

{% endswagger-parameter %}
{% endswagger %}

{% swagger method="get" path="/is-user-banned" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="tg_id" type="int" %}

{% endswagger-parameter %}
{% endswagger %}

{% swagger method="delete" path="/unban-user" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="tg_id" type="int" %}

{% endswagger-parameter %}
{% endswagger %}

