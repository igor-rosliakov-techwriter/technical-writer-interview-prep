# Databases for Technical Writer Interviews

A cheat sheet on database questions and practical tasks for technical writer interviews.

The first seven questions cover reusable fundamentals. The last six come from published interview experiences, including technical writer exercises at a database company. Wording is translated or condensed. Where a source reports only the topic of an exercise, this guide does not claim to reproduce the original prompt.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — quick recall, interview answer, details.
- 🇷🇺 **Русский** — быстро вспомнить, ответ на собеседовании, подробнее.

---

**General questions / Общие вопросы**

## 1. What is a database? / Что такое база данных?

### 🇬🇧 English

#### Quick recall

**A database stores and organizes data so applications can retrieve and change it. A database management system (DBMS) provides the tools and rules for working with that data.**

#### Interview answer

> A database is an organized collection of data. A DBMS such as PostgreSQL or Oracle Database stores the data, handles queries and updates, and helps enforce rules such as access permissions and data constraints. In a relational database, data is commonly represented as tables connected by keys.

#### Details

Keep the distinction between *data* and the *system managing it*. A table has columns that describe fields and rows that hold records. SQL is a language used to define, query, and change relational data; it is not the database product itself.

For a technical writer, the useful follow-up is: Which product and version does the reader use? What data model, permissions, and SQL dialect do the examples assume?

### 🇷🇺 Русский

#### Быстро вспомнить

**База данных хранит и организует данные. Система управления базами данных (СУБД) даёт инструменты и правила для работы с ними.**

#### Ответ на собеседовании

> База данных — организованный набор данных. СУБД, например PostgreSQL или Oracle Database, хранит их, выполняет запросы и изменения, управляет доступом и помогает соблюдать ограничения данных. В реляционной базе данные обычно представлены таблицами, связанными ключами.

#### Подробнее

Важно различать сами данные и систему, которая ими управляет. У таблицы есть столбцы с описанием полей и строки с записями. SQL — язык для определения, чтения и изменения реляционных данных, а не название СУБД.

Техписателю стоит уточнить продукт и версию, модель данных, нужные права и диалект SQL, для которого написаны примеры.

**Interview evidence / Источник вопроса:** [Technical writer questions reported for Oracle](https://www.ambitionbox.com/profiles/Technical-Writer/interview-questions).

---

## 2. What are the main parts of a simple SQL query? / Из каких частей состоит простой SQL-запрос?

### 🇬🇧 English

#### Quick recall

**`SELECT` chooses output columns, `FROM` names the data source, and `WHERE` filters rows.**

#### Interview answer

> In a basic query, `FROM` identifies the table, `WHERE` limits which rows qualify, and `SELECT` specifies what to return. `ORDER BY` can sort the result. For grouped results, `GROUP BY` collects rows and `HAVING` filters groups.

#### Details

```sql
SELECT id, email
FROM users
WHERE active = TRUE
ORDER BY id;
```

Read this as: take rows from `users`, keep active users, return their IDs and emails, then sort by ID. `SELECT *` returns all columns, but explicit columns make examples and result descriptions easier to maintain. SQL dialects differ, so check the target product before documenting syntax.

### 🇷🇺 Русский

#### Быстро вспомнить

**`SELECT` задаёт столбцы результата, `FROM` указывает источник, а `WHERE` отбирает строки.**

#### Ответ на собеседовании

> В простом запросе `FROM` указывает таблицу, `WHERE` задаёт условие отбора строк, а `SELECT` определяет, какие данные вернуть. `ORDER BY` сортирует результат. Для итогов по группам используют `GROUP BY`, а `HAVING` отбирает готовые группы.

#### Подробнее

Запрос выше берёт строки из `users`, оставляет активных пользователей, возвращает их идентификаторы и адреса электронной почты, затем сортирует по `id`. `SELECT *` возвращает все столбцы, но перечисление нужных полей делает пример и описание результата устойчивее к изменениям таблицы. Синтаксис нужно проверять для конкретной СУБД.

**Interview evidence / Источник вопроса:** [An interviewer describes asking about the body of a SQL query](https://www.reddit.com/r/SQL/comments/1dp6n2q/). **Technical reference / Справка:** [PostgreSQL `SELECT`](https://www.postgresql.org/docs/current/sql-select.html).

---

## 3. How do primary keys, unique constraints, and foreign keys differ? / Чем отличаются первичный ключ, `UNIQUE` и внешний ключ?

### 🇬🇧 English

#### Quick recall

**A primary key identifies a row. `UNIQUE` prevents duplicate values in specified columns. A foreign key links a row to a valid row in another table.**

#### Interview answer

> A primary key is the chosen unique, non-null identifier for a table's rows. A unique constraint enforces uniqueness without making the column the table's primary identifier. A foreign key requires a value to match an allowed key in another table, unless the foreign-key column is allowed to be null.

#### Details

For example, `users.id` may be the primary key, `users.email` may be unique, and `orders.user_id` may reference `users.id`. A table has one primary-key constraint, which can cover several columns. Rules for null values in unique constraints vary by DBMS and configuration; avoid promising identical behavior across products.

### 🇷🇺 Русский

#### Быстро вспомнить

**Первичный ключ определяет строку. `UNIQUE` запрещает повторения в указанных столбцах. Внешний ключ связывает запись с допустимой записью другой таблицы.**

#### Ответ на собеседовании

> Первичный ключ — выбранный уникальный идентификатор строки, который не может быть `NULL`. Ограничение `UNIQUE` следит за уникальностью значения, но не делает столбец главным идентификатором таблицы. Внешний ключ требует, чтобы значение ссылалось на допустимый ключ другой таблицы, если само поле не допускает `NULL`.

#### Подробнее

Например, `users.id` может быть первичным ключом, `users.email` — уникальным полем, а `orders.user_id` — ссылкой на `users.id`. В таблице одно ограничение первичного ключа, но оно может состоять из нескольких столбцов. Правила для `NULL` в `UNIQUE` зависят от СУБД и настроек.

**Interview evidence / Источник вопроса:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/). **Technical reference / Справка:** [PostgreSQL constraints](https://www.postgresql.org/docs/current/ddl-constraints.html).

---

## 4. What are normalization and denormalization? / Что такое нормализация и денормализация?

### 🇬🇧 English

#### Quick recall

**Normalization organizes related facts into tables to reduce unwanted duplication. Denormalization deliberately adds some duplication to support a particular workload.**

#### Interview answer

> Normalization separates data into related tables so each fact has a clear home. For example, customer details can live in `customers`, while orders refer to a customer ID. Denormalization may copy selected values into another table to make common reads simpler or faster, at the cost of keeping copies consistent.

#### Details

Do not treat denormalization as an automatic improvement. Ask which queries matter, how often data changes, and which source is authoritative. Documentation should explain the relationship between tables and whether duplicated fields are snapshots or kept in sync.

### 🇷🇺 Русский

#### Быстро вспомнить

**Нормализация распределяет связанные факты по таблицам, сокращая лишние повторы. Денормализация осознанно добавляет часть повторов под конкретную нагрузку.**

#### Ответ на собеседовании

> При нормализации данные разделяют на связанные таблицы, чтобы у каждого факта было понятное место хранения. Например, сведения о клиенте лежат в `customers`, а заказ ссылается на идентификатор клиента. При денормализации некоторые значения копируют для удобства или скорости частых чтений, но копии нужно согласовывать.

#### Подробнее

Денормализация не всегда ускоряет систему. Нужно узнать, какие запросы важны, как часто меняются данные и где хранится исходное значение. В документации стоит объяснить связи таблиц и указать, являются ли дублируемые поля снимками данных или обновляются вместе с источником.

**Interview evidence / Источник вопроса:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/).

---

## 5. What is the difference between `INNER JOIN` and `OUTER JOIN`? / Чем `INNER JOIN` отличается от `OUTER JOIN`?

### 🇬🇧 English

#### Quick recall

**`INNER JOIN` keeps matching rows from both sides. An outer join can also keep unmatched rows, filling the missing side with nulls.**

#### Interview answer

> An inner join returns rows that satisfy the join condition in both tables. A left outer join also keeps every row from the left table, even if no row matches on the right. Right and full outer joins preserve the right side or both sides respectively, if the DBMS supports them.

#### Details

```sql
SELECT u.id, o.id AS order_id
FROM users AS u
LEFT JOIN orders AS o ON o.user_id = u.id;
```

This includes users without orders; their `order_id` is `NULL`. Replacing `LEFT JOIN` with `INNER JOIN` removes those users. If one user has several orders, the user appears in several result rows. A filter on the right-hand table in `WHERE` can remove the unmatched rows, so inspect both `ON` and `WHERE` when explaining a query.

### 🇷🇺 Русский

#### Быстро вспомнить

**`INNER JOIN` оставляет совпавшие строки. Внешнее соединение может сохранить и строки без пары, подставив `NULL` со стороны недостающей таблицы.**

#### Ответ на собеседовании

> `INNER JOIN` возвращает строки, для которых выполнилось условие соединения в обеих таблицах. `LEFT OUTER JOIN` дополнительно сохраняет все строки левой таблицы, даже если справа нет совпадения. Правое и полное внешние соединения сохраняют правую сторону или обе стороны, если СУБД их поддерживает.

#### Подробнее

Пример выше покажет и пользователей без заказов: их `order_id` будет `NULL`. При `INNER JOIN` такие пользователи исчезнут из результата. Если у пользователя несколько заказов, он появится в нескольких строках. Условие на правую таблицу в `WHERE` может убрать строки без пары, поэтому при чтении запроса проверяй и `ON`, и `WHERE`.

**Interview evidence / Источник вопроса:** [Oracle engineer on a question he asks](https://asktom.oracle.com/Misc/interview-question.html). **Technical reference / Справка:** [PostgreSQL joins](https://www.postgresql.org/docs/current/tutorial-join.html).

---

## 6. What is a transaction, and what does ACID mean? / Что такое транзакция и что означает ACID?

### 🇬🇧 English

#### Quick recall

**A transaction groups operations into one unit. ACID describes atomicity, consistency, isolation, and durability.**

#### Interview answer

> A transaction lets related database changes succeed or fail together. Atomicity means all or none of its changes take effect. Consistency means committed changes preserve defined data rules. Isolation describes how concurrent transactions interact. Durability means committed changes survive a failure according to the DBMS guarantees.

#### Details

When moving money between accounts, debit and credit should be part of one transaction. `COMMIT` completes it; `ROLLBACK` discards uncommitted changes. Isolation is not a single behavior across all DBMSs: products and configured isolation levels affect what concurrent transactions can observe. For documentation, check retry behavior and error handling as well as the happy path.

### 🇷🇺 Русский

#### Быстро вспомнить

**Транзакция объединяет операции в одно целое. ACID обозначает атомарность, согласованность, изоляцию и долговечность.**

#### Ответ на собеседовании

> Транзакция позволяет связанным изменениям выполниться вместе либо не примениться вовсе. Атомарность означает «всё или ничего». Согласованность сохраняет заданные правила данных после фиксации. Изоляция описывает взаимодействие параллельных транзакций. Долговечность означает сохранность зафиксированных изменений в рамках гарантий СУБД.

#### Подробнее

При переводе денег списание и зачисление должны входить в одну транзакцию. `COMMIT` фиксирует её, `ROLLBACK` отменяет ещё не зафиксированные изменения. Поведение параллельных операций зависит от СУБД и уровня изоляции. В документации нужно учитывать повторные попытки и ошибки, а не только успешный сценарий.

**Interview evidence / Источник вопроса:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/). **Technical references / Справка:** [PostgreSQL transactions](https://www.postgresql.org/docs/current/tutorial-transactions.html), [isolation levels](https://www.postgresql.org/docs/current/transaction-iso.html).

---

## 7. Why use an index, and what kinds are there? / Зачем нужен индекс и какие бывают виды?

### 🇬🇧 English

#### Quick recall

**An index is a data structure that can help the DBMS find rows efficiently. It also takes storage and maintenance work.**

#### Interview answer

> An index may speed up filtering, joins, or sorting when it matches the query and the optimizer chooses it. Indexes cost space and add work to writes, so I would choose them for actual access patterns rather than every column. PostgreSQL's common default is a B-tree index; it also offers other types for different kinds of searches.

#### Details

A B-tree often supports equality and range conditions. PostgreSQL also has, for example, GIN indexes for searching components of array-like values and BRIN indexes that summarize ranges of table blocks. Index types and use cases depend on the DBMS. To describe a slow query accurately, inspect its execution plan instead of assuming that an index will always be used.

### 🇷🇺 Русский

#### Быстро вспомнить

**Индекс помогает СУБД находить строки. Он занимает место и требует обновления при изменении данных.**

#### Ответ на собеседовании

> Индекс может ускорить отбор, соединение или сортировку, если подходит запросу и СУБД решает его использовать. Он занимает место и добавляет работу при записи, поэтому индексируют под реальные запросы, а не каждый столбец. В PostgreSQL тип по умолчанию — B-tree; для других задач есть и другие типы.

#### Подробнее

B-tree часто подходит для поиска по равенству и диапазону. В PostgreSQL есть также GIN для поиска элементов внутри составных значений и BRIN, который хранит сводку по диапазонам блоков таблицы. Набор типов зависит от СУБД. Если запрос медленный, нужно смотреть план его выполнения, а не предполагать, что индекс обязательно будет использован.

**Interview evidence / Источник вопроса:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/). **Technical references / Справка:** [PostgreSQL index types](https://www.postgresql.org/docs/current/indexes-types.html), [examining index usage](https://www.postgresql.org/docs/current/indexes-examine.html).

---

**Specific reported exercises / Конкретные задания из опубликованных примеров**

## 8. Install a DBMS, create a database and table, and document a SQL statement / Установите СУБД, создайте базу и таблицу, затем опишите SQL-команду

### 🇬🇧 English

#### Quick recall

**The deliverable is a tested procedure and an accurate explanation of what the SQL statement does.**

#### Interview answer

> I would verify the product version and prerequisites, perform the setup myself, create the database and table, then run the statement against test data. In the documentation I would show the exact command, expected result, required permissions, and any failure cases I observed or verified.

#### Details

This was a take-home task reported by a technical writer who interviewed at Cockroach Labs. The published account does not name the SQL statement. Do not pretend the exercise was about a particular command. For a real submission, use a disposable test environment and distinguish tested behavior from assumptions.

### 🇷🇺 Русский

#### Быстро вспомнить

**Результат — проверенная инструкция и точное объяснение действия SQL-команды.**

#### Ответ на собеседовании

> Я уточню версию продукта и требования к окружению, сам выполню установку, создам базу и таблицу, затем запущу команду на тестовых данных. В инструкции покажу точную команду, ожидаемый результат, необходимые права и проверенные случаи ошибок.

#### Подробнее

Это домашнее задание описала техписательница, проходившая собеседование в Cockroach Labs. Какую именно SQL-команду ей дали, автор не уточнила. При выполнении подобного задания нужен отдельный тестовый стенд, а непроверенные предположения следует отличать от подтверждённого поведения.

**Interview evidence / Источник задания:** [First-hand Cockroach Labs interview account](https://www.cockroachlabs.com/blog/navigating-tech-writer/).

---

## 9. Learn and document a distributed transaction model / Разберитесь в модели распределённых транзакций и опишите её

### 🇬🇧 English

#### Quick recall

**A distributed transaction spans data held across multiple nodes while the database coordinates a consistent outcome.**

#### Interview answer

> I would ask what a transaction can span, when it is considered committed, what isolation guarantee users get, and how applications handle conflicts or retries. I would repeat my understanding to the engineer, then write for the intended reader with one concrete scenario and the relevant limits.

#### Details

In the reported Cockroach Labs interview, an engineer explained the distributed transaction model and the candidate documented it afterward. The public account does not contain a verbatim question or the full technical explanation. CockroachDB's documentation describes atomic transactions across distributed instances and possible retry errors under contention. Those are product-specific behaviors to verify before writing instructions.

### 🇷🇺 Русский

#### Быстро вспомнить

**Распределённая транзакция затрагивает данные на нескольких узлах, а СУБД согласует результат.**

#### Ответ на собеседовании

> Я уточню, какие данные может охватывать транзакция, когда она считается зафиксированной, какую изоляцию получает приложение и что делать при конфликте или повторной попытке. Затем перескажу инженеру своё понимание и напишу объяснение для нужной аудитории с конкретным примером и ограничениями.

#### Подробнее

На описанном собеседовании инженер объяснял модель распределённых транзакций, после чего кандидатка её документировала. Дословный вопрос и полное техническое объяснение не опубликованы. Документация CockroachDB описывает атомарные транзакции в распределённой системе и возможные ошибки, требующие повтора при конкурирующих операциях. Это свойства конкретного продукта, их нужно проверять перед публикацией инструкции.

**Interview evidence / Источник задания:** [First-hand Cockroach Labs interview account](https://www.cockroachlabs.com/blog/navigating-tech-writer/). **Technical reference / Справка:** [CockroachDB developer basics](https://www.cockroachlabs.com/docs/stable/developer-basics.html).

---

## 10. Learn and document online schema changes / Разберитесь в изменениях схемы работающей базы и опишите их

### 🇬🇧 English

#### Quick recall

**A schema change alters the structure of database objects, such as tables or indexes. An online schema change is designed to let the database keep serving work during supported changes.**

#### Interview answer

> I would ask which schema changes are supported online, how long they may take, what happens to reads and writes, and how to monitor or recover from a failure. I would document prerequisites, steps, observable states, compatibility considerations, and the limits for the specific DBMS version.

#### Details

The Cockroach Labs candidate reported a technical discussion about online schema changes followed by a writing task. The public account does not include the exact prompt. Avoid a blanket promise of zero downtime for every database or every operation: capabilities and restrictions vary by product and change type.

### 🇷🇺 Русский

#### Быстро вспомнить

**Изменение схемы меняет структуру объектов базы, например таблиц или индексов. Онлайн-изменение позволяет продолжать работу базы во время поддерживаемых операций.**

#### Ответ на собеседовании

> Я уточню, какие операции поддерживаются без остановки, сколько они могут длиться, что происходит с чтением и записью, как отслеживать выполнение и как действовать при ошибке. Затем опишу требования, шаги, наблюдаемые состояния и ограничения для конкретной версии СУБД.

#### Подробнее

Кандидатка в Cockroach Labs рассказала о техническом обсуждении изменений схемы работающей базы и последующем письменном задании. Точный текст задания не опубликован. Возможности зависят от продукта и операции, поэтому обещание работы без простоя нужно проверять для каждого случая.

**Interview evidence / Источник задания:** [First-hand Cockroach Labs interview account](https://www.cockroachlabs.com/blog/navigating-tech-writer/). **Technical reference / Справка:** [CockroachDB online schema changes](https://www.cockroachlabs.com/docs/stable/online-schema-changes).

---

## 11. Count rows by month and find the busiest month / Посчитайте строки по месяцам и найдите месяц с наибольшим числом строк

### 🇬🇧 English

#### Quick recall

**`COUNT(*)` counts rows, `GROUP BY month` produces one count per existing month, and a maximum may have ties.**

#### Interview answer

> I would count rows per month with `GROUP BY`, then look for the highest count. Before selecting just one month, I would ask what to do if several months tie. I would also clarify whether the report must include months with zero rows.

#### Details

```sql
SELECT month, COUNT(*) AS row_count
FROM t
GROUP BY month
ORDER BY row_count DESC, month;
```

This lists months present in `t`, with the largest counts first. `LIMIT 1` would return only one winner and hide ties. The original interviewer explicitly highlighted ambiguity in the question about the month with most rows. A technical writer should make the tie rule and zero-row-month rule explicit in a report's documentation.

### 🇷🇺 Русский

#### Быстро вспомнить

**`COUNT(*)` считает строки, `GROUP BY month` даёт итог по каждому представленному месяцу, а максимальный результат может встречаться несколько раз.**

#### Ответ на собеседовании

> Я сгруппирую строки по месяцу и посчитаю их число. Перед выбором одного месяца уточню, что делать при одинаковом максимуме. Ещё спрошу, должны ли в отчёте появиться месяцы, за которые нет строк.

#### Подробнее

Запрос выше показывает только месяцы, которые есть в таблице `t`, начиная с наиболее частых. `LIMIT 1` оставит одного победителя и скроет равенство результатов. Интервьюер отдельно указал на неоднозначность вопроса о месяце с максимальным числом строк. Техписателю стоит зафиксировать правила для ничьей и месяцев с нулём записей.

**Interview evidence / Источник вопросов:** [Oracle engineer's published interview questions](https://asktom.oracle.com/Misc/interview-question.html).

---

## 12. Solve JOIN tasks using the Oracle HR schema / Решите задачи с `JOIN` на схеме Oracle HR

### 🇬🇧 English

#### Quick recall

**Find the relationship between tables first, then choose the join that matches the required rows.**

#### Interview answer

> I would identify the requested output fields, find their source tables and connecting keys, decide whether unmatched rows should remain, and build the query one join at a time. Then I would check sample results for missing rows and unexpected duplicates.

#### Details

A candidate for a database engineer role reported solving several `JOIN` tasks on the Oracle HR sample schema. The exact tasks were not published, so this entry records the method rather than inventing their conditions. For a technical writer, that method also helps explain where each documented output field comes from.

### 🇷🇺 Русский

#### Быстро вспомнить

**Сначала найди связь таблиц, затем выбери тип соединения по тому, какие строки должны остаться в результате.**

#### Ответ на собеседовании

> Я определю нужные поля результата, найду таблицы и связывающие их ключи, решу, нужно ли сохранять строки без пары, и добавлю соединения по одному. Затем проверю результат на пропавшие строки и неожиданные дубликаты.

#### Подробнее

Кандидат на позицию инженера баз данных рассказал, что решал задачи с `JOIN` на учебной схеме Oracle HR. Точные условия не опубликованы, поэтому здесь описан подход, а не вымышленное задание. Техписателю такой подход помогает также объяснять происхождение полей в результате запроса.

**Interview evidence / Источник задания:** [Reported database engineer interview at Therap](https://tahanima.github.io/recruitment-stories-experience-of-riham-at-therap/).

---

## 13. Show each employee and their manager / Покажите каждого сотрудника и его руководителя

### 🇬🇧 English

#### Quick recall

**A self-join joins a table to itself using different aliases.**

#### Interview answer

> If employees and managers are stored in the same table, I would join `employees` to itself on `manager_id = id`. I would use a left join if the report must also include employees without a manager.

#### Details

This illustrative query assumes a table `employees(id, name, manager_id)`. The published interview report describes the employee-manager task but does not publish its exact schema.

```sql
SELECT e.name AS employee, m.name AS manager
FROM employees AS e
LEFT JOIN employees AS m ON e.manager_id = m.id;
```

The alias `e` means the employee row, and `m` means the manager row. A top-level employee appears with a `NULL` manager. If the report must exclude such employees, use an inner join instead.

### 🇷🇺 Русский

#### Быстро вспомнить

**Самосоединение связывает таблицу с ней самой через два разных псевдонима.**

#### Ответ на собеседовании

> Если сотрудники и руководители лежат в одной таблице, я соединю `employees` с ней самой по условию `manager_id = id`. Выберу `LEFT JOIN`, если отчёт должен включать и сотрудников без руководителя.

#### Подробнее

Пример выше использует условную таблицу `employees(id, name, manager_id)`. В опубликованном рассказе есть само задание, но точная схема таблицы не приведена. Псевдоним `e` обозначает сотрудника, `m` — руководителя. Сотрудник верхнего уровня получит `NULL` в поле руководителя. При `INNER JOIN` он исчезнет из результата.

**Interview evidence / Источник задания:** [First-hand report from a senior data analyst interview](https://www.reddit.com/r/SQL/comments/1lxzz8x/here_are_some_sql_questions_i_was_asked_for_a/).

---

## What this research suggests / Что показал поиск

### 🇬🇧 English

#### Quick recall

**For a general technical writer role, start with SQL basics and clear explanations. Database product roles may add hands-on documentation exercises.**

#### Interview answer

> I can explain relational data, keys, queries, joins, transactions, and indexes at a practical level. Given a database product, I can verify a command in a test environment and turn its behavior, prerequisites, results, and limitations into documentation.

#### Details

The strongest technical-writer-specific evidence here is the [first-hand Cockroach Labs interview account](https://www.cockroachlabs.com/blog/navigating-tech-writer/) and the company's [published technical writer exercises](https://github.com/cockroachlabs/open-sourced-interview-process/blob/master/DocumentationExercises.md). Other question sources describe SQL, analyst, or database engineer interviews. They show that these questions are real, not that every technical writer will receive them. Prepare questions 1-7 and exercises 8, 11, and 12 first; go deeper into exercises 9 and 10 for database-product roles.

### 🇷🇺 Русский

#### Быстро вспомнить

**Для обычной роли техписателя сначала нужны основы SQL и ясные объяснения. В компаниях, разрабатывающих СУБД, могут добавить практическое задание на документацию.**

#### Ответ на собеседовании

> Я могу на практическом уровне объяснить реляционные данные, ключи, запросы, соединения, транзакции и индексы. Работая с конкретной СУБД, я проверю команду в тестовой среде и опишу её поведение, требования, результат и ограничения.

#### Подробнее

Самое прямое свидетельство о собеседовании техписателя здесь — [рассказ кандидатки в Cockroach Labs](https://www.cockroachlabs.com/blog/navigating-tech-writer/) и [опубликованные компанией задания](https://github.com/cockroachlabs/open-sourced-interview-process/blob/master/DocumentationExercises.md). Остальные источники относятся к собеседованиям по SQL, аналитике или инженерии баз данных. Они подтверждают, что вопросы реальны, но не обещают их на каждом собеседовании техписателя. Сначала подготовь вопросы 1–7 и задания 8, 11, 12; к заданиям 9 и 10 углубляйся для вакансий в компаниях, разрабатывающих СУБД.
