# CI/CD and DevOps for Technical Writer Interviews

Five fundamentals and five interview practice scenarios. English comes
first, followed by Russian. Sources distinguish reported questions from
adaptations of published topics. Earlier sources unavailable for rechecking
on 2026-11-03 are marked unverified. These engineering-role examples do not
predict what every technical writer will be asked.

Пять базовых вопросов и пять практических сценариев. Прямые сообщения о
вопросах отделены от адаптаций опубликованных тем. Старые источники,
недоступные для повторной проверки 2026-11-03, отмечены отдельно.

---

**General questions / Общие вопросы**

## 1. What are CI, continuous delivery, and continuous deployment? / Что такое CI, continuous delivery и continuous deployment?

### 🇬🇧 English

#### Interview answer

> CI frequently integrates changes with automated checks. Continuous delivery keeps changes releasable; continuous deployment automatically releases changes that pass the required checks.

#### Details

CI is a practice of frequent integration supported by automated builds and tests, not merely a configured server. Teams use “CD” for both delivery and deployment. Delivery keeps a release ready, with production release controlled by a decision; deployment automates that decision for changes passing the gates.

### 🇷🇺 Русский

#### Ответ на собеседовании

> CI регулярно объединяет изменения с автоматическими проверками. Continuous delivery поддерживает готовность к выпуску; continuous deployment автоматически выпускает прошедшие проверки изменения.

#### Подробнее

CI — практика частого объединения изменений с автоматическими сборками и тестами, а не просто настроенный сервер. CD означает и delivery, и deployment. Delivery поддерживает готовность к выпуску, оставляя решение о production отдельным; deployment автоматизирует выпуск прошедших проверки изменений.

**Topic-based practice / Подготовка по теме:** [Reported CI/CD flow questions](https://www.reddit.com/r/devopsjobs/comments/1qepvk2/devops_interview_questions_recently_attended/). The definition comparison here is a study question, not a verbatim report. / Сравнение определений здесь учебное, а не дословно опубликованное. **Technical reference / Справка:** [GitLab CI/CD](https://docs.gitlab.com/ci/).

## 2. What are a pipeline, job, stage, and runner? / Что такое pipeline, job, stage и runner?

### 🇬🇧 English

#### Interview answer

> A pipeline organizes jobs; a runner executes them. In GitLab, stages group jobs into ordered phases, with dependencies able to change that order.

#### Details

For GitHub Actions, distinguish workflow, job, step, and runner. Do not assume “stage” is a universal product term.

Independent GitHub Actions jobs can run in parallel, subject to available runners and limits. `needs` defines dependencies. GitLab normally orders stages; jobs within a stage can run in parallel, while `needs` enables a dependency graph across stages.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Pipeline объединяет задачи, runner выполняет их. В GitLab stages группируют задачи в последовательные этапы; зависимости могут менять порядок выполнения.

#### Подробнее

В GitHub Actions используются workflow, job, step и runner. Не стоит переносить термин «stage» на любую платформу.

Независимые задачи GitHub Actions могут выполняться параллельно с учётом доступных runner и лимитов; `needs` задаёт зависимости. В GitLab стадии обычно идут последовательно, задачи одной стадии могут идти параллельно, а `needs` строит зависимости между стадиями.

**Topic-based practice / Подготовка по теме:** [Candidate reports GitLab CI/CD questions](https://www.reddit.com/r/devops/comments/1r98h8f/juniorr_devops_interview_experience_questions_i/). The four-term comparison is an explanatory expansion. / Сравнение четырёх терминов добавлено для подготовки. **Technical references / Справка:** [GitLab pipelines](https://docs.gitlab.com/ci/pipelines/), [GitHub Actions](https://docs.github.com/en/actions/get-started/understand-github-actions).

## 3. What is a build artifact, and how is it different from a cache? / Что такое артефакт сборки и чем он отличается от кеша?

### 🇬🇧 English

#### Interview answer

> An artifact is a job's retained output, such as a package or report. A cache stores reusable data to speed up future jobs.

#### Details

Retention and access rules depend on the CI platform. In docs, say which job creates an artifact, where it is found, and how long it remains available.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Артефакт — сохранённый результат задачи, например пакет или отчёт. Кеш хранит повторно используемые данные для ускорения следующих запусков.

#### Подробнее

Срок хранения и доступ зависят от платформы. В документации нужно указать, какая задача создала артефакт, где его найти и когда он исчезнет.

**Interview evidence / Источник вопроса:** [Candidate reports being asked about GitLab artifacts](https://www.reddit.com/r/devops/comments/1r98h8f/juniorr_devops_interview_experience_questions_i/). **Technical references / Справка:** [GitLab job artifacts](https://docs.gitlab.com/ci/jobs/job_artifacts/), [GitLab caching](https://docs.gitlab.com/ci/caching/).

## 4. How does a change move from commit to production? / Как изменение доходит от коммита до production?

### 🇬🇧 English

#### Interview answer

> A typical flow is review and checks, build a versioned artifact, test, approve where required, deploy, and verify. The exact gates depend on the team.

#### Details

Record the commit or artifact version, deployment target, owner, and rollback procedure. A successful job log does not necessarily prove the application works for users.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Типичный путь: ревью и проверки, сборка версионированного артефакта, тестирование, нужные согласования, развёртывание и проверка результата. Условия зависят от команды.

#### Подробнее

Нужно фиксировать версию, целевую среду, владельца процесса и способ отката. Зелёный статус задачи сам по себе не доказывает работоспособность приложения для пользователя.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/devops/comments/cvwdjo/). **Technical reference / Справка:** [GitHub Actions workflows](https://docs.github.com/en/actions/concepts/workflows-and-actions/workflows).

## 5. What does DevOps mean in this context? / Что в этом контексте означает DevOps?

### 🇬🇧 English

#### Interview answer

> DevOps brings development and operations together through shared responsibility, automation, and feedback. It is a working approach, not a particular tool.

#### Details

Ask who owns deployment, incidents, and documentation updates; organizations implement DevOps differently.

### 🇷🇺 Русский

#### Ответ на собеседовании

> DevOps объединяет разработку и эксплуатацию через общую ответственность, автоматизацию и обратную связь. Это подход к работе, а не конкретный инструмент.

#### Подробнее

Уточняйте, кто отвечает за выпуск, инциденты и актуальность документации: процессы различаются.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/devops/comments/dxo6pt/). **Technical reference / Справка:** [AWS introduction to DevOps](https://aws.amazon.com/devops/what-is-devops/).

---

**Interview practice; see source status / Практика: см. статус источника**

## 6. Design a pipeline for a Python web app from push to production. / Опишите pipeline для Python-приложения от push до production.

### 🇬🇧 English

#### Interview answer

> I would test the change, build one versioned artifact, validate it in staging, and deploy that same artifact with approval, monitoring, and a recovery plan.

#### Details

This is an outline, not a production-ready pipeline. Clarify linting, tests, artifact identity, secrets, database migrations, smoke tests, and approvals. Reusing the same artifact avoids untested rebuild differences; environment configuration still needs validation. A rollback may not reverse a database migration.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я проверю изменение, соберу версионированный артефакт, протестирую его на стенде и выпущу тот же артефакт с согласованием, мониторингом и планом восстановления.

#### Подробнее

Это схема, а не готовый production pipeline. Уточни линтер, тесты, идентичность артефакта, секреты, миграции, smoke tests и согласования. Один артефакт исключает различия от повторной сборки, но настройки каждой среды всё равно нужно проверить. Откат приложения может не отменить миграцию базы.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/devops/comments/cvwdjo/). **Technical reference / Справка:** [GitHub Actions concepts](https://docs.github.com/en/actions/get-started/understand-github-actions).

## 7. What is the difference between Git, GitHub Actions, and GitLab CI/CD? / Чем отличаются Git, GitHub Actions и GitLab CI/CD?

### 🇬🇧 English

#### Interview answer

> Git tracks versions. GitHub Actions and GitLab CI/CD automate workflows such as builds, tests, and deployment, using their own configuration and runners.

#### Details

GitHub is not Git, and GitLab is not GitLab CI/CD alone.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Git хранит версии. GitHub Actions и GitLab CI/CD автоматизируют сборку, тесты и развёртывание через свои настройки и runner.

#### Подробнее

GitHub — не то же самое, что Git, а GitLab не сводится к CI/CD.

**Interview evidence / Источник вопроса:** [Candidate lists these exact comparisons](https://www.reddit.com/r/devops/comments/1r98h8f/juniorr_devops_interview_experience_questions_i/). **Technical references / Справка:** [GitHub Actions](https://docs.github.com/en/actions/get-started/understand-github-actions), [GitLab CI/CD](https://docs.gitlab.com/ci/).

## 8. How would you improve an existing pipeline? / Как улучшить существующий pipeline?

### 🇬🇧 English

#### Interview answer

> I would measure delays and failures first, then improve the bottleneck. Parallel checks and caching help only if required correctness and security checks remain intact.

#### Details

Never optimize away a security or correctness gate just to make the pipeline green faster.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Сначала я измерю задержки и сбои, затем исправлю узкое место. Параллельные проверки и кеш не должны убирать необходимые проверки корректности и безопасности.

#### Подробнее

Не следует убирать проверку безопасности или корректности только ради ускорения зелёного статуса.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/devops/comments/dxo6pt/). **Technical reference / Справка:** [GitLab pipeline efficiency](https://docs.gitlab.com/ci/pipelines/pipeline_efficiency/).

## 9. A pipeline fails intermittently. What do you investigate? / Pipeline иногда падает. Что проверите?

### 🇬🇧 English

#### Interview answer

> I would compare successful and failed runs: logs, environment, dependencies, external services, and test data. Retries alone do not fix the underlying cause.

#### Details

Retries can reduce disruption temporarily but can also hide defects. Distinguish infrastructure failure from application-test failure.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я сравню успешные и неудачные запуски: логи, окружение, зависимости, внешние сервисы и тестовые данные. Повторы сами по себе не устраняют причину.

#### Подробнее

Повторный запуск может временно помочь, но способен скрыть ошибку. Нужно отличать сбой инфраструктуры от сбоя теста.

**Adapted scenario / Адаптированный сценарий:** [Published questions about maintaining and diagnosing pipelines](https://www.reddit.com/r/devopsjobs/comments/1qepvk2/devops_interview_questions_recently_attended/). Intermittent failure is a practice variant, not the exact prompt. / Нестабильное падение — вариант для тренировки, не дословное условие. **Technical reference / Справка:** [GitHub Actions workflow run logs](https://docs.github.com/en/actions/how-tos/monitor-workflows/use-workflow-run-logs).

## 10. How do you ensure the integrity of a CI/CD pipeline? / Как обеспечить целостность CI/CD pipeline?

### 🇬🇧 English

#### Interview answer

> I would protect changes and credentials, minimize workflow permissions, and verify artifact provenance. Deployment must use the intended, tested artifact.

#### Details

Use reviewed workflow changes, branch protection, least-privilege tokens, isolated runners, verified dependencies, and artifact provenance. Pin third-party Actions to a reviewed full commit SHA and keep it updated. Never execute untrusted pull-request code with privileged credentials; secret masking is not a complete defense. Document trust boundaries and approvals.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я защищу изменения и учётные данные, ограничу права workflow и проверю происхождение артефакта. Развёртываться должен именно нужный проверенный артефакт.

#### Подробнее

Нужны ревью workflow, защита веток, минимальные права токенов, изоляция runner, проверенные зависимости и происхождение артефактов. Сторонние Actions закрепляй на проверенном полном SHA коммита и обновляй его. Нельзя выполнять недоверенный код pull request с привилегированными учётными данными; маскирование секретов не даёт полной защиты. Опиши границы доверия и согласования.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/devops/comments/1988j1q/). **Technical reference / Справка:** [Secure use of GitHub Actions](https://docs.github.com/en/actions/reference/security/secure-use).
