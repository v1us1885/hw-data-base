# Домашнее задание к занятию «Базы данных» - Филатов А. В.

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

---
### Легенда

Заказчик передал вам [файл в формате Excel](https://github.com/netology-code/sdb-homeworks/blob/main/resources/hw-12-1.xlsx), в котором сформирован отчёт. 

На основе этого отчёта нужно выполнить следующие задания.

### Задание 1

Опишите не менее семи таблиц, из которых состоит база данных:

- какие данные хранятся в этих таблицах;
- какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.

Приведите решение к следующему виду:

Сотрудники (

- идентификатор, первичный ключ, serial,
- фамилия varchar(50),
- ...
- идентификатор структурного подразделения, внешний ключ, integer).

### Решение 1
1. **Таблица "Сотрудники" (`Employees`):**
   - `employee_id` (serial, primary key) - уникальный идентификатор сотрудника
   - `full_name` (varchar(50)) - полное имя сотрудника
   - `salary` (numeric) - оклад сотрудника
   - `position_id` (integer, foreign key) - внешний ключ, связывающий сотрудника с конкретной должностью
   - `department_type_id` (integer, foreign key) - внешний ключ, связывающий сотрудника с конкретным типом подразделения
   - `structural_unit_id` (integer, foreign key) - внешний ключ, связывающий сотрудника с конкретным структурным подразделением
   - `hire_date` (date) - дата найма сотрудника
   - `assigned_project` (varchar(100)) - проект, на который назначен сотрудник

2. **Таблица "Структурные подразделения" (`StructuralUnits`):**
   - `structural_unit_id` (serial, primary key) - уникальный идентификатор структурного подразделения
   - `unit_name` (varchar(50)) - название подразделения
   - `unit_type_id` (integer, foreign key) - внешний ключ, связывающий подразделение с конкретным типом подразделения
   - `address_id` (integer, foreign key) - внешний ключ, связывающий подразделение с конкретным адресом

3. **Таблица "Проекты" (`Projects`):**
   - `project_id` (serial, primary key) - уникальный идентификатор проекта
   - `project_name` (varchar(100)) - название проекта
   - `start_date` (date) - дата начала проекта
   - `end_date` (date) - дата завершения проекта
   - `project_description` (text) - описание проекта

4. **Таблица "Зарплаты" (`Salaries`):**
   - `salary_id` (serial, primary key) - уникальный идентификатор записи о зарплате
   - `employee_id` (integer, foreign key) - внешний ключ, связывающий запись о зарплате с конкретным сотрудником
   - `salary_amount` (numeric) - сумма зарплаты
   - `payment_date` (date) - дата выплаты зарплаты

5. **Таблица "Должности" (`Positions`):**
   - `position_id` (serial, primary key) - уникальный идентификатор должности
   - `position_name` (varchar(50)) - название должности
   - `responsibilities` (text) - обязанности, связанные с должностью
   - `required_qualifications` (text) - требования к квалификации для данной должности

6. **Таблица "Типы подразделений" (`DepartmentTypes`):**
   - `department_type_id` (serial, primary key) - уникальный идентификатор типа подразделения
   - `type_name` (varchar(50)) - название типа подразделения

7. **Таблица "Адреса" (`Addresses`):**
   - `address_id` (serial, primary key) - уникальный идентификатор адреса
   - `location` (varchar(100)) - местонахождение


Такие определения таблиц позволяют явно определить структуру базы данных, а типы данных PostgreSQL, такие как varchar, text, numeric, integer, serial и date, используются для соответствующих столбцов для обеспечения корректного хранения данных.