# API for Technical Writer Interviews

A cheat sheet on core API topics for junior and middle technical writer interviews.

It covers the practical basics: API concepts, REST, SOAP, GraphQL, endpoints, HTTP methods, parameters, JSON, OpenAPI/Swagger, and API documentation workflows.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — short interview answer, details.
- 🇷🇺 **Русский** — короткий ответ на собеседовании, подробнее.

---

## 1. What is an API and why is it used? / Что такое API и зачем он нужен?

### 🇬🇧 English

#### Interview answer

> An API is a contract for interacting with software: available operations, required inputs, and expected outputs. Clients use it without knowing the implementation.

#### Details

An API can be thought of as a contract between software components. It
defines which operations are available, what data should be provided,
and what result can be expected.

For example, an application can call a music service API to retrieve
information about an artist or tracks. The client does not need to know
how the service stores or processes this information internally.

APIs are not limited to communication over the Internet. They can be
used between web services over HTTP, between microservices, or inside an
application through library interfaces.

### 🇷🇺 Русский

#### Ответ на собеседовании

> API — контракт взаимодействия с программой: доступные операции, входные данные и результаты. Клиенту не нужно знать внутреннюю реализацию.

#### Подробнее

API можно воспринимать как контракт между двумя программными
компонентами: он определяет, какие операции доступны, какие данные нужно
передать и какой результат можно получить.

Например, приложение может обратиться к API музыкального сервиса и
запросить информацию об исполнителе или треках. Клиенту не нужно знать,
как сервис хранит эти данные в базе или обрабатывает их внутри —
достаточно знать правила API.

API не обязательно работает через интернет. API может использоваться
между веб-сервисами по HTTP, между микросервисами или даже внутри
программы — например, когда код обращается к функциям библиотеки.

---

## 2. What types of APIs are there? / Какие виды API бывают?

### 🇬🇧 English

#### Interview answer

> APIs can expose local library functions or remote services. REST, SOAP, and GraphQL describe different approaches to designing or interacting with APIs.

#### Details

It is useful not to mix different classifications. Web API and Library
API describe where and how an interface is used, while REST, SOAP, and
GraphQL represent different approaches to system communication.

REST is an architectural style commonly used for HTTP APIs. SOAP is a
protocol with strict rules and XML messages. GraphQL is a query language
and API approach that lets clients specify exactly which data they need.

Another classification is by audience: public, partner, or internal APIs.
This is independent of the API's protocol or architectural style.

### 🇷🇺 Русский

#### Ответ на собеседовании

> API может предоставлять функции локальной библиотеки или удалённого сервиса. REST, SOAP и GraphQL — разные подходы к устройству API и работе с ним.

#### Подробнее

Важно не смешивать разные классификации. Web API и Library API
описывают, где и как используется интерфейс, а REST, SOAP и GraphQL —
разные способы организации взаимодействия между системами.

REST — архитектурный стиль, который часто используется для HTTP API.
SOAP — отдельный протокол со строгими правилами и XML-сообщениями.
GraphQL — язык запросов и подход к API, в котором клиент может точно
указать, какие данные ему нужны.

Другая классификация — по аудитории: публичные, партнёрские и внутренние
API. Она не зависит от протокола или архитектурного стиля.

---

## 3. What is a REST API and what does RESTful mean? / Что такое REST API и что значит RESTful?

### 🇬🇧 English

#### Interview answer

> REST is an architectural style built around resources and a uniform interface. Requests are stateless: each contains the context needed to process it.

#### Details

For example, a user can be represented as a resource:

```text
GET /users/123
```

This request may mean "retrieve the user with ID 123."

The request:

```text
DELETE /users/123
```

targets the same resource but performs a different operation because it
uses a different HTTP method.

REST is not a program or a separate network protocol. It is an
architectural style with a set of principles. In real-world web APIs,
REST commonly works over HTTP and frequently uses JSON for data
exchange.

REST's constraints are client-server separation, stateless requests,
cacheability, a uniform interface, a layered system, and optional
code-on-demand. The uniform interface includes resource identification,
representations, self-describing messages, and hypermedia controls.

**Stateless** does not prohibit storing resources in a database: it means
the server does not need a remembered client session to interpret a request.
**RESTful** means following these constraints, not merely using HTTP and JSON.

### 🇷🇺 Русский

#### Ответ на собеседовании

> REST — архитектурный стиль, основанный на ресурсах и едином интерфейсе. Запросы независимы: каждый содержит контекст, необходимый для его обработки.

#### Подробнее

Например, ресурсом может быть пользователь:

```text
GET /users/123
```

Такой запрос может означать «получить пользователя с ID 123».

А запрос:

```text
DELETE /users/123
```

обращается к тому же ресурсу, но выполняет другое действие благодаря
другому HTTP-методу.

REST — не отдельная программа и не специальный сетевой протокол. Это
архитектурный стиль с набором принципов. В реальных веб-API REST обычно
работает поверх HTTP, а данные очень часто передаются в JSON.

Ограничения REST: разделение клиента и сервера, независимые запросы,
кешируемость, единый интерфейс, многоуровневость и необязательный
code-on-demand. Единый интерфейс включает идентификацию ресурсов,
представления, самодостаточные сообщения и гипермедийные переходы.

**Stateless** не запрещает хранить ресурсы в БД: для понимания запроса
серверу не должна требоваться сохранённая клиентская сессия.
**RESTful** означает соблюдение ограничений, а не просто HTTP и JSON.

---

## 4. How is REST different from SOAP? / Чем REST отличается от SOAP?

### 🇬🇧 English

#### Interview answer

> REST is an architectural style; SOAP is an XML-based messaging protocol. REST does not require JSON, and neither approach is inherently more secure.

#### Details

The first important difference is the definition itself: REST is an
architectural style, while SOAP is a complete protocol.

REST does not require a particular data format, although JSON is very
common in practice. SOAP messages use a strictly defined XML structure.

SOAP defines an envelope and processing rules and can use different
underlying transports, not just HTTP. Extensions such as WS-Security
add message-level security; they are not automatically enabled by SOAP.
Complexity, performance, and security depend on the actual contract,
implementation, and configuration, not the label alone.

### 🇷🇺 Русский

#### Ответ на собеседовании

> REST — архитектурный стиль, SOAP — протокол обмена XML-сообщениями. REST не требует JSON, и ни один подход не безопаснее сам по себе.

#### Подробнее

Главное различие начинается уже с определения: REST — архитектурный
стиль, а SOAP — полноценный протокол.

REST не требует конкретного формата данных, хотя на практике очень часто
используется JSON. SOAP-сообщения имеют строго определенную
XML-структуру.

SOAP задаёт структуру конверта и правила обработки и может работать
поверх разных транспортов, не только HTTP. Расширения вроде WS-Security
добавляют защиту сообщений, но не включаются автоматически самим SOAP.
Сложность, производительность и безопасность зависят от контракта,
реализации и настроек, а не только от названия подхода.

---

## 5. What is GraphQL and why is it used? / Что такое GraphQL и зачем он нужен?

### 🇬🇧 English

#### Interview answer

> GraphQL is a query language and execution model for APIs. Clients request fields allowed by the schema and their permissions.

#### Details

Imagine that a UI only needs a user's name and the names of their latest
orders. With REST, the client may sometimes need to call several
resources or receive an object containing more fields than necessary.

With GraphQL, the client can explicitly request only the required
fields. This helps reduce **over-fetching**, when the server returns
unnecessary data, and in some cases **under-fetching**, when one
response does not contain enough data and additional requests are
required.

Saying that "the client chooses the response format" is slightly
inaccurate. A better formulation is that **the client specifies the
fields and structure it wants to query**.

The server defines the schema and enforces authorization. Selecting fewer
fields does not guarantee fewer database queries or better performance.
GraphQL is not a universal replacement for REST. It is another approach
that can be especially useful when clients have complex and different
data requirements.

### 🇷🇺 Русский

#### Ответ на собеседовании

> GraphQL — язык запросов и модель их выполнения для API. Клиент запрашивает поля, доступные в схеме и разрешённые его правами.

#### Подробнее

Представим, что интерфейсу нужны только имя пользователя и названия его
последних заказов. В REST для этого иногда приходится обращаться к
нескольким ресурсам или получать объект, содержащий больше полей, чем
нужно.

В GraphQL клиент может явно запросить только необходимые поля. Это
помогает бороться с **over-fetching**, когда сервер возвращает лишние
данные, и в некоторых сценариях с **under-fetching**, когда одного
ответа недостаточно и приходится делать дополнительные запросы.

Фраза «клиент выбирает формат ответа» не совсем точна. Лучше говорить:
**клиент определяет набор и структуру запрашиваемых полей**.

Схему задаёт сервер, он же проверяет права. Меньше полей в запросе не
гарантирует меньше запросов к БД или лучшую производительность.
GraphQL не является универсальной заменой REST. Это другой подход,
который особенно удобен, когда клиенты имеют сложные и различающиеся
требования к данным.

---

## 6. What is an endpoint? / Что такое endpoint?

### 🇬🇧 English

#### Interview answer

> In an HTTP API, an endpoint is an address used to access a resource or operation. The HTTP method specifies the action at that address.

#### Details

In everyday conversation, an endpoint is often described simply as an
API URL. This is a useful simplification, but the operation is not
defined by the address alone.

For example:

```text
GET /users/123
DELETE /users/123
```

The URI is the same, but the operations are different. The first request
may retrieve the user, while the second may delete that user.

That is why API documentation normally describes an endpoint together
with its HTTP method, parameters, request body, responses, and possible
errors.

### 🇷🇺 Русский

#### Ответ на собеседовании

> В HTTP API endpoint — адрес обращения к ресурсу или операции. HTTP-метод уточняет действие по этому адресу.

#### Подробнее

В разговорной речи endpoint часто называют просто URL API. Для базового
собеседования это допустимое упрощение, но важно понимать, что действие
определяется не только адресом.

Например:

```text
GET /users/123
DELETE /users/123
```

URI одинаковый, но операции разные. Первый запрос может получить
пользователя, второй — удалить его.

Поэтому при документировании API endpoint обычно рассматривают вместе с
HTTP-методом, параметрами, телом запроса, ответами и возможными
ошибками.

---

## 7. Endpoint vs HTTP method / Чем endpoint отличается от HTTP-метода?

### 🇬🇧 English

#### Interview answer

> The endpoint identifies where to send a request; the method specifies the action. GET /users/123 and DELETE /users/123 address the same resource but perform different operations.

#### Details

Common HTTP methods include:

| Method | Typical purpose |
| --- | --- |
| `GET` | Retrieve a representation |
| `POST` | Submit data for processing, possibly creating a resource |
| `PUT` | Create or replace the state at the target URI |
| `PATCH` | Apply partial modifications |
| `DELETE` | Request removal of the target resource |

The API contract defines inputs and outcomes while respecting HTTP
semantics. DELETE does not promise physical erasure of every stored copy.

For a technical writer, the **method + path** combination is one of the
core units of API reference documentation.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Endpoint указывает, куда отправить запрос, метод — какое действие выполнить. GET /users/123 и DELETE /users/123 обращаются к одному ресурсу, но выполняют разные операции.

#### Подробнее

Основные HTTP-методы:

| Метод | Типичное назначение |
| --- | --- |
| `GET` | Получить представление ресурса |
| `POST` | Передать данные на обработку, в том числе для создания ресурса |
| `PUT` | Создать или заменить состояние по заданному URI |
| `PATCH` | Применить частичные изменения |
| `DELETE` | Запросить удаление ресурса |

Контракт API уточняет входы и результаты с соблюдением семантики HTTP.
DELETE не обещает физического стирания всех сохранённых копий данных.

Для техрайтера связка **method + path** — одна из основных единиц
справочной документации API.

---

## 8. What are API parameters? / Что такое параметры API и какие они бывают?

### 🇬🇧 English

#### Interview answer

> Parameters supply values in the path, query, headers, or cookies. The request body carries a separate payload, such as data for a new user.

#### Details

##### Path parameters

They are part of the path and commonly identify a specific resource:

```text
GET /users/123
```

Here, `123` is the value of a `user_id` path parameter.

##### Query parameters

They appear after `?` and are often used for filtering, searching,
sorting, or pagination:

```text
GET /users?status=active&page=2
```

Here, `status` and `page` are query parameters.

##### Headers

Headers contain request metadata. For example:

```text
Authorization: Bearer <token>
Content-Type: application/json
```

##### Request body

The body contains the main request data, for example when creating a
user:

```json
{
  "name": "Igor",
  "email": "igor@example.com"
}
```

OpenAPI 3 also supports cookie parameters. Its Parameter Object describes
path, query, header, or cookie parameters; `requestBody` describes the body
separately. Authentication is normally declared through security schemes,
not an ordinary `Authorization` header parameter.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Параметры передают значения в пути, строке запроса, заголовках или cookies. Тело запроса — отдельная полезная нагрузка, например данные нового пользователя.

#### Подробнее

##### Path parameters

Являются частью пути и обычно идентифицируют конкретный ресурс:

```text
GET /users/123
```

Здесь `123` — значение path-параметра `user_id`.

##### Query parameters

Передаются после `?` и часто используются для фильтрации, поиска,
сортировки или пагинации:

```text
GET /users?status=active&page=2
```

Здесь `status` и `page` — query parameters.

##### Headers

Передают метаданные запроса. Например:

```text
Authorization: Bearer <token>
Content-Type: application/json
```

##### Request body

Содержит основные данные запроса, например при создании пользователя:

```json
{
  "name": "Igor",
  "email": "igor@example.com"
}
```

OpenAPI 3 также поддерживает параметры cookie. Parameter Object описывает
параметры path, query, header или cookie; `requestBody` отдельно описывает
тело. Аутентификацию обычно задают через security schemes, а не обычный
параметр заголовка `Authorization`.

---

## 9. What is JSON and why is it common in APIs? / Что такое JSON и почему его часто используют в API?

### 🇬🇧 English

#### Interview answer

> JSON is a language-independent text format for structured data. APIs commonly use it because many tools and languages can parse it.

#### Details

JSON stands for **JavaScript Object Notation**, but it is now used
independently of JavaScript.

For example:

```json
{
  "id": 123,
  "name": "Igor",
  "active": true,
  "skills": ["Git", "REST", "Markdown"]
}
```

JSON supports objects, arrays, strings, numbers, Boolean values, and
`null`.

A JSON object looks similar to a Python dictionary, which is a useful
analogy. However, JSON is an independent text format, while a Python
`dict` is a data structure in a particular programming language.

JSON is common in REST APIs because it is relatively compact, easy to
understand, and well supported across languages and tools.

### 🇷🇺 Русский

#### Ответ на собеседовании

> JSON — независимый от языка текстовый формат структурированных данных. Его часто используют в API благодаря широкой поддержке инструментами и языками.

#### Подробнее

JSON расшифровывается как **JavaScript Object Notation**, но давно
используется независимо от JavaScript.

Пример:

```json
{
  "id": 123,
  "name": "Igor",
  "active": true,
  "skills": ["Git", "REST", "Markdown"]
}
```

JSON поддерживает объекты, массивы, строки, числа, логические значения и
`null`.

По структуре JSON-объект действительно напоминает Python dictionary,
поэтому такая аналогия помогает запомнить принцип. Но JSON —
самостоятельный текстовый формат, а Python `dict` — структура данных
конкретного языка программирования.

JSON часто используют в REST API, потому что он относительно компактный,
понятный и имеет хорошую поддержку в разных языках и инструментах.

---

## 10. What are OpenAPI and Swagger? / Что такое OpenAPI и Swagger?

### 🇬🇧 English

#### Interview answer

> OpenAPI is a standard for describing HTTP APIs in a machine-readable form. Swagger is a family of tools for working with those descriptions.

#### Details

An OpenAPI description is commonly written in YAML or JSON. It can
describe available operations, parameters, request and response schemas,
status codes, and authentication methods.

A minimal OpenAPI 3.1 example (not a claim about the latest version).
The parameter needs a schema; `openapi`, `info`, and `paths` make this a
complete document. Response schemas would be added for an actual API:

``` yaml
openapi: 3.1.0
info:
  title: Example Users API
  version: 1.0.0
paths:
  /users/{userId}:
    get:
      parameters:
        - name: userId
          in: path
          required: true
          schema:
            type: integer
      responses:
        "200":
          description: User found
        "404":
          description: User not found
```

Swagger is not simply "a program." The name is used for several tools.
For example, **Swagger UI** renders an OpenAPI description as an
interactive web page where developers can inspect API operations and,
when enabled, send test requests.

For an interview, remember:

```text
OpenAPI = specification
Swagger = tools around OpenAPI
```

### 🇷🇺 Русский

#### Ответ на собеседовании

> OpenAPI — стандарт машиночитаемого описания HTTP API. Swagger — семейство инструментов для работы с такими описаниями.

#### Подробнее

OpenAPI-описание обычно хранится в YAML или JSON. Оно может содержать
информацию о доступных операциях, параметрах, схемах запросов и ответов,
статус-кодах и способах авторизации.

Минимальный пример OpenAPI 3.1 (это не утверждение о последней версии).
Параметру нужна схема; `openapi`, `info` и `paths` составляют полный
документ. Для реального API следует добавить схемы ответов:

``` yaml
openapi: 3.1.0
info:
  title: Example Users API
  version: 1.0.0
paths:
  /users/{userId}:
    get:
      parameters:
        - name: userId
          in: path
          required: true
          schema:
            type: integer
      responses:
        "200":
          description: User found
        "404":
          description: User not found
```

Swagger — не просто «программа». Под этим названием существует
несколько инструментов. Например, **Swagger UI** превращает
OpenAPI-описание в интерактивную веб-страницу, где можно посмотреть
операции API и, если это разрешено, отправить тестовые запросы.

Для собеседования особенно важно не путать:

```text
OpenAPI = specification
Swagger = tools around OpenAPI
```

---

## 11. How does a technical writer document an API? / Как технический писатель документирует API?

### 🇬🇧 English

#### Interview answer

> I would document authentication, a working first request, operations, inputs, outputs, and errors. Then I would test examples against the intended API version.

#### Details

API documentation can be organized into several layers.

##### Overview

It explains:

-   what the API does;
-   who it is for;
-   its main capabilities;
-   the base URL;
-   important requirements or limitations.

##### Getting Started

It should help a developer make a successful request as quickly as
possible:

1.  obtain credentials or a token;
2.  configure authentication;
3.  send a simple request;
4.  receive the expected response.

##### API Reference

For each operation, documentation commonly includes:

-   HTTP method;
-   path / endpoint;
-   operation purpose;
-   path and query parameters;
-   required headers;
-   request body and schema;
-   request example;
-   successful response;
-   response schema;
-   status codes;
-   possible errors.

##### Guides / Use Cases

Reference documentation answers "what does this operation do?", while
guides explain **how to solve a real task using one or more API
operations**.

For example:

-   create a customer;
-   create an order;
-   check its status;
-   handle an error.

For a technical writer, the job is not only to turn an OpenAPI file into
readable text. It is also important to validate the documentation from
the user's perspective: can a developer actually follow it, send a
request, and get the expected result?

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я опишу аутентификацию, первый рабочий запрос, операции, входы, результаты и ошибки. Затем проверю примеры на нужной версии API.

#### Подробнее

Хорошую API-документацию удобно разделять на несколько уровней.

##### Overview

Объясняет:

-   что делает API;
-   для кого оно предназначено;
-   какие основные возможности предоставляет;
-   где находится base URL;
-   какие есть ограничения или требования.

##### Getting Started

Помогает разработчику как можно быстрее сделать первый успешный запрос:

1.  получить credentials или token;
2.  настроить авторизацию;
3.  отправить простой запрос;
4.  увидеть ожидаемый ответ.

##### API Reference

Для каждой операции обычно описывают:

-   HTTP method;
-   path / endpoint;
-   назначение операции;
-   path и query parameters;
-   необходимые headers;
-   request body и его schema;
-   пример запроса;
-   успешный response;
-   response schema;
-   status codes;
-   возможные ошибки.

##### Guides / Use Cases

Reference отвечает на вопрос «что делает конкретная операция», а guides
показывают, **как решить реальную задачу с помощью нескольких операций
API**.

Например:

-   создать клиента;
-   создать заказ;
-   проверить его статус;
-   обработать ошибку.

Для техрайтера важно не только переписать OpenAPI-файл человеческим
языком, но и проверить документацию как пользователь: можно ли по ней
действительно выполнить запрос и получить ожидаемый результат.

---

## 12. Who is the audience for API documentation? / Кто является аудиторией API-документации?

### 🇬🇧 English

#### Interview answer

> Usually, API docs serve developers integrating a service. I would identify their task and prior knowledge before choosing the depth of explanation.

#### Details

Audience affects documentation structure.

A developer using the product for the first time needs a clear
getting-started guide, authentication instructions, and a working
example.

An experienced developer who already uses the API may primarily need
accurate reference information: parameters, data types, schemas, status
codes, and edge cases.

For an internal API, users may already understand the product
architecture. Public API documentation cannot rely on the same internal
context.

So identifying the audience is not just a formal documentation step. It
determines what needs explanation and what can reasonably be assumed.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Обычно API-документация нужна разработчикам для интеграции сервиса. Сначала я уточню их задачу и знания, затем выберу глубину объяснения.

#### Подробнее

Определение аудитории влияет на структуру документации.

Разработчику, который впервые использует продукт, нужен понятный getting
started, объяснение авторизации и рабочий пример.

Опытному разработчику, который уже интегрировал API, важнее точный
reference: параметры, типы данных, schemas, status codes и edge cases.

Если API внутреннее, аудитория может хорошо знать архитектуру продукта.
Для публичного API нельзя рассчитывать на внутренний контекст.

Поэтому «для кого документация?» — не формальный вопрос. От ответа
зависит, что нужно объяснять подробно, а что можно считать известным.

---

## 13. How do you know if an API is well documented? / Как понять, что API задокументирован хорошо?

### 🇬🇧 English

#### Interview answer

> Good API docs let the target reader complete a real task. The reference is accurate, examples work, and errors and limitations are clear.

#### Details

API documentation quality should not be measured by the amount of text
or whether everything fits on one or two screens.

More useful questions are:

-   Is the API purpose clear?
-   Is the getting-started guide easy to find?
-   Can the user obtain credentials and understand authentication?
-   Can they copy an example and make a successful first request?
-   Are required and optional parameters documented?
-   Are request and response schemas clear?
-   Are important status codes and errors explained?
-   Are real use cases included?
-   Does the documentation match actual API behavior?
-   Can users quickly find the information they need?

A useful practical criterion is: **can a member of the target audience
complete their task using the documentation without asking the writer or
developers for basic explanations?**

### 🇷🇺 Русский

#### Ответ на собеседовании

> Хорошая API-документация позволяет читателю решить реальную задачу: справочник точен, примеры работают, ошибки и ограничения объяснены.

#### Подробнее

Качество API-документации нельзя измерить количеством текста или тем,
помещается ли она на один-два экрана.

Полезнее проверить несколько вещей:

-   понятно ли назначение API;
-   легко ли найти getting started;
-   можно ли получить credentials и разобраться с authentication;
-   можно ли скопировать пример и сделать первый запрос;
-   описаны ли обязательные и необязательные параметры;
-   понятны ли request и response schemas;
-   перечислены ли основные status codes и ошибки;
-   есть ли реальные use cases;
-   совпадает ли документация с фактическим поведением API;
-   легко ли найти нужную информацию.

Хороший практический критерий: **может ли представитель целевой
аудитории выполнить задачу по документации без обращения к автору или
разработчикам за базовыми пояснениями?**

---

## Core model / Главная схема

### 🇬🇧 English

```text
Client
  ↓
HTTP request
  ├─ Method: GET / POST / PATCH / DELETE
  ├─ Path: /users/123
  ├─ Query parameters: ?status=active
  ├─ Headers: Authorization, Content-Type
  └─ Optional body: for example, JSON
  ↓
API
  ↓
HTTP response
  ├─ Status code: 200 / 400 / 404 / 500
  ├─ Headers
  └─ Optional body: for example, JSON
```

Example:

```http
GET /users/123?details=true HTTP/1.1
Host: api.example.com
Authorization: Bearer <token>
```

Here:

```text
GET                  → HTTP method
/users/123           → path / endpoint
123                  → path parameter
details=true         → query parameter
Authorization        → request header
Bearer <token>       → header value
```

### 🇷🇺 Русский

```text
Клиент
  ↓
HTTP request
  ├─ Method: GET / POST / PATCH / DELETE
  ├─ Path: /users/123
  ├─ Query parameters: ?status=active
  ├─ Headers: Authorization, Content-Type
  └─ Необязательное тело: например JSON
  ↓
API
  ↓
HTTP response
  ├─ Status code: 200 / 400 / 404 / 500
  ├─ Headers
  └─ Необязательное тело: например JSON
```

Пример:

```http
GET /users/123?details=true HTTP/1.1
Host: api.example.com
Authorization: Bearer <token>
```

Здесь:

```text
GET                  → HTTP method
/users/123           → path / endpoint
123                  → path parameter
details=true         → query parameter
Authorization        → request header
Bearer <token>       → значение header
```

## References / Источники

Technical review: 2026-11-03. / Техническая проверка: 2026-11-03.

- [REST constraints: Fielding, chapter 5](https://ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm), [SOAP 1.2](https://www.w3.org/TR/soap12-part1/), [GraphQL specification](https://spec.graphql.org/October2021/).
- [HTTP semantics](https://www.rfc-editor.org/rfc/rfc9110.html), [JSON specification](https://www.rfc-editor.org/rfc/rfc8259.html).
- [OpenAPI 3.1.1 specification](https://spec.openapis.org/oas/v3.1.1.html), [Swagger tools](https://swagger.io/tools/).
