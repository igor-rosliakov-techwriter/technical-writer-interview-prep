# API for Technical Writer Interviews

A cheat sheet on core API topics for junior and middle technical writer interviews.

It covers the practical basics: API concepts, REST, SOAP, GraphQL, endpoints, HTTP methods, parameters, JSON, OpenAPI/Swagger, and API documentation workflows.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — quick recall, interview answer, details.
- 🇷🇺 **Русский** — быстро вспомнить, ответ на собеседовании, подробнее.

---

## 1. What is an API and why is it used? / Что такое API и зачем он нужен?

### 🇬🇧 English

#### Quick recall

**An API is a programming interface that defines rules for communication
between software components. It allows one system to access data or
functionality from another without knowing its internal
implementation.**

#### Interview answer

> API stands for Application Programming Interface. It is a set of rules
> and mechanisms that allows software systems to interact with each
> other. A client can request data or perform an operation without
> knowing how the other system is implemented internally.

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

#### Быстро вспомнить

**API — это программный интерфейс, который определяет правила
взаимодействия между программами. Он позволяет одной системе получать
данные или вызывать функции другой системы, не зная, как она устроена
внутри.**

#### Ответ на собеседовании

> API, или Application Programming Interface, — это набор правил и
> способов взаимодействия между программами. Одна программа может
> отправить запрос другой системе, получить данные или выполнить
> определенное действие, при этом ей не нужно знать внутреннюю
> реализацию этой системы.

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

#### Quick recall

**APIs can be classified in different ways. For example, Web APIs are
used for network communication and Library APIs expose functionality
inside code; common approaches to web APIs include REST, SOAP, and
GraphQL.**

#### Interview answer

> There are different types of APIs. Web APIs are used for communication
> between applications over a network, usually via HTTP, while Library
> APIs expose functions and classes directly to code. Common approaches
> to web APIs include REST, SOAP, and GraphQL.

#### Details

It is useful not to mix different classifications. Web API and Library
API describe where and how an interface is used, while REST, SOAP, and
GraphQL represent different approaches to system communication.

REST is an architectural style commonly used for HTTP APIs. SOAP is a
protocol with strict rules and XML messages. GraphQL is a query language
and API approach that lets clients specify exactly which data they need.

For a junior or middle interview, a high-level understanding of these
differences and a stronger understanding of REST is usually enough.

### 🇷🇺 Русский

#### Быстро вспомнить

**API можно классифицировать по-разному. Например, бывают Web API для
взаимодействия по сети и Library API для работы с библиотеками в коде;
среди распространенных подходов к веб-API — REST, SOAP и GraphQL.**

#### Ответ на собеседовании

> API бывают разных типов. Например, Web API используются для
> взаимодействия приложений по сети, обычно через HTTP, а Library API
> предоставляют функции и классы для использования непосредственно в
> коде. Среди распространенных подходов к созданию веб-API я знаю REST,
> SOAP и GraphQL.

#### Подробнее

Важно не смешивать разные классификации. Web API и Library API
описывают, где и как используется интерфейс, а REST, SOAP и GraphQL —
разные способы организации взаимодействия между системами.

REST — архитектурный стиль, который часто используется для HTTP API.
SOAP — отдельный протокол со строгими правилами и XML-сообщениями.
GraphQL — язык запросов и подход к API, в котором клиент может точно
указать, какие данные ему нужны.

На junior/middle собеседовании обычно достаточно понимать эти различия
на верхнем уровне и уметь подробнее объяснить REST.

---

## 3. What is a REST API and what does RESTful mean? / Что такое REST API и что значит RESTful?

### 🇬🇧 English

#### Quick recall

**REST is an architectural style for designing APIs. In REST, data is
represented as resources identified by URIs, and operations are usually
expressed through standard HTTP methods such as GET, POST, PUT, PATCH,
and DELETE.**

#### Interview answer

> A REST API is an API designed according to REST principles. Clients
> usually work with resources through URIs and use standard HTTP
> methods: for example, GET to retrieve data, POST to create it, PUT or
> PATCH to update it, and DELETE to remove it.

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

The term **RESTful** generally means that an API follows REST principles
rather than merely using HTTP.

### 🇷🇺 Русский

#### Быстро вспомнить

**REST — это архитектурный стиль для построения API. В REST данные
представлены как ресурсы, к которым обращаются по URI, а действия обычно
выражаются стандартными HTTP-методами — GET, POST, PUT, PATCH,
DELETE.**

#### Ответ на собеседовании

> REST API — это API, построенный по принципам архитектурного стиля
> REST. Обычно клиент работает с ресурсами через URI и использует
> стандартные HTTP-методы: например, GET для получения данных, POST для
> создания, PATCH или PUT для обновления и DELETE для удаления.

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

Слово **RESTful** обычно означает, что API следует принципам REST, а не
просто использует HTTP.

---

## 4. How is REST different from SOAP? / Чем REST отличается от SOAP?

### 🇬🇧 English

#### Quick recall

**REST is an architectural style that is usually simpler and more
flexible, while SOAP is a strict messaging protocol based on XML. SOAP
is often found in enterprise systems that require formal contracts and
additional standards.**

#### Interview answer

> REST is an architectural style, while SOAP is a protocol. REST APIs
> are usually lightweight and commonly use HTTP and JSON. SOAP uses XML
> and follows stricter rules and standards, so it can be found in
> enterprise systems where formal contracts, security standards, or
> reliable messaging are important.

#### Details

The first important difference is the definition itself: REST is an
architectural style, while SOAP is a complete protocol.

REST does not require a particular data format, although JSON is very
common in practice. SOAP messages use a strictly defined XML structure.

SOAP is also associated with additional standards such as WS-Security.
This is one reason it has historically been used in large enterprise,
financial, and integration systems.

This does not mean that REST is insecure or that SOAP is always better
for security. REST APIs can also be strongly secured. For an interview,
the important point is that SOAP provides a more formal standards-based
ecosystem, while REST is usually simpler and lighter for modern web
APIs.

### 🇷🇺 Русский

#### Быстро вспомнить

**REST — архитектурный стиль, обычно более простой и гибкий; SOAP —
строгий протокол обмена сообщениями, который использует XML. SOAP часто
встречается в корпоративных системах, где важны формальные контракты и
дополнительные стандарты.**

#### Ответ на собеседовании

> REST — это архитектурный стиль, а SOAP — протокол. REST API обычно
> легче и проще, часто используют HTTP и JSON. SOAP использует XML и
> имеет более строгие правила и стандарты, поэтому его можно встретить в
> enterprise-системах, где важны формальные контракты, безопасность или
> надежная обработка сообщений.

#### Подробнее

Главное различие начинается уже с определения: REST — архитектурный
стиль, а SOAP — полноценный протокол.

REST не требует конкретного формата данных, хотя на практике очень часто
используется JSON. SOAP-сообщения имеют строго определенную
XML-структуру.

SOAP также связан с набором дополнительных стандартов, например
WS-Security. Поэтому его исторически часто использовали в крупных
корпоративных, финансовых и интеграционных системах.

Это не означает, что REST «небезопасный», а SOAP всегда «лучше для
безопасности». REST API тоже могут быть хорошо защищены. На
собеседовании важнее показать понимание того, что SOAP предлагает более
формализованную экосистему стандартов, а REST обычно проще и легче для
большинства современных веб-API.

---

## 5. What is GraphQL and why is it used? / Что такое GraphQL и зачем он нужен?

### 🇬🇧 English

#### Quick recall

**GraphQL lets the client specify exactly which data fields it needs.
Requests are typically sent to a single endpoint, and the response
structure follows the requested fields.**

#### Interview answer

> GraphQL is a query language and an approach to building APIs where the
> client specifies exactly which data it needs. Unlike a typical REST
> API with multiple resource endpoints, GraphQL commonly uses a single
> endpoint and can retrieve related data in one request.

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

GraphQL is not a universal replacement for REST. It is another approach
that can be especially useful when clients have complex and different
data requirements.

### 🇷🇺 Русский

#### Быстро вспомнить

**GraphQL позволяет клиенту самому указать, какие именно поля данных ему
нужны. Обычно запросы отправляются на один endpoint, а структура ответа
соответствует запрошенным данным.**

#### Ответ на собеседовании

> GraphQL — это язык запросов и подход к созданию API, в котором
> клиент сам определяет, какие данные ему нужны. В отличие от типичного
> REST API с множеством ресурсов и endpoints, GraphQL обычно использует
> один endpoint и позволяет получить связанные данные одним запросом.

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

GraphQL не является универсальной заменой REST. Это другой подход,
который особенно удобен, когда клиенты имеют сложные и различающиеся
требования к данным.

---

## 6. What is an endpoint? / Что такое endpoint?

### 🇬🇧 English

#### Quick recall

**An endpoint is a specific access point in an API where a client sends
a request. In a web API, it is usually identified by a URI and used
together with an HTTP method.**

#### Interview answer

> An endpoint is an API access point used to work with a particular
> resource or operation. For example, `/users/123` can identify a
> particular user, while the HTTP method defines what operation we want
> to perform on that resource.

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

#### Быстро вспомнить

**Endpoint — это конкретная точка доступа к API, к которой клиент
отправляет запрос. В веб-API она обычно определяется URI и используется
вместе с HTTP-методом.**

#### Ответ на собеседовании

> Endpoint — это точка API, через которую клиент обращается к
> определенному ресурсу или операции. Например, `/users/123` может быть
> endpoint для работы с конкретным пользователем, а HTTP-метод
> определяет, что именно мы хотим сделать с этим ресурсом.

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

#### Quick recall

**An endpoint answers "where should the request go?", while the HTTP
method answers "what should be done?". The same resource can support
several methods.**

#### Interview answer

> An endpoint identifies the API resource or access point, while the
> HTTP method defines the operation. For example, `GET /users/123` may
> retrieve a user, while `DELETE /users/123` may delete the same user.

#### Details

Common HTTP methods include:

  Method     Typical purpose
  ———- ——————————————-
  `GET`      Retrieve data
  `POST`     Create a resource or trigger an operation
  `PUT`      Replace or update a resource
  `PATCH`    Partially update a resource
  `DELETE`   Delete a resource

These are typical HTTP semantics; the exact behavior is defined by the
API.

For a technical writer, the **method + path** combination is one of the
core units of API reference documentation.

### 🇷🇺 Русский

#### Быстро вспомнить

**Endpoint отвечает на вопрос «куда отправить запрос», а HTTP-метод —
«что сделать». Один и тот же ресурс может поддерживать несколько
методов.**

#### Ответ на собеседовании

> Endpoint указывает, к какому ресурсу или точке API мы обращаемся, а
> HTTP-метод определяет операцию. Например, `GET /users/123` может
> получить пользователя, а `DELETE /users/123` — удалить того же
> пользователя.

#### Подробнее

Основные HTTP-методы:

  Метод      Типичное назначение
  ———- —————————————-
  `GET`      Получить данные
  `POST`     Создать ресурс или запустить операцию
  `PUT`      Полностью заменить или обновить ресурс
  `PATCH`    Частично обновить ресурс
  `DELETE`   Удалить ресурс

Важно понимать, что это типичные семантики методов, а конкретное
поведение определяет API.

Для техрайтера связка **method + path** — одна из основных единиц
справочной документации API.

---

## 8. What are API parameters? / Что такое параметры API и какие они бывают?

### 🇬🇧 English

#### Quick recall

**Parameters provide additional values for a request, such as a resource
ID, filter, sorting option, or page number. Common types are path and
query parameters; requests can also contain headers and a request
body.**

#### Interview answer

> Parameters provide values that refine an API request. For example, a
> user ID can be a path parameter in `/users/123`, while filtering or
> pagination can use query parameters such as
> `/users?status=active&page=2`. Requests can also contain headers and a
> body.

#### Details

### Path parameters

They are part of the path and commonly identify a specific resource:

```text
GET /users/123
```

Here, `123` is the value of a `user_id` path parameter.

### Query parameters

They appear after `?` and are often used for filtering, searching,
sorting, or pagination:

```text
GET /users?status=active&page=2
```

Here, `status` and `page` are query parameters.

### Headers

Headers contain request metadata. For example:

```text
Authorization: Bearer <token>
Content-Type: application/json
```

### Request body

The body contains the main request data, for example when creating a
user:

```json
{
  "name": "Igor",
  "email": "igor@example.com"
}
```

Strictly speaking, headers and the request body are not always described
as "parameters." It is better to understand **path/query parameters,
headers, and the request body** as separate parts of an HTTP request.

### 🇷🇺 Русский

#### Быстро вспомнить

**Параметры передают запросу дополнительные значения: например, ID
ресурса, фильтр, сортировку или номер страницы. Чаще всего различают
path parameters и query parameters; данные также могут передаваться в
headers и request body.**

#### Ответ на собеседовании

> Параметры уточняют запрос и передают API необходимые значения.
> Например, ID пользователя может быть path-параметром `/users/123`, а
> фильтр или пагинация — query-параметром
> `/users?status=active&page=2`. Кроме этого, запрос может содержать
> headers и body.

#### Подробнее

### Path parameters

Являются частью пути и обычно идентифицируют конкретный ресурс:

```text
GET /users/123
```

Здесь `123` — значение path-параметра `user_id`.

### Query parameters

Передаются после `?` и часто используются для фильтрации, поиска,
сортировки или пагинации:

```text
GET /users?status=active&page=2
```

Здесь `status` и `page` — query parameters.

### Headers

Передают метаданные запроса. Например:

```text
Authorization: Bearer <token>
Content-Type: application/json
```

### Request body

Содержит основные данные запроса, например при создании пользователя:

```json
{
  "name": "Igor",
  "email": "igor@example.com"
}
```

Строго говоря, headers и body не всегда называют «параметрами» в
документации. Лучше уметь различать **path/query parameters, headers и
request body** как отдельные части HTTP-запроса.

---

## 9. What is JSON and why is it common in APIs? / Что такое JSON и почему его часто используют в API?

### 🇬🇧 English

#### Quick recall

**JSON is a lightweight text format for structured data exchange. It is
human-readable, easy for software to process, and supported by almost
every popular programming language.**

#### Interview answer

> JSON is a text format for representing structured data and is widely
> used in web APIs. It is relatively compact, human-readable, easy to
> parse, and supported by most programming languages.

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

#### Быстро вспомнить

**JSON — легковесный текстовый формат обмена структурированными
данными. Он читаем человеком, легко обрабатывается программами и
поддерживается практически всеми популярными языками программирования.**

#### Ответ на собеседовании

> JSON — это текстовый формат представления структурированных данных,
> который очень часто используется в веб-API. Он достаточно компактный,
> легко читается человеком, легко парсится программами и поддерживается
> большинством языков программирования.

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

#### Quick recall

**The OpenAPI Specification is a standard for machine-readable
descriptions of HTTP APIs. Swagger is a family of tools that work with
OpenAPI, such as Swagger UI.**

#### Interview answer

> OpenAPI is a specification for formally describing an API, including
> paths, HTTP methods, parameters, request bodies, responses, data
> schemas, and authentication. Swagger is a set of tools built around
> OpenAPI, such as Swagger UI for displaying interactive API
> documentation.

#### Details

An OpenAPI description is commonly written in YAML or JSON. It can
describe available operations, parameters, request and response schemas,
status codes, and authentication methods.

A simplified example:

``` yaml
paths:
  /users/{userId}:
    get:
      parameters:
        - name: userId
          in: path
          required: true
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

#### Быстро вспомнить

**OpenAPI Specification — стандарт машиночитаемого описания HTTP API.
Swagger — семейство инструментов для работы с OpenAPI, например
Swagger UI.**

#### Ответ на собеседовании

> OpenAPI — это спецификация, с помощью которой можно формально
> описать API: paths, HTTP-методы, параметры, request body, ответы,
> схемы данных и авторизацию. Swagger — это набор инструментов вокруг
> OpenAPI, например Swagger UI для отображения интерактивной
> API-документации.

#### Подробнее

OpenAPI-описание обычно хранится в YAML или JSON. Оно может содержать
информацию о доступных операциях, параметрах, схемах запросов и ответов,
статус-кодах и способах авторизации.

Упрощенный пример:

``` yaml
paths:
  /users/{userId}:
    get:
      parameters:
        - name: userId
          in: path
          required: true
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

#### Quick recall

**API documentation should help developers understand the API,
authenticate, make their first request, and correctly use individual
operations. It should cover endpoints, methods, parameters, requests,
responses, errors, and practical examples.**

#### Interview answer

> I would first identify the API purpose and target audience and make
> sure a developer can go from authentication to a successful first
> request. In the API reference, I would document endpoints and HTTP
> methods, parameters, headers and request bodies, response formats,
> status codes, and errors. I would also provide a getting-started guide
> and examples of common use cases.

#### Details

API documentation can be organized into several layers.

### Overview

It explains:

-   what the API does;
-   who it is for;
-   its main capabilities;
-   the base URL;
-   important requirements or limitations.

### Getting Started

It should help a developer make a successful request as quickly as
possible:

1.  obtain credentials or a token;
2.  configure authentication;
3.  send a simple request;
4.  receive the expected response.

### API Reference

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

### Guides / Use Cases

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

#### Быстро вспомнить

**API-документация должна помочь разработчику понять назначение API,
авторизоваться, выполнить первый запрос и правильно использовать
конкретные операции. В ней нужны endpoints, методы, параметры, запросы,
ответы, ошибки и практические примеры.**

#### Ответ на собеседовании

> Я бы сначала определил назначение API и его целевую аудиторию, а затем
> проверил, что разработчик может пройти путь от авторизации до первого
> рабочего запроса. В reference-документации я бы описал endpoints и
> HTTP-методы, параметры, headers и request body, форматы ответов,
> статус-коды и ошибки. Кроме reference, я бы добавил getting started и
> примеры основных use cases.

#### Подробнее

Хорошую API-документацию удобно разделять на несколько уровней.

### Overview

Объясняет:

-   что делает API;
-   для кого оно предназначено;
-   какие основные возможности предоставляет;
-   где находится base URL;
-   какие есть ограничения или требования.

### Getting Started

Помогает разработчику как можно быстрее сделать первый успешный запрос:

1.  получить credentials или token;
2.  настроить авторизацию;
3.  отправить простой запрос;
4.  увидеть ожидаемый ответ.

### API Reference

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

### Guides / Use Cases

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

#### Quick recall

**The main audience for API documentation is developers and other
technical users who integrate with the API. Their goals and existing
knowledge determine the required level of explanation and examples.**

#### Interview answer

> API documentation is usually written for developers integrating a
> service into an application. The audience can also include solution
> engineers, QA specialists, partners, or internal developers. Before
> writing, I would identify what users already know and what task they
> need to complete.

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

#### Быстро вспомнить

**Основная аудитория API-документации — разработчики и другие
технические специалисты, которые интегрируют систему с API. Их задачи и
уровень знаний определяют глубину объяснений и примеры.**

#### Ответ на собеседовании

> Чаще всего API-документацию используют разработчики, которые
> интегрируют сервис со своим приложением. Но аудитория может включать
> solution engineers, QA, партнеров или внутренних разработчиков.
> Поэтому перед написанием документации важно понять, что пользователь
> уже знает и какую задачу он пытается решить.

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

#### Quick recall

**Good API documentation allows its target developer to complete a
typical workflow independently — from authentication and the first
request to handling responses and errors. It should be accurate, clear,
complete, and practically verifiable.**

#### Interview answer

> I consider an API well documented when a developer can understand its
> purpose, authenticate, make the first request, and implement common
> use cases without additional help. The reference should accurately
> describe parameters, requests, responses, and errors, and the examples
> should work against the real API.

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

#### Быстро вспомнить

**Хорошая API-документация позволяет целевому разработчику
самостоятельно выполнить типичный сценарий — от авторизации и первого
запроса до обработки ответа и ошибок. Она должна быть точной, понятной,
полной и проверяемой на практике.**

#### Ответ на собеседовании

> Я считаю API хорошо задокументированным, если разработчик может без
> дополнительных вопросов понять назначение API, авторизоваться, сделать
> первый запрос и реализовать основные сценарии. Reference должен точно
> описывать параметры, запросы, ответы и ошибки, а примеры должны быть
> рабочими и соответствовать реальному поведению API.

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
  └─ Body: JSON
  ↓
API
  ↓
HTTP response
  ├─ Status code: 200 / 400 / 404 / 500
  ├─ Headers
  └─ Body: for example, JSON
```

Example:

```http
GET /users/123?details=true
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
  └─ Body: JSON
  ↓
API
  ↓
HTTP response
  ├─ Status code: 200 / 400 / 404 / 500
  ├─ Headers
  └─ Body: например JSON
```

Пример:

```http
GET /users/123?details=true
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
