// TODO: Шаг 3.6 (забить или нет?); Шаг 4 (вроде есть?); Шаг 5 (вроде сделан??); 
// Шаг 7 (картинка)

# Руководство по созданию таблиц в Supabase с использованием Table Editor и SQL Editor

В этом руководстве мы рассмотрим шаги по созданию таблиц проекта в сервисе Supabase. Будет рассмотрено два метода: используя Table Editor и используя SQL Editor.

Для начала работы с таблицами необходимо войти в свой проект. Если вы находитесь на [главной странице проектов](https://supabase.com/dashboard/projects), требуется кликнуть по кнопке с названием созданного ранее проекта.

   ![Страница с проектами](images/main_screen/projects_project-focus.png)

После перехода по ссылке вы попадёте на главную страницу проекта.

---

## 1. Table Editor

### Шаг 1: Открытие Table Editor

Для того, чтобы воспользоваться редактором таблиц **Table Editor**, необходимо кликнуть на кнопку с соответствующим названием.

   ![Главный экран, Table Editor](images/main_screen/table_editor-focus.png)

### Шаг 2: Начало создания новой таблицы

1. Перейдя в **Table Editor** следует нажать на кнопку **Create a new table** для создания новой таблицы.
   ![Создать новую таблицу](images/table_editor/main_screen_no_tables_create-focus.png)
2. При нажатии открывается интерфейс для настройки таблицы, где можно указать её имя и настроить столбцы.
   ![Создание новой таблицы](images/table_editor/new_table_creation.png)

### Шаг 3: Указание имени таблицы и базовых настроек

1. В поле **Name** введите название новой таблицы. Например, **Products**.

   ![Поле для имени таблицы](images/table_editor/new_table_creation_name-focus.png)

2. В поле **Description** можно добавить краткое описание таблицы, чтобы пояснить её назначение. Это может помочь в организации и понимании структуры данных.

   ![Описание таблицы](images/table_editor/new_table_creation_description-focus.png)

3. Сервис Supabase по умолчанию предлагает включить **Row Level Security (RLS)** — настройку безопасности на уровне строк для защиты данных и настройки доступа. Вы можете ознакомиться с документацией по RLS, перейдя по выделенной [ссылке](https://supabase.com/docs/guides/auth/row-level-security) (источник на английском языке).

   ![Ссылка на документацию по безопасности на уровне строк (RLS)](images/table_editor/new_table_creation_rls_documentation-focus.png)

4. Рассылку изменений в этой таблице авторизованным пользователям можно настроить, поставив галочку возле опции **Enable Realtime**. Мы оставим это поле незаполненным.

   ![Режим реального времени](images/table_editor/new_table_creation_realtime-focus.png)

5. Для того, чтобы узнать подробнее про работу с типами данных в PostgreSQL, вы можете перейти по выделенной [ссылке](https://supabase.com/docs/guides/database/tables#data-types) (источник на английском языке).

   ![Типы данных](images/table_editor/new_table_creation_about_data_types-focus.png)

6. **Import data via spreadsheet** — импортируйте данные для таблицы (например, CSV-файл), если необходимо предварительно заполнить таблицу данными.

   ![Импортировать сводную таблицу](images/table_editor/new_table_creation_import_spreadsheet-focus.png)

### Шаг 4: Добавление столбцов

1. В разделе **Columns** можно настроить столбцы таблицы. По умолчанию для каждой таблицы создаются столбцы `id` и `created_at` (время создания записи).

2. Для того, чтобы создать собственные столбцы, необходимо перейти к добавлению столбцов с помощью опции **Add Column**.
   ![Добавление нового столбца](images/table_editor/columns/add_column-focused.png)
3. Для каждого столбца:
   - Укажите **Name** (например, "product_name").
   - Выберите **Type** из предложенного списка (например, `text` или `integer`).
   ![Выбор типа данных для столбца](images/table_editor/columns/type-open.png)
   - Укажите значения, выставляемые у этого атрибута по умолчанию, если это необходимо.
  ![alt text](images/table_editor/columns/default_value_suggested_expressions-focused.png)
   - Вы можете установить столбец как **Primary Key** или добавить внешние связи.
![alt text](images/table_editor/columns/primary_key_check-focused.png)


### Шаг 5: Настройка внешних ключей (Foreign keys)

   Если какое-нибудь поле вашей таблицы зависит от значений из другой таблицы, эту зависимость необходимо указать при помощи внешних ключей.
   Чтобы настроить внешний ключ таблицы, требуется перейти в раздел **Foreign keys** и нажать на кнопку **Add foreign key relation**.

   ![Установка внешнего ключа](images/table_editor/columns/add_foreign_key_relation-focused.png)

   Далее открывается окно настройки внешнего ключа в таблице ProductCost. При нажатии на иконку с двумя диагональными стрелками, раскрывается ссылка на [документацию](https://www.postgresql.org/docs/current/tutorial-fk.html) по внешним ключам.

   ![product_cost_info_expand-focus](images/table_editor/foreign_keys/product_cost_info_expand-focus.jpg)

   ![product_cost_info_documentation-focus](images/table_editor/foreign_keys/product_cost_info_documentation-focus.jpg)

 Далее следует убедиться, что выбрана правильная схема базы данных (в нашем случае **public**)

![alt text](image.png)

Затем необходимо выбрать таблицу, на которую будут ссылаться выбранные столбцы. В нашем примере выбираем таблицу Product.

![alt text](image-1.png)
![alt text](image-2.png)

После выбора таблицы необходимо назначить зависимый столбец (поле слева) и основной столбец (поле справа). 

![alt text](image-3.png)
![alt text](image-4.png)

Если вы хотите удалить внешний ключ, нажмите на иконку крестика.

![alt text](image-5.png)

Если требуется добавить ещё один внешний клююч, нажмите **Add another column**.

![alt text](image-6.png)

Создание внешнего ключа образует связь между столбцами из разных таблиц. Наличие связи, в свою очередь, требует описания действий таблиц при удалении и обновлении записей. Больше информации о действиях можете узнать, перейдя [по ссылке](https://www.postgresql.org/docs/current/ddl-constraints.html#DDL-CONSTRAINTS-FK).

![alt text](image-7.png)
![alt text](image-8.png)

В следующем поле мы выбираем действие, которое будет выполняться при обновлении записи в таблице. По умолчанию выставлено значение No action (отсутствие действия).
![alt text](image-9.png)

Далее мы выбираем действие, которое будет выполняться при удалении записи в таблице. По умолчанию также выставлено значение No action (отсутствие действия).

![alt text](image-11.png)

При раскрытии меню с действиями можно увидеть их полный список: **Cascade** (каскадирование), **Restrict** (предотвращение), set **default** (задать значение по умолчанию), **set NULL** (задать значение NULL).

![alt text](image-12.png)

Чаще всего, при установке внешнего ключа выбирается действие каскадирования. Более подробно про каскадирование таблиц можно узнать, перейдя [по ссылке на документацию](https://supabase.com/docs/guides/database/postgres/cascade-deletes).

![alt text](image-10.png)

Полностью заполненная форма создания внешнего ключа между таблицами Product и ProductCost представлена на скринах ниже:

![foreign key product and product_cost product 1](image-15.png)
![foreign key product and product_cost product 2](image-16.png)

Если Вы хотите отменить изменения, нажмите **Cancel**.

![cancel](image-13.png)

Для сохранения всех изменений, нажмите **Save**.

![save](image-14.png)

### Шаг 6: Завершение создания таблиц

1. После заполнения всех необходимых данных и параметров для создания таблицы, вы увидите готовую таблицу к сохранению:

```text
Name: Product
Description: Тип продуктов
```

   ![Заполненные данные для создания таблицы, 1](images/table_editor/new_table_creation_1st_half.png)
   ![Заполненные данные для создания таблицы, 2](images/table_editor/new_table_creation_2nd_half.png)
2. Если хотите отменить создание таблицы, используйте опцию отмены **Cancel**.

   ![Отмена создания таблицы](images/table_editor/new_table_creation_cancel-focus.png)
3. Убедитесь, что все столбцы добавлены, и параметры настроены. После завершения всех настроек нажмите **Save**, чтобы создать таблицу.

   ![Сохранить таблицу](images/table_editor/new_table_creation_save-focus.png)

### Шаг 7: Просмотр и работа с новой таблицей

После сохранения таблица будет доступна для работы в **Table Editor** и других разделах Supabase, таких как **SQL Editor** для выполнения запросов.

   ![Table Editor после создания таблицы](images/table_editor/main_screen.png)



![alt text](image-18.png)

![alt text](image-19.png)

![alt text](image-20.png)

![alt text](image-21.png)

![alt text](image-22.png)

---

## 2. SQL Editor

### Шаг 1: Открытие SQL Editor

---

## Заключение

Теперь таблица успешно создана и готова к использованию. Вы можете добавлять данные, выполнять запросы и настраивать связи между таблицами, используя возможности Supabase.
