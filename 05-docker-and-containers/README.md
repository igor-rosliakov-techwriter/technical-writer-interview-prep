# Docker for Technical Writer Interviews

A cheat sheet on core Docker and container topics for junior and middle technical writer interviews.

It covers the practical basics: Docker, containerization, Dockerfile, images, containers, build and run workflows, ports, Docker Compose, runtime, dependencies, and layers.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — short interview answer, details.
- 🇷🇺 **Русский** — короткий ответ на собеседовании, подробнее.

---

## 1. What is Docker? / Что такое Docker?

### 🇬🇧 English

#### Interview answer

> Docker builds and runs containerized applications. An image packages application files and dependencies; containers run instances of that image.

#### Details

One of the main problems Docker solves is the classic "it works on my
machine" issue. Different computers may have different versions of
Python, Node.js, system libraries, or other components.

Docker helps reproduce the environment on compatible hosts. CPU
architecture, kernel features, configuration, and external services still
matter; an image is not a guarantee of identical behavior everywhere.

```text
Dockerfile → docker build → Image → docker run → Container
```

### 🇷🇺 Русский

#### Ответ на собеседовании

> Docker собирает и запускает контейнеризированные приложения. Образ содержит файлы и зависимости; контейнеры запускают экземпляры этого образа.

#### Подробнее

Одна из основных проблем, которую решает Docker, — ситуация «у меня
работает, а у тебя нет». Например, у двух разработчиков могут быть
разные версии Python, Node.js, системных библиотек или других
компонентов.

Docker помогает воспроизводить окружение на совместимых хостах.
Архитектура CPU, возможности ядра, настройки и внешние сервисы всё равно
важны: образ не гарантирует одинакового поведения на любой машине.

Упрощенная схема:

```text
Dockerfile → docker build → Image → docker run → Container
```

---

## 2. Why is Docker used? / Зачем нужен Docker?

### 🇬🇧 English

#### Interview answer

> Docker makes application environments more reproducible across development, testing, and deployment. Host compatibility and external configuration still matter.

#### Details

Without containerization, an application may work on one developer's
computer but fail on another because of different dependencies or
runtime versions.

Docker is also commonly used for local development, testing, CI/CD,
deployment, and running multiple isolated services.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Docker делает окружение приложения воспроизводимее при разработке, тестировании и развёртывании. Совместимость хоста и внешние настройки всё равно важны.

#### Подробнее

Без контейнеризации приложение может работать у одного разработчика и не
работать у другого из-за различий в окружении.

Docker также удобен для:

-   локальной разработки;
-   тестирования;
-   CI/CD;
-   развертывания приложений;
-   запуска нескольких изолированных сервисов.

---

## 3. What is containerization? / Что такое контейнеризация?

### 🇬🇧 English

#### Interview answer

> Containerization packages applications for execution in isolated environments. Typical Linux containers share a kernel instead of booting a separate guest OS.

#### Details

A typical Linux container uses namespaces and resource controls to
isolate processes. It shares the kernel with other containers on that
Linux host; this is not an absolute security boundary. Privileged mode
and broad mounts can expose the host.

Image layers are an implementation detail of Docker images, not the
definition of containerization itself.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Контейнеризация подготавливает приложения к запуску в изолированном окружении. Обычные Linux-контейнеры используют общее ядро вместо загрузки отдельной гостевой ОС.

#### Подробнее

Обычный Linux-контейнер использует namespaces и ограничения ресурсов для
изоляции процессов. Он разделяет ядро с другими контейнерами этого
Linux-хоста, но не даёт абсолютной защиты. Привилегированный режим и
широкие монтирования могут открыть доступ к хосту.

Важно не смешивать контейнеризацию со слоями Docker image. Слои — это
механизм хранения и сборки образа, а контейнеризация — более общий
принцип изолированного запуска приложений.

---

## 4. Container vs virtual machine / Чем контейнер отличается от виртуальной машины?

### 🇬🇧 English

#### Interview answer

> A VM normally has its own guest kernel. Linux containers share a kernel and isolate processes, so their overhead is usually lower.

#### Details

Saying that a container "has no OS at all" is too simplistic. An image
may contain a Linux user-space filesystem and tools, but the container
does not boot its own separate kernel like a virtual machine.

Docker Desktop runs Linux containers in a Linux VM on macOS and on Windows
with a Linux backend. They share that VM's Linux kernel, not the macOS or
Windows kernel. Windows containers also have distinct isolation modes.

### 🇷🇺 Русский

#### Ответ на собеседовании

> У VM обычно своё гостевое ядро. Linux-контейнеры используют общее ядро и изолируют процессы, поэтому накладные расходы обычно ниже.

#### Подробнее

Упрощённая схема для обычных Linux-контейнеров и VM:

```text
Virtual Machine:
Hardware
→ Hypervisor (directly or through a host OS)
→ Guest OS
→ Application

Container:
Hardware
→ Host OS
→ Container runtime
→ Container
→ Application
```

Фраза «у контейнера вообще нет ОС» неточна. В image могут находиться
файловая система и пользовательские компоненты Linux-дистрибутива, но
контейнер не загружает собственное отдельное ядро ОС как VM.

В Docker Desktop на macOS и Windows с Linux-бэкендом Linux-контейнеры
работают в Linux-VM и разделяют её ядро, а не ядро macOS или Windows.
У Windows-контейнеров есть отдельные режимы изоляции.

---

## 5. What is a Dockerfile? / Что такое Dockerfile?

### 🇬🇧 English

#### Interview answer

> A Dockerfile is a text recipe for building an image: base image, files, dependencies, and startup defaults.

#### Details

A Dockerfile itself is not a running environment. Docker first reads it
during the image build process.

```dockerfile
FROM python:3.12
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

This assumes `requirements.txt` and `app.py` exist. `RUN` executes during
build; `CMD` supplies a default startup command or arguments and can be
overridden. Use `.dockerignore` to exclude local files and secrets from
the build context. Pinning a tag alone does not make builds immutable.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Dockerfile — текстовая инструкция сборки образа: базовый образ, файлы, зависимости и настройки запуска по умолчанию.

#### Подробнее

Простой пример:

```dockerfile
FROM python:3.12
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

Здесь:

-   `FROM` — выбирает базовый image;
-   `WORKDIR` — задает рабочую директорию;
-   `COPY` — копирует файлы;
-   `RUN` — выполняет команду во время сборки;
-   `CMD` — задает команду, которая будет выполняться при запуске
    контейнера, если её не переопределили.

Dockerfile сам по себе не является работающим окружением. Сначала его
нужно использовать для сборки image.

Пример предполагает наличие `requirements.txt` и `app.py`. `RUN`
выполняется при сборке, а `CMD` задаёт команду или аргументы запуска по
умолчанию. Через `.dockerignore` исключают локальные файлы и секреты из
контекста сборки. Один лишь тег образа не гарантирует неизменность сборок.

---

## 6. What is a Docker image? / Что такое Docker Image?

### 🇬🇧 English

#### Interview answer

> An image is a read-only template containing filesystem layers and configuration. Docker uses it to create containers.

#### Details

The core flow is:

```text
Dockerfile
    ↓ docker build
Docker Image
    ↓ docker run
Container
```

The image is a reusable artifact between the build instructions and the
running container. It can be built once, stored, distributed, and used
to create multiple containers.

An image digest identifies fixed content, while a tag such as `latest`
or `3.12` can later point to different content. Images can be stored in a
registry. `docker images` lists local images.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Образ — шаблон только для чтения, содержащий слои файловой системы и настройки. Docker создаёт из него контейнеры.

#### Подробнее

Главная цепочка:

```text
Dockerfile
    ↓ docker build
Docker Image
    ↓ docker run
Container
```

Image нужен как промежуточный готовый артефакт между инструкцией сборки
и работающим контейнером.

Docker не должен заново выполнять весь Dockerfile каждый раз, когда
нужно запустить приложение. Image можно собрать один раз, сохранить,
передать на другую машину и создать из него любое количество
контейнеров.

Image обычно состоит из нескольких слоев и хранится во внутреннем
хранилище Docker. Его также можно отправить в container registry,
например Docker Hub или GitHub Container Registry.

Список локальных образов можно посмотреть командой:

```bash
docker images
```

Digest идентифицирует конкретное содержимое, а тег вроде `latest` или
`3.12` может позднее указывать на другой образ.

---

## 7. Dockerfile vs image / В чем разница между Dockerfile и Image?

### 🇬🇧 English

#### Interview answer

> A Dockerfile describes how to build; an image is the built artifact. Changing the Dockerfile requires a rebuild to affect new containers.

#### Details

A useful model is:

```text
Dockerfile = recipe
Image      = built template
Container  = instance (running or stopped)
```

Changing the Dockerfile does not automatically modify an existing image.
The image must be rebuilt.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Dockerfile описывает сборку, image — её готовый результат. Чтобы правка Dockerfile попала в новые контейнеры, образ нужно пересобрать.

#### Подробнее

Полезная аналогия:

```text
Dockerfile = рецепт
Image      = приготовленная заготовка
Container  = экземпляр (запущенный или остановленный)
```

Если Dockerfile изменить, уже существующий image сам по себе не
изменится. Чтобы изменения попали в образ, его нужно пересобрать.

---

## 8. What is a container? / Что такое контейнер?

### 🇬🇧 English

#### Interview answer

> A container is an instance of an image with its own configuration and runtime state. It can be running or stopped.

#### Details

Strictly speaking, a container can also exist in a stopped state, so "a
running image" is a useful beginner shorthand rather than a complete
technical definition.

Docker Compose is not required to create multiple containers.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Контейнер — экземпляр образа со своими настройками и состоянием. Он может быть запущен или остановлен.

#### Подробнее

Важно: технически контейнер может существовать и в остановленном
состоянии, поэтому формулировка «контейнер — это только запущенный
image» удобна для первого понимания, но немного упрощена.

Из одного image:

```text
             → Container 1
Image ──────→ Container 2
             → Container 3
```

Docker Compose для этого не обязателен. Несколько контейнеров можно
запускать обычными командами `docker run`.

---

## 9. Image vs container / В чем разница между Image и Container?

### 🇬🇧 English

#### Interview answer

> An image is a reusable template; a container is a particular instance. A container's writable layer does not change the original image.

#### Details

Changes made inside a running container do not automatically modify the
original image.

The writable layer survives stopping and starting the same container,
but is removed when that container is removed. Use volumes or bind
mounts for data that must outlive it; shared mounts can also connect
otherwise separate containers.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Образ — повторно используемый шаблон, контейнер — конкретный экземпляр. Записываемый слой контейнера не меняет исходный образ.

#### Подробнее

Удобно сравнить с программой:

```text
Image     → что должно быть запущено
Container → конкретный экземпляр этого запуска
```

Изменения, возникающие во время работы конкретного контейнера, не
превращают автоматически исходный image в новый образ.

Записываемый слой сохраняется при остановке и запуске того же контейнера,
но удаляется вместе с контейнером. Для более долгого хранения используют
volumes или bind mounts. Общие монтирования могут связывать данные разных
контейнеров, несмотря на отдельное состояние каждого.

---

## 10. How is an image created? What does `docker build` do? / Как создается Docker Image? Что делает `docker build`?

### 🇬🇧 English

#### Interview answer

> docker build processes a Dockerfile and build context to produce an image. Cached build results can avoid repeating unchanged work.

#### Details

For example:

```bash
docker build -t my-app .
```

-   `docker build` starts the build;
-   `-t my-app` assigns a name or tag;
-   `.` uses the current directory as the build context.

### 🇷🇺 Русский

#### Ответ на собеседовании

> docker build обрабатывает Dockerfile и контекст сборки, создавая образ. Кеш помогает не выполнять неизменившиеся шаги заново.

#### Подробнее

Например:

```bash
docker build -t my-app .
```

Здесь:

-   `docker build` — запустить сборку;
-   `-t my-app` — присвоить image имя или tag;
-   `.` — использовать текущую директорию как build context.

После этого можно выполнить:

```bash
docker run my-app
```

Dockerfile нужен во время сборки. Для обычного запуска уже собранного
image Dockerfile не требуется.

---

## 11. How do you run a container? What does `docker run` do? / Как запустить контейнер? Что делает `docker run`?

### 🇬🇧 English

#### Interview answer

> docker run creates and starts a new container from an image. docker start restarts an existing stopped container.

#### Details

For example:

```bash
docker run nginx
```

This creates a new container from the `nginx` image, pulling it if needed
under the default pull policy. It runs in the foreground; `-d` detaches
the CLI. When the main process exits, the container stops unless a restart
policy restarts it. Port publishing is a separate option.

### 🇷🇺 Русский

#### Ответ на собеседовании

> docker run создаёт и запускает новый контейнер из образа. docker start запускает уже существующий остановленный контейнер.

#### Подробнее

Например:

```bash
docker run nginx
```

Docker использует image `nginx` и создает из него новый контейнер.

При стандартной pull policy отсутствующий образ скачивается. Команда
работает на переднем плане; `-d` отсоединяет CLI. После завершения
основного процесса контейнер останавливается, если его не перезапустит
настроенная restart policy.

Важно: `docker run` сам по себе не означает автоматический проброс
портов. Для этого используется, например, `-p`.

---

## 12. Can multiple containers be created from one image? / Можно ли создать несколько контейнеров из одного Image?

### 🇬🇧 English

#### Interview answer

> Yes. One image can create many containers, each with separate runtime state and a writable layer.

#### Details

Compose is not required: repeat `docker run` to create new instances.
Containers can still share volumes or networks. Publishing the same host
address and port twice usually causes a conflict, so choose different
host ports when necessary.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Да. Из одного образа можно создать много контейнеров, у каждого своё состояние выполнения и записываемый слой.

#### Подробнее

Например, один и тот же image веб-приложения может использоваться для
запуска нескольких экземпляров приложения.

Docker Compose упрощает управление несколькими связанными сервисами, но
сам механизм создания нескольких контейнеров от Compose не зависит.

Контейнеры могут использовать общие тома и сети. Повторная публикация
одного адреса и порта хоста обычно вызывает конфликт: при необходимости
выбирают разные порты хоста.

---

## 13. What is a port? / Что такое порт?

### 🇬🇧 English

#### Interview answer

> A TCP or UDP port is a number used to identify a transport endpoint at an IP address. An application process listens on it, not the whole container.

#### Details

The entire container does not "run on a port." A process inside the
container listens on a particular port.

For example, nginx listens on TCP port 80. TCP 80 and UDP 80 are different
endpoints. In bridge mode the container has its own network namespace;
host networking is a different mode.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Порт TCP или UDP — номер транспортной конечной точки по IP-адресу. Его слушает процесс приложения, а не контейнер целиком.

#### Подробнее

Важно: не контейнер целиком «запускается на порту».

В контейнере запускается один или несколько процессов. Конкретное
приложение может слушать сетевой порт.

Например:

```text
Container
└── nginx process
    └── listens on port 80
```

TCP 80 и UDP 80 — разные конечные точки. В режиме bridge контейнер имеет
собственный сетевой namespace; host networking работает иначе. Если
приложение слушает `80` внутри bridge-контейнера, это не означает
автоматической доступности через порт `80` хоста.

---

## 14. What is port mapping or port publishing? / Что значит пробросить или опубликовать порт?

### 🇬🇧 English

#### Interview answer

> Port publishing maps a host address and port to a container port. For example, -p 8080:80 forwards host port 8080 to container port 80.

#### Details

For default bridge networking: `browser → host:8080 → container:80 → nginx`.
This publishes a host port, not a new application listener. On native
Linux, the host may already reach a bridge container by its container IP
without publishing; Docker Desktop networking differs.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Публикация порта связывает адрес и порт хоста с портом контейнера. Например, -p 8080:80 перенаправляет порт 8080 хоста на порт 80 контейнера.

#### Подробнее

Например:

```text
Browser
   ↓
localhost:8080
   ↓
Host port 8080
   ↓ Docker port mapping
Container port 80
   ↓
nginx
```

То есть мы не «запускаем контейнер на порту 80». Внутри контейнера nginx
слушает `80`, а Docker предоставляет путь к этому сервису через
выбранный порт хоста.

На обычном Linux-хосте bridge-контейнер может быть доступен по своему IP
и без публикации. Публикация создаёт доступ через порт хоста; в Docker
Desktop сетевые ограничения отличаются. Схема выше относится к bridge,
а не ко всем сетевым режимам.

---

## 15. What does `docker run -p 8080:80 nginx` mean? / Что означает `docker run -p 8080:80 nginx`?

### 🇬🇧 English

#### Interview answer

> It creates and starts an nginx container and publishes its TCP port 80 on host port 8080. By default, publishing binds all host addresses, not just localhost.

#### Details

The mapping is `HOST_PORT:CONTAINER_PORT`. With a local Docker daemon,
visit `http://localhost:8080`. For a local-only example, use
`docker run -p 127.0.0.1:8080:80 nginx`. Default bind settings can be
changed, and remote accessibility also depends on routing and firewalls.
With a remote daemon, the host port belongs to that remote host.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Команда создаёт и запускает nginx и публикует TCP-порт 80 контейнера на порту 8080 хоста. По умолчанию привязка охватывает все адреса хоста, не только localhost.

#### Подробнее

Разбор:

```text
docker run    -p       8080 : 80       nginx
│             │        │      │        │
│             │        │      │        └─ image
│             │        │      └────────── container port
│             │        └───────────────── host port
│             └────────────────────────── publish/map port
└──────────────────────────────────────── create and run container
```

Обычно после такой команды локально можно обратиться к:

```text
http://localhost:8080
```

Важно: публикация порта не означает автоматически, что сервис доступен
«из всего интернета». Это зависит также от адреса привязки, сети хоста,
firewall, инфраструктуры и других настроек.

Без явно заданного адреса стандартная настройка публикует порт на всех
адресах хоста. Для локального примера: `docker run -p 127.0.0.1:8080:80 nginx`.
Настройку привязки по умолчанию можно изменить. При удалённом Docker
daemon порт относится к удалённому хосту, а не к твоему компьютеру.

---

## 16. What is `EXPOSE` and how is it different from `-p`? / Что такое `EXPOSE` и чем он отличается от `-p`?

### 🇬🇧 English

#### Interview answer

> EXPOSE records the intended container port as image metadata. -p actually publishes a port; EXPOSE alone neither publishes it nor starts a listener.

#### Details

`EXPOSE 80` is not equivalent to `docker run -p 8080:80 my-app`.
You can publish a port with `-p` even without EXPOSE. `-P` publishes
exposed ports on automatically assigned host ports; `-p` uses an explicit
mapping. The application still has to listen on the container port.

### 🇷🇺 Русский

#### Ответ на собеседовании

> EXPOSE записывает предполагаемый порт контейнера в метаданные образа. -p публикует порт; сам EXPOSE не публикует его и не запускает слушающий процесс.

#### Подробнее

```dockerfile
EXPOSE 80
```

не эквивалентно:

```bash
docker run -p 8080:80 my-app
```

Первое описывает предполагаемый внутренний порт. Второе настраивает
публикацию порта при запуске контейнера.

Для `-p` инструкция EXPOSE не обязательна. Ключ `-P` публикует exposed-порты
на автоматически назначенных портах хоста, `-p` задаёт конкретное
сопоставление. Приложение всё равно должно слушать порт контейнера.

---

## 17. What is Docker Compose? / Что такое Docker Compose?

### 🇬🇧 English

#### Interview answer

> Docker Compose defines and manages services, networks, and volumes in a YAML file. docker compose up creates and starts the configured application.

#### Details

For example, a project may contain a frontend, backend, and PostgreSQL
database. Instead of maintaining several long `docker run` commands,
their configuration can be stored in one Compose file.

The modern command is:

```bash
docker compose up
```

The older `docker-compose` spelling belongs to the legacy standalone
tool; use the command supported by the installed Compose version.
Compose also works for a single service.

A schematic file, not a complete runnable application:

```yaml
services:
  web:
    build: .
    ports:
      - "127.0.0.1:8080:80"
  db:
    image: postgres:17
    environment:
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:?Set a local test password}
    volumes:
      - db-data:/var/lib/postgresql/data
volumes:
  db-data:
```

It needs the web Dockerfile, application connection settings, and a local
test password. Do not commit real credentials. Starting a database does
not mean it is ready: use a healthcheck and `depends_on` with
`condition: service_healthy` when needed, plus application retry handling.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Docker Compose описывает сервисы, сети и тома в YAML-файле и управляет ими. docker compose up создаёт и запускает настроенное приложение.

#### Подробнее

Например, проект может состоять из:

```text
Frontend
Backend
PostgreSQL
```

Вместо нескольких длинных `docker run` конфигурация описывается в одном
файле. Это схема, а не готовое запускаемое приложение:

``` yaml
services:
  web:
    build: .
    ports:
      - "127.0.0.1:8080:80"

  db:
    image: postgres:17
    environment:
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:?Set a local test password}
    volumes:
      - db-data:/var/lib/postgresql/data
volumes:
  db-data:
```

Потребуются Dockerfile веб-приложения, его настройки подключения и
локальный тестовый пароль. Реальные секреты коммитить нельзя.
После настройки сервисы запускают командой:

```bash
docker compose up
```

Современная команда — `docker compose` с пробелом. Старое отдельное
приложение и команда часто встречаются как `docker-compose`.

Compose работает и с одним сервисом. Запуск БД ещё не означает готовность:
при необходимости используют healthcheck и `depends_on` с
`condition: service_healthy`, а приложение должно обрабатывать повторы.
Секрет через environment в примере — упрощение для локального теста,
не рекомендация для production. Путь тома здесь относится к postgres:17.

---

## 18. Docker Compose vs `docker run` / Чем Docker Compose отличается от `docker run`?

### 🇬🇧 English

#### Interview answer

> docker run creates one container using CLI options. Compose stores service configuration in YAML and manages related containers together.

#### Details

Both approaches can start many containers; Compose is not mandatory for
that. It also manages shared networks and volumes. `docker compose up`
reconciles service configuration and may recreate changed containers;
`docker compose start` starts existing stopped containers.

### 🇷🇺 Русский

#### Ответ на собеседовании

> docker run создаёт один контейнер с параметрами CLI. Compose хранит настройки сервисов в YAML и управляет связанными контейнерами вместе.

#### Подробнее

Compose не является обязательным условием для нескольких контейнеров.

Можно написать:

```bash
docker run ...
docker run ...
docker run ...
```

Но по мере роста количества портов, volumes, environment variables и
сетевых настроек такие команды становятся неудобными.

Compose сохраняет эту конфигурацию как код:

```text
docker run → параметры в CLI
Docker Compose → параметры в compose.yaml
```

`docker compose up` приводит сервисы к описанной конфигурации и может
пересоздать изменённые контейнеры. `docker compose start` запускает уже
существующие остановленные контейнеры.

---

## 19. Why use Docker Compose? / Зачем нужен Docker Compose?

### 🇬🇧 English

#### Interview answer

> Compose makes a multi-service setup repeatable and easy to share. One file captures the configuration instead of several long run commands.

#### Details

A backend and database can share declared networks, volumes, environment
settings, and healthchecks. `depends_on` in its short form controls startup
order, not application readiness. Compose does not automatically provide
the distributed scheduling and recovery guarantees of a cluster platform.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Compose делает запуск нескольких сервисов воспроизводимым и удобным для команды. Настройки хранятся в одном файле вместо нескольких длинных команд.

#### Подробнее

Он помогает описать:

-   какие сервисы нужны;
-   из каких images они запускаются;
-   какие порты публикуются;
-   какие переменные окружения передаются;
-   какие volumes используются;
-   в каких сетях работают сервисы.

Краткая форма `depends_on` задаёт порядок запуска, но не проверяет
готовность приложения. Compose сам по себе не даёт распределённого
размещения и восстановления, как кластерная платформа.

---

## 20. What is a runtime? / Что такое runtime?

### 🇬🇧 English

#### Interview answer

> A runtime provides what a program needs to execute, such as Python's interpreter or the JVM. A container runtime is software that starts and manages containers.

#### Details

The word `runtime` can also mean the period when a program is executing:

```text
at runtime
```

as opposed to:

```text
at build time
```

In Docker discussions, `container runtime` is another related term
referring to software responsible for running and managing containers at
a lower level.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Runtime обеспечивает выполнение программы: например, интерпретатор Python или JVM. Container runtime — ПО для запуска и управления контейнерами.

#### Подробнее

Слово `runtime` используется в нескольких близких значениях.

##### 1. Runtime как период выполнения

Фраза:

```text
at runtime
```

означает:

> во время выполнения программы

В противоположность, например:

```text
at build time
```

— во время сборки.

##### 2. Runtime environment

Это среда, в которой выполняется программа.

Примеры:

```text
Python → Python interpreter/runtime
Java → JVM
JavaScript server application → Node.js
```

##### 3. Container runtime

В Docker-контексте можно встретить и отдельное понятие
`container runtime` — программный компонент, отвечающий за
непосредственный запуск и управление контейнерами на низком уровне.

Поэтому на интервью важно понимать контекст вопроса.

---

## 21. What are dependencies? / Что такое dependencies?

### 🇬🇧 English

#### Interview answer

> Dependencies are components an application needs, such as libraries or packages. Specifying their versions helps reproduce the environment.

#### Details

For example, a Python application may depend on Flask or requests. A
dependency is a component, not its version. Pin and test compatible
versions, including transitive dependencies; lockfiles or constraints
help. Pinning does not replace security updates or vulnerability checks.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Зависимости — компоненты, необходимые приложению, например библиотеки и пакеты. Указание версий помогает воспроизводить окружение.

#### Подробнее

Например, Python-приложение может использовать:

```text
Flask
requests
pandas
```

Это его зависимости.

Закрепляй и проверяй совместимые версии, включая транзитивные зависимости;
для этого полезны lockfiles или constraints. Закрепление не заменяет
обновлений безопасности и проверки уязвимостей.

Важно не говорить, что dependency — это просто «версия программы».
Dependency — сам внешний компонент, а версия определяет, какой именно
его вариант нужен.

---

## 22. What is a Docker image layer? / Что такое layer в Docker Image?

### 🇬🇧 English

#### Interview answer

> An image layer records filesystem changes. Layers can be shared and reused; not every Dockerfile instruction adds a filesystem layer.

#### Details

A layer is not the same thing as a dependency.

Different images can share base layers; a base image itself often contains
several layers. `COPY` and `RUN` commonly change the filesystem, while
`CMD` and `EXPOSE` set metadata. Cache reuse depends on instruction inputs
and cache validity, not only identical Dockerfile text.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Слой образа хранит изменения файловой системы. Слои можно переиспользовать; не каждая инструкция Dockerfile добавляет файловый слой.

#### Подробнее

Layer — это **не dependency**.

Например:

```dockerfile
FROM python:3.12
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
```

Упрощенно image можно представить так:

```text
Layer 4 → application files
Layer 3 → installed Python packages
Layer 2 → requirements.txt
Base    → Python image (usually multiple layers)
```

Слои дают два важных преимущества:

1.  **Кэширование.** Если входы шага не изменились и кеш пригоден, Docker
    может использовать результат повторно. Одного совпадения текста
    Dockerfile недостаточно.
2.  **Переиспользование.** Разные images могут использовать общие
    базовые слои.

Не буквально каждая инструкция Dockerfile создает файловый слой, поэтому
на собеседовании безопаснее говорить: **многие инструкции сборки
формируют слои image**.

Например, `COPY` и `RUN` обычно меняют файловую систему, а `CMD` и
`EXPOSE` записывают метаданные. Базовый Python-образ сам обычно состоит
из нескольких слоёв, а не из одного.

---

## Core flow / Главная схема

### 🇬🇧 English

The most important flow:

```text
Dockerfile
    │
    │ docker build
    ▼
Docker Image
    │
    │ docker run
    ▼
Container
    │
    ▼
Application process
```

For a network application:

```text
Browser
    │
    │ localhost:8080
    ▼
Host port 8080
    │
    │ Docker port mapping
    ▼
Container port 80
    │
    ▼
nginx
```

For multiple services:

```text
compose.yaml
    │
    │ docker compose up
    ▼
┌─────────────┐
│ Frontend    │
├─────────────┤
│ Backend     │
├─────────────┤
│ Database    │
└─────────────┘
```

### 🇷🇺 Русский

Самая важная цепочка:

```text
Dockerfile
    │
    │ docker build
    ▼
Docker Image
    │
    │ docker run
    ▼
Container
    │
    ▼
Application process
```

Для сетевого приложения:

```text
Browser
    │
    │ localhost:8080
    ▼
Host port 8080
    │
    │ Docker port mapping
    ▼
Container port 80
    │
    ▼
nginx
```

Для нескольких сервисов:

```text
compose.yaml
    │
    │ docker compose up
    ▼
┌─────────────┐
│ Frontend    │
├─────────────┤
│ Backend     │
├─────────────┤
│ Database    │
└─────────────┘
```

---

## Interview minimum / Минимум, который стоит помнить перед собеседованием

### 🇬🇧 English

```text
Docker         → containerization platform
Dockerfile     → build instructions
docker build   → builds an image
Image          → immutable template
docker run     → creates and starts a container
Container      → instance of an image
-p 8080:80     → host 8080 → container 80
Docker Compose → configuration and orchestration of related services
Runtime        → program execution environment
Dependencies   → components required by an application
Layers         → parts of a Docker image created during the build
```

### 🇷🇺 Русский

```text
Docker        → платформа контейнеризации
Dockerfile    → инструкция сборки
docker build  → собирает image
Image         → неизменяемый шаблон
docker run    → создает и запускает container
Container     → экземпляр image
-p 8080:80    → host 8080 → container 80
Docker Compose → конфигурация и запуск связанных сервисов
Runtime       → среда выполнения программы
Dependencies  → компоненты, необходимые приложению
Layers        → части Docker image, формируемые при сборке
```

## References / Источники

Technical review: 2026-11-03. / Техническая проверка: 2026-11-03.

- [Containers and VMs](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/), [Docker Desktop VM](https://docs.docker.com/desktop/troubleshoot-and-support/faqs/linuxfaqs/), [container storage](https://docs.docker.com/engine/storage/).
- [Dockerfile reference](https://docs.docker.com/reference/dockerfile/), [image layers](https://docs.docker.com/get-started/docker-concepts/building-images/understanding-image-layers/), [docker run](https://docs.docker.com/engine/containers/run/).
- [Port publishing](https://docs.docker.com/engine/network/port-publishing/), [Compose startup order](https://docs.docker.com/compose/how-tos/startup-order/), [PostgreSQL official image](https://hub.docker.com/_/postgres).
