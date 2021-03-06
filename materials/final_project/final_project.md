{% include header.md %}

{% include important-news.md %}

Разработка финального проекта
===
{% include module-not-completed-advanced.md %}

Технические требования к финальному проекту
---------------------
1. Приложение выполняется в виде WEB-приложения, т.е. браузер - это единственный интерфейс пользователей. 
1. В качестве платформы следует использовать Spring MVC фреймворк, запускающийся как Spring Boot приложение. Для 
шаблонов страниц следует использовать JSP.
1. Все стили следует хранить в отдельных css-файлах. Все скрипты - в отдельных js-файлах. Крайне желательно сверстать 
и оформить формы покрасивее.
1. Классы и методы должны иметь отражающую их функциональность названия и должны быть грамотно структурированы по 
пакетам. Иными словами, необходимо показать умение проектировать относительно большие системы.
1. Информацию необходимо хранить в базе данных. Для доступа использовать JDBC template. В качестве СУБД рекомендуется 
использовать MySQL или PostgreSQL.
1. Приложение должно поддерживать работу с кириллицей, в том числе и при хранении информации в БД.
1. Архитектура приложения должна соответствовать шаблону Model-View-Controller (MVC) и Data Access Object (DAO).
1. При разработке бизнес-логики необходимо использовать сессию пользователя.
1. Должна присутсвовать возможность регистрации пользователей. 
1. Должна присутсвовать возможность войти в систему под двумя или более ролями с разных браузеров.
1. Необходимо предусмотреть возможность развернуть приложение на нашей стороне: параметры подключения к базе данных 
хранить в конфигурационных properties-файлах, хранить SQL-скрипты для создания и начального наполнения базы.

Общие пользовательские сценарии обязательные для всех вариантов работ
---------------------
1. Страницы регистрации и авторизации должны быть реализованы в виде отдельных страниц.
1. Неавторизованному пользователю доступны только страницы регистрации и авторизации. При попытке открыть любую другую 
страницу (через URL) происходит редирект на страницу авторизации.
1. Авторизация происходит по комбинации логина и пароля.
1. В случае неправильно введенного логина или пароля пользователю отображается сообщение об ошибке под формой 
авторизации.
1. Форма регистрации пользователя должна содержать как минимум следующие поля - "Логин", "Пароль", "Имя", 
"Дата рождения", "Тип регистрирующегося пользователя" (типы прописаны в рамках каждого варианта, например "Студент" 
или "Преподаватель", тип выбирается через выпадашку select).
1. В случае попытки регистрации пользователя с использованием логина, который уже имеется в системе, пользователю 
отображается сообщение об ошибке под формой регистрации.
1. При прохождении успешной регистрации пользователь становится автоматически авторизованным и происходит редирект 
на главную страницу сайта.
1. При введении корректного сочетания логина и пароля пользователь становится авторизованным и происходит редирект 
на главную страницу сайта.
1. При попытке авторизованного пользователя перейти на страницу регистрации или авторизации (через URL) происходит 
редирект на главную страницу сайта.
1. В верхней части сайта в любом углу всегда должно отображаться имя текущего авторизованного пользователя.
1. В верхней части сайта в любом углу всегда должна отображаться кнопка "Выход". При нажатии на нее пользователь 
перестает быть авторизованным и происходит редирект на страницу авторизации.
1. Авторизованному пользователю в верхней части сайта всегда отображается меню со списком доступных страниц (список 
предусмотрен вариантом).
1. Доступные страницы в списке меню могут отличаться в зависимости от типа авторизованного пользователя (например 
"Администратор" видит в меню помимо общедоступных сстраниц, страницы доступные только для данного типа пользователей).
1. При попытке пользователя перейти на страницу (через URL) которая не доступна данному типу пользователей происходит 
редирект на главную страницу.

Варианты финальных работ
---------------------
### Система Факультатив
Существует перечень **Курсов**, за каждым из которых закреплен один **Преподаватель**. 
**Студент** записывается на один или несколько **Курсов**. **Преподаватель** составляет расписание **Занятий**.
**Преподаватель** отмечает посещаемость **Студентов**. **Студенты** выполняют **Лабораторные работы**.
По окончании обучения **Преподаватель** выставляет оценку **Студенту** и добавляет **Отзыв**.

**Сущности:**
1. Курс
1. Преподаватель
1. Студент
1. Занятие
1. Отзыв
1. Лабораторная работа

**Пользовательские сценарии:**
1. На главной странице сайта Преподаватель видит список его Курсов.
1. На главной странице сайта Студент видит список всех текущих и доступных для записи Курсов.
1. Преподаватель и Студент при нажатии на строчку курса переходят на страницу данного Курса. В ней находится список тем,
количество часов, отведенное на каждую тему и лабораторная работа.
1. Преподаватель видит список студентов, которые записалсь к нему на курс. Он может отметить посещаемость и успеваемость
Студента по данному курсу.
1. Преподаватель может запросить выписку по всем Курсам, Студентам и их текущему прогрессу. 
1. Студент может прикреплять Лабораторную работу к Курсу.
1. Преподаватель может проверять Лабораторную работу и ставить ей Оценку.
