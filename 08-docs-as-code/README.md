# Docs as Code for Technical Writer Interviews

Five general questions and five published interview prompts or reported exercises. English is primary; the Russian block follows. A hiring-site question bank is evidence that a prompt has been published for interviewers, not proof that a particular candidate was asked it. Reported candidate exercises are labeled separately.

---

**General questions / Общие вопросы**

## 1. What is Docs as Code? / Что такое Docs as Code?

### 🇬🇧 English

#### Quick recall
**Treat documentation changes with many of the same tools and review practices as code changes.**

#### Interview answer
> Docs as Code commonly uses plain-text source, version control, issue tracking, pull requests, automated checks, and a publishing pipeline. It brings writers and engineers into a shared workflow, but it is a working approach, not a requirement that every document be written in Markdown.

#### Details
Ask where source lives, how previews work, who reviews accuracy, and who publishes. The right toolchain depends on audience and content.

### 🇷🇺 Русский

#### Быстро вспомнить
**Документацию меняют и проверяют многими теми же средствами, что и код.**

#### Ответ на собеседовании
> Обычно Docs as Code включает текстовые исходники, контроль версий, задачи, pull request, автоматические проверки и публикацию. Это помогает писателям и инженерам работать вместе, но не означает, что любой документ обязательно должен быть в Markdown.

#### Подробнее
Уточняйте, где лежат исходники, как получить превью, кто проверяет точность и кто публикует материал. Инструменты выбирают под аудиторию и тип контента.

**Published interview prompt / Опубликованный вопрос:** [Technical writer interview question bank](https://www.pitchnhire.com/interview-questions/technical-writer). **Technical reference / Справка:** [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).

## 2. What are the roles of Markdown, Git, and a static-site generator? / Зачем нужны Markdown, Git и генератор статического сайта?

### 🇬🇧 English

#### Quick recall
**Markdown stores content, Git tracks revisions, and the generator builds the reader-facing site.**

#### Interview answer
> I write source files in a supported markup format, use Git to track and review changes, and run a generator to render pages with navigation, templates, and links. The deployed site is an output; the source repository is usually where the authoritative editable version lives.

#### Details
Markdown flavors and generator features differ. Check the project's configuration before using extensions or raw HTML.

### 🇷🇺 Русский

#### Быстро вспомнить
**Markdown хранит текст, Git — историю, генератор собирает сайт для читателя.**

#### Ответ на собеседовании
> Я редактирую исходные файлы в поддерживаемой разметке, Git хранит изменения и помогает проводить ревью, а генератор строит страницы, навигацию и ссылки. Опубликованный сайт — результат сборки; редактируемый источник обычно находится в репозитории.

#### Подробнее
Варианты Markdown и возможности генераторов различаются. Расширения и HTML нужно сверять с конфигурацией проекта.

**Published interview prompt / Опубликованный вопрос:** [Interview bank asks about Markdown, Git, and static-site generators](https://www.pitchnhire.com/interview-questions/technical-writer). **Technical reference / Справка:** [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).

## 3. How does a documentation pull request work? / Как проходит pull request для документации?

### 🇬🇧 English

#### Quick recall
**Change source, inspect preview and checks, get review, merge, publish.**

#### Interview answer
> I create a focused change, explain its user impact in the pull request, and check the rendered preview. Automated checks catch mechanical issues; subject-matter reviewers validate technical accuracy; editorial reviewers check clarity and consistency. After approval, the change merges and follows the team's publication process.

#### Details
Do not treat a green linter as proof of technical truth. Record which product version the change applies to.

### 🇷🇺 Русский

#### Быстро вспомнить
**Изменить исходник, проверить превью и тесты, получить ревью, слить и опубликовать.**

#### Ответ на собеседовании
> Я делаю ограниченное изменение, описываю его пользу для читателя в pull request и проверяю отображение страницы. Автоматические проверки ловят технические дефекты, эксперт подтверждает факты, редактор проверяет ясность и терминологию. После одобрения изменение попадает в процесс публикации.

#### Подробнее
Зелёный линтер не подтверждает фактическую точность. Нужно указать, к какой версии продукта относится правка.

**Published interview prompt / Опубликованный вопрос:** [Interview bank asks about Docs-as-Code workflows](https://www.pitchnhire.com/interview-questions/technical-writer). **Technical reference / Справка:** [GitHub pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

## 4. What can automated documentation checks catch? / Что могут найти автоматические проверки документации?

### 🇬🇧 English

#### Quick recall
**Broken links, invalid markup, style violations, build failures, and sometimes broken examples.**

#### Interview answer
> A docs pipeline can build the site and run link, spelling, style, accessibility, or code-example checks. Each check has limits: an existing link may point to obsolete information, and a passing code snippet may still be misleading. Human technical review remains necessary.

#### Details
External-link checks can be flaky; distinguish unavailable sites from actual broken links before editing content.

### 🇷🇺 Русский

#### Быстро вспомнить
**Битые ссылки, ошибки разметки, нарушения стиля, сбой сборки и иногда неработающие примеры.**

#### Ответ на собеседовании
> Pipeline документации может собирать сайт и проверять ссылки, орфографию, стиль, доступность или исполняемые примеры. У каждого теста есть предел: работающая ссылка может вести к устаревшим сведениям, а запускающийся пример — вводить в заблуждение. Экспертное ревью всё равно нужно.

#### Подробнее
Внешние ссылки иногда недоступны временно; сначала отделите такой сбой от действительно неверного URL.

**Published interview prompt / Опубликованный вопрос:** [Interview bank asks about docs-as-code and CI](https://www.pitchnhire.com/interview-questions/technical-writer). **Technical reference / Справка:** [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).

## 5. When might Docs as Code be a poor fit? / Когда Docs as Code может не подойти?

### 🇬🇧 English

#### Quick recall
**When the workflow blocks contributors or cannot support the content's real needs.**

#### Interview answer
> I would assess contributor skills, required formats, localization, reuse, approval rules, and publishing needs. A Git-based workflow is valuable when it improves collaboration and traceability; a hybrid authoring interface or another system may be better when nontechnical contributors need to work often.

#### Details
Avoid treating the toolchain as a status symbol. Measure whether it helps readers and maintainers.

### 🇷🇺 Русский

#### Быстро вспомнить
**Когда процесс мешает авторам или не поддерживает реальные требования к контенту.**

#### Ответ на собеседовании
> Я оценю навыки участников, форматы, локализацию, повторное использование, согласования и публикацию. Git-процесс полезен, если улучшает совместную работу и историю изменений; для частых правок нетехнических специалистов может подойти гибридный интерфейс или другая система.

#### Подробнее
Инструменты не показатель статуса. Важно, помогают ли они читателям и команде сопровождения.

**Published discussion / Опубликованное обсуждение:** [Technical writers discuss limitations of Docs as Code](https://www.reddit.com/r/technicalwriting/comments/1c74f89/what_exactly_is_the_docsascode_process/). **Technical reference / Справка:** [Write the Docs: Docs as Code](https://www.writethedocs.org/guide/docs-as-code/).

---

**Published questions and tasks / Опубликованные вопросы и задания**

## 6. Describe your Docs-as-Code workflow. / Опишите свой процесс Docs as Code.

### 🇬🇧 English

#### Quick recall
**Show an actual change from issue to published page.**

#### Interview answer
> In this preparation repository, I can point to a Markdown change, its Git commit, and the published GitHub version. In a team workflow I would add an issue, branch and pull request, preview, automated checks, technical review, and release synchronization. I would be explicit about which steps I have actually performed myself.

#### Details
Do not claim experience with a generator or CI pipeline merely because you have used Git and Markdown.

### 🇷🇺 Русский

#### Быстро вспомнить
**Показать реальное изменение от задачи до опубликованной страницы.**

#### Ответ на собеседовании
> В этом учебном репозитории я могу показать изменение Markdown, коммит и версию на GitHub. В командном процессе добавились бы задача, ветка и pull request, превью, автоматические проверки, техническое ревью и привязка к релизу. Я чётко отмечу, какие шаги выполнял сам.

#### Подробнее
Опыт Git и Markdown ещё не означает опыта с генератором сайта и CI.

**Published interview prompt / Опубликованный вопрос:** [“Describe your experience with docs-as-code workflows”](https://www.pitchnhire.com/interview-questions/technical-writer).

## 7. How would you structure one repository for internal and external API docs? / Как организовать один репозиторий для внутренней и внешней API-документации?

### 🇬🇧 English

#### Quick recall
**Separate audiences and publication paths; audit permissions before sharing source.**

#### Interview answer
> I would map what each audience needs, then separate public and internal content by directories or repositories according to access risk. I would define ownership, reuse rules, review gates, and separate build targets. I would verify that internal secrets and endpoints cannot leak through the public build or repository access.

#### Details
There is no universal directory layout. In the reported exercise, the task was to explain the repository structure, not to implement a specific architecture.

### 🇷🇺 Русский

#### Быстро вспомнить
**Разделить аудитории и публикацию; проверить права доступа к исходникам.**

#### Ответ на собеседовании
> Сначала определю потребности внешних и внутренних читателей, затем разделю контент по каталогам или репозиториям в зависимости от рисков доступа. Задам владельцев, правила повторного использования, ревью и отдельные варианты сборки. Проверю, что внутренние данные не попадут в публичный сайт или доступный репозиторий.

#### Подробнее
Универсальной структуры нет. В описанном кандидатом задании просили обосновать организацию репозитория, а не реализовать заданную схему.

**Reported interview task / Описанное задание:** [Candidate reports an API-doc repository design exercise](https://www.reddit.com/r/technicalwriting/comments/16mxn8v/).

## 8. How do you read code and test technical instructions? / Как вы читаете код и проверяете технические инструкции?

### 🇬🇧 English

#### Quick recall
**Trace inputs and outputs, then run the documented procedure in a controlled environment.**

#### Interview answer
> I would read enough code or tests to understand inputs, main branches, outputs, and errors. Then I would run the documented steps against the intended version and compare observed results with the draft. If a build or test fails, I would inspect its log and verify the cause before editing the instructions.

#### Details
Reading code helps discover behavior, but it does not replace running the user-facing procedure or getting a technical review.

### 🇷🇺 Русский

#### Быстро вспомнить
**Проследить входы и результаты кода, затем выполнить инструкцию в контролируемой среде.**

#### Ответ на собеседовании
> Прочитаю код или тесты настолько, чтобы понять входы, основные ветвления, результаты и ошибки. Затем выполню документированные шаги для нужной версии и сравню реальный результат с черновиком. Если сборка или тест падают, изучу лог и проверю причину перед правкой текста.

#### Подробнее
Чтение кода помогает найти поведение, но не заменяет проверки пользовательского сценария и технического ревью.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank asks how candidates read code and test instructions](https://www.pitchnhire.com/interview-questions/technical-writer).

## 9. A code example in published docs breaks after an API change. How do you prevent recurrence? / Пример кода сломался после изменения API. Как предотвратить повторение?

### 🇬🇧 English

#### Quick recall
**Fix the example, link doc ownership to API changes, test examples where feasible.**

#### Interview answer
> I would reproduce and correct the example for affected versions, then determine how the API change escaped documentation review. I would connect docs to release or pull-request checklists and add executable example tests where practical. I would also provide a clear correction note if users may have copied the broken example.

#### Details
Some examples cannot be tested automatically without credentials or live services; document their verification method.

### 🇷🇺 Русский

#### Быстро вспомнить
**Исправить пример, связать изменение API с ревью документации и проверять примеры.**

#### Ответ на собеседовании
> Воспроизведу ошибку и исправлю пример для затронутых версий. Затем выясню, почему изменение API прошло без обновления документации. Добавлю связь с релизными задачами или pull request и, где возможно, автоматическую проверку примера. Если пользователи могли скопировать неверный код, явно отмечу исправление.

#### Подробнее
Некоторые примеры нельзя запускать в CI без секретов или внешнего сервиса; тогда нужен описанный ручной способ проверки.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank gives this exact broken-example scenario](https://www.pitchnhire.com/interview-questions/technical-writer).

## 10. How do you raise quality, consistency, and discoverability across a docs set? / Как повысить качество, единообразие и доступность всего комплекта документации?

### 🇬🇧 English

#### Quick recall
**Audit recurring problems, set shared conventions, and measure whether readers find answers.**

#### Interview answer
> I would review search queries, support issues, and the docs structure to find recurring gaps. Then I would maintain a glossary, style rules, templates, clear ownership, and review checks in the repository. I would improve navigation and redirects where needed, and validate the result with reader feedback rather than only counting pages.

#### Details
Automated style checks help consistency, but cannot decide whether a page answers the reader's question.

### 🇷🇺 Русский

#### Быстро вспомнить
**Найти повторяющиеся проблемы, договориться о правилах и проверить, находят ли читатели ответы.**

#### Ответ на собеседовании
> Изучу поисковые запросы, обращения и структуру документации, чтобы найти системные пробелы. Затем поддержу глоссарий, правила стиля, шаблоны, владельцев разделов и проверки при ревью. При необходимости улучшу навигацию и перенаправления, а результат сверю с отзывами читателей, не только с числом страниц.

#### Подробнее
Автоматическая проверка стиля помогает единообразию, но не решает, отвечает ли страница на вопрос читателя.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank asks about quality, consistency, and discoverability](https://www.pitchnhire.com/interview-questions/technical-writer).
