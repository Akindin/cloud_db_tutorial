# Типы данных в SQL (PostgreSQL)

В этом руководстве мы рассмотрим основные типы данных, поддерживаемые PostgreSQL, и их использование. Понимание типов данных является важным аспектом при проектировании базы данных.

---

## Основные категории типов данных

Типы данных в PostgreSQL делятся на несколько основных категорий:

1. **Числовые**
2. **Символьные**
3. **Дата и время**
4. **Булевы**
5. **Структурированные**
6. **Геометрические**
7. **JSON и XML**
8. **Пользовательские**

---

## 1. Числовые типы данных

Числовые типы данных используются для хранения целых и дробных чисел.

### Целые числа

- `SMALLINT`: Целое число от -32,768 до 32,767.
- `INTEGER` или `INT`: Целое число от -2,147,483,648 до 2,147,483,647.
- `BIGINT`: Целое число от -9,223,372,036,854,775,808 до 9,223,372,036,854,775,807.

### Дробные числа

- `REAL`: Число с плавающей точкой (4 байта).
- `DOUBLE PRECISION`: Число с двойной точностью (8 байт).
- `NUMERIC` или `DECIMAL`: Число с фиксированной точностью.

Пример:
```sql
CREATE TABLE example_numbers (
    id SERIAL PRIMARY KEY,
    small_value SMALLINT,
    big_value BIGINT,
    precise_value NUMERIC(10, 2)
);
```

---

## 2. Символьные типы данных

Используются для хранения строк текста.

- `CHAR(n)`: Строка фиксированной длины.
- `VARCHAR(n)`: Строка переменной длины, максимальная длина — n символов.
- `TEXT`: Текст переменной длины без ограничения.

Пример:
```sql
CREATE TABLE example_text (
    id SERIAL PRIMARY KEY,
    fixed_length CHAR(10),
    variable_length VARCHAR(50),
    unlimited_length TEXT
);
```

---

## 3. Типы данных для даты и времени

Позволяют хранить значения даты, времени или их комбинации.

- `DATE`: Только дата (гггг-мм-дд).
- `TIME`: Только время (чч:мм:сс).
- `TIMESTAMP`: Дата и время.
- `INTERVAL`: Интервал времени.
- `TIMETZ` и `TIMESTAMPTZ`: Включают часовой пояс.

Пример:
```sql
CREATE TABLE example_datetime (
    id SERIAL PRIMARY KEY,
    event_date DATE,
    event_time TIME,
    event_timestamp TIMESTAMPTZ
);
```

---

## 4. Булевы типы данных

- `BOOLEAN`: Принимает значения `TRUE`, `FALSE` или `NULL`.

Пример:
```sql
CREATE TABLE example_boolean (
    id SERIAL PRIMARY KEY,
    is_active BOOLEAN
);
```

---

## 5. Структурированные типы данных

Для хранения сложных структур данных.

- `ARRAY`: Массив значений.
- `JSON` и `JSONB`: Структурированные данные в формате JSON.
- `XML`: Хранение XML-данных.

Пример:
```sql
CREATE TABLE example_structured (
    id SERIAL PRIMARY KEY,
    tags TEXT[],
    metadata JSONB
);
```

---

## 6. Геометрические типы данных

Используются для хранения геометрических объектов.

- `POINT`: Точка в двумерном пространстве.
- `LINE`, `LSEG`: Линия и отрезок.
- `BOX`, `CIRCLE`, `POLYGON`: Фигуры.

Пример:
```sql
CREATE TABLE example_geometry (
    id SERIAL PRIMARY KEY,
    location POINT,
    area CIRCLE
);
```

---

## 7. Пользовательские типы данных

PostgreSQL позволяет создавать собственные типы данных, такие как перечисления (ENUM) или домены (DOMAIN).

Пример:
```sql
CREATE TYPE mood AS ENUM ('happy', 'sad', 'neutral');
CREATE TABLE example_custom (
    id SERIAL PRIMARY KEY,
    current_mood mood
);
```

---

## Заключение

Теперь вы знакомы с основными типами данных в PostgreSQL. Использование подходящих типов данных поможет оптимизировать производительность и упростить работу с базой данных.

