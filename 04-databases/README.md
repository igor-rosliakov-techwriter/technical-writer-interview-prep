# Databases for Technical Writer Interviews

A cheat sheet on database questions and practical tasks for technical writer interviews.

The first seven questions cover reusable fundamentals. The last six come from published interview experiences, including technical writer exercises at a database company. Wording is translated or condensed. Where a source reports only the topic of an exercise, this guide does not claim to reproduce the original prompt.

Review: 2026-11-03. The Cockroach Labs, Therap, and employee-manager reports
were rechecked. Other earlier interview sources that could not be opened
are marked unverified; their attribution is not treated as confirmed.

Проверка: 2026-11-03. Рассказы Cockroach Labs, Therap и задание о сотрудниках
и руководителях проверены повторно. Недоступные старые источники отмечены;
их атрибуция не считается подтверждённой.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — short interview answer, details.
- 🇷🇺 **Русский** — короткий ответ на собеседовании, подробнее.

---

**General questions / Общие вопросы**

## 1. What is a database? / Что такое база данных?

### 🇬🇧 English

#### Interview answer

> A database is an organized collection of data. A DBMS manages its storage, queries, updates, permissions, and constraints.

#### Details

Keep the distinction between *data* and the *system managing it*. A table has columns that describe fields and rows that hold records. SQL is a language used to define, query, and change relational data; it is not the database product itself.

For a technical writer, the useful follow-up is: Which product and version does the reader use? What data model, permissions, and SQL dialect do the examples assume?

### 🇷🇺 Русский

#### Ответ на собеседовании

> База данных — организованный набор данных. СУБД управляет хранением, запросами, изменениями, доступом и ограничениями.

#### Подробнее

Важно различать сами данные и систему, которая ими управляет. У таблицы есть столбцы с описанием полей и строки с записями. SQL — язык для определения, чтения и изменения реляционных данных, а не название СУБД.

Техписателю стоит уточнить продукт и версию, модель данных, нужные права и диалект SQL, для которого написаны примеры.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.ambitionbox.com/profiles/Technical-Writer/interview-questions).

---

## 2. What are the main parts of a simple SQL query? / Из каких частей состоит простой SQL-запрос?

### 🇬🇧 English

#### Interview answer

> SELECT chooses output, FROM its source, and WHERE filters rows. GROUP BY forms groups, HAVING filters groups, and ORDER BY sorts results.

#### Details

```sql
SELECT id, email
FROM users
WHERE active = TRUE
ORDER BY id;
```

Read this as: take rows from `users`, keep active users, return their IDs and emails, then sort by ID. `SELECT *` returns all columns, but explicit columns make examples and result descriptions easier to maintain. SQL dialects differ, so check the target product before documenting syntax.

### 🇷🇺 Русский

#### Ответ на собеседовании

> SELECT выбирает результат, FROM — источник, WHERE фильтрует строки. GROUP BY создаёт группы, HAVING фильтрует группы, ORDER BY сортирует результат.

#### Подробнее

```sql
SELECT id, email
FROM users
WHERE active = TRUE
ORDER BY id;
```

Этот запрос берёт строки из `users`, оставляет активных пользователей, возвращает их идентификаторы и адреса электронной почты, затем сортирует по `id`. `SELECT *` возвращает все столбцы, но перечисление нужных полей делает пример и описание результата устойчивее к изменениям таблицы. Синтаксис нужно проверять для конкретной СУБД.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/SQL/comments/1dp6n2q/). **Technical reference / Справка:** [PostgreSQL `SELECT`](https://www.postgresql.org/docs/current/sql-select.html).

---

## 3. How do primary keys, unique constraints, and foreign keys differ? / Чем отличаются первичный ключ, `UNIQUE` и внешний ключ?

### 🇬🇧 English

#### Interview answer

> A primary key uniquely identifies rows and excludes NULL. UNIQUE enforces uniqueness; a foreign key enforces a reference to an eligible key, including within the same table.

#### Details

For example, `users.id` may be the primary key, `users.email` may be unique, and `orders.user_id` may reference `users.id`. A table has one primary-key constraint, which can cover several columns. Rules for null values in unique constraints vary by DBMS and configuration; avoid promising identical behavior across products.

A foreign key can reference the same table or another table, usually a primary or eligible unique key. A nullable foreign-key column can contain NULL without a matching row; composite keys have additional matching rules. Check the DBMS and constraint definition.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Первичный ключ уникально определяет строки и исключает NULL. UNIQUE обеспечивает уникальность, внешний ключ — ссылочную целостность, в том числе внутри одной таблицы.

#### Подробнее

Например, `users.id` может быть первичным ключом, `users.email` — уникальным полем, а `orders.user_id` — ссылкой на `users.id`. В таблице одно ограничение первичного ключа, но оно может состоять из нескольких столбцов. Правила для `NULL` в `UNIQUE` зависят от СУБД и настроек.

Внешний ключ может ссылаться на ту же или другую таблицу, обычно на первичный или подходящий уникальный ключ. Nullable-столбец внешнего ключа может содержать NULL без строки-пары; у составных ключей есть дополнительные правила сопоставления. Проверяй СУБД и определение ограничения.

**Interview evidence / Источник вопроса:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/). **Technical reference / Справка:** [PostgreSQL constraints](https://www.postgresql.org/docs/current/ddl-constraints.html).

---

## 4. What are normalization and denormalization? / Что такое нормализация и денормализация?

### 🇬🇧 English

#### Interview answer

> Normalization reduces redundancy and update anomalies by organizing related data. Denormalization deliberately adds redundancy for a specific access pattern, with consistency trade-offs.

#### Details

Do not treat denormalization as an automatic improvement. Ask which queries matter, how often data changes, and which source is authoritative. Documentation should explain the relationship between tables and whether duplicated fields are snapshots or kept in sync.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Нормализация уменьшает дублирование и аномалии обновления, упорядочивая данные. Денормализация намеренно добавляет дублирование под конкретные запросы, усложняя согласованность.

#### Подробнее

Денормализация не всегда ускоряет систему. Нужно узнать, какие запросы важны, как часто меняются данные и где хранится исходное значение. В документации стоит объяснить связи таблиц и указать, являются ли дублируемые поля снимками данных или обновляются вместе с источником.

**Interview evidence / Источник вопроса:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/).

---

## 5. What is the difference between `INNER JOIN` and `OUTER JOIN`? / Чем `INNER JOIN` отличается от `OUTER JOIN`?

### 🇬🇧 English

#### Interview answer

> INNER JOIN returns matching row combinations. OUTER JOIN also preserves unmatched rows from one or both sides, filling missing values with NULL.

#### Details

```sql
SELECT u.id, o.id AS order_id
FROM users AS u
LEFT JOIN orders AS o ON o.user_id = u.id;
```

This includes users without orders; their `order_id` is `NULL`. Replacing `LEFT JOIN` with `INNER JOIN` removes those users. If one user has several orders, the user appears in several result rows. A filter on the right-hand table in `WHERE` can remove the unmatched rows, so inspect both `ON` and `WHERE` when explaining a query.

### 🇷🇺 Русский

#### Ответ на собеседовании

> INNER JOIN возвращает сочетания совпавших строк. OUTER JOIN сохраняет также строки без пары с одной или обеих сторон, подставляя NULL.

#### Подробнее

```sql
SELECT u.id, o.id AS order_id
FROM users AS u
LEFT JOIN orders AS o ON o.user_id = u.id;
```

Этот пример покажет и пользователей без заказов: их `order_id` будет `NULL`. При `INNER JOIN` такие пользователи исчезнут из результата. Если у пользователя несколько заказов, он появится в нескольких строках. Условие на правую таблицу в `WHERE` может убрать строки без пары, поэтому при чтении запроса проверяй и `ON`, и `WHERE`.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://asktom.oracle.com/Misc/interview-question.html). **Technical reference / Справка:** [PostgreSQL joins](https://www.postgresql.org/docs/current/tutorial-join.html).

---

## 6. What is a transaction, and what does ACID mean? / Что такое транзакция и что означает ACID?

### 🇬🇧 English

#### Interview answer

> A transaction groups operations into one unit. ACID means all-or-nothing changes, preserved constraints, controlled concurrency, and durability after commit.

#### Details

When moving money between accounts, debit and credit should be part of one transaction. `COMMIT` completes it; `ROLLBACK` discards uncommitted changes. Isolation is not a single behavior across all DBMSs: products and configured isolation levels affect what concurrent transactions can observe. For documentation, check retry behavior and error handling as well as the happy path.

ACID expands to **Atomicity, Consistency, Isolation, Durability**. Consistency means preserving defined invariants, not that every replica instantly returns the same value. Transactions can also be read-only. Durability depends on the database's guarantees and configuration.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Транзакция объединяет операции в одно целое. ACID означает «всё или ничего», сохранение ограничений, изоляцию параллельных операций и долговечность после фиксации.

#### Подробнее

При переводе денег списание и зачисление должны входить в одну транзакцию. `COMMIT` фиксирует её, `ROLLBACK` отменяет ещё не зафиксированные изменения. Поведение параллельных операций зависит от СУБД и уровня изоляции. В документации нужно учитывать повторные попытки и ошибки, а не только успешный сценарий.

ACID — **Atomicity, Consistency, Isolation, Durability**: атомарность, согласованность, изоляция, долговечность. Согласованность здесь — сохранение заданных инвариантов, а не мгновенное совпадение значений на всех репликах. Транзакции могут быть и read-only. Долговечность зависит от гарантий СУБД и настроек.

**Interview evidence / Источник вопроса:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/). **Technical references / Справка:** [PostgreSQL transactions](https://www.postgresql.org/docs/current/tutorial-transactions.html), [isolation levels](https://www.postgresql.org/docs/current/transaction-iso.html).

---

## 7. Why use an index, and what kinds are there? / Зачем нужен индекс и какие бывают виды?

### 🇬🇧 English

#### Interview answer

> An index can speed up reads but costs storage and write work. Types depend on the DBMS; PostgreSQL uses B-tree by default and also offers GIN and BRIN.

#### Details

A B-tree often supports equality and range conditions. PostgreSQL also has, for example, GIN indexes for searching components of array-like values and BRIN indexes that summarize ranges of table blocks. Index types and use cases depend on the DBMS. To describe a slow query accurately, inspect its execution plan instead of assuming that an index will always be used.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Индекс может ускорить чтение, но занимает место и усложняет запись. Типы зависят от СУБД: в PostgreSQL по умолчанию B-tree, также есть GIN и BRIN.

#### Подробнее

B-tree часто подходит для поиска по равенству и диапазону. В PostgreSQL есть также GIN для поиска элементов внутри составных значений и BRIN, который хранит сводку по диапазонам блоков таблицы. Набор типов зависит от СУБД. Если запрос медленный, нужно смотреть план его выполнения, а не предполагать, что индекс обязательно будет использован.

**Interview evidence / Источник вопроса:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/). **Technical references / Справка:** [PostgreSQL index types](https://www.postgresql.org/docs/current/indexes-types.html), [examining index usage](https://www.postgresql.org/docs/current/indexes-examine.html).

---

**Specific reported exercises / Конкретные задания из опубликованных примеров**

## 8. Install a DBMS, create a database and table, and document a SQL statement / Установите СУБД, создайте базу и таблицу, затем опишите SQL-команду

### 🇬🇧 English

#### Interview answer

> I would perform the setup and SQL task in a test environment, then document prerequisites, commands, expected results, and verified errors.

#### Details

This was a take-home task reported by a technical writer who interviewed at Cockroach Labs. The published account does not name the SQL statement. Do not pretend the exercise was about a particular command. For a real submission, use a disposable test environment and distinguish tested behavior from assumptions.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я выполню установку и SQL-задание в тестовой среде, затем опишу требования, команды, ожидаемые результаты и проверенные ошибки.

#### Подробнее

Это домашнее задание описала техписательница, проходившая собеседование в Cockroach Labs. Какую именно SQL-команду ей дали, автор не уточнила. При выполнении подобного задания нужен отдельный тестовый стенд, а непроверенные предположения следует отличать от подтверждённого поведения.

**Interview evidence / Источник задания:** [First-hand Cockroach Labs interview account](https://www.cockroachlabs.com/blog/navigating-tech-writer/).

---

## 9. Learn and document a distributed transaction model / Разберитесь в модели распределённых транзакций и опишите её

### 🇬🇧 English

#### Interview answer

> I would clarify transaction scope, commit, isolation, and retries. Then I would confirm my understanding with the engineer and explain one concrete scenario.

#### Details

In the reported Cockroach Labs interview, an engineer explained the distributed transaction model and the candidate documented it afterward. The public account does not contain a verbatim question or the full technical explanation. CockroachDB's documentation describes atomic transactions across distributed instances and possible retry errors under contention. Those are product-specific behaviors to verify before writing instructions.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я уточню границы транзакции, фиксацию, изоляцию и повторы. Затем сверю понимание с инженером и объясню конкретный сценарий.

#### Подробнее

На описанном собеседовании инженер объяснял модель распределённых транзакций, после чего кандидатка её документировала. Дословный вопрос и полное техническое объяснение не опубликованы. Документация CockroachDB описывает атомарные транзакции в распределённой системе и возможные ошибки, требующие повтора при конкурирующих операциях. Это свойства конкретного продукта, их нужно проверять перед публикацией инструкции.

**Interview evidence / Источник задания:** [First-hand Cockroach Labs interview account](https://www.cockroachlabs.com/blog/navigating-tech-writer/). **Technical reference / Справка:** [CockroachDB developer basics](https://www.cockroachlabs.com/docs/stable/developer-basics.html).

---

## 10. Learn and document online schema changes / Разберитесь в изменениях схемы работающей базы и опишите их

### 🇬🇧 English

#### Interview answer

> I would verify supported operations, effects on reads and writes, and recovery steps. Online schema changes do not automatically mean zero downtime.

#### Details

The Cockroach Labs candidate reported a technical discussion about online schema changes followed by a writing task. The public account does not include the exact prompt. Avoid a blanket promise of zero downtime for every database or every operation: capabilities and restrictions vary by product and change type.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я проверю допустимые операции, влияние на чтение и запись и восстановление после ошибок. Online-изменения схемы не гарантируют отсутствие простоя.

#### Подробнее

Кандидатка в Cockroach Labs рассказала о техническом обсуждении изменений схемы работающей базы и последующем письменном задании. Точный текст задания не опубликован. Возможности зависят от продукта и операции, поэтому обещание работы без простоя нужно проверять для каждого случая.

**Interview evidence / Источник задания:** [First-hand Cockroach Labs interview account](https://www.cockroachlabs.com/blog/navigating-tech-writer/). **Technical reference / Справка:** [CockroachDB online schema changes](https://www.cockroachlabs.com/docs/stable/online-schema-changes).

---

## 11. Count rows by month and find the busiest month / Посчитайте строки по месяцам и найдите месяц с наибольшим числом строк

### 🇬🇧 English

#### Interview answer

> I would group rows by month and count them. First, I would clarify the date range, ties, and whether empty months must appear.

#### Details

```sql
SELECT month, COUNT(*) AS row_count
FROM t
GROUP BY month
ORDER BY row_count DESC, month;
```

This lists months present in `t`, with the largest counts first. `LIMIT 1` would return only one winner and hide ties. The task is ambiguous without a tie rule and a zero-row-month rule; document both. The original interview attribution could not be reverified in this review.

Here `month` is an existing grouping column. If it only contains numbers 1-12, different years are combined. For timestamps, define a year-month bucket and reporting timezone. Including absent months requires a calendar table or generated series.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я сгруппирую строки по месяцам и подсчитаю их. Сначала уточню период, правило для равных максимумов и необходимость месяцев без записей.

#### Подробнее

```sql
SELECT month, COUNT(*) AS row_count
FROM t
GROUP BY month
ORDER BY row_count DESC, month;
```

Этот запрос показывает только месяцы из таблицы `t`, начиная с наиболее частых. `LIMIT 1` оставит одного победителя и скроет равенство результатов. Без правил для ничьей и месяцев с нулём записей задача неоднозначна; их нужно зафиксировать. Исходную атрибуцию интервью повторно проверить не удалось.

Здесь `month` — готовый столбец группировки. Если в нём только числа 1–12, разные годы объединятся. Для timestamp сначала задай год-месяц и часовой пояс отчёта. Чтобы включить отсутствующие месяцы, нужна календарная таблица или сгенерированный ряд.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://asktom.oracle.com/Misc/interview-question.html).

---

## 12. Solve JOIN tasks using the Oracle HR schema / Решите задачи с `JOIN` на схеме Oracle HR

### 🇬🇧 English

#### Interview answer

> I would map output fields to tables, find join keys, and decide whether to keep unmatched rows. Then I would check missing and duplicated results.

#### Details

A candidate for a database engineer role reported solving several `JOIN` tasks on the Oracle HR sample schema. The exact tasks were not published, so this entry records the method rather than inventing their conditions. For a technical writer, that method also helps explain where each documented output field comes from.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я сопоставлю поля с таблицами, найду ключи соединения и решу, сохранять ли строки без пары. Затем проверю пропуски и дублирование результатов.

#### Подробнее

Кандидат на позицию инженера баз данных рассказал, что решал задачи с `JOIN` на учебной схеме Oracle HR. Точные условия не опубликованы, поэтому здесь описан подход, а не вымышленное задание. Техписателю такой подход помогает также объяснять происхождение полей в результате запроса.

**Interview evidence / Источник задания:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/).

---

## 13. Show each employee and their manager / Покажите каждого сотрудника и его руководителя

### 🇬🇧 English

#### Interview answer

> I would self-join employees using the employee's manager_id and the manager's id. LEFT JOIN keeps employees without a manager.

#### Details

This illustrative query assumes a table `employees(id, name, manager_id)`. The published interview report describes the employee-manager task but does not publish its exact schema.

```sql
SELECT e.name AS employee, m.name AS manager
FROM employees AS e
LEFT JOIN employees AS m ON e.manager_id = m.id;
```

The alias `e` means the employee row, and `m` means the manager row. A top-level employee appears with a `NULL` manager. If the report must exclude such employees, use an inner join instead.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я соединю таблицу сотрудников с ней самой по manager_id сотрудника и id руководителя. LEFT JOIN сохранит сотрудников без руководителя.

#### Подробнее

```sql
SELECT e.name AS employee, m.name AS manager
FROM employees AS e
LEFT JOIN employees AS m ON e.manager_id = m.id;
```

Этот пример использует условную таблицу `employees(id, name, manager_id)`. В опубликованном рассказе есть само задание, но точная схема таблицы не приведена. Псевдоним `e` обозначает сотрудника, `m` — руководителя. Сотрудник верхнего уровня получит `NULL` в поле руководителя. При `INNER JOIN` он исчезнет из результата.

**Interview evidence / Источник задания:** [First-hand report from a senior data analyst interview](https://www.reddit.com/r/SQL/comments/1lxzz8x/here_are_some_sql_questions_i_was_asked_for_a/).

---

## What this research suggests / Что показал поиск

### 🇬🇧 English

The strongest technical-writer-specific evidence here is the [first-hand Cockroach Labs interview account](https://www.cockroachlabs.com/blog/navigating-tech-writer/) and the company's [published technical writer exercises](https://github.com/cockroachlabs/open-sourced-interview-process/blob/master/DocumentationExercises.md). Other question sources describe SQL, analyst, or database engineer interviews. They show that these questions are real, not that every technical writer will receive them. Prepare questions 1-7 and exercises 8, 11, and 12 first; go deeper into exercises 9 and 10 for database-product roles.

### 🇷🇺 Русский

Самое прямое свидетельство о собеседовании техписателя здесь — [рассказ кандидатки в Cockroach Labs](https://www.cockroachlabs.com/blog/navigating-tech-writer/) и [опубликованные компанией задания](https://github.com/cockroachlabs/open-sourced-interview-process/blob/master/DocumentationExercises.md). Остальные источники относятся к собеседованиям по SQL, аналитике или инженерии баз данных. Они подтверждают, что вопросы реальны, но не обещают их на каждом собеседовании техписателя. Сначала подготовь вопросы 1–7 и задания 8, 11, 12; к заданиям 9 и 10 углубляйся для вакансий в компаниях, разрабатывающих СУБД.
