# Docs as Code for Technical Writer Interviews

Five study questions and five interview practice prompts. English comes
first, followed by Russian. Questions 1–4 expand the published Docs-as-Code
topic; question 5 comes from a professional discussion, not an interview.
Published question banks are not evidence that a candidate received a
particular question. The earlier source for question 7 could not be
reverified on 2026-11-03 and is marked accordingly.

Вопросы 1–4 раскрывают опубликованную тему Docs as Code; вопрос 5 взят из
профессионального обсуждения, не из интервью. Банк вопросов не доказывает,
что их задавали конкретному кандидату. Старый источник вопроса 7 повторно
проверить не удалось; это отмечено у ссылки.

---

**General questions / Общие вопросы**

## 1. What is Docs as Code? / Что такое Docs as Code?

### 🇬🇧 English

#### Interview answer

> Docs as Code uses development practices for documentation: version control, review, automated checks, and publishing. It does not require a particular markup language.

#### Details

Ask where source lives, how previews work, who reviews accuracy, and who publishes. The right toolchain depends on audience and content.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Docs as Code применяет к документации контроль версий, ревью, автоматические проверки и публикацию. Конкретный язык разметки не обязателен.

#### Подробнее

Уточняйте, где лежат исходники, как получить превью, кто проверяет точность и кто публикует материал. Инструменты выбирают под аудиторию и тип контента.

**Topic-based practice / Подготовка по опубликованной теме:** [Technical writer interview question bank](https://www.pitchnhire.com/interview-questions/technical-writer). **Technical reference / Справка:** [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).

## 2. What are the roles of Markdown, Git, and a static-site generator? / Зачем нужны Markdown, Git и генератор статического сайта?

### 🇬🇧 English

#### Interview answer

> Markdown structures the source text; Git tracks versions; a static-site generator builds publishable pages from that source.

#### Details

Markdown flavors and generator features differ. Check the project's configuration before using extensions or raw HTML.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Markdown оформляет исходный текст, Git хранит версии, генератор статического сайта собирает из исходников страницы для публикации.

#### Подробнее

Варианты Markdown и возможности генераторов различаются. Расширения и HTML нужно сверять с конфигурацией проекта.

**Topic-based practice / Подготовка по опубликованной теме:** [Interview bank asks about Markdown, Git, and static-site generators](https://www.pitchnhire.com/interview-questions/technical-writer). **Technical reference / Справка:** [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).

## 3. How does a documentation pull request work? / Как проходит pull request для документации?

### 🇬🇧 English

#### Interview answer

> I would submit a focused change, check its preview, get technical and editorial review, and merge it after the required checks pass.

#### Details

Do not treat a green linter as proof of technical truth. Record which product version the change applies to.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я отправлю небольшую целостную правку, проверю превью, получу техническое и редакторское ревью и объединю изменения после обязательных проверок.

#### Подробнее

Зелёный линтер не подтверждает фактическую точность. Нужно указать, к какой версии продукта относится правка.

**Topic-based practice / Подготовка по опубликованной теме:** [Interview bank asks about Docs-as-Code workflows](https://www.pitchnhire.com/interview-questions/technical-writer). **Technical reference / Справка:** [GitHub pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

## 4. What can automated documentation checks catch? / Что могут найти автоматические проверки документации?

### 🇬🇧 English

#### Interview answer

> Automation can catch build errors, broken links, style issues, and failing examples. It cannot replace checking that the explanation is technically correct and useful.

#### Details

External-link checks can be flaky; distinguish unavailable sites from actual broken links before editing content.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Автоматизация выявляет ошибки сборки, ссылок, стиля и примеров. Она не заменяет проверку технической точности и полезности объяснения.

#### Подробнее

Внешние ссылки иногда недоступны временно; сначала отделите такой сбой от действительно неверного URL.

**Topic-based practice / Подготовка по опубликованной теме:** [Interview bank asks about docs-as-code and CI](https://www.pitchnhire.com/interview-questions/technical-writer). **Technical reference / Справка:** [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).

## 5. When might Docs as Code be a poor fit? / Когда Docs as Code может не подойти?

### 🇬🇧 English

#### Interview answer

> I would compare the workflow with contributor skills, reuse, localization, and publishing needs. A CMS or hybrid interface may fit better than direct Git editing.

#### Details

Avoid treating the toolchain as a status symbol. Measure whether it helps readers and maintainers.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я сопоставлю процесс с навыками участников, повторным использованием, локализацией и публикацией. CMS или гибридный интерфейс могут подойти лучше прямой работы в Git.

#### Подробнее

Инструменты не показатель статуса. Важно, помогают ли они читателям и команде сопровождения.

**Published discussion / Опубликованное обсуждение:** [Technical writers discuss limitations of Docs as Code](https://www.reddit.com/r/technicalwriting/comments/1c74f89/what_exactly_is_the_docsascode_process/). **Technical reference / Справка:** [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).

---

**Interview practice; see source status / Практика: см. статус источника**

## 6. Describe your Docs-as-Code workflow. / Опишите свой процесс Docs as Code.

### 🇬🇧 English

#### Interview answer

> I would show a real Markdown change and its Git history, explain my own contribution, and distinguish that experience from workflow steps I only know theoretically.

#### Details

Do not claim experience with a generator or CI pipeline merely because you have used Git and Markdown.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я покажу реальную правку Markdown и её историю Git, объясню свой вклад и отделю практический опыт от этапов, знакомых только теоретически.

#### Подробнее

Опыт Git и Markdown ещё не означает опыта с генератором сайта и CI.

**Published interview prompt / Опубликованный вопрос:** [“Describe your experience with docs-as-code workflows”](https://www.pitchnhire.com/interview-questions/technical-writer).

## 7. How would you structure one repository for internal and external API docs? / Как организовать один репозиторий для внутренней и внешней API-документации?

### 🇬🇧 English

#### Interview answer

> I would separate audiences and build outputs, then enforce access boundaries. Directories alone do not protect internal content from repository readers.

#### Details

There is no universal layout. Directories and separate build targets are organizational tools, not access controls. Anyone who can read the repository can normally read both directories and their history. Use separate access-controlled repositories when audiences must not see each other's sources; never store secrets in either docs set.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я разделю аудитории и результаты сборки, затем обеспечу разграничение доступа. Одни каталоги не защищают внутренний контент от читателей репозитория.

#### Подробнее

Универсальной структуры нет. Каталоги и отдельные сборки организуют материалы, но не ограничивают доступ. Читатель репозитория обычно видит оба каталога и их историю. Если исходники нужно скрыть от части аудитории, используй отдельные репозитории с нужными правами; секреты не храни ни в одном комплекте документации.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/technicalwriting/comments/16mxn8v/).

## 8. How do you read code and test technical instructions? / Как вы читаете код и проверяете технические инструкции?

### 🇬🇧 English

#### Interview answer

> I would trace inputs, branches, outputs, and errors, then run the documented procedure for the target version. Unverified behavior needs confirmation.

#### Details

Reading code helps discover behavior, but it does not replace running the user-facing procedure or getting a technical review.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я прослежу входы, ветвления, результаты и ошибки, затем выполню инструкцию на нужной версии. Непроверенное поведение нужно подтвердить.

#### Подробнее

Чтение кода помогает найти поведение, но не заменяет проверки пользовательского сценария и технического ревью.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank asks how candidates read code and test instructions](https://www.pitchnhire.com/interview-questions/technical-writer).

## 9. A code example in published docs breaks after an API change. How do you prevent recurrence? / Пример кода сломался после изменения API. Как предотвратить повторение?

### 🇬🇧 English

#### Interview answer

> I would reproduce and fix the example, then connect docs review to API changes. Where practical, I would add executable example tests.

#### Details

Some examples cannot be tested automatically without credentials or live services; document their verification method.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я воспроизведу и исправлю пример, затем свяжу ревью документации с изменениями API. Где возможно, добавлю автоматический запуск примеров.

#### Подробнее

Некоторые примеры нельзя запускать в CI без секретов или внешнего сервиса; тогда нужен описанный ручной способ проверки.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank gives this exact broken-example scenario](https://www.pitchnhire.com/interview-questions/technical-writer).

## 10. How do you raise quality, consistency, and discoverability across a docs set? / Как повысить качество, единообразие и доступность всего комплекта документации?

### 🇬🇧 English

#### Interview answer

> I would find recurring reader problems, then improve terminology, navigation, ownership, and review checks. Reader feedback should confirm whether the changes help.

#### Details

Automated style checks help consistency, but cannot decide whether a page answers the reader's question.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я найду повторяющиеся проблемы читателей и улучшу терминологию, навигацию, ответственность за разделы и проверки. Пользу изменений нужно подтвердить обратной связью.

#### Подробнее

Автоматическая проверка стиля помогает единообразию, но не решает, отвечает ли страница на вопрос читателя.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank asks about quality, consistency, and discoverability](https://www.pitchnhire.com/interview-questions/technical-writer).
