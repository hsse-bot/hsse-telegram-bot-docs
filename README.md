# UsersManagingService

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
&#x20;**<название переменной>:<ее тип>**
{% endhint %}

## Base

Класс, который наследует `DeclarativeBase` из `sqlalchemy.orm`

## User

Класс, который задает таблицу `users` в БД

### Свойства

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
