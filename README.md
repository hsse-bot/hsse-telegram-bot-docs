# UsersManagingService Classes

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
&#x20;**<название переменной>:<ее тип>**
{% endhint %}

## Base

Класс, который наследует `DeclarativeBase` из `sqlalchemy.orm`

## User

Класс, который задает таблицу `users` в БД

`name:Mapped[str]` - имя пользователя (макс. 32 символа)

`surname:Mapped[str]` - фамилия пользователя (макс. 32 символа)

`role_id:Mapped[int]` - ID роли, которая есть у пользователя

`student_info_id:Mapped[Optional[int]]` - ID записи дополнительной информации о пользователе

`tg_id:Mapped[int]` - ID пользователя в ТГ (primary key)

`role:Mapped[Role]` - объект роли, полученный по role\_id

`student_info:Mapped[StudentInfo]` - объект дополнительной информации о студенте (если пользователь таковым является), полученный по student\_info\_id

`score:Mapped[int]` - рейтинг пользователя

## Role

Класс, который задает таблицу `roles` в БД

`id:Mapped[int]` - ID роли

`role_name:Mapped[str]` - имя роли

## StudentInfo

Класс, который задает таблицу `students_additional_infos` в БД

`id:Mapped[int]` - ID информации

`room_number:Mapped[int]` - номер комнаты

## UserData

Класс, который описывает сущность пользователя.

{% hint style="info" %}
Данный тип **никаким образом не связан** с БД
{% endhint %}

`name:str` - имя пользователя (макс. 32 символа)

`surname:str` - фамилия пользователя (макс. 32 символа)

`tg_id:int` - ID пользователя в ТГ

`role:RoleData` - объект роли

`student_info:Optional[StudentInfoData]` - объект дополнительной информации о студенте (если пользователь таковым является)

`score:int` - рейтинг пользователя

## StudentInfoData

`room_number:int` - номер комнаты

`is_male:bool` - true, если мужчина

## RoleData

`id:int` - ID роли

`name:str` - Имя роли

## UserDelta

`new_name:str` - новое имя

`new_surname:str` - новая фамилия

`new_role_id:int` - новый ID роли

`student_info_delta:StudentInfoDelta` - изменение доп информации студента

`new_score:int` - новый счет пользователя

## StudentInfoDelta

`room_number:int` - номер комнаты

`is_male:boolean` - true, если мужчина

## IUserRepository

Интерфейс предоставляет возможность манипулировать данными, которые связаны с пользователями

`create_user(user:UserData)` - создает пользователя

`get_user(tg_id:int):UserData` - получает пользователя по ID тг. Возвращает объект UserData

`get_all_users():UserData[]` - получает всех пользователей

`update_user(tg_id:int, delta:UserDelta)` - изменяет пользователя

`delete_user(tg_id:int)` - удаляет пользователя

## MySqlUserRepository

Имплементация IUserRepository, которая использует MySQL БД для работы с данными

`create_user(user:UserData)` - создает пользователя

`get_user(tg_id:int):UserData` - получает пользователя по ID тг. Возвращает объект UserData

`get_all_users():UserData[]` - получает всех пользователей

`update_user(tg_id:int, delta:UserDelta)` - изменяет пользователя

`delete_user(tg_id:int)` - удаляет пользователя

## RedisUserRepository

Имплементация IUserRepository, которая использует Redis и оригинальную имплементацию IUserRepository для работы с данными

`create_user(user:UserData)` - создает пользователя

`get_user(tg_id:int):UserData` - получает пользователя по ID тг. Возвращает объект UserData

`get_all_users():UserData[]` - получает всех пользователей

`update_user(tg_id:int, delta:UserDelta)` - изменяет пользователя

`delete_user(tg_id:int)` - удаляет пользователя

## IRolesRepository

Интерфейс предоставляет возможность манипулировать данными, которые связаны с ролями

`create_role(role_name:str):RoleData` - создает новую роль

`delete_role(role_id:int)` - удаляет роль

`get_role(role_id:int):RoleData` - получает роль по ID

`get_all_roles():RoleData[]` - получает все роли

## main.py (в схеме как Global)

`create_user()` - выполняет следующий API-запрос

`get_user()` - выполняет следующий API-запрос

`get_all_users()` - выполняет следующий API-запрос

`update_user()` - выполняет следующий API-запрос

`delete_user()` - выполняет следующий API-запрос

`get_role()` - выполняет следующий API-запрос

`get_roles()` - выполняет следующий API-запрос
