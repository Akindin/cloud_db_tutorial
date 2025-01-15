# Руководство по использованию команд ALTER и DROP TABLE в SQL (PostgreSQL)

В этом руководстве рассмотрим основные способы применения команды `ALTER` для изменения структуры таблиц. Также продемонстрируем использование команды `DROP TABLE` для удаления таблицы.

---

## 1. Добавление новых столбцов

Для добавления нового столбца в таблицу используется команда `ADD COLUMN`.

Пример: Добавим столбцы `address` и `phone` в таблицу `Storage`.

```sql
ALTER TABLE "Storage"
ADD COLUMN address VARCHAR(255),
ADD COLUMN phone VARCHAR(20);
```

Добавим уникальный СНИЛС для сотрудников в таблицу `Employee`:

```sql
ALTER TABLE "Employee"
ADD COLUMN snils VARCHAR(11) UNIQUE;
```

---

## 2. Изменение внешних ключей

Для обновления внешних ключей добавим действия `ON UPDATE` и `ON DELETE` для различных таблиц.

Пример:

```sql
-- Удаляем старый внешний ключ для product_id в таблице ProductCost
ALTER TABLE "ProductCost"
DROP CONSTRAINT "ProductCost_product_id_fkey";

-- Добавляем новый внешний ключ с действиями ON UPDATE CASCADE и ON DELETE RESTRICT
ALTER TABLE "ProductCost"
ADD CONSTRAINT "ProductCost_product_id_fkey"
FOREIGN KEY (product_id)
REFERENCES "Product"(id)
ON UPDATE CASCADE
ON DELETE RESTRICT;

-- Удаляем старые внешние ключи для таблицы ProductOperation
ALTER TABLE "ProductOperation"
DROP CONSTRAINT "productoperation_product_id_fkey",
DROP CONSTRAINT "productoperation_operation_id_fkey";

-- Добавляем новые внешние ключи для product_id с ON UPDATE CASCADE и ON DELETE CASCADE
ALTER TABLE "ProductOperation"
ADD CONSTRAINT "productoperation_product_id_fkey"
FOREIGN KEY (product_id)
REFERENCES "Product"(id)
ON UPDATE CASCADE
ON DELETE CASCADE;

-- Добавляем новые внешние ключи для operation_id с ON UPDATE CASCADE и ON DELETE CASCADE
ALTER TABLE "ProductOperation"
ADD CONSTRAINT "productoperation_operation_id_fkey"
FOREIGN KEY (operation_id)
REFERENCES "Operation"(id)
ON UPDATE CASCADE
ON DELETE CASCADE;

-- Удаляем старые внешние ключи в таблице Operation
ALTER TABLE "Operation"
DROP CONSTRAINT "Operation_storage_id_fkey";
ALTER TABLE "Operation"
DROP CONSTRAINT "Operation_employee_id_fkey";

-- Добавляем новые внешние ключи с ON UPDATE CASCADE и ON DELETE RESTRICT
ALTER TABLE "Operation"
ADD CONSTRAINT "operation_storage_id_fkey"
FOREIGN KEY (storage_id)
REFERENCES "Storage"(id)
ON UPDATE CASCADE
ON DELETE RESTRICT;

ALTER TABLE "Operation"
ADD CONSTRAINT "operation_employee_id_fkey"
FOREIGN KEY (employee_id)
REFERENCES "Employee"(id)
ON UPDATE CASCADE
ON DELETE RESTRICT;

-- Удаляем старые внешние ключи в таблице Work
ALTER TABLE "Work"
DROP CONSTRAINT "Work_storage_id_fkey";
ALTER TABLE "Work"
DROP CONSTRAINT "Work_employee_id_fkey";

-- Добавляем новые внешние ключи с ON UPDATE CASCADE и ON DELETE RESTRICT
ALTER TABLE "Work"
ADD CONSTRAINT "work_storage_id_fkey"
FOREIGN KEY (storage_id)
REFERENCES "Storage"(id)
ON UPDATE RESTRICT
ON DELETE RESTRICT;

ALTER TABLE "Work"
ADD CONSTRAINT "work_employee_id_fkey"
FOREIGN KEY (employee_id)
REFERENCES "Employee"(id)
ON UPDATE CASCADE
ON DELETE RESTRICT;
```

> Для выполнения операций по изменению значений таблицы, см. [руководство по обновлению данных](../update/index.md).

> Для выполнения операций по удалению данных, см. [руководство по удалению данных](../delete/index.md).

---

## 3. Удаление столбцов

Для удаления столбца используется команда `DROP COLUMN`.

Пример: Следующий код удалит столбец `description` из таблицы `Product`.

```sql
ALTER TABLE Product
DROP COLUMN description;
```

---

## 4. Удаление таблицы

Для удаления таблицы используется команда `DROP TABLE`. Важно убедиться, что удаление не затронет существующие таблицы, на которые есть ссылки.

Пример: Создадим временную таблицу и затем удалим её.

```sql
CREATE TABLE TempTable (
    id SERIAL PRIMARY KEY,
    temp_data TEXT
);

-- Удаляем временную таблицу TempTable
DROP TABLE TempTable;
```

---

## Заключение

Команда `ALTER` предоставляет мощные возможности для управления структурой таблиц в базе данных. Соблюдайте осторожность при изменении или удалении таблиц, чтобы избежать потери данных или нарушения связей.

