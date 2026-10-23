# Technical English: Common Sentence Patterns

Шпаргалка для написания технической документации и подготовки к собеседованиям на английском.

**Как пользоваться:** учи не отдельные слова, а связки слов. Для каждой конструкции придумай 1–2 собственных примера. Начни с раздела **Must know**: именно в этих конструкциях ты уже ошибался при переводах.

## 1. Must know: 12 конструкций

### 1. `allow + someone + to + verb` — позволять кому-либо что-либо делать

- ✅ `The API allows clients to retrieve user data.` — API позволяет клиентам получать данные пользователей.
- ❌ `The API allows retrieving clients data` — здесь меняется смысл и нарушается форма *clients' data*; если имеется в виду «позволяет клиентам получать данные», назови действующее лицо.
- ✅ Также возможно: `The API allows data retrieval.` — API позволяет получать данные (другая грамматическая конструкция).

**Шаблон:** `The system allows users to ...`

### 2. `let + someone + verb` — позволять (обычно менее формально)

- ✅ `This option lets users export reports.` — Эта опция позволяет пользователям экспортировать отчёты.
- ❌ `This option lets users to export reports.`
- ❌ `This option lets exporting reports.`

**Помни:** после `let` нет `to`; после `allow + someone` оно есть.

### 3. `to + verb` — чтобы выполнить действие

- ✅ `To publish the documentation, run the build command.` — Чтобы опубликовать документацию, запустите команду сборки.
- ❌ `For publish the documentation, ...`

**Шаблон инструкции:** `To [achieve a goal], [do an action].`

### 4. `before/after + verb-ing` — до/после действия

- ✅ `Before deploying the application, run the tests.` — Перед развёртыванием приложения запустите тесты.
- ✅ `After updating the configuration, restart the service.` — После обновления конфигурации перезапустите сервис.
- ❌ `Before deploy the application, ...`

**Также правильно:** `Before you deploy the application, ...`

### 5. `need to + verb` / `it is necessary to + verb` — нужно что-либо сделать

- ✅ `You need to configure the remote repository.` — Нужно настроить удалённый репозиторий.
- ✅ `It is necessary to configure the remote repository.` — Необходимо настроить удалённый репозиторий.
- ❌ `It's need to configure ...`

**В инструкции чаще проще:** `Configure the remote repository.`

### 6. `use + tool + to + verb` — использовать инструмент для действия

- ✅ `Use Git to track changes.` — Используйте Git для отслеживания изменений.
- ✅ `Use a CI/CD pipeline to validate links.` — Используйте CI/CD-пайплайн для проверки ссылок.
- ❌ `Use Git for track changes.`

**Также правильно:** `Use Git for version control.` (`for + noun`, а не `for + verb`.)

### 7. `by + verb-ing` — посредством действия

- ✅ `You can update the repository by running git pull.` — Репозиторий можно обновить, выполнив `git pull`.
- ❌ `You can update the repository by run git pull.`

**Шаблон:** `[Result] by [doing something].`

### 8. `when/if + present simple` — когда/если (даже о будущем)

- ✅ `When the build finishes, the pipeline runs tests.` — Когда сборка завершится, пайплайн запустит тесты.
- ✅ `If all checks pass, the application can be deployed.` — Если все проверки пройдут, приложение можно развернуть.
- ❌ `When the build will finish, ...` (для обычного придаточного времени).

### 9. `can + verb` — может сделать

- ✅ `A container can run without a separate operating system.` — Контейнер может работать без отдельной ОС.
- ❌ `A container can to run ...`
- ❌ `A container can runs ...`

**Помни:** после `can` — начальная форма глагола без `to`.

### 10. `be + past participle` — пассивный залог

- ✅ `The configuration is stored in a YAML file.` — Конфигурация хранится в YAML-файле.
- ✅ `The documentation is generated automatically.` — Документация генерируется автоматически.
- ❌ `The configuration stored in a YAML file.` (если нужен именно пассив в настоящем времени).

**Когда полезно:** если важнее действие или результат, а не исполнитель.

### 11. `help + (to) verb` / `help + someone + (to) verb` — помогать делать

- ✅ `Automated tests help detect errors early.` — Автоматические тесты помогают рано обнаруживать ошибки.
- ✅ `The tool helps developers identify broken links.` — Инструмент помогает разработчикам находить неработающие ссылки.
- ❌ `Tests help detecting errors.` (в значении этой конструкции).

### 12. `enable + someone + to + verb` — давать возможность

- ✅ `This feature enables users to manage permissions.` — Эта функция позволяет пользователям управлять правами доступа.
- ❌ `This feature enables users manage permissions.`

**Сравни:** `allow users to`, `enable users to`, `let users`.

---

## 2. Готовые связки для документации

| Задача | Естественная английская конструкция | Пример |
|---|---|---|
| Запустить команду | `run a command` | `Run git status to check the working tree.` |
| Выполнить проверку | `run a check` / `validate` | `The pipeline validates the configuration.` |
| Проверки прошли | `checks pass` | `If all checks pass, merge the pull request.` |
| Проверки не прошли | `checks fail` | `The deployment stops if a check fails.` |
| Обнаружить ошибку | `detect an error` | `Tests help detect errors early.` |
| Отслеживать изменения | `track changes` | `Git tracks changes to documentation.` |
| Хранить рядом с кодом | `store alongside source code` | `Store documentation alongside source code.` |
| Получать данные | `retrieve data` | `Use GET to retrieve user data.` |
| Отправить запрос | `send a request` | `The client sends a GET request.` |
| Вернуть ответ | `return a response` | `The server returns a JSON response.` |
| Сослаться на ключ | `reference a key` | `The foreign key references a primary key.` |
| Подготовить к развёртыванию | `prepare for deployment` | `The pipeline prepares the build for deployment.` |
| Развернуть в окружении | `deploy to an environment` | `Deploy the application to a test environment.` |
| Создать из образа | `create from an image` | `Docker creates a container from an image.` |
| Настроить один раз | `configure ... once` | `Configure the remote repository once.` |

### Частые ошибки с существительными и артиклями

- `source code` (обычно **без** `a`): `Store documentation with source code.`
- `Git`, `GitHub`, `Docker` (обычно **без** `the`): `Use Git`; `Push commits to GitHub`.
- `a GET request`, `a Docker image`, `a CI/CD pipeline` — исчисляемые существительные в единственном числе обычно требуют определителя.
- `the client sends`, `the server returns`, `the pipeline runs` — в Present Simple после `he/she/it` и единственного числа обычно добавляется `-s`.
- `changes` → `them`, `documentation` → `it`: согласуй местоимение с существительным.

---

## 3. Пять моделей предложений, которые можно использовать сразу

1. **Определение:** `A [term] is a [category] that [function].`  
   `A Docker image is a template that contains the files required to create a container.`
2. **Возможность:** `[Feature] allows [users] to [action].`  
   `The API allows clients to retrieve records.`
3. **Инструкция:** `To [goal], [imperative action].`  
   `To create a new branch, run git switch -c branch-name.`
4. **Условие:** `If [condition], [result].`  
   `If the tests fail, the pipeline stops.`
5. **Процесс:** `When [event], [system] [action].`  
   `When a client sends a request, the server returns a response.`

---

## 4. Мини-тренировка: переведи на английский

Сначала переведи сам, затем раскрой ответы ниже.

1. Чтобы проверить конфигурацию, запустите команду проверки.
2. API позволяет клиентам получать информацию о заказах.
3. Перед публикацией документации проверьте ссылки.
4. Если все тесты пройдут, пайплайн развернёт приложение в тестовом окружении.
5. Git помогает отслеживать изменения в документации.
6. Конфигурация хранится в файле YAML.
7. Используйте Docker для запуска приложения в контейнере.
8. Когда сервер получает запрос, он возвращает ответ.

<details>
<summary>Возможные ответы</summary>

1. `To validate the configuration, run the validation command.`
2. `The API allows clients to retrieve information about orders.`
3. `Before publishing the documentation, check the links.`
4. `If all tests pass, the pipeline will deploy the application to a test environment.`
5. `Git helps track changes in documentation.`
6. `The configuration is stored in a YAML file.`
7. `Use Docker to run the application in a container.`
8. `When the server receives a request, it returns a response.`

</details>

## 5. Как выучить без зубрёжки

- **День 1:** конструкции 1–4; составь по одному предложению с каждой.
- **День 2:** конструкции 5–8; повтори вчерашние без подсказок.
- **День 3:** конструкции 9–12; переведи первые четыре упражнения.
- **День 4:** переведи оставшиеся упражнения и перепиши любые ответы, где ошибся.
- **Дальше:** при работе с документацией замечай эти конструкции и пробуй использовать их в собственных предложениях.

**Главное:** не пытайся заучить весь список сразу. Достаточно освоить 2–4 шаблона и использовать их несколько раз в контексте.
