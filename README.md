# TelegramInterectionsService



## IUserManagingService

#### Methods:

* add\_user\_to\_database(user) - request to add new user to database&#x20;
* add\_user\_role(user, role) - add new role to the user roles list
* add\_admin(user) - adding new admin to admin team
* set\_score(user, new\_score) - sets new activity rating
* change\_score(user, delta\_score) - adds delta to user activity rating
* top\_score() - shows top 10 people with highest activity rating
* get\_score(user) - shows user activity rating
* change\_user\_info(user, new\_data) - changes user info
* check\_user\_privileges(user) - show user rights

## IFormsManagingService

#### Methods:

* create\_form(form) - creates new form
* delete\_form(form) - delete existing form
* show\_forms() - show all existing forms
* export\_form(export\_type, form\_name) - export form data to export\_type format
* change\_ticket\_status(ticket, new\_status) - forcibly change ticket status to new one

## IMaterialHelpService

#### Methods:

* get\_ticket(user) - shows all user tickets
* create\_ticket() - initiates a dialog to fill the ticket
* get\_tickets(filters) - shows all tickets satisfying filters



## ITelegramNotifierService

#### Methods:

* notify(category, text) - sends some text to all users that are subscribed to category
* create\_category(category) - creates new notify category
* delete\_category(category) - deletes notify category
* subs\_user\_to\_category(user, category) - directly adds user to notify category
* unsubs\_user\_to\_categoty(user, categoty) - directly removes user from notify category



## RegisrationStates

#### Attributes:

* entering\_name - state when user writes his first name
* entering\_surname - state when user writes his last name
* entering\_group - state when user writes his group number
* entering\_bio - state when user adds smth. to his bio

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
