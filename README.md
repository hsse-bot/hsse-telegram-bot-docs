# Page

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



## MaterialHelpStates

#### Attributes:

* &#x20;ticket\_text -&#x20;
* bill\_photo
