## Введение

SQL (Structured Query Language) — это стандартный язык для работы с реляционными базами данных. Он используется для создания, чтения, обновления и удаления данных (CRUD).

## Основные операторы

### SELECT
Используется для выборки данных из таблицы.

```sql
SELECT * FROM users; -- Выбрать все столбцы из таблицы users
SELECT name, email FROM users; -- Выбрать только имя и email
```

### WHERE
Фильтрует записи по определенному условию.

```sql
SELECT * FROM users WHERE age > 18;
SELECT * FROM orders WHERE status = 'completed';
```

### INSERT
Добавляет новые записи в таблицу.

```sql
INSERT INTO users (name, email, age) VALUES ('John Doe', 'john@example.com', 25);
```

### UPDATE
Обновляет существующие записи.

```sql
UPDATE users SET age = 26 WHERE name = 'John Doe';
```

### DELETE
Удаляет записи из таблицы.

```sql
DELETE FROM users WHERE id = 1;
```

## Агрегатные функции

SQL предоставляет функции для выполнения вычислений над набором значений.

* `COUNT(*)`: Подсчитывает количество строк.
* `SUM(column)`: Суммирует значения в столбце.
* `AVG(column)`: Вычисляет среднее значение.
* `MIN(column)`: Находит минимальное значение.
* `MAX(column)`: Находит максимальное значение.

```sql
SELECT COUNT(*) FROM orders;
SELECT AVG(price) FROM products;
```

## Группировка данных (GROUP BY)

Позволяет группировать строки с одинаковыми значениями в указанных столбцах. Часто используется с агрегатными функциями.

```sql
SELECT status, COUNT(*) FROM orders GROUP BY status;
```

## Сортировка (ORDER BY)

Сортирует результат выборки.

```sql
SELECT * FROM users ORDER BY age DESC; -- Сортировка по убыванию возраста
```

## Объединение таблиц (JOIN)

Позволяет получать данные из нескольких таблиц одновременно.

### INNER JOIN
Возвращает только те строки, для которых есть совпадение в обеих таблицах.

```sql
SELECT users.name, orders.id 
FROM users 
INNER JOIN orders ON users.id = orders.user_id;
```

### LEFT JOIN
Возвращает все строки из левой таблицы и совпадающие строки из правой. Если совпадения нет, возвращается NULL.

```sql
SELECT users.name, orders.id 
FROM users 
LEFT JOIN orders ON users.id = orders.user_id;
```

## Типы данных

* `INTEGER`: Целое число.
* `VARCHAR(n)`: Строка переменной длины (до n символов).
* `TEXT`: Длинный текст.
* `BOOLEAN`: Логическое значение (TRUE/FALSE).
* `DATE`: Дата.
* `TIMESTAMP`: Дата и время.

## Практические советы

1. **Используйте алиасы (AS)** для улучшения читаемости запросов.
2. **Всегда фильтруйте данные (WHERE)** перед группировкой, если это возможно, для повышения производительности.
3. **Избегайте `SELECT *`** в продакшн-коде, перечисляйте только нужные столбцы.
4. **Используйте транзакции** для операций, изменяющих данные, чтобы обеспечить целостность.
