# IT Basics for Technical Writer Interviews

A cheat sheet on core IT topics for technical writer interviews.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — short interview answer, details.
- 🇷🇺 **Русский** — короткий ответ на собеседовании, подробнее.

---

## 1. Client-server architecture / Клиент-серверная архитектура

### 🇬🇧 English

#### Interview answer

> The client requests a service; the server processes the request and returns a result.

#### Details

The client initiates communication; the server provides a service. A client can be a browser, mobile or desktop application, CLI tool, or another service.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Клиент запрашивает услугу; сервер обрабатывает запрос и возвращает результат.

#### Подробнее

Клиент инициирует взаимодействие, сервер предоставляет сервис. Клиентом может быть браузер, мобильное или desktop-приложение, CLI или другой сервис. Типичный поток: `Client → Backend → Database/Services → Backend → Client`.

---

## 2. Frontend vs backend / Frontend и backend

### 🇬🇧 English

#### Interview answer

> Frontend handles the user interface; backend handles server-side logic, permissions, and data processing.

#### Details

For example, the frontend submits form data; the backend validates it, checks permissions, updates the database, and returns a result.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Frontend отвечает за интерфейс; backend выполняет серверную логику, проверяет права и обрабатывает данные.

#### Подробнее

Например, пользователь нажимает «Создать задачу». Frontend показывает форму и отправляет данные. Backend проверяет данные и права, записывает изменения в БД и возвращает результат.

---

## 3. What happens when you enter a URL? / Что происходит после ввода URL в браузере?

### 🇬🇧 English

#### Interview answer

> The browser resolves the host, establishes a connection, sends an HTTP request, and processes the response. For HTTPS, the connection is protected with TLS.

#### Details

For a fresh HTTPS connection over HTTP/1.1 or HTTP/2: `URL → DNS → TCP → TLS → HTTP request → HTTP response → rendering`.

HTTP/3 uses QUIC over UDP with TLS 1.3, not a TCP connection. Cached DNS results, cached responses, and reused connections can skip steps. After receiving HTML, the browser usually requests CSS, scripts, and images; redirects can trigger another request.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Браузер определяет адрес сервера, устанавливает соединение, отправляет HTTP-запрос и обрабатывает ответ. Для HTTPS соединение защищается с помощью TLS.

#### Подробнее

Для нового HTTPS-соединения через HTTP/1.1 или HTTP/2: `URL → DNS → TCP → TLS → HTTP-запрос → HTTP-ответ → отображение`.

HTTP/3 использует QUIC поверх UDP с TLS 1.3, а не TCP. Кеш DNS, кеш ответов и повторное использование соединения позволяют пропустить часть шагов. После HTML браузер обычно запрашивает CSS, скрипты и изображения; перенаправление может вызвать новый запрос.

---

## 4. DNS / DNS

### 🇬🇧 English

#### Interview answer

> DNS is a distributed naming system. It retrieves records for domain names, including IP addresses.

#### Details

A simplified recursive lookup is `root → TLD → authoritative server → record`. A/AAAA records contain IP addresses; MX identifies mail servers and TXT contains text. DNS is not limited to website addresses.

### 🇷🇺 Русский

#### Ответ на собеседовании

> DNS — распределённая система имён. Она позволяет получать записи домена, в том числе IP-адреса.

#### Подробнее

Упрощённая цепочка поиска: `root → TLD (.com, .ru) → авторитетный сервер → запись`. A/AAAA содержат IP-адреса, MX указывает почтовые серверы, TXT хранит текст. DNS не ограничивается адресами сайтов.

---

## 5. DNS resolver / DNS-резолвер

### 🇬🇧 English

#### Interview answer

> A recursive DNS resolver finds DNS records for a client, using its cache or querying other DNS servers.

#### Details

The local stub resolver typically asks a recursive resolver to do the lookup. A recursive resolver can query the hierarchy or forward the request. Cached answers have a limited lifetime, so the full chain is not repeated for every lookup.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Рекурсивный DNS-резолвер находит записи для клиента: берёт ответ из кеша или обращается к другим DNS-серверам.

#### Подробнее

Локальный stub resolver обычно передаёт запрос рекурсивному резолверу. Тот обходит DNS-иерархию или пересылает запрос другому серверу. Ответы кешируются на ограниченное время, поэтому полная цепочка нужна не при каждом обращении.

---

## 6. IP address / IP-адрес

### 🇬🇧 English

#### Interview answer

> An IP address identifies a network interface for routing traffic. IPv4 addresses have 32 bits; IPv6 addresses have 128 bits.

#### Details

An IP address is a network-level identifier and is not necessarily a one-to-one identifier of a website.

### 🇷🇺 Русский

#### Ответ на собеседовании

> IP-адрес идентифицирует сетевой интерфейс и используется для маршрутизации. Адрес IPv4 содержит 32 бита, IPv6 — 128 бит.

#### Подробнее

IP — не просто «адрес сайта». Один IP может обслуживать много сайтов, а один сайт может использовать несколько IP. Есть публичные и приватные IP-адреса.

---

## 7. TCP / TCP

### 🇬🇧 English

#### Interview answer

> TCP provides a reliable, ordered byte stream between applications. It establishes a connection and retransmits lost data.

#### Details

The classic handshake is `SYN → SYN-ACK → ACK`. TCP handles acknowledgments, retransmission, ordering, and flow control. It does not preserve application-message boundaries, and a broken connection can still cause an operation to fail.

### 🇷🇺 Русский

#### Ответ на собеседовании

> TCP передаёт между приложениями надёжный, упорядоченный поток байтов. Он устанавливает соединение и повторно передаёт потерянные данные.

#### Подробнее

Соединение обычно устанавливается через `SYN → SYN-ACK → ACK`. TCP управляет подтверждениями, повторной передачей, порядком и потоком данных. Границы сообщений приложения он не сохраняет; при разрыве соединения операция всё равно может завершиться ошибкой.

---

## 8. TLS / TLS

### 🇬🇧 English

#### Interview answer

> TLS protects data in transit through encryption and integrity checks. In typical HTTPS connections, it also authenticates the server using a certificate.

#### Details

In a typical full HTTPS handshake, the client validates the server's certificate and both sides establish keys. TLS also supports resumption and other authentication modes, so a certificate exchange is not mandatory in every handshake. Transport protection does not prove that the website itself is trustworthy.

### 🇷🇺 Русский

#### Ответ на собеседовании

> TLS защищает передаваемые данные шифрованием и проверкой целостности. В типичном HTTPS-соединении он также подтверждает подлинность сервера по сертификату.

#### Подробнее

В типичном полном HTTPS-handshake клиент проверяет сертификат сервера, стороны устанавливают ключи. TLS также поддерживает возобновление сессий и другие режимы аутентификации, поэтому сертификат передаётся не в каждом handshake. Защита соединения не доказывает добросовестность самого сайта.

---

## 9. HTTP / HTTP

### 🇬🇧 English

#### Interview answer

> HTTP is an application-layer request-response protocol: a client sends a request and a server returns a response.

#### Details

HTTP can carry many data formats; `Content-Type` tells the recipient how to interpret the body.

### 🇷🇺 Русский

#### Ответ на собеседовании

> HTTP — протокол прикладного уровня: клиент отправляет запрос, сервер возвращает ответ.

#### Подробнее

HTTP может передавать HTML, JSON, XML, изображения, PDF, аудио, видео и другие данные. Заголовок `Content-Type` сообщает получателю, как интерпретировать тело сообщения.

---

## 10. HTTP vs HTTPS / HTTP и HTTPS

### 🇬🇧 English

#### Interview answer

> HTTPS is HTTP protected by TLS. It adds encryption, integrity, and authentication without changing HTTP method semantics.

#### Details

The HTTP request-response model remains the same; TLS adds transport security.

### 🇷🇺 Русский

#### Ответ на собеседовании

> HTTPS — это HTTP с защитой TLS: шифрованием, контролем целостности и аутентификацией. Смысл HTTP-методов при этом не меняется.

#### Подробнее

Для HTTPS через HTTP/1.1 или HTTP/2 модель выглядит как `HTTP → TLS → TCP`. В HTTP/3 используется QUIC со встроенным TLS 1.3. В обычной речи корректно говорить «HTTPS-запрос».

---

## 11. HTTP request / HTTP-запрос

### 🇬🇧 English

#### Interview answer

> An HTTP request has a method, a target, headers, and optionally a body. Together they specify what the client asks the server to do.

#### Details

In HTTP/1.1, the request line contains the method, target, and protocol version.

### 🇷🇺 Русский

#### Ответ на собеседовании

> HTTP-запрос содержит метод, адресуемый ресурс, заголовки и необязательное тело. Они определяют, что клиент просит выполнить.

#### Подробнее

Пример: `POST /users HTTP/1.1`. Здесь `POST` — method, `/users` — target/path, далее идут headers, затем пустая строка и при наличии body.

---

## 12. Main HTTP methods / Основные HTTP-методы

### 🇬🇧 English

#### Interview answer

> GET reads; POST submits data for processing; PUT creates or replaces at the target URI; PATCH applies partial changes; DELETE requests removal.

#### Details

PUT targets a specific URI and can create a missing resource or replace its representation. POST can create a resource, but also performs other processing. GET, PUT, and DELETE are idempotent by defined semantics; POST and PATCH are not necessarily so. Idempotent means repeating the request has the same intended effect, not necessarily the same response.

### 🇷🇺 Русский

#### Ответ на собеседовании

> GET читает; POST отправляет данные на обработку; PUT создаёт или заменяет по заданному URI; PATCH вносит частичные изменения; DELETE запрашивает удаление.

#### Подробнее

PUT обращается к конкретному URI и может создать отсутствующий ресурс или заменить его представление. POST не ограничивается созданием: это также другие виды обработки. GET, PUT и DELETE идемпотентны по определению; POST и PATCH — не обязательно. Идемпотентность означает одинаковый предполагаемый эффект повтора, а не одинаковые ответы.

---

## 13. HTTP response / HTTP-ответ

### 🇬🇧 English

#### Interview answer

> An HTTP response contains a status code, headers, and optionally a body with returned data.

#### Details

For example, an HTTP/1.1 response can begin with `HTTP/1.1 200 OK`, followed by headers, a blank line, and a body. Responses to HEAD, and responses with status 204 or 304, have no body.

### 🇷🇺 Русский

#### Ответ на собеседовании

> HTTP-ответ содержит статус-код, заголовки и необязательное тело с возвращаемыми данными.

#### Подробнее

Например, HTTP/1.1-ответ начинается с `HTTP/1.1 200 OK`, затем идут заголовки, пустая строка и тело. Ответы на HEAD, а также ответы 204 и 304 тела не содержат.

---

## 14. HTTP status codes / HTTP status codes

### 🇬🇧 English

#### Interview answer

> Status codes describe the result: 1xx informational, 2xx success, 3xx redirection, 4xx client error, and 5xx server error.

#### Details

Remember `200 OK`, `201 Created`, `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, `500 Internal Server Error`, `502 Bad Gateway`, and `503 Service Unavailable`. The 3xx class includes `304 Not Modified`: use the cached representation, rather than necessarily redirecting to a new URL.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Статус-коды описывают результат: 1xx — информация, 2xx — успех, 3xx — перенаправление, 4xx — ошибка клиента, 5xx — ошибка сервера.

#### Подробнее

Важно знать: `200 OK`, `201 Created`, `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, `500 Internal Server Error`, `502 Bad Gateway`, `503 Service Unavailable`. В класс 3xx входит `304 Not Modified`: используется кешированное представление, а не обязательно переход на новый URL.

---

## 15. 401 vs 403 / 401 и 403

### 🇬🇧 English

#### Interview answer

> 401 means valid authentication credentials are missing. 403 means the server understood the request but refuses to fulfill it.

#### Details

A 401 response must include a `WWW-Authenticate` challenge. A 403 can mean insufficient permissions, but can also have reasons unrelated to credentials; it does not prove that the caller is authenticated. Remember: `401 → valid credentials needed`; `403 → request refused`.

### 🇷🇺 Русский

#### Ответ на собеседовании

> 401 означает отсутствие подходящих учётных данных для аутентификации. 403 означает, что сервер понял запрос, но отказывается его выполнять.

#### Подробнее

Ответ 401 должен содержать `WWW-Authenticate`. Причиной 403 могут быть недостаточные права или ограничения, не связанные с учётными данными: этот код не доказывает, что клиент аутентифицирован. Запоминалка: `401 → нужны подходящие учётные данные`; `403 → запрос отклонён`.

---

## 16. HTTP headers / HTTP headers

### 🇬🇧 English

#### Interview answer

> HTTP headers carry metadata, such as content type, authentication information, and caching rules.

#### Details

Common examples include `Content-Type`, `Accept`, `Authorization`, `Cookie`, and `Cache-Control`.

### 🇷🇺 Русский

#### Ответ на собеседовании

> HTTP-заголовки передают метаданные: например, тип содержимого, данные аутентификации и правила кеширования.

#### Подробнее

Примеры: `Content-Type`, `Accept`, `Authorization`, `Cookie`, `Cache-Control`.

---

## 17. HTTP body / HTTP body

### 🇬🇧 English

#### Interview answer

> The body carries the message's data, such as JSON, HTML, or a file. Not every HTTP message has a body.

#### Details

GET request content has no generally defined semantics: do not add a GET body unless the API explicitly supports it. For example, a POST request can carry JSON describing a new user. Response bodies can contain data or error information, subject to method and status rules.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Тело содержит передаваемые данные: например, JSON, HTML или файл. Оно есть не у каждого HTTP-сообщения.

#### Подробнее

У тела GET-запроса нет общепринятой семантики: не добавляй его без явной поддержки со стороны API. POST, например, может передать JSON с данными нового пользователя. Тело ответа может содержать данные или описание ошибки с учётом правил метода и статус-кода.

---

## 18. How does HTTP transfer media? / Как HTTP передает изображения, аудио и видео?

### 🇬🇧 English

#### Interview answer

> HTTP can carry binary media in the response body. Content-Type identifies the media format, such as image/jpeg or video/mp4.

#### Details

Large media resources may also be requested in byte ranges.

### 🇷🇺 Русский

#### Ответ на собеседовании

> HTTP может передавать бинарные медиафайлы в теле ответа. Content-Type указывает формат: например, image/jpeg или video/mp4.

#### Подробнее

Примеры: `image/jpeg`, `audio/mpeg`, `video/mp4`. Большие медиафайлы также могут запрашиваться частями с помощью range requests.

---

## 19. Cookies / Cookies

### 🇬🇧 English

#### Interview answer

> Cookies are small pieces of data stored by the browser and sent with matching requests. They are often used for sessions and preferences.

#### Details

The server sends `Set-Cookie`, and the browser can later send `Cookie` according to scope and browser policy. `HttpOnly` blocks access through JavaScript cookie APIs; `Secure` restricts transmission to secure connections; `SameSite` limits cross-site sending. These controls complement, not replace, application security.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Cookies — небольшие данные, которые браузер хранит и отправляет с подходящими запросами. Их часто используют для сессий и настроек.

#### Подробнее

Сервер отправляет `Set-Cookie`, браузер затем может отправить `Cookie` с учётом области действия и своей политики. `HttpOnly` закрывает доступ через JavaScript API cookies, `Secure` ограничивает передачу защищёнными соединениями, `SameSite` ограничивает межсайтовую отправку. Это дополнительные меры, а не замена защите приложения.

---

## 20. Sessions / Sessions

### 🇬🇧 English

#### Interview answer

> A session connects multiple requests to the same application state. With server-side sessions, the client usually sends a cookie containing a session ID.

#### Details

The session ID links a request to server-side data, often stored in a database or cache. It should be unpredictable, expire appropriately, and be invalidated when needed. A session is not a TCP connection; signed client-side state is a different implementation option.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Сессия связывает несколько запросов с одним состоянием приложения. При серверной сессии клиент обычно передаёт её идентификатор в cookie.

#### Подробнее

По идентификатору сервер находит данные сессии, часто в БД или кеше. Идентификатор должен быть непредсказуемым, иметь срок действия и при необходимости отзываться. Сессия не равна TCP-соединению; хранение подписанного состояния на клиенте — другой вариант реализации.

---

## 21. Docs as Code / Docs as Code

### 🇬🇧 English

#### Interview answer

> Docs as Code applies development practices to documentation: version control, review, automated checks, and publishing.

#### Details

Docs as Code is a workflow concept, not a specific tool or file format.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Docs as Code применяет к документации практики разработки: контроль версий, ревью, автоматические проверки и публикацию.

#### Подробнее

Минимальный workflow: `Markdown → Git → Pull Request → Review`. Более зрелый процесс добавляет linting, spell checking, link checks, build и automated deployment. Это подход, а не конкретный инструмент.

---

## Core flow / Главная схема

### 🇬🇧 English

```text
URL → resolve host → secure connection → HTTP request → response → rendering
```

For HTTPS, HTTP/1.1 and HTTP/2 use TLS over TCP; HTTP/3 uses QUIC with TLS. Caching and connection reuse can skip steps. HTTP itself is stateless; cookies and sessions can maintain application state across requests.

### 🇷🇺 Русский

```text
URL → адрес сервера → защищённое соединение → HTTP-запрос → ответ → отображение
```

Для HTTPS HTTP/1.1 и HTTP/2 используют TLS поверх TCP; HTTP/3 — QUIC с TLS. Кеш и повторное использование соединения позволяют пропустить часть шагов. HTTP не хранит состояние между запросами; cookies и sessions помогают хранить его на уровне приложения.

## References / Источники

Technical review: 2026-11-03. / Техническая проверка: 2026-11-03.

- [DNS: RFC 1034](https://www.rfc-editor.org/rfc/rfc1034.html), [TCP: RFC 9293](https://www.rfc-editor.org/rfc/rfc9293.html), [TLS 1.3: RFC 8446](https://www.rfc-editor.org/rfc/rfc8446.html).
- [HTTP semantics: RFC 9110](https://www.rfc-editor.org/rfc/rfc9110.html), [HTTP/3: RFC 9114](https://www.rfc-editor.org/rfc/rfc9114.html), [MDN: cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cookies).
- [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).
