# Technical English: устойчивые сочетания для повторения

> Личный справочник по ошибкам из тренировок перевода технической документации (раунды 47–75).
>
> **Цель:** запоминать выражения целиком, а не переводить слова по одному.

## Как повторять

1. Закрой английскую колонку и переведи русское выражение на английский.
2. Придумай с ним короткую инструкцию или описание поведения сервиса.
3. Сверься с примерами и обрати внимание на предлоги и артикли.
4. Раз в несколько дней возвращайся к разделу **«Особенно частые ошибки»**.

**Обозначения:** `❌` — ошибка из тренировок или близкий к ней неудачный вариант; `✅` — вариант для документации. Не всякая альтернатива неверна: где возможны оба варианта, это отмечено.

---

## 1. Операции, запросы и ошибки

| Выражение на английском | По-русски | Пример |
|---|---|---|
| **process a request** | обработать запрос | The server processes incoming requests. |
| **handle an error** | обработать ошибку | Handle the error before retrying. |
| **perform an operation** | выполнить операцию | The service performs the operation asynchronously. |
| **execute a command** | выполнить команду | Execute the command in the terminal. |
| **run checks / run tests** | выполнить проверки / тесты | Run checks before merging. |
| **raise an error** | выдать ошибку | PostgreSQL raises an error if the constraint is violated. |
| **issue a notice** | вывести уведомление | PostgreSQL issues a notice. |
| **return a status code** | вернуть код состояния | The API may return a 429 status code. |
| **retry a request** | повторить попытку запроса | Retry the request after the delay. |
| **resubmit a request** | повторно отправить запрос (например, после исправления) | Correct the fields and resubmit the request. |
| **continue to fail** | продолжать завершаться с ошибкой | If requests continue to fail, inspect the logs. |
| **result in data loss** | привести к потере данных | This operation may result in data loss. |
| **cause an error / cause data loss** | вызвать ошибку / потерю данных | An invalid value can cause an error. |
| **acknowledge receipt of an event** | подтвердить получение события | Acknowledge receipt before lengthy processing. |
| **place an event in a queue** | поместить событие в очередь | Place the event in a queue for later processing. |
| **process asynchronously** | обрабатывать асинхронно | Process the event asynchronously. |

**Типичные ошибки:**

- ❌ `make a processing of a request` → ✅ `process a request`.
- ❌ `cause to the deleting data` → ✅ `cause data loss` / `result in data loss`.
- ❌ `requests will continue failed` → ✅ `requests continue to fail`.
- ❌ `processing of the request was made` → ✅ `the request was processed`.
- ❌ `represent a warning` (в значении «вывести предупреждение») → ✅ `issue a warning`.

## 2. Настройка и технические действия

| Выражение на английском | По-русски | Пример |
|---|---|---|
| **specify the path to a file** | указать путь к файлу | Specify the path to the configuration file. |
| **specify an IP address explicitly** | явно указать IP-адрес | Explicitly specify `127.0.0.1`. |
| **configure a workflow to run on push** | настроить запуск процесса по событию push | Configure the workflow to run on `push`. |
| **trigger a workflow** | вызвать запуск рабочего процесса | A commit can trigger a workflow. |
| **define a dependency** | задать зависимость | Define a dependency using `needs`. |
| **depend on a job** | зависеть от задания | Deployment jobs depend on tests. |
| **enable a feature / enable encryption** | включить функцию / шифрование | Enable encryption at rest. |
| **set an expiration date** | установить дату истечения срока | Set an expiration date for the token. |
| **grant permissions / grant access** | предоставить права / доступ | Grant only the required permissions. |
| **restrict access to** | ограничить круг лиц, имеющих доступ | Restrict access to authorized users. |
| **revoke a token** | отозвать токен | Revoke the exposed token immediately. |
| **leave something unchanged** | оставить что-либо без изменений | Leave the existing table unchanged. |
| **a setting applies to** | настройка применяется к | This setting applies to every object. |
| **meet the requirements / conditions** | соответствовать требованиям / условиям | The object meets the rule conditions. |
| **schedule an operation** | запланировать операцию | The service schedules the operation. |
| **complete an operation** | завершить операцию | The operation may not complete immediately. |

**Типичные ошибки:**

- ❌ `put the versioning bucket on` → ✅ `enable bucket versioning`.
- ❌ `set path by option` → ✅ `specify the path using the option`.
- ❌ `fit to the expected JSON structure` → ✅ `match the expected JSON structure`.
- ❌ `the object meets with conditions` → ✅ `the object meets the conditions`.
- ❌ `restrict access by the local computer` → ✅ `restrict access to localhost`.

## 3. Git, CI/CD и Docs as Code

| Выражение на английском | По-русски | Пример |
|---|---|---|
| **merge a pull request into a branch** | влить пулл-реквест в ветку | Merge the pull request into `main`. |
| **push commits to a remote repository** | отправить коммиты в удалённый репозиторий | Push the new commits to the remote repository. |
| **commit a file to a repository** | добавить файл коммитом в репозиторий | Never commit secrets to a repository. |
| **required checks have passed** | обязательные проверки пройдены | Ensure that all required checks have passed. |
| **changes have been approved** | изменения одобрены | The changes have been approved by reviewers. |
| **run in parallel** | выполняться параллельно | Jobs run in parallel by default. |
| **a job is skipped** | задание пропускается | The job is skipped if the condition is false. |
| **a job fails** | задание завершается с ошибкой | If a job fails, check its logs. |
| **build outputs** | результаты сборки | Download the build outputs. |
| **retention period** | срок хранения | Customize the artifact retention period. |
| **maintain documentation** | сопровождать документацию | Reusable schemas are easier to maintain. |
| **reduce duplication** | сократить дублирование | References reduce duplication. |

**Типичные ошибки:**

- ❌ `send commits in the repository` → ✅ `push commits to the repository`.
- ❌ `merge ... with main` → ✅ `merge ... into main` (для вливания изменений).
- ❌ `run with the push event` → ✅ `run on the push event`.
- ❌ `build conclusions` (вместо результатов сборки) → ✅ `build outputs`.

## 4. API, HTTP и данные

| Выражение на английском | По-русски | Пример |
|---|---|---|
| **request body** | тело запроса | The request body contains required fields. |
| **response header / request header** | заголовок ответа / запроса | Check the `Content-Type` response header. |
| **valid credentials** | действительные учётные данные | Provide valid credentials. |
| **the required permissions** | необходимые права доступа | The token lacks the required permissions. |
| **the resource exists** | ресурс существует | Check whether the resource exists. |
| **the HTTP method you are using** | используемый HTTP-метод | Ensure that the HTTP method you are using is supported. |
| **match a pattern / match a schema** | соответствовать шаблону / схеме | The file path must match the pattern. |
| **a schema definition** | определение схемы | Specify the path to the schema definition. |
| **reusable components** | переиспользуемые компоненты | Define reusable components in OpenAPI. |
| **data returned by a query** | данные, возвращённые запросом | The table contains data returned by a query. |
| **column names and data types** | имена столбцов и типы данных | Column names are determined by the query. |
| **remaining requests** | оставшиеся запросы | Check the number of requests remaining. |
| **rate-limit window** | период действия ограничения | The counter resets after the rate-limit window. |
| **exceed the rate limit** | превысить лимит запросов | The client exceeded the rate limit. |
| **due to rate limiting** | из-за ограничения частоты запросов | Requests may fail due to rate limiting. |
| **increase the interval between retries** | увеличить интервал между попытками | Gradually increase the interval between retries. |

**Типичные ошибки:**

- ❌ `body request` → ✅ `request body`.
- ❌ `current credentials` (если «действительные») → ✅ `valid credentials`.
- ❌ `resource is existing` → ✅ `resource exists`.
- ❌ `rate limit of API requests` → ✅ `API rate limit`.
- ❌ `number of the remaining requests` → ✅ `number of remaining requests`.
- ❌ `the header of the Content-Type response` → ✅ `the Content-Type response header`.

## 5. Docker, Linux и облачные сервисы

| Выражение на английском | По-русски | Пример |
|---|---|---|
| **pass environment variables to a container** | передать переменные окружения контейнеру | Pass variables using `--env-file`. |
| **define variables as key-value pairs** | задать переменные парами «ключ — значение» | Define variables as key-value pairs. |
| **bind a port to an interface** | привязать порт к интерфейсу | Docker binds the port to all host interfaces. |
| **publish a port** | опубликовать порт | Publish a port using `-p`. |
| **make an application accessible** | сделать приложение доступным | Make the application accessible from localhost. |
| **ready to accept connections** | готов принимать соединения | Wait until the database is ready to accept connections. |
| **configure a health check** | настроить проверку работоспособности | Configure a health check for the database. |
| **wait for a health check to pass** | дождаться успешного прохождения проверки | Wait for the health check to pass. |
| **storage space / consume storage space** | место в хранилище / занимать его | Old versions consume storage space. |
| **storage class** | класс хранения | Move objects to a lower-cost storage class. |
| **upload an object to a bucket** | загрузить объект в бакет | Upload an object to a bucket. |
| **download a file from a bucket** | скачать файл из бакета | Download the file from the bucket. |
| **encryption at rest** | шифрование данных при хранении | Enable encryption at rest. |
| **encryption in transit** | шифрование при передаче | Use TLS for encryption in transit. |
| **preserve file permissions** | сохранять права доступа к файлам | Copy the files and preserve their permissions. |

**Типичные ошибки:**

- ❌ `transfer variables to container` → ✅ `pass variables to a container`.
- ❌ `all host net interfaces` → ✅ `all host network interfaces`.
- ❌ `Docker linked the port` → ✅ `Docker binds the port`.
- ❌ `takes the store place` → ✅ `consumes storage space`.
- ❌ `REST encryption` (в значении шифрования при хранении) → ✅ `encryption at rest`.
- ❌ `download objects to a bucket` → ✅ `upload objects to a bucket`.

---

## 6. Универсальные грамматические шаблоны для техдокументации

| Шаблон | Пример | Типичная ловушка |
|---|---|---|
| **allow + object + to + verb** | Versioning allows you to store multiple versions. | ❌ `allows storing you` |
| **need + to + verb** | You need to specify the path. | ❌ `need specify` |
| **before / when + -ing** | Before starting the app, check the configuration. | ❌ `before the app running` |
| **during + noun** | Errors were found during the review. | ❌ `while review` |
| **while + -ing / clause** | While reviewing the docs, check the examples. | Не путать с `during` |
| **prevent + object + from + -ing** | This prevents data from being exposed. | ❌ `prevent data from the deleting` |
| **protect + object + from + noun** | Protect data from accidental deletion. | Не смешивать с `prevent` |
| **ensure that + clause** | Ensure that the resource exists. | Не заменять на прямой вопрос |
| **check whether + subject + verb** | Check whether the service is running. | ❌ `check whether is the service running` |
| **which / what + subject + verb** | Specify which formats the client supports. | ❌ `which formats does the client support` после `specify` |
| **if + Present Simple** | If requests continue to fail, retry later. | ❌ `If requests will continue failed` |
| **continue to + verb** | The service continues to run. | ❌ `continue failed` |
| **make it easier to + verb** | This makes it easier to analyze logs. | ❌ `make the analyse easier` |
| **related to + noun** | Find records related to the request. | ❌ `records relate to` без `that` |
| **result in + noun** | The change may result in data loss. | ❌ `result to` |
| **add + object + to + destination** | Add a trace ID to each record. | ❌ `add to them a trace ID` — не ошибка во всех контекстах, но неестественно здесь |
| **apply to + object** | The rule applies to all objects. | ❌ `applies for` |
| **use + tool + to + verb** | Use `chmod` to change permissions. | ❌ `for change` |
| **using + option / command** | Specify the path using `--env-file`. | ❌ `by the parameter` |
| **as + format** | Define variables as a list. | ❌ `like list` |
| **the + noun + that + verb** | All applications that use the token. | ❌ `all using the token applications` |
| **Present Perfect for completed prerequisites** | Ensure all checks have passed. | `passed` возможен в других контекстах, но здесь важен результат к моменту слияния |
| **Present Simple Passive** | The selected format is specified in the header. | ❌ `is specifying` при пассивном значении |

### Артикли и согласование: короткие напоминания

- **`each` без артикля:** ✅ `each field`, `each row`; ❌ `the each row`, `an each field`.
- **`data` обычно без `a`:** ✅ `data`, `the data`; ❌ `a data`.
- **Исчисляемое существительное в единственном числе обычно требует определителя:** ✅ `a container`, `the request`, `an IP address`; ❌ `to container`, `send request`.
- **Третье лицо единственного числа в Present Simple:** ✅ `a client exceeds`, `the format makes`, `the command creates`; ❌ `client exceed`, `format make`, `command populate`.
- **Множественное число — без `-s` у глагола:** ✅ `structured logs contain`; ❌ `structured logs contains`.
- **Глаголы состояния:** ✅ `you know`, `the resource exists`; ❌ `you are know`, `the resource is existing`.
- **`that/which` для определения:** ✅ `files that match the pattern`; ❌ `files what don't match`.

---

## 7. Особенно частые ошибки — карточки для повторения

Попробуй перевести **без просмотра ответов**:

1. Обработать запрос.
2. Выполнить операцию.
3. Выдать ошибку.
4. Передать переменные окружения контейнеру.
5. Указать путь к конфигурационному файлу.
6. Ограничить доступ авторизованными пользователями.
7. Проверить, существует ли ресурс.
8. Убедиться, что все проверки пройдены.
9. Отправить коммиты в удалённый репозиторий.
10. Файлы, соответствующие шаблону.
11. Данные, возвращённые запросом.
12. Приложения, которые используют токен.
13. Если запросы продолжают завершаться с ошибкой.
14. Это упрощает анализ логов.
15. Добавить идентификатор трассировки к записи.
16. Задать переменные в виде пар «ключ — значение».
17. Ограничение частоты запросов.
18. Объект соответствует условиям правила.
19. Занимать место в хранилище.
20. Дождаться успешного прохождения проверки работоспособности.

<details>
<summary>Ответы</summary>

1. `process a request`
2. `perform an operation`
3. `raise an error`
4. `pass environment variables to a container`
5. `specify the path to the configuration file`
6. `restrict access to authorized users`
7. `check whether the resource exists`
8. `ensure that all checks have passed`
9. `push commits to a remote repository`
10. `files that match the pattern`
11. `data returned by a query`
12. `applications that use the token`
13. `if requests continue to fail`
14. `this makes it easier to analyze logs`
15. `add a trace ID to a record`
16. `define variables as key-value pairs`
17. `rate limiting` / `rate limit` (в зависимости от контекста)
18. `the object meets the rule conditions`
19. `consume storage space`
20. `wait for the health check to pass`

</details>

---

## 8. Мини-шпаргалка: глагол + типичное дополнение

```text
process     a request / an event
handle      an error / an exception
perform     an operation / a check
execute     a command / a query
run         tests / checks / a workflow
raise       an error / an exception
issue       a notice / a warning
return      a response / a status code
retry       a request / an operation
resubmit    a request
pass        an argument / environment variables
grant       access / permissions
revoke      a token
specify     a path / an address / a value
define      a variable / a dependency
configure   a service / a workflow
enable      encryption / versioning
restrict    access to ...
match       a pattern / a schema
meet        requirements / conditions
trigger     a workflow / an event
push        commits to a remote repository
merge       a pull request into a branch
bind        a port to an interface
publish     a port
preserve    file permissions
consume     storage space
maintain    documentation
reduce      duplication
```

**Приоритет повторения:** сначала разделы **6** и **7**, затем разделы **1–5** по очереди. Этот файл можно дополнять новыми выражениями по мере следующих раундов.
