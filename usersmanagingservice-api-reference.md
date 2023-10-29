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
        "isMale": true
    }
}
</code></pre>

### StudentInfoDelta

```json
"studentInfoDelta": {
    "newRoomNumber": 217, // Изменение номера комнаты
    "newIsMale": true // Изменение пола (-_-)
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

{% swagger-response status="200: OK" description="Если успешно, возвращает измененный объект User" %}

{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Что-то пошло не так..." %}

{% endswagger-response %}
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
