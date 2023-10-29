# UsersManagingService Classes

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
&#x20;**<название переменной>:<ее тип>**
{% endhint %}

## Base

Класс, который наследует `DeclarativeBase` из `sqlalchemy.orm`

## User

Класс, который задает таблицу `users` в БД

name:Mapped\[str] - имя пользователя (макс. 32 символа)

surname:Mapped\[str] - фамилия пользователя (макс. 32 символа)

role\_id:Mapped\[int] - ID роли, которая есть у пользователя

student\_info\_id:Mapped\[Optional\[int]] - ID записи дополнительной информации о пользователе

tg\_id:Mapped\[int] - ID пользователя в ТГ (primary key)

role:Mapped\[Role] - объект роли, полученный по role\_id

student\_info:Mapped\[StudentInfo] - объект дополнительной информации о студенте (если пользователь таковым является), полученный по student\_info\_id

## Role

Класс, который задает таблицу `roles` в БД

id:Mapped\[int] - ID роли

role\_name:Mapped\[str] - имя роли

## StudentInfo

Класс, который задает таблицу `students_additional_infos` в БД

id:Mapped\[int] - ID информации

room\_number:Mapped\[int] - номер комнаты

## UserData

Класс, который описывает сущность пользователя.

{% hint style="info" %}
Данный тип **никаким образом не связан** с БД
{% endhint %}

name:str - имя пользователя (макс. 32 символа)

surname:str - фамилия пользователя (макс. 32 символа)

tg\_id:int - ID пользователя в ТГ

role:RoleData - объект роли

student\_info:Optional\[StudentInfoData] - объект дополнительной информации о студенте (если пользователь таковым является)

## StudentInfoData

room\_number:int - номер комнаты

## RoleData

id:int - ID роли

name:str - Имя роли

## UserDelta

new\_name:str - новое имя

new\_surname:str - новая фамилия

new\_role\_id:int - новый ID роли

student\_info\_delta:StudentInfoDelta - изменение доп информации студента

## StudentInfoDelta

room\_number:int - номер комнаты

is\_male:boolean - true, если мужчина

## IUserRepository

Интерфейс предоставляет возможность манипулировать данными, которые связаны с пользователями

create\_user(user:UserData) - создает пользователя

get\_user(tg\_id:int):UserData - получает пользователя по ID тг. Возвращает объект UserData

update\_user(tg\_id:int, delta:UserDelta) - изменяет пользователя

delete\_user(tg\_id:int) - удаляет пользователя

## MySqlUserRepository

Имплементация IUserRepository, которая использует MySQL БД для работы с данными

create\_user(user:UserData) - создает пользователя

get\_user(tg\_id:int):UserData - получает пользователя по ID тг. Возвращает объект UserData

update\_user(tg\_id:int, delta:UserDelta) - изменяет пользователя

delete\_user(tg\_id:int) - удаляет пользователя

## RedisUserRepository

Имплементация IUserRepository, которая использует Redis и оригинальную имплементацию IUserRepository для работы с данными

create\_user(user:UserData) - создает пользователя

get\_user(tg\_id:int):UserData - получает пользователя по ID тг. Возвращает объект UserData

update\_user(tg\_id:int, delta:UserDelta) - изменяет пользователя

delete\_user(tg\_id:int) - удаляет пользователя

get\_all\_users():UserData\[] - получает всех пользователей

## IRolesRepository

Интерфейс предоставляет возможность манипулировать данными, которые связаны с ролями

create\_role(role\_name:str):RoleData - создает новую роль

delete\_role(role\_id:int) - удаляет роль

get\_role(role\_id:int):RoleData - получает роль по ID

get\_all\_roles():RoleData\[] - получает все роли

## main.py (в схеме как Global)

create\_user() - выполняет следующий API-запрос

get\_user() - выполняет следующий API-запрос

update\_user() - выполняет следующий API-запрос

delete\_user() - выполняет следующий API-запрос

get\_role() - выполняет следующий API-запрос

get\_roles() - выполняет следующий API-запрос
