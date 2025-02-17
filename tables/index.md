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


   Добавление внешнего ключа будет рассмотрено на связи между таблицами **`Product`** и **`ProductCost`**. Для продолжения вам необходимо убедиться, что у вас созданы созданы обе таблицы:

   Таблица **`Product`**:
   ![Заполненные данные для создания таблицы Product, 1](images/table_editor/new_table_creation_1st_half.png)
   ![Заполненные данные для создания таблицы Product, 2](images/table_editor/new_table_creation_2nd_half.png)

   Таблцица `ProductCost` (пока без заполненного внешнего ключа):
   ![Заполненные данные для создания таблицы ProductCost, 1](image-36.png)
   ![Заполненные данные для создания таблицы ProductCost, 2](image-37.png)

   Чтобы настроить внешний ключ в таблице, требуется перейти в раздел **Foreign keys** и нажать на кнопку **Add foreign key relation**.

   ![Установка внешнего ключа](images/table_editor/columns/add_foreign_key_relation-focused.png)

   Далее открывается окно настройки внешнего ключа в таблице `ProductCost`. При нажатии на иконку с двумя диагональными стрелками, раскрывается ссылка на [документацию](https://www.postgresql.org/docs/current/tutorial-fk.html) по внешним ключам.

   ![product_cost_info_expand-focus](images/table_editor/foreign_keys/product_cost_info_expand-focus.jpg)

   ![product_cost_info_documentation-focus](images/table_editor/foreign_keys/product_cost_info_documentation-focus.jpg)

 Далее следует убедиться, что выбрана правильная схема базы данных (в нашем случае **public**)

![alt text](image.png)

Затем необходимо выбрать таблицу, на которую будут ссылаться выбранные столбцы. В нашем примере выбираем таблицу `Product`.

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

Полностью заполненная форма создания внешнего ключа между таблицами `Product` и `ProductCost` представлена на скринах ниже:

![foreign key product and product_cost product 1](image-15.png)
![foreign key product and product_cost product 2](image-16.png)

Если Вы хотите отменить изменения, нажмите **Cancel**.

![cancel](image-13.png)

Для сохранения всех изменений, нажмите **Save**.

![save](image-14.png)

### Шаг 6: Завершение создания таблиц

1. После заполнения всех необходимых данных и параметров для создания таблиц, вы увидите готовую таблицу к сохранению:

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

Убедитесь, что у вас созданы все остальные таблицы. (Также, вы имеете возможность сделать это быстрее при помощи SQL Editor, который будет рассмотрен в следующем пункте).

Заполненная таблица **`Storage`**:

![alt text](image-18.png)

![alt text](image-19.png)

Заполненная таблица **`Employee`**:

![alt text](image-20.png)

![alt text](image-21.png)

Заполненная таблица **`Operation`**:

![alt text](image-22.png)

![alt text](image-23.png)

![alt text](image-24.png)

![alt text](image-25.png)

![alt text](image-26.png)

![alt text](image-27.png)

![alt text](image-28.png)

Заполненная таблица **`ProductOperation`**:

![alt text](image-29.png)

![alt text](image-30.png)

![alt text](image-31.png)

![alt text](image-32.png)

![alt text](image-33.png)

![alt text](image-34.png)

Заполненная таблица **`ProductCost`** (с заполненными внешними ключами):

![alt text](image-36.png)

![alt text](image-37.png)

![alt text](image-38.png)

![alt text](image-39.png)

![alt text](image-40.png)

### Шаг 7: Просмотр и работа с новой таблицей

После сохранения таблицы будут доступна для работы в **Table Editor** и других разделах Supabase, таких как **SQL Editor** для выполнения запросов.

![Table Editor после создания таблицы](image-35.png)

---

## 2. SQL Editor




# Руководство по созданию таблиц в Supabase с помощью SQL Editor

### Шаг 1: Открытие SQL Editor

Для того, чтобы воспользоваться редактором таблиц **SQL Editor**, необходимо кликнуть на кнопку с соответствующим названием.

![SQL Editor Фокус](images\main_screen\sql_editor-focus.png)

При переходе по указанной выше кнопке будет отображено главное окно редактора **SQL Editor**.

![main screen](images/sql_editor/main_screen.png) 

Для того, чтобы исполнить нижеописанный SQL код, необходимо скопировать его и нажать на кнопку **Run CTRL**.

![run focused](images/sql_editor/run-focused.png)

---

### Шаг 2: Создание типа `operation_type`

Создание перечисляемого типа для обозначения операций.

```sql
CREATE TYPE operation_type AS ENUM (
  'поступление',
  'списание'
);
```

---

### Шаг 3: Создание типа `measurement_unit`

Создание перечисляемого типа для единиц измерения.

```sql
CREATE TYPE measurement_unit AS ENUM (
  'килограммы',
  'штуки',
  'литры',
  'метры'
);
```

---

### Шаг 4: Создание таблицы `Product`

Эта таблица содержит информацию о продуктах.

```sql
CREATE TABLE Product (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR NOT NULL,
    description VARCHAR,
    measurement_unit measurement_unit
);
```

- **id**: Уникальный идентификатор продукта (Primary Key).
- **name**: Название продукта.
- **description**: Описание продукта (может быть NULL).
- **measurement\_unit**: Единица измерения продукта.

---

### Шаг 5: Создание таблицы `ProductCost`

Таблица для хранения стоимости продуктов на определённые даты.

```sql
CREATE TABLE ProductCost (
    id BIGSERIAL PRIMARY KEY,
    date TIMESTAMPTZ NOT NULL,
    cost FLOAT8 NOT NULL,
    product_id BIGINT NOT NULL REFERENCES Product(id)
);
```

- **id**: Уникальный идентификатор стоимости (Primary Key).
- **date**: Дата, когда была зафиксирована стоимость.
- **cost**: Стоимость продукта.
- **product\_id**: Внешний ключ, ссылающийся на `Product(id)`.

---

### Шаг 6: Создание таблицы `Employee`

Таблица для хранения информации о сотрудниках.

```sql
CREATE TABLE Employee (
    id BIGSERIAL PRIMARY KEY,
    fullname VARCHAR NOT NULL,
    is_manager BOOLEAN
);
```

- **id**: Уникальный идентификатор сотрудника (Primary Key).
- **fullname**: Полное имя сотрудника.
- **is\_manager**: Флаг, указывающий, является ли сотрудник менеджером.

---

### Шаг 7: Создание таблицы `Storage`

Таблица для хранения информации о складах.

```sql
CREATE TABLE Storage (
    id BIGSERIAL PRIMARY KEY,
    number INT NOT NULL
);
```

- **id**: Уникальный идентификатор склада (Primary Key).
- **number**: Номер склада.

---

### Шаг 8: Создание таблицы `Work`

Таблица для учета работы сотрудников на складах.

```sql
CREATE TABLE Work (
    storage_id BIGINT NOT NULL REFERENCES Storage(id),
    employee_id BIGINT NOT NULL REFERENCES Employee(id),
    date_start TIMESTAMP NOT NULL,
    date_end TIMESTAMP,
    wage_rate NUMERIC,
    PRIMARY KEY (storage_id, employee_id)
);
```

- **storage\_id**: Внешний ключ, ссылающийся на `Storage(id)`.
- **employee\_id**: Внешний ключ, ссылающийся на `Employee(id)`.
- **date\_start**: Дата начала работы.
- **date\_end**: Дата окончания работы (может быть NULL).
- **wage\_rate**: Ставка оплаты труда.

---

### Шаг 9: Создание таблицы `Operation`

Таблица для хранения информации об операциях на складах.

```sql
CREATE TABLE Operation (
    id BIGSERIAL PRIMARY KEY,
    date TIMESTAMPTZ NOT NULL,
    type operation_type NOT NULL,
    storage_id BIGINT NOT NULL REFERENCES Storage(id),
    employee_id BIGINT REFERENCES Employee(id)
);
```

- **id**: Уникальный идентификатор операции (Primary Key).
- **date**: Дата операции.
- **type**: Тип операции.
- **storage\_id**: Внешний ключ, ссылающийся на `Storage(id)`.
- **employee\_id**: Внешний ключ, ссылающийся на `Employee(id)` (может быть NULL).

---

### Шаг 10: Создание таблицы `ProductOperation`

Таблица для учета операций с продуктами.

```sql
CREATE TABLE ProductOperation (
    id BIGSERIAL PRIMARY KEY,
    count INT NOT NULL,
    product_id BIGINT NOT NULL REFERENCES Product(id),
    operation_id BIGINT NOT NULL REFERENCES Operation(id)
);
```

- **id**: Уникальный идентификатор (Primary Key).
- **count**: Количество продукта, связанное с операцией.
- **product\_id**: Внешний ключ, ссылающийся на `Product(id)`.
- **operation\_id**: Внешний ключ, ссылающийся на `Operation(id)`.

---

## Заключение

Теперь таблица успешно создана и готова к использованию. Вы можете добавлять данные, выполнять запросы и настраивать связи между таблицами, используя возможности Supabase.
