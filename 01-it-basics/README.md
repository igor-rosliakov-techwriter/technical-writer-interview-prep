# IT Basics for Technical Writer Interviews

A cheat sheet on core IT topics for technical writer interviews.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — quick recall, interview answer, details.
- 🇷🇺 **Русский** — быстро вспомнить, ответ на собеседовании, подробнее.

---

## 1. Client-server architecture / Клиент-серверная архитектура

### 🇬🇧 English

#### Quick recall

**Client-server architecture is a model in which a client sends requests and a server processes them and returns responses.**

#### Interview answer

> Client-server architecture is a model where a client, such as a browser or mobile application, sends a request to a server. The server processes the request according to its business logic, may interact with a database or other services, and returns a response to the client.

#### Details

The client initiates communication; the server provides a service. A client can be a browser, mobile or desktop application, CLI tool, or another service.

### 🇷🇺 Русский

#### Быстро вспомнить

**Клиент-серверная архитектура — это модель, в которой клиент отправляет запросы, а сервер их обрабатывает и возвращает ответы.** Сервер при необходимости обращается к базе данных, API или другим сервисам.

#### Ответ на собеседовании

> Клиент-серверная архитектура — это модель взаимодействия, в которой клиент, например браузер или мобильное приложение, отправляет запрос серверу. Сервер обрабатывает запрос согласно бизнес-логике, при необходимости обращается к базе данных или другим сервисам и возвращает клиенту ответ.

#### Подробнее

Клиент инициирует взаимодействие, сервер предоставляет сервис. Клиентом может быть браузер, мобильное или desktop-приложение, CLI или другой сервис. Типичный поток: `Client → Backend → Database/Services → Backend → Client`.

---

## 2. Frontend vs backend / Frontend и backend

### 🇬🇧 English

#### Quick recall

**Frontend is the client-side part users interact with. Backend is the server-side part responsible for business logic, request processing, and data.**

#### Interview answer

> Frontend is responsible for the user interface and user interaction. Backend processes requests from the frontend, implements business logic, communicates with databases and other services, and returns the result.

#### Details

For example, the frontend submits form data; the backend validates it, checks permissions, updates the database, and returns a result.

### 🇷🇺 Русский

#### Быстро вспомнить

**Frontend — клиентская часть приложения, с которой взаимодействует пользователь. Backend — серверная часть, которая отвечает за бизнес-логику, обработку запросов и работу с данными.**

#### Ответ на собеседовании

> Frontend отвечает за пользовательский интерфейс и взаимодействие пользователя с приложением. Backend принимает запросы от frontend, выполняет бизнес-логику, взаимодействует с базами данных и другими сервисами и возвращает результат.

#### Подробнее

Например, пользователь нажимает «Создать задачу». Frontend показывает форму и отправляет данные. Backend проверяет данные и права, записывает изменения в БД и возвращает результат.

---

## 3. What happens when you enter a URL? / Что происходит после ввода URL в браузере?

### 🇬🇧 English

#### Quick recall

**The browser resolves the server IP using DNS, establishes a connection, performs TLS for HTTPS, sends an HTTP request, receives an HTTP response, and renders the page.**

#### Interview answer

> When a user enters a URL, the browser first determines the server's IP address, usually using DNS. It then establishes a connection to the server and, for HTTPS, establishes a secure TLS connection. The browser sends an HTTP request, the server processes it and returns an HTTP response with a status code, headers, and a body. The browser processes the response and renders the page.

#### Details

A useful flow to remember is: `URL → DNS → IP → TCP → TLS → HTTP Request → Server → HTTP Response → Browser`.

### 🇷🇺 Русский

#### Быстро вспомнить

**Браузер получает IP через DNS, устанавливает соединение, для HTTPS выполняет TLS, отправляет HTTP-запрос, получает HTTP-ответ и отображает страницу.**

#### Ответ на собеседовании

> Когда пользователь вводит URL, браузеру сначала нужно определить IP-адрес сервера. Он проверяет локальные данные и при необходимости обращается к DNS-резолверу. После получения IP устанавливается соединение с сервером, а для HTTPS выполняется TLS handshake. Затем браузер отправляет HTTP-запрос. Сервер его обрабатывает и возвращает HTTP-ответ со статус-кодом, заголовками и телом. Браузер обрабатывает ответ и отображает страницу.

#### Подробнее

Полезная цепочка: `URL → DNS → IP → TCP → TLS → HTTP Request → Server → HTTP Response → Browser`. После получения HTML браузер обычно делает дополнительные запросы за CSS, JavaScript, изображениями, шрифтами и другими ресурсами.

---

## 4. DNS / DNS

### 🇬🇧 English

#### Quick recall

**DNS is a distributed hierarchical system that maps domain names to IP addresses.**

#### Interview answer

> DNS is a distributed hierarchical naming system used to resolve domain names to IP addresses. A DNS resolver can return a cached result or query the DNS hierarchy to find the required address.

#### Details

A simplified lookup path is: `Root → TLD → authoritative DNS → DNS record`.

### 🇷🇺 Русский

#### Быстро вспомнить

**DNS — распределенная иерархическая система, которая сопоставляет доменные имена с IP-адресами.**

#### Ответ на собеседовании

> DNS — это распределенная иерархическая система имен, которая позволяет определить IP-адрес по доменному имени. Обычно клиент обращается к DNS-резолверу, который либо берет результат из кеша, либо получает его через DNS-систему.

#### Подробнее

Упрощенная цепочка: `Root → TLD (.com, .ru) → authoritative DNS → нужная DNS-запись`. Root направляет к TLD, TLD — к авторитетному серверу конкретного домена.

---

## 5. DNS resolver / DNS-резолвер

### 🇬🇧 English

#### Quick recall

**A DNS resolver is a service that performs DNS lookups on behalf of a client.**

#### Interview answer

> A DNS resolver receives a DNS query from a client. It first checks its cache and, if necessary, queries the DNS hierarchy until it obtains the required record, then returns the result to the client.

#### Details

Resolvers cache records, reducing the need to repeat the full lookup chain.

### 🇷🇺 Русский

#### Быстро вспомнить

**DNS-резолвер — это посредник, который выполняет DNS-поиск за клиент.**

#### Ответ на собеседовании

> DNS-резолвер получает DNS-запрос от клиента. Сначала он проверяет кеш, а если нужной записи нет, обращается к DNS-инфраструктуре, получает результат и возвращает его клиенту.

#### Подробнее

Резолвер может обращаться к root-, TLD- и авторитетным DNS-серверам. Полученные ответы он кеширует, поэтому полная цепочка не выполняется при каждом запросе.

---

## 6. IP address / IP-адрес

### 🇬🇧 English

#### Quick recall

**An IP address identifies a host or network interface in an IP network and is used to route packets to their destination.**

#### Interview answer

> An IP address is used to identify a host or network interface and route network traffic. IPv4 uses 32-bit addresses, usually represented as four numbers from 0 to 255, while IPv6 uses 128-bit addresses.

#### Details

An IP address is a network-level identifier and is not necessarily a one-to-one identifier of a website.

### 🇷🇺 Русский

#### Быстро вспомнить

**IP-адрес — это сетевой адрес узла или интерфейса, используемый для маршрутизации данных в IP-сети.**

#### Ответ на собеседовании

> IP-адрес используется для идентификации узла или сетевого интерфейса в IP-сети и для маршрутизации данных. IPv4 использует 32-битные адреса, обычно записываемые четырьмя числами от 0 до 255, а IPv6 использует 128-битные адреса.

#### Подробнее

IP — не просто «адрес сайта». Один IP может обслуживать много сайтов, а один сайт может использовать несколько IP. Есть публичные и приватные IP-адреса.

---

## 7. TCP / TCP

### 🇬🇧 English

#### Quick recall

**TCP is a transport protocol that provides reliable and ordered delivery of data between endpoints.**

#### Interview answer

> TCP is a connection-oriented transport protocol. It provides reliable and ordered delivery and retransmits data when necessary. A TCP connection is established using a three-way handshake.

#### Details

The classic handshake is `SYN → SYN-ACK → ACK`.

### 🇷🇺 Русский

#### Быстро вспомнить

**TCP — транспортный протокол, который обеспечивает надежную и упорядоченную передачу данных между двумя сторонами.**

#### Ответ на собеседовании

> TCP — транспортный протокол с установлением соединения. Он обеспечивает надежную и упорядоченную передачу данных, обнаруживает потери и при необходимости повторно передает данные.

#### Подробнее

Соединение классически устанавливается через three-way handshake: `SYN → SYN-ACK → ACK`. TCP также отвечает за порядок, подтверждения, повторные передачи и управление потоком.

---

## 8. TLS / TLS

### 🇬🇧 English

#### Quick recall

**TLS is a cryptographic protocol that protects data in transit through encryption, integrity protection, and authentication.**

#### Interview answer

> TLS provides secure communication between a client and a server. During the TLS handshake, the server presents its certificate and the parties establish encryption parameters. HTTP traffic can then be transmitted securely.

#### Details

For interview purposes, remember encryption, integrity, and server authentication.

### 🇷🇺 Русский

#### Быстро вспомнить

**TLS защищает данные при передаче: шифрует их, обеспечивает целостность и помогает проверить подлинность сервера.**

#### Ответ на собеседовании

> TLS — криптографический протокол для защищенной передачи данных. При установлении HTTPS-соединения клиент и сервер выполняют TLS handshake, сервер предоставляет сертификат, стороны согласовывают параметры защищенного соединения, после чего HTTP-трафик передается в зашифрованном виде.

#### Подробнее

Для техрайтера достаточно понимать три задачи TLS: шифрование, целостность и аутентификация сервера по сертификату.

---

## 9. HTTP / HTTP

### 🇬🇧 English

#### Quick recall

**HTTP is an application-layer protocol that defines request-response communication between clients and servers. It can transfer both text and binary data.**

#### Interview answer

> HTTP is an application-layer protocol based on a request-response model. A client sends an HTTP request containing a method, target resource, headers, and optionally a body. The server returns an HTTP response containing a status, headers, and a body.

#### Details

HTTP can carry many data formats; `Content-Type` tells the recipient how to interpret the body.

### 🇷🇺 Русский

#### Быстро вспомнить

**HTTP — протокол прикладного уровня для обмена запросами и ответами между клиентом и сервером. Через HTTP можно передавать как текстовые, так и бинарные данные.**

#### Ответ на собеседовании

> HTTP — это протокол прикладного уровня, основанный на модели request-response. Клиент отправляет HTTP-запрос, содержащий метод, целевой ресурс, заголовки и при необходимости тело. Сервер возвращает HTTP-ответ со статусом, заголовками и телом.

#### Подробнее

HTTP может передавать HTML, JSON, XML, изображения, PDF, аудио, видео и другие данные. Заголовок `Content-Type` сообщает получателю, как интерпретировать тело сообщения.

---

## 10. HTTP vs HTTPS / HTTP и HTTPS

### 🇬🇧 English

#### Quick recall

**HTTPS is HTTP transported over a secure TLS connection.**

#### Interview answer

> HTTPS uses HTTP for application-level communication and TLS to provide encryption, integrity, and server authentication.

#### Details

The HTTP request-response model remains the same; TLS adds transport security.

### 🇷🇺 Русский

#### Быстро вспомнить

**HTTPS — это HTTP, передаваемый через защищенное TLS-соединение.**

#### Ответ на собеседовании

> HTTPS использует HTTP на прикладном уровне и TLS для шифрования, контроля целостности и проверки подлинности сервера. Методы HTTP, структура запросов и ответов при этом сохраняются.

#### Подробнее

Упрощенно: `HTTP → TLS → transport/network layers`. В обычной речи нормально говорить «HTTPS-запрос».

---

## 11. HTTP request / HTTP-запрос

### 🇬🇧 English

#### Quick recall

**An HTTP request contains a method and target, headers, and optionally a body. GET, POST, PUT, PATCH, and DELETE are HTTP methods, not headers.**

#### Interview answer

> An HTTP request contains a method, request target, headers, and optionally a body. The method describes the intended operation, while headers provide metadata such as content type or authentication information.

#### Details

In HTTP/1.1, the request line contains the method, target, and protocol version.

### 🇷🇺 Русский

#### Быстро вспомнить

**HTTP-запрос содержит метод и целевой ресурс, заголовки и при необходимости тело. GET, POST, PUT, PATCH и DELETE — это методы HTTP, а не заголовки.**

#### Ответ на собеседовании

> HTTP-запрос содержит метод, целевой путь или ресурс, заголовки и при необходимости тело. Метод описывает предполагаемую операцию, а заголовки передают метаданные, например тип содержимого или данные для аутентификации.

#### Подробнее

Пример: `POST /users HTTP/1.1`. Здесь `POST` — method, `/users` — target/path, далее идут headers, затем пустая строка и при наличии body.

---

## 12. Main HTTP methods / Основные HTTP-методы

### 🇬🇧 English

#### Quick recall

**GET retrieves, POST creates or submits, PUT replaces, PATCH partially updates, and DELETE removes a resource.**

#### Interview answer

> GET is commonly used to retrieve data, POST to submit data or create a resource, PUT to replace a resource, PATCH to partially update it, and DELETE to remove it.

#### Details

These are common semantics, especially in REST-style APIs.

### 🇷🇺 Русский

#### Быстро вспомнить

**GET — получить, POST — создать или отправить данные на обработку, PUT — заменить, PATCH — частично изменить, DELETE — удалить.**

#### Ответ на собеседовании

> Основные HTTP-методы описывают предполагаемое действие над ресурсом. GET обычно используют для получения данных, POST — для отправки данных или создания ресурса, PUT — для полной замены, PATCH — для частичного изменения, DELETE — для удаления.

#### Подробнее

Это общая семантика HTTP и распространенная практика REST API. Конкретный API может использовать методы неидеально или по своим соглашениям.

---

## 13. HTTP response / HTTP-ответ

### 🇬🇧 English

#### Quick recall

**An HTTP response contains a status, headers, and optionally a body with returned data.**

#### Interview answer

> An HTTP response contains a status code, response headers, and usually a body. The status code indicates the result of processing the request, while the body contains the returned data.

#### Details

The status describes the result, headers carry metadata, and the body carries the payload.

### 🇷🇺 Русский

#### Быстро вспомнить

**HTTP-ответ содержит статус, заголовки и при необходимости тело с возвращаемыми данными.**

#### Ответ на собеседовании

> HTTP-ответ содержит статус запроса, заголовки и обычно тело ответа. Статус-код показывает результат обработки, заголовки содержат метаданные, а тело может содержать HTML, JSON, изображение, файл или другие данные.

#### Подробнее

Например: `HTTP/1.1 200 OK`, затем заголовки вроде `Content-Type`, затем body с данными.

---

## 14. HTTP status codes / HTTP status codes

### 🇬🇧 English

#### Quick recall

**HTTP status codes indicate the result of processing a request: 2xx success, 3xx redirection, 4xx client/request/access problems, and 5xx server errors.**

#### Interview answer

> HTTP status codes describe the result of a request: 2xx means success, 3xx redirection, 4xx client-side problems, and 5xx server-side errors.

#### Details

Common examples include 200, 201, 400, 401, 403, 404, 500, 502, and 503.

### 🇷🇺 Русский

#### Быстро вспомнить

**Статус-коды HTTP показывают результат обработки запроса: 2xx — успех, 3xx — перенаправление, 4xx — проблема с запросом или доступом, 5xx — ошибка сервера.**

#### Ответ на собеседовании

> HTTP status code показывает результат обработки запроса. Например, 2xx означает успешную обработку, 4xx — что запрос не может быть выполнен из-за проблемы с запросом или доступом клиента, а 5xx — проблему на стороне сервера.

#### Подробнее

Важно знать: `200 OK`, `201 Created`, `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, `500 Internal Server Error`, `502 Bad Gateway`, `503 Service Unavailable`.

---

## 15. 401 vs 403 / 401 и 403

### 🇬🇧 English

#### Quick recall

**401 means valid authentication credentials are required. 403 means the server understands the request but refuses access.**

#### Interview answer

> 401 means valid authentication credentials are required. 403 means the server understands the request but refuses access.

#### Details

A useful memory aid is: `401 → Who are you?`, `403 → I know who you are, but you cannot access this.`

### 🇷🇺 Русский

#### Быстро вспомнить

**401 — нужна корректная аутентификация. 403 — сервер понял запрос, но доступ запрещен.**

#### Ответ на собеседовании

> 401 обычно означает, что для выполнения запроса требуется корректная аутентификация. 403 означает, что сервер понял запрос, но отказывается предоставлять доступ.

#### Подробнее

Запоминалка: `401 → Кто ты?` и `403 → Я знаю, кто ты, но тебе нельзя.`

---

## 16. HTTP headers / HTTP headers

### 🇬🇧 English

#### Quick recall

**HTTP headers contain metadata about a request or response.**

#### Interview answer

> HTTP headers contain metadata about a request or response, such as content type, authentication information, caching rules, and cookies.

#### Details

Common examples include `Content-Type`, `Accept`, `Authorization`, `Cookie`, and `Cache-Control`.

### 🇷🇺 Русский

#### Быстро вспомнить

**HTTP headers — это метаданные запроса или ответа: тип данных, авторизация, cookies, кеширование и другие параметры.**

#### Ответ на собеседовании

> HTTP headers передают дополнительную информацию о запросе или ответе. Например, Content-Type описывает формат тела сообщения, Authorization может содержать данные для аутентификации, а Cookie передает cookies клиента.

#### Подробнее

Примеры: `Content-Type`, `Accept`, `Authorization`, `Cookie`, `Cache-Control`.

---

## 17. HTTP body / HTTP body

### 🇬🇧 English

#### Quick recall

**The HTTP body is the message payload — the actual data being transferred. It can contain text or binary data.**

#### Interview answer

> The HTTP body contains the actual payload being transferred, such as JSON, HTML, an image, a file, or another data format.

#### Details

Not every HTTP request or response has a body.

### 🇷🇺 Русский

#### Быстро вспомнить

**HTTP body — это полезная нагрузка сообщения, то есть сами передаваемые данные. Тело может быть текстовым или бинарным и присутствует не всегда.**

#### Ответ на собеседовании

> Body — это часть HTTP-сообщения, в которой передаются сами данные. Это может быть JSON, HTML, XML, изображение, PDF, видео или другой контент.

#### Подробнее

Не каждый запрос или ответ имеет body. Например, GET-запрос часто идет без тела, а POST обычно может содержать данные.

---

## 18. How does HTTP transfer media? / Как HTTP передает изображения, аудио и видео?

### 🇬🇧 English

#### Quick recall

**HTTP can carry binary data in the message body. `Content-Type` tells the client how to interpret those bytes.**

#### Interview answer

> HTTP is not limited to text. The response body can contain binary data such as images, audio, or video, while the Content-Type header tells the client how to interpret that data.

#### Details

Large media resources may also be requested in byte ranges.

### 🇷🇺 Русский

#### Быстро вспомнить

**HTTP может передавать бинарные данные в body, а `Content-Type` сообщает клиенту, как интерпретировать эти байты.**

#### Ответ на собеседовании

> HTTP не ограничен текстом. Тело ответа может содержать бинарные данные, например изображение, аудио или видео. Заголовок Content-Type сообщает клиенту, какой это тип данных.

#### Подробнее

Примеры: `image/jpeg`, `audio/mpeg`, `video/mp4`. Большие медиафайлы также могут запрашиваться частями с помощью range requests.

---

## 19. Cookies / Cookies

### 🇬🇧 English

#### Quick recall

**A cookie is a small piece of data stored by the browser and sent with matching future requests according to cookie rules.**

#### Interview answer

> Cookies allow a website to store small pieces of data in the browser. They can be used for session management, preferences, personalization, analytics, and other purposes.

#### Details

Important cookie attributes include `HttpOnly`, `Secure`, `SameSite`, and expiration settings.

### 🇷🇺 Русский

#### Быстро вспомнить

**Cookie — небольшой фрагмент данных, который браузер хранит и может автоматически отправлять серверу с последующими подходящими запросами.**

#### Ответ на собеседовании

> Cookie — это небольшой фрагмент данных, который сайт сохраняет в браузере. Браузер может автоматически отправлять cookie обратно серверу с последующими подходящими запросами. Cookies используются, например, для управления сессиями, настроек и персонализации.

#### Подробнее

Сервер может отправить `Set-Cookie: session_id=abc123`, а браузер затем вернуть `Cookie: session_id=abc123`. Важные атрибуты: `HttpOnly`, `Secure`, `SameSite`, `Expires/Max-Age`.

---

## 20. Sessions / Sessions

### 🇬🇧 English

#### Quick recall

**A session is a mechanism for maintaining state across multiple requests. With traditional server-side sessions, the server stores session data and the browser usually stores a session identifier in a cookie.**

#### Interview answer

> HTTP is stateless, so applications need an additional mechanism to maintain user state between requests. With server-side sessions, the server stores the session data and the browser typically sends a session ID in a cookie.

#### Details

The session ID links a browser request to server-side session data.

### 🇷🇺 Русский

#### Быстро вспомнить

**Сессия — механизм сохранения состояния между запросами. При классической server-side session данные хранятся на сервере, а браузер обычно хранит cookie с идентификатором сессии.**

#### Ответ на собеседовании

> HTTP является stateless-протоколом, поэтому приложениям нужен дополнительный механизм для сохранения состояния пользователя между запросами. Один из классических вариантов — server-side sessions: сервер хранит данные сессии, а браузер получает cookie с идентификатором сессии и отправляет его с последующими запросами.

#### Подробнее

Типичный поток после логина: сервер создает `session_id`, отправляет его в cookie, браузер сохраняет cookie и отправляет его дальше, а сервер по ID находит сессию и узнает пользователя.

---

## 21. Docs as Code / Docs as Code

### 🇬🇧 English

#### Quick recall

**Docs as Code is an approach where documentation is managed using tools and workflows similar to software development: text-based source files, Git, branches, reviews, CI checks, builds, and automated publishing.**

#### Interview answer

> Docs as Code is an approach where documentation follows a development-like workflow. Documentation source files are stored in version control, typically Git, and changes are made through branches, commits, and pull requests. They can be reviewed, automatically checked in CI, and then built and published after merging.

#### Details

Docs as Code is a workflow concept, not a specific tool or file format.

### 🇷🇺 Русский

#### Быстро вспомнить

**Docs as Code — это подход, при котором документацию ведут примерно теми же инструментами и процессами, что и программный код: текстовые файлы, Git, ветки, review, CI, сборка и публикация.**

#### Ответ на собеседовании

> Docs as Code — это подход к работе с документацией, при котором она хранится в системе контроля версий и проходит похожий на разработку workflow. Например, технический писатель пишет документацию в Markdown, создает Git-ветку, делает commit и pull request, после чего изменения проходят review. Автоматические проверки могут проверять стиль, ссылки и сборку, а после merge документация может автоматически публиковаться.

#### Подробнее

Минимальный workflow: `Markdown → Git → Pull Request → Review`. Более зрелый процесс добавляет linting, spell checking, link checks, build и automated deployment. Это подход, а не конкретный инструмент.

---

## Core flow / Главная схема

### 🇬🇧 English

```text
URL → DNS → IP → TCP → TLS → HTTP Request → Server → HTTP Response → Browser
```

HTTP itself is stateless; cookies and sessions can help an application maintain user state across requests.

### 🇷🇺 Русский

```text
URL → DNS → IP → TCP → TLS → HTTP Request → Server → HTTP Response → Browser
```

HTTP сам по себе stateless; cookies и sessions помогают приложению сохранять состояние пользователя между запросами.
