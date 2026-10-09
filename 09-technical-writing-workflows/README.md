# Technical Writing Workflows for Interviews

Five process fundamentals and five situational questions published for technical writer interviewers. English is primary and comes first; each Russian block stands on its own. The hiring question bank is a list of recommended prompts, not a transcript of a specific interview. Replace illustrative process answers with your real examples before using them in an interview.

---

**General questions / Общие вопросы**

## 1. How do you identify the audience and task? / Как определить аудиторию и задачу читателя?

### 🇬🇧 English

#### Quick recall
**Find who reads, what they know, and what they need to do.**

#### Interview answer
> I start with the reader's role and goal, then identify prerequisites, expected outcome, and likely blockers. I check support requests, product usage, and conversations with users or customer-facing teams where available. This keeps the document organized around a task rather than the team's internal component list.

#### Details
“Developers” is often too broad: a first-time integrator and an experienced maintainer need different entry points.

### 🇷🇺 Русский

#### Быстро вспомнить
**Узнать, кто читает, что уже знает и какую задачу решает.**

#### Ответ на собеседовании
> Сначала определю роль и цель читателя, необходимые знания, ожидаемый результат и вероятные препятствия. По возможности проверю обращения в поддержку, использование продукта и обратную связь от пользователей или клиентских команд. Тогда материал будет строиться вокруг задачи, а не списка внутренних компонентов.

#### Подробнее
«Разработчики» — слишком широкая аудитория: новичку в интеграции и опытному сопровождающему нужны разные входные точки.

**Published interview prompt / Опубликованный вопрос:** [“How do you structure documentation around user tasks?”](https://www.pitchnhire.com/interview-questions/technical-writer). **Reference / Справка:** [Google developer documentation style: audience](https://developers.google.com/style/audience).

## 2. How do you learn an unfamiliar feature? / Как разобраться в незнакомой функции?

### 🇬🇧 English

#### Quick recall
**Read source material, try the feature, ask targeted questions, verify the result.**

#### Interview answer
> I inspect the feature spec, interface, API behavior, code or tests when accessible, and existing documentation. I try the user path myself, list unknowns, and ask the engineer precise questions with examples. I then verify the draft against the product and have an SME review technical claims.

#### Details
Say which steps you personally used before; do not imply you independently read production code if you have not.

### 🇷🇺 Русский

#### Быстро вспомнить
**Изучить исходные материалы, попробовать функцию, задать точные вопросы, проверить результат.**

#### Ответ на собеседовании
> Изучу спецификацию, интерфейс, поведение API, код или тесты при наличии доступа и старую документацию. Пройду пользовательский сценарий, соберу неизвестные места и задам инженеру конкретные вопросы. Затем проверю черновик на продукте и отдам эксперту на проверку фактов.

#### Подробнее
На собеседовании честно отмечайте, какие этапы выполняли сами, а какие пока знаете только теоретически.

**Published interview prompt / Опубликованный вопрос:** [“Describe a time you had to document a feature you barely understood”](https://www.pitchnhire.com/interview-questions/technical-writer).

## 3. How do you plan and produce a documentation change? / Как спланировать и выпустить изменение документации?

### 🇬🇧 English

#### Quick recall
**Scope → research → outline → draft → validate → review → publish → maintain.**

#### Interview answer
> I define audience, product version, and success criteria first. Then I gather sources, outline the task flow, write and test examples, get technical and editorial review, and publish with the relevant release. I assign ownership for follow-up corrections because publication is not the end of the document's life.

#### Details
Small urgent fixes may compress the stages, but should not skip verification of safety-critical instructions.

### 🇷🇺 Русский

#### Быстро вспомнить
**Рамки → исследование → план → черновик → проверка → ревью → публикация → сопровождение.**

#### Ответ на собеседовании
> Сначала определяю аудиторию, версию продукта и критерий успеха. Затем собираю источники, строю сценарий, пишу и проверяю примеры, получаю техническое и редакторское ревью и публикую материал вместе с нужным релизом. После публикации должен остаться владелец исправлений.

#### Подробнее
Срочная маленькая правка может пройти этапы быстрее, но инструкции с риском для пользователя требуют обязательной проверки.

**Published interview prompt / Опубликованный вопрос:** [Interview bank on documentation process and keeping docs current](https://www.pitchnhire.com/interview-questions/technical-writer). **Reference / Справка:** [Write the Docs guide](https://www.writethedocs.org/guide/).

## 4. How do you verify technical accuracy? / Как проверить техническую точность?

### 🇬🇧 English

#### Quick recall
**Test steps, compare to authoritative behavior, and ask an SME about unresolved claims.**

#### Interview answer
> I run the procedure or code sample in the intended environment when possible, check versions and permissions, and compare output to the documented result. I flag statements I cannot verify and ask an engineer to review them. I keep an evidence trail so later updates can identify what changed.

#### Details
A successful test in one environment does not prove universal behavior. State the tested platform, version, and assumptions.

### 🇷🇺 Русский

#### Быстро вспомнить
**Выполнить шаги, сравнить с реальным поведением и вынести непроверенное эксперту.**

#### Ответ на собеседовании
> По возможности выполню инструкцию или пример кода в целевой среде, проверю версии и права, сравню результат с описанием. Непроверенные утверждения отмечу и передам инженеру. Сохраню следы проверки, чтобы при обновлении было видно, что изменилось.

#### Подробнее
Успех в одном окружении не гарантирует одинаковое поведение везде. Укажите проверенные платформу, версию и допущения.

**Published interview prompt / Опубликованный вопрос:** [“How do you read code and test technical instructions?”](https://www.pitchnhire.com/interview-questions/technical-writer).

## 5. How do you know documentation is useful? / Как понять, что документация полезна?

### 🇬🇧 English

#### Quick recall
**Look at task completion and reader signals, not just page views.**

#### Interview answer
> I define what the page should help the reader do, then look for signals: fewer repeated support questions, successful onboarding, search terms, feedback, and usability observations. I interpret metrics cautiously because a drop in traffic can mean either success or poor discoverability.

#### Details
Pair numbers with examples from readers; avoid inventing a percentage improvement without a measured baseline.

### 🇷🇺 Русский

#### Быстро вспомнить
**Смотреть на выполнение задачи и сигналы читателей, а не только на просмотры.**

#### Ответ на собеседовании
> Определю, какое действие должна поддержать страница, затем посмотрю на повторяющиеся обращения, успешность подключения, поисковые запросы, отзывы и наблюдения за пользователями. Метрики нужно толковать осторожно: падение трафика бывает и хорошим знаком, и проблемой навигации.

#### Подробнее
Дополняйте цифры конкретными историями читателей. Не называйте проценты улучшения без исходного измерения.

**Published interview prompt / Опубликованный вопрос:** [Interview bank asks what made a documentation piece effective](https://www.pitchnhire.com/interview-questions/technical-writer).

---

**Published situational questions / Опубликованные ситуационные вопросы**

## 6. Engineers are too busy to give details for an urgent doc. What do you do? / Инженеры заняты, а документ срочный. Что делать?

### 🇬🇧 English

#### Quick recall
**Research independently, ask small precise questions, expose uncertainty.**

#### Interview answer
> I would inspect the feature, spec, tests, and related tickets, then prepare a draft and a short list of blocking questions. I would ask the right owner for a quick factual review rather than a broad interview. If critical behavior remains unverified, I would narrow the document or delay that claim instead of guessing.

#### Details
Urgency changes the communication format, not the need for accuracy.

### 🇷🇺 Русский

#### Быстро вспомнить
**Разобраться самостоятельно, задать короткие точные вопросы, явно отметить неопределённость.**

#### Ответ на собеседовании
> Проверю функцию, спецификацию, тесты и связанные задачи, затем подготовлю черновик и список вопросов, без которых нельзя публиковать. Попрошу ответственного быстро проверить факты, а не проводить длинное интервью. Если важное поведение не подтверждено, сужу материал или отложу это утверждение.

#### Подробнее
Срочность меняет формат взаимодействия, но не отменяет точность.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank: busy engineers and urgent docs](https://www.pitchnhire.com/interview-questions/technical-writer).

## 7. You inherit outdated, disorganized docs. Where do you start? / Досталась устаревшая и запутанная документация. С чего начать?

### 🇬🇧 English

#### Quick recall
**Inventory, prioritize high-impact errors, fix incrementally.**

#### Interview answer
> I would map pages to users and product versions, find high-traffic or high-risk paths, and compare them with current behavior. I would fix dangerous or blocking inaccuracies first, then improve navigation and duplication. I would track ownership and establish a change signal so the set does not decay again.

#### Details
Do not promise to rewrite everything before learning which pages users actually need.

### 🇷🇺 Русский

#### Быстро вспомнить
**Инвентаризация, приоритизация вредных ошибок, постепенное исправление.**

#### Ответ на собеседовании
> Сопоставлю страницы с аудиториями и версиями продукта, найду самые востребованные и рискованные сценарии и сверю их с текущим поведением. Сначала исправлю ошибки, которые мешают или вредят пользователю, затем навигацию и дублирование. Назначу владельцев и сигнал об изменениях продукта.

#### Подробнее
Не стоит обещать переписать всё, пока не ясно, какие страницы действительно нужны.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank: inherited outdated documentation](https://www.pitchnhire.com/interview-questions/technical-writer).

## 8. A feature ships without docs and users are confused. What do you do? / Функция вышла без документации, пользователи не понимают её. Что делать?

### 🇬🇧 English

#### Quick recall
**Resolve the immediate user blocker, then repair the release process.**

#### Interview answer
> I would identify the user task and failure point from support and product evidence, verify the workflow with the product owner, and publish a focused correction quickly. Then I would review why docs were missed and add documentation to release readiness so the next feature does not repeat the gap.

#### Details
Escalate if the missing instruction could cause data loss or security exposure; a short FAQ alone may be insufficient.

### 🇷🇺 Русский

#### Быстро вспомнить
**Снять текущую проблему пользователя, затем исправить релизный процесс.**

#### Ответ на собеседовании
> По обращениям и данным продукта найду задачу и точку затруднения, проверю сценарий с владельцем функции и быстро выпущу точечную инструкцию. Затем разберу, почему документацию пропустили, и включу её в критерии готовности следующего релиза.

#### Подробнее
При риске потери данных или утечки нужно эскалировать проблему; короткого FAQ может быть мало.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank: undocumented shipped feature](https://www.pitchnhire.com/interview-questions/technical-writer).

## 9. Two teams use different terms for the same concept. What do you do? / Две команды называют одно понятие по-разному. Что делать?

### 🇬🇧 English

#### Quick recall
**Verify whether the concepts are identical, choose a canonical term, keep findability.**

#### Interview answer
> I would ask both teams for definitions and examples before assuming the terms are synonyms. If they refer to the same concept, I would agree on a canonical term with product owners, update the glossary and UI/docs where feasible, and keep redirects or aliases so readers can still find the content.

#### Details
Do not silently rename a UI label in docs if the product still uses the old wording.

### 🇷🇺 Русский

#### Быстро вспомнить
**Проверить смысл, выбрать основной термин и сохранить поисковую доступность.**

#### Ответ на собеседовании
> Сначала попрошу обе команды дать определения и примеры: возможно, это разные понятия. Если смысл одинаков, согласую основной термин с владельцами продукта, обновлю глоссарий и по возможности интерфейс и документацию. Старые названия оставлю как поисковые синонимы или перенаправления.

#### Подробнее
Не стоит молча переименовывать элемент в документации, если интерфейс всё ещё показывает прежнее название.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank: conflicting terminology](https://www.pitchnhire.com/interview-questions/technical-writer).

## 10. How do you handle technical review feedback? / Как работать с замечаниями технического рецензента?

### 🇬🇧 English

#### Quick recall
**Separate factual corrections from wording preferences; resolve both for the reader.**

#### Interview answer
> I would thank the reviewer, verify technical corrections in the product or source, and update the draft. If a suggested wording makes the text harder for the intended audience, I would explain the reader need and propose a technically accurate alternative. I would record unresolved decisions and request explicit approval for high-risk claims.

#### Details
The goal is shared accuracy and usability, not winning an edit debate.

### 🇷🇺 Русский

#### Быстро вспомнить
**Отделить исправление факта от предпочтения в формулировке и решить вопрос в интересах читателя.**

#### Ответ на собеседовании
> Проверю технические замечания по продукту или исходникам и исправлю черновик. Если предложенная формулировка затрудняет чтение целевой аудитории, объясню почему и предложу точный, но более ясный вариант. Нерешённые вопросы зафиксирую; рискованные утверждения опубликую только после подтверждения.

#### Подробнее
Цель — общая точность и полезность, а не победа в споре о правке.

**Published interview prompt / Опубликованный вопрос:** [Recruiter bank: handling technical reviewers](https://www.pitchnhire.com/interview-questions/technical-writer).
