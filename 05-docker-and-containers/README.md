# Docker for Technical Writer Interviews

A cheat sheet on core Docker and container topics for junior and middle technical writer interviews.

It covers the practical basics: Docker, containerization, Dockerfile, images, containers, build and run workflows, ports, Docker Compose, runtime, dependencies, and layers.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — quick recall, interview answer, details.
- 🇷🇺 **Русский** — быстро вспомнить, ответ на собеседовании, подробнее.

---

## 1. What is Docker? / Что такое Docker?

### 🇬🇧 English

#### Quick recall

**Docker is a platform for containerizing and running applications in
isolated containers. It packages an application with the environment and
dependencies it needs so it can run consistently on different
machines.**

#### Interview answer

> Docker is a containerization platform. It lets us package an
> application and its required dependencies into a Docker image and then
> run isolated containers from that image in a predictable environment.

#### Details

One of the main problems Docker solves is the classic "it works on my
machine" issue. Different computers may have different versions of
Python, Node.js, system libraries, or other components.

Docker lets us define the required environment and reproduce it on
another machine where Docker is available.

```text
Dockerfile → docker build → Image → docker run → Container
```

### 🇷🇺 Русский

#### Быстро вспомнить

**Docker — это платформа для контейнеризации и запуска приложений в
изолированных контейнерах. Она позволяет упаковать приложение вместе с
необходимым окружением и зависимостями, чтобы оно одинаково запускалось
на разных машинах.**

#### Ответ на собеседовании

> Docker — это платформа для контейнеризации приложений. С ее помощью
> приложение и необходимые ему зависимости можно упаковать в Docker
> image, а затем запускать из этого образа изолированные контейнеры с
> предсказуемым окружением.

#### Подробнее

Одна из основных проблем, которую решает Docker, — ситуация «у меня
работает, а у тебя нет». Например, у двух разработчиков могут быть
разные версии Python, Node.js, системных библиотек или других
компонентов.

Docker позволяет заранее определить окружение приложения и
воспроизводить его на другой машине, где установлен Docker.

Упрощенная схема:

```text
Dockerfile → docker build → Image → docker run → Container
```

---

## 2. Why is Docker used? / Зачем нужен Docker?

### 🇬🇧 English

#### Quick recall

**Docker provides reproducible environments: an application runs with
the runtime, libraries, and other dependencies it was prepared for.**

#### Interview answer

> Docker helps reduce differences between developer machines, test
> environments, and servers. We define the application environment,
> build an image, and can run containers from the same image in
> different environments.

#### Details

Without containerization, an application may work on one developer's
computer but fail on another because of different dependencies or
runtime versions.

Docker is also commonly used for local development, testing, CI/CD,
deployment, and running multiple isolated services.

### 🇷🇺 Русский

#### Быстро вспомнить

**Docker нужен для воспроизводимого окружения: приложение запускается с
теми версиями runtime, библиотек и других зависимостей, для которых оно
было подготовлено.**

#### Ответ на собеседовании

> Docker помогает избежать различий между окружениями разработчиков,
> тестовыми стендами и серверами. Мы описываем окружение приложения,
> собираем image и можем запускать контейнеры из одного и того же образа
> в разных местах.

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

#### Quick recall

**Containerization is a way to package and run an application with its
dependencies in an isolated environment called a container.**

#### Interview answer

> Containerization is an approach where an application and its required
> environment are prepared so the application can run consistently in
> isolated containers across different machines.

#### Details

A container isolates an application from other processes and
applications on the host, but it does not require a separate full guest
operating system like a virtual machine does.

Image layers are an implementation detail of Docker images, not the
definition of containerization itself.

### 🇷🇺 Русский

#### Быстро вспомнить

**Контейнеризация — это способ упаковать и запускать приложение с его
зависимостями в изолированной среде — контейнере.**

#### Ответ на собеседовании

> Контейнеризация — это подход, при котором приложение и необходимое
> ему окружение подготавливаются так, чтобы приложение можно было
> запускать в изолированных контейнерах одинаковым образом на разных
> машинах.

#### Подробнее

Контейнер изолирует приложение от других процессов и приложений на
хосте, но при этом не требует отдельной полноценной гостевой ОС, как
виртуальная машина.

Важно не смешивать контейнеризацию со слоями Docker image. Слои — это
механизм хранения и сборки образа, а контейнеризация — более общий
принцип изолированного запуска приложений.

---

## 4. Container vs virtual machine / Чем контейнер отличается от виртуальной машины?

### 🇬🇧 English

#### Quick recall

**A virtual machine runs a full guest OS with its own kernel, while
containers share the host OS kernel. This usually makes containers
lighter and faster to start.**

#### Interview answer

> A virtual machine virtualizes a complete machine and normally includes
> a separate guest operating system. A container isolates application
> processes while sharing the host OS kernel, so it usually requires
> fewer resources and starts faster.

#### Details

Saying that a container "has no OS at all" is too simplistic. An image
may contain a Linux user-space filesystem and tools, but the container
does not boot its own separate kernel like a virtual machine.

### 🇷🇺 Русский

#### Быстро вспомнить

**Виртуальная машина запускает полноценную гостевую ОС со своим ядром, а
контейнеры используют ядро хостовой ОС. Поэтому контейнеры обычно легче
и быстрее запускаются.**

#### Ответ на собеседовании

> Виртуальная машина виртуализирует целую машину и обычно содержит
> отдельную гостевую операционную систему. Контейнер изолирует процессы
> приложения, но использует ядро хостовой ОС, поэтому требует меньше
> ресурсов и быстрее запускается.

#### Подробнее

Упрощенно:

```text
Virtual Machine:
Hardware
→ Host OS
→ Hypervisor
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

---

## 5. What is a Dockerfile? / Что такое Dockerfile?

### 🇬🇧 English

#### Quick recall

**A Dockerfile is a text file containing instructions Docker uses to
build an image. It is the build recipe, not the image itself and not a
container.**

#### Interview answer

> A Dockerfile is a file containing a sequence of instructions for
> building a Docker image. It can define a base image, copy application
> files, install dependencies, and specify the command used to start the
> application.

#### Details

A Dockerfile itself is not a running environment. Docker first reads it
during the image build process.

### 🇷🇺 Русский

#### Быстро вспомнить

**Dockerfile — это текстовый файл с инструкциями, по которым Docker
собирает image. Это рецепт сборки, а не сам образ и не контейнер.**

#### Ответ на собеседовании

> Dockerfile — это файл с последовательностью инструкций для сборки
> Docker image. В нем можно указать базовый image, скопировать файлы
> приложения, установить зависимости и определить команду запуска.

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
    контейнера.

Dockerfile сам по себе не является работающим окружением. Сначала его
нужно использовать для сборки image.

---

## 6. What is a Docker image? / Что такое Docker Image?

### 🇬🇧 English

#### Quick recall

**A Docker image is a ready-made immutable template used to create
containers. It is a build artifact containing the application's
filesystem, dependencies, and metadata required to run it.**

#### Interview answer

> A Docker image is an immutable template for creating containers. It is
> commonly built from a Dockerfile using `docker build` and contains the
> application, required files and dependencies, and information about
> how it should run.

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

### 🇷🇺 Русский

#### Быстро вспомнить

**Docker image — это готовый неизменяемый шаблон, из которого Docker
создает контейнеры. Он является результатом сборки и содержит файловую
систему приложения, зависимости и метаданные, необходимые для запуска.**

#### Ответ на собеседовании

> Docker image — это неизменяемый шаблон для создания контейнеров.
> Обычно он собирается по Dockerfile командой `docker build` и содержит
> приложение, необходимые файлы и зависимости, а также информацию о том,
> как его запускать.

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

---

## 7. Dockerfile vs image / В чем разница между Dockerfile и Image?

### 🇬🇧 English

#### Quick recall

**A Dockerfile describes how to build the environment, while an image is
the already-built result of those instructions.**

#### Interview answer

> A Dockerfile is source text containing build instructions. A Docker
> image is the resulting artifact produced by `docker build`. When
> starting a container, Docker uses the image rather than rebuilding the
> Dockerfile every time.

#### Details

A useful model is:

```text
Dockerfile = recipe
Image      = built template
Container  = running instance
```

Changing the Dockerfile does not automatically modify an existing image.
The image must be rebuilt.

### 🇷🇺 Русский

#### Быстро вспомнить

**Dockerfile говорит, как собрать окружение, а image — уже собранный
результат этих инструкций.**

#### Ответ на собеседовании

> Dockerfile — это исходный текст с инструкциями сборки. Docker image
> — готовый артефакт, полученный после выполнения этих инструкций
> командой `docker build`. При запуске Docker использует image, а не
> заново читает Dockerfile.

#### Подробнее

Полезная аналогия:

```text
Dockerfile = рецепт
Image      = приготовленная заготовка
Container  = запущенный экземпляр этой заготовки
```

Если Dockerfile изменить, уже существующий image сам по себе не
изменится. Чтобы изменения попали в образ, его нужно пересобрать.

---

## 8. What is a container? / Что такое контейнер?

### 🇬🇧 English

#### Quick recall

**A container is an instance of a Docker image created to run an
application. An image is the template; a container is a specific
isolated environment created from it.**

#### Interview answer

> A container is an isolated instance of a Docker image in which an
> application can run. Multiple independent containers can be created
> from the same image.

#### Details

Strictly speaking, a container can also exist in a stopped state, so "a
running image" is a useful beginner shorthand rather than a complete
technical definition.

Docker Compose is not required to create multiple containers.

### 🇷🇺 Русский

#### Быстро вспомнить

**Контейнер — это экземпляр Docker image, созданный для выполнения
приложения. Image — шаблон, container — конкретная изолированная
среда, созданная из него.**

#### Ответ на собеседовании

> Контейнер — это изолированный экземпляр Docker image, в котором
> выполняется приложение. Из одного image можно создавать и запускать
> несколько независимых контейнеров.

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

#### Quick recall

**An image is an immutable template; a container is an instance created
from that template. One image can be used to create many containers.**

#### Interview answer

> A Docker image stores the prepared environment and acts as a template.
> `docker run` creates a specific container from that image and starts
> the application's process inside it.

#### Details

Changes made inside a running container do not automatically modify the
original image.

### 🇷🇺 Русский

#### Быстро вспомнить

**Image — неизменяемый шаблон, container — созданный из него
экземпляр. Один image можно использовать для создания множества
контейнеров.**

#### Ответ на собеседовании

> Docker image хранит подготовленное окружение и используется как
> шаблон. `docker run` создает из него конкретный контейнер и запускает
> процесс приложения внутри этого контейнера.

#### Подробнее

Удобно сравнить с программой:

```text
Image     → что должно быть запущено
Container → конкретный экземпляр этого запуска
```

Изменения, возникающие во время работы конкретного контейнера, не
превращают автоматически исходный image в новый образ.

---

## 10. How is an image created? What does `docker build` do? / Как создается Docker Image? Что делает `docker build`?

### 🇬🇧 English

#### Quick recall

**`docker build` reads a Dockerfile and builds a Docker image from its
instructions. The resulting image is stored locally and can then be used
to create containers.**

#### Interview answer

> During `docker build`, Docker reads the Dockerfile and build context,
> executes the build instructions, and creates an image. Build results
> can be cached, making subsequent builds faster.

#### Details

For example:

```bash
docker build -t my-app .
```

-   `docker build` starts the build;
-   `-t my-app` assigns a name or tag;
-   `.` uses the current directory as the build context.

### 🇷🇺 Русский

#### Быстро вспомнить

**`docker build` читает Dockerfile и собирает по его инструкциям Docker
image. Результат сборки сохраняется локально и затем может
использоваться для создания контейнеров.**

#### Ответ на собеседовании

> При `docker build` Docker получает Dockerfile и build context,
> выполняет инструкции сборки и создает image. Результаты шагов могут
> кэшироваться, поэтому повторная сборка часто выполняется быстрее.

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

#### Quick recall

**`docker run` creates a new container from the specified image and
starts its configured process. Ports are published only when explicitly
requested.**

#### Interview answer

> To run a container, we use `docker run <image>`. Docker creates a
> container from the image, applies the requested configuration, and
> starts the application command defined in the image or provided by the
> user.

#### Details

For example:

```bash
docker run nginx
```

This creates a new container from the `nginx` image. Port publishing is
a separate option.

### 🇷🇺 Русский

#### Быстро вспомнить

**`docker run` создает новый контейнер из указанного image и запускает в
нем настроенный процесс. Порты публикуются только если это отдельно
указано параметрами команды.**

#### Ответ на собеседовании

> Для запуска контейнера используется `docker run <image>`. Docker
> создает контейнер из image, применяет переданные настройки и запускает
> команду приложения, определенную в image или указанную пользователем.

#### Подробнее

Например:

```bash
docker run nginx
```

Docker использует image `nginx` и создает из него новый контейнер.

Важно: `docker run` сам по себе не означает автоматический проброс
портов. Для этого используется, например, `-p`.

---

## 12. Can multiple containers be created from one image? / Можно ли создать несколько контейнеров из одного Image?

### 🇬🇧 English

#### Quick recall

**Yes. An image is a template, so multiple independent containers can be
created from the same image. Docker Compose is not required for this.**

#### Interview answer

> Yes, multiple containers can be created from the same Docker image.
> Each container is a separate instance with its own runtime state while
> sharing the same image as its base.

### 🇷🇺 Русский

#### Быстро вспомнить

**Да. Image — это шаблон, поэтому из одного и того же image можно
создать любое количество независимых контейнеров. Docker Compose для
этого не обязателен.**

#### Ответ на собеседовании

> Да, из одного Docker image можно создавать несколько контейнеров.
> Каждый контейнер является отдельным экземпляром с собственным
> состоянием выполнения, хотя все они основаны на одном image.

#### Подробнее

Например, один и тот же image веб-приложения может использоваться для
запуска нескольких экземпляров приложения.

Docker Compose упрощает управление несколькими связанными сервисами, но
сам механизм создания нескольких контейнеров от Compose не зависит.

---

## 13. What is a port? / Что такое порт?

### 🇬🇧 English

#### Quick recall

**A port is a numeric network address used to identify a particular
service or process on a machine. An application listens on a port to
accept network connections.**

#### Interview answer

> An IP address identifies a machine, while a port identifies a
> particular network service on that machine. For example, a web server
> inside a container may listen on port `80`.

#### Details

The entire container does not "run on a port." A process inside the
container listens on a particular port.

### 🇷🇺 Русский

#### Быстро вспомнить

**Порт — это числовой сетевой адрес конкретного сервиса или процесса
на машине. Приложение слушает определенный порт, чтобы принимать сетевые
соединения.**

#### Ответ на собеседовании

> IP-адрес позволяет определить машину, а номер порта — конкретный
> сетевой сервис на этой машине. Например, веб-сервер внутри контейнера
> может слушать порт `80`.

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

У контейнера есть собственное сетевое окружение. Если приложение внутри
него слушает `80`, это еще не означает, что тот же сервис автоматически
доступен через порт `80` хост-компьютера.

---

## 14. What is port mapping or port publishing? / Что значит пробросить или опубликовать порт?

### 🇬🇧 English

#### Quick recall

**Port mapping connects a host port to a container port. Traffic sent to
the published host port is forwarded to the application listening on the
corresponding port inside the container.**

#### Interview answer

> A container has its own network environment, so an application's
> internal port is not automatically available through the host. With
> `-p`, we can publish it, for example by mapping host port `8080` to
> container port `80`.

### 🇷🇺 Русский

#### Быстро вспомнить

**Проброс порта связывает порт хост-машины с портом контейнера. Запрос,
пришедший на опубликованный порт хоста, Docker направляет приложению,
которое слушает соответствующий порт внутри контейнера.**

#### Ответ на собеседовании

> Контейнер имеет собственное сетевое окружение, поэтому внутренний порт
> приложения не обязательно доступен с хоста. С помощью `-p` можно
> опубликовать порт контейнера: например, связать порт `8080` хоста с
> портом `80` контейнера.

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

---

## 15. What does `docker run -p 8080:80 nginx` mean? / Что означает `docker run -p 8080:80 nginx`?

### 🇬🇧 English

#### Quick recall

**The command creates and starts a container from the `nginx` image and
maps host port `8080` to container port `80`. A request to
`localhost:8080` reaches nginx listening on port `80` inside the
container.**

#### Interview answer

> `docker run` creates and starts the container, `-p` publishes a port,
> `8080` is the host port, `80` is the container port, and `nginx` is
> the image name. Traffic sent to host port `8080` is forwarded to port
> `80` in the container.

### 🇷🇺 Русский

#### Быстро вспомнить

**Команда создает и запускает контейнер из image `nginx` и связывает
порт `8080` хоста с портом `80` контейнера. Обращение к `localhost:8080`
попадает в nginx, который внутри контейнера слушает `80`.**

#### Ответ на собеседовании

> `docker run` создает и запускает контейнер, `-p` публикует порт,
> `8080` — порт хоста, `80` — порт контейнера, а `nginx` — имя
> image. Поэтому запрос на порт `8080` хоста Docker перенаправит на порт
> `80` контейнера, где nginx принимает HTTP-запросы.

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

---

## 16. What is `EXPOSE` and how is it different from `-p`? / Что такое `EXPOSE` и чем он отличается от `-p`?

### 🇬🇧 English

#### Quick recall

**`EXPOSE` documents the port an application is expected to use inside
the container, but it does not publish that port on the host by itself.
`-p` creates the actual host-to-container port mapping.**

#### Interview answer

> `EXPOSE 80` documents that the application is expected to listen on
> port `80` inside the image. To make it available through a host port,
> we use `docker run -p`, for example `-p 8080:80`.

### 🇷🇺 Русский

#### Быстро вспомнить

**`EXPOSE` в Dockerfile указывает, какой порт приложение предполагает
использовать внутри контейнера, но сам по себе не публикует его на
хосте. `-p` реально создает сопоставление порта хоста и контейнера.**

#### Ответ на собеседовании

> `EXPOSE 80` документирует, что приложение внутри image ожидается на
> порту `80`. Чтобы сделать этот порт доступным через конкретный порт
> хоста, при запуске используется `docker run -p`, например
> `-p 8080:80`.

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

---

## 17. What is Docker Compose? / Что такое Docker Compose?

### 🇬🇧 English

#### Quick recall

**Docker Compose lets us declaratively define and run multiple related
containers or services together. Their configuration is stored in a YAML
file.**

#### Interview answer

> Docker Compose is used for multi-service applications. A
> `compose.yaml` file can define images or builds, ports, environment
> variables, volumes, networks, and service relationships, and the
> services can then be managed as one application.

#### Details

For example, a project may contain a frontend, backend, and PostgreSQL
database. Instead of maintaining several long `docker run` commands,
their configuration can be stored in one Compose file.

The modern command is:

```bash
docker compose up
```

The older `docker-compose` spelling is still commonly seen.

### 🇷🇺 Русский

#### Быстро вспомнить

**Docker Compose позволяет декларативно описать и вместе запускать
несколько связанных контейнеров или сервисов. Их конфигурация хранится в
YAML-файле.**

#### Ответ на собеседовании

> Docker Compose используется для приложений из нескольких сервисов. В
> `compose.yaml` можно описать images или правила сборки, порты,
> переменные окружения, volumes, сети и зависимости между сервисами, а
> затем управлять ими как единым приложением.

#### Подробнее

Например, проект может состоять из:

```text
Frontend
Backend
PostgreSQL
```

Вместо нескольких длинных `docker run` конфигурация описывается в одном
файле:

``` yaml
services:
  web:
    build: .
    ports:
      - "8080:80"

  db:
    image: postgres
```

После этого сервисы можно запустить командой:

```bash
docker compose up
```

Современная команда — `docker compose` с пробелом. Старое отдельное
приложение и команда часто встречаются как `docker-compose`.

---

## 18. Docker Compose vs `docker run` / Чем Docker Compose отличается от `docker run`?

### 🇬🇧 English

#### Quick recall

**`docker run` is convenient for starting and configuring individual
containers from the command line. Docker Compose is more convenient when
configuration for multiple related services needs to be stored and
reproduced.**

#### Interview answer

> With `docker run`, containers can be started manually with
> command-line options. Docker Compose stores application configuration
> in a YAML file and makes it easy to start multiple related services
> consistently with one command.

### 🇷🇺 Русский

#### Быстро вспомнить

**`docker run` удобно использовать для запуска и настройки отдельного
контейнера из командной строки. Docker Compose удобнее, когда нужно
хранить конфигурацию нескольких связанных сервисов и запускать их
вместе.**

#### Ответ на собеседовании

> Через `docker run` можно вручную запускать отдельные контейнеры и
> передавать им параметры. Docker Compose позволяет описать конфигурацию
> приложения в YAML-файле и воспроизводимо запускать несколько связанных
> сервисов одной командой.

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

---

## 19. Why use Docker Compose? / Зачем нужен Docker Compose?

### 🇬🇧 English

#### Quick recall

**Docker Compose avoids keeping a multi-container application's
configuration in a collection of long `docker run` commands. It makes
service configuration explicit, reproducible, and easier to share.**

#### Interview answer

> Compose is especially useful for local development and testing of
> multi-service applications. For example, a backend, database, and
> other services can be defined in one configuration and started
> together with `docker compose up`.

### 🇷🇺 Русский

#### Быстро вспомнить

**Docker Compose нужен, чтобы не хранить конфигурацию многоконтейнерного
приложения в наборе длинных команд `docker run`. Он делает конфигурацию
сервисов явной, повторяемой и удобной для командной работы.**

#### Ответ на собеседовании

> Compose особенно полезен для локальной разработки и тестирования
> приложений из нескольких сервисов. Например, можно одной конфигурацией
> определить backend, database и другие сервисы, их порты и окружение, а
> затем запустить все командой `docker compose up`.

#### Подробнее

Он помогает описать:

-   какие сервисы нужны;
-   из каких images они запускаются;
-   какие порты публикуются;
-   какие переменные окружения передаются;
-   какие volumes используются;
-   в каких сетях работают сервисы.

---

## 20. What is a runtime? / Что такое runtime?

### 🇬🇧 English

#### Quick recall

**A runtime, when referring to a runtime environment, is the software
environment required to execute a program. For example, Python, Node.js,
and the JVM provide execution environments for their respective code.**

#### Interview answer

> A runtime is an execution environment that provides the mechanisms and
> components required to run a program. For example, Python code needs
> the Python interpreter, Java bytecode runs on the JVM, and server-side
> JavaScript can run in Node.js.

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

#### Быстро вспомнить

**Runtime в значении среды выполнения — это программная среда,
необходимая для выполнения программы. Например, Python interpreter,
Node.js или JVM обеспечивают выполнение соответствующего кода.**

#### Ответ на собеседовании

> Runtime — это среда выполнения, которая предоставляет механизм и
> необходимые компоненты для запуска программы. Например, Python-коду
> нужен интерпретатор Python, Java bytecode выполняется JVM, а
> JavaScript вне браузера может выполняться в Node.js.

#### Подробнее

Слово `runtime` используется в нескольких близких значениях.

### 1. Runtime как период выполнения

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

### 2. Runtime environment

Это среда, в которой выполняется программа.

Примеры:

```text
Python → Python interpreter/runtime
Java → JVM
JavaScript server application → Node.js
```

### 3. Container runtime

В Docker-контексте можно встретить и отдельное понятие
`container runtime` — программный компонент, отвечающий за
непосредственный запуск и управление контейнерами на низком уровне.

Поэтому на интервью важно понимать контекст вопроса.

---

## 21. What are dependencies? / Что такое dependencies?

### 🇬🇧 English

#### Quick recall

**Dependencies are external libraries, packages, or other components an
application relies on. A dependency's version is a property of the
dependency, not the dependency itself.**

#### Interview answer

> Dependencies are components an application requires to work, such as
> libraries and packages. Docker helps create a predictable environment
> where the required dependencies are installed in the expected
> versions.

### 🇷🇺 Русский

#### Быстро вспомнить

**Dependencies — это внешние библиотеки, пакеты и другие компоненты,
от которых зависит работа приложения. Версия зависимости —
характеристика зависимости, а не сама зависимость.**

#### Ответ на собеседовании

> Dependencies — это компоненты, которые приложение использует для
> своей работы, например библиотеки и пакеты. Docker помогает
> подготовить предсказуемое окружение, в котором нужные зависимости
> установлены в ожидаемых версиях.

#### Подробнее

Например, Python-приложение может использовать:

```text
Flask
requests
pandas
```

Это его зависимости.

Версии:

```text
Flask==3.0.0
requests==2.32.0
```

позволяют точнее зафиксировать окружение.

Важно не говорить, что dependency — это просто «версия программы».
Dependency — сам внешний компонент, а версия определяет, какой именно
его вариант нужен.

---

## 22. What is a Docker image layer? / Что такое layer в Docker Image?

### 🇬🇧 English

#### Quick recall

**A Docker image consists of layers — immutable filesystem parts
created during the build process. Many Dockerfile instructions result in
a new image layer.**

#### Interview answer

> A layer is a part of a Docker image representing filesystem changes
> from a particular build step. Docker can reuse cached layers, which
> can make subsequent builds faster.

#### Details

A layer is not the same thing as a dependency.

Layers provide caching and reuse. Different images can also share common
base layers.

### 🇷🇺 Русский

#### Быстро вспомнить

**Docker image состоит из слоев — неизменяемых частей файловой
системы, создаваемых в процессе сборки. Многие инструкции Dockerfile
приводят к созданию нового слоя.**

#### Ответ на собеседовании

> Layer — это часть Docker image, представляющая изменения файловой
> системы на определенном этапе сборки. Docker может переиспользовать
> уже созданные слои из кэша, поэтому повторные сборки могут выполняться
> быстрее.

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
Layer 1 → base Python image
```

Слои дают два важных преимущества:

1.  **Кэширование.** Если ранние инструкции не изменились, Docker может
    использовать их результат повторно.
2.  **Переиспользование.** Разные images могут использовать общие
    базовые слои.

Не буквально каждая инструкция Dockerfile создает файловый слой, поэтому
на собеседовании безопаснее говорить: **многие инструкции сборки
формируют слои image**.

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
