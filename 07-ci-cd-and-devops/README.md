# CI/CD and DevOps for Technical Writer Interviews

Five fundamentals and five questions/tasks traceable to published DevOps interview accounts. English is primary and precedes a separate Russian block. These accounts are not transcripts; task wording is condensed. A technical writer should understand and document the workflow, not pretend to be a release engineer.

---

**General questions / Общие вопросы**

## 1. What are CI, continuous delivery, and continuous deployment? / Что такое CI, continuous delivery и continuous deployment?

### 🇬🇧 English

#### Quick recall
**CI checks changes frequently; delivery keeps a releasable artifact ready; deployment releases automatically.**

#### Interview answer
> Continuous integration runs automated checks when changes are combined. Continuous delivery automates preparation and validation so a release can be approved and deployed. Continuous deployment goes one step further and releases every change that passes the required gates automatically.

#### Details
Teams use “CD” for both delivery and deployment. Ask which one they mean and which environments require approval.

### 🇷🇺 Русский

#### Быстро вспомнить
**CI часто проверяет изменения; delivery готовит релиз; deployment автоматически выпускает его.**

#### Ответ на собеседовании
> Непрерывная интеграция запускает проверки при объединении изменений. Непрерывная доставка готовит проверенный артефакт к выпуску, который может требовать подтверждения. Непрерывное развёртывание автоматически выпускает каждое изменение, прошедшее обязательные проверки.

#### Подробнее
Сокращение CD означает и delivery, и deployment. Лучше уточнить, какой процесс и какие ручные согласования приняты в команде.

**Interview evidence / Источник вопроса:** [Candidate reports being asked “What is CI/CD?”](https://www.reddit.com/r/devops/comments/1wygyop/how_to_actually_pass_interviews/). **Technical reference / Справка:** [GitLab CI/CD](https://docs.gitlab.com/ci/).

## 2. What are a pipeline, job, stage, and runner? / Что такое pipeline, job, stage и runner?

### 🇬🇧 English

#### Quick recall
**A pipeline is the workflow; jobs do work; stages organize ordering; runners execute jobs.**

#### Interview answer
> A pipeline starts on a configured event and consists of jobs such as build, test, and deploy. In GitLab, stages group jobs and commonly run in sequence, while a runner executes each job. Other CI systems use different terminology and dependency models.

#### Details
For GitHub Actions, distinguish workflow, job, step, and runner. Do not assume “stage” is a universal product term.

### 🇷🇺 Русский

#### Быстро вспомнить
**Pipeline — процесс, job — задача, stage — порядок групп задач, runner — исполнитель.**

#### Ответ на собеседовании
> Pipeline запускается по заданному событию и состоит из задач сборки, тестирования или выпуска. В GitLab задачи объединяются в стадии, которые обычно идут по порядку; runner выполняет задачи. В других системах названия и схема зависимостей могут отличаться.

#### Подробнее
В GitHub Actions используются workflow, job, step и runner. Не стоит переносить термин «stage» на любую платформу.

**Interview evidence / Источник вопроса:** [Candidate reports GitLab CI/CD questions](https://www.reddit.com/r/devops/comments/1r98h8f/juniorr_devops_interview_experience_questions_i/). **Technical references / Справка:** [GitLab pipelines](https://docs.gitlab.com/ci/pipelines/), [GitHub Actions](https://docs.github.com/en/actions/get-started/understand-github-actions).

## 3. What is a build artifact, and how is it different from a cache? / Что такое артефакт сборки и чем он отличается от кеша?

### 🇬🇧 English

#### Quick recall
**An artifact is an output to retain or pass on; a cache speeds repeated work.**

#### Interview answer
> A build artifact can be a package, binary, generated site, or test report produced by a job. Later jobs may download it. A cache normally stores reusable dependencies or intermediate data to make subsequent runs faster; it should not be the sole source of a required release artifact.

#### Details
Retention and access rules depend on the CI platform. In docs, say which job creates an artifact, where it is found, and how long it remains available.

### 🇷🇺 Русский

#### Быстро вспомнить
**Артефакт — результат работы, который сохраняют или передают дальше; кеш ускоряет повторные запуски.**

#### Ответ на собеседовании
> Артефактом может быть пакет, исполняемый файл, собранный сайт или отчёт о тестах. Следующие задачи могут его скачать. Кеш обычно содержит зависимости или промежуточные данные, чтобы ускорить сборку, и не должен быть единственным хранилищем обязательного результата релиза.

#### Подробнее
Срок хранения и доступ зависят от платформы. В документации нужно указать, какая задача создала артефакт, где его найти и когда он исчезнет.

**Interview evidence / Источник вопроса:** [Candidate reports being asked about GitLab artifacts](https://www.reddit.com/r/devops/comments/1r98h8f/juniorr_devops_interview_experience_questions_i/). **Technical references / Справка:** [GitLab job artifacts](https://docs.gitlab.com/ci/jobs/job_artifacts/), [GitLab caching](https://docs.gitlab.com/ci/caching/).

## 4. How does a change move from commit to production? / Как изменение доходит от коммита до production?

### 🇬🇧 English

#### Quick recall
**Trigger → validate → build → store → deploy → verify.**

#### Interview answer
> A commit or pull request triggers checks. After review and successful tests, CI builds a versioned artifact. The release process promotes that artifact through environments, performs required approvals, deploys it, and verifies the result. The exact gates are team-specific.

#### Details
Record the commit or artifact version, deployment target, owner, and rollback procedure. A successful job log does not necessarily prove the application works for users.

### 🇷🇺 Русский

#### Быстро вспомнить
**Событие → проверки → сборка → хранение → развёртывание → проверка.**

#### Ответ на собеседовании
> Коммит или pull request запускает проверки. После ревью и тестов CI создаёт версионированный артефакт. Релизный процесс проводит его через среды, согласования, развёртывание и проверку результата. Конкретные условия зависят от команды.

#### Подробнее
Нужно фиксировать версию, целевую среду, владельца процесса и способ отката. Зелёный статус задачи сам по себе не доказывает работоспособность приложения для пользователя.

**Interview evidence / Источник вопроса:** [Candidate describes a whiteboard pipeline-design interview](https://www.reddit.com/r/devops/comments/cvwdjo/). **Technical reference / Справка:** [GitHub Actions workflows](https://docs.github.com/en/actions/concepts/workflows-and-actions/workflows).

## 5. What does DevOps mean in this context? / Что в этом контексте означает DevOps?

### 🇬🇧 English

#### Quick recall
**A way of improving collaboration and feedback across development and operations, supported by automation.**

#### Interview answer
> DevOps is not a synonym for one CI product or one job title. It joins practices such as shared ownership, small changes, automated checks, observable releases, and fast feedback. For a writer, release notes, runbooks, and docs changes should participate in that same flow.

#### Details
Ask who owns deployment, incidents, and documentation updates; organizations implement DevOps differently.

### 🇷🇺 Русский

#### Быстро вспомнить
**Это совместная работа разработки и эксплуатации с быстрым циклом обратной связи и автоматизацией.**

#### Ответ на собеседовании
> DevOps — не название одного CI-инструмента и не обязательно отдельная должность. Это практики совместной ответственности, небольших изменений, автоматических проверок, наблюдаемого выпуска и быстрой обратной связи. Техписателю важно встроить в этот цикл документацию, release notes и инструкции для поддержки.

#### Подробнее
Уточняйте, кто отвечает за выпуск, инциденты и актуальность документации: процессы различаются.

**Interview evidence / Источник вопроса:** [DevOps interview discussion of pipeline design and ownership](https://www.reddit.com/r/devops/comments/dxo6pt/). **Technical reference / Справка:** [AWS introduction to DevOps](https://aws.amazon.com/devops/what-is-devops/).

---

**Published questions and tasks / Опубликованные вопросы и задания**

## 6. Design a pipeline for a Python web app from push to production. / Опишите pipeline для Python-приложения от push до production.

### 🇬🇧 English

#### Quick recall
**State triggers, quality gates, artifact, environments, and rollback.**

#### Interview answer
> I would run lint and tests on the pull request, build one identifiable artifact after merge, then deploy it to a test environment. After smoke tests and approval where required, I would promote the same artifact to production, monitor it, and retain a rollback path. I would clarify database migration and secret handling before calling the design complete.

#### Details
This is an outline, not a production-ready pipeline. The interview prompt in the account asks the candidate to walk through these decisions.

### 🇷🇺 Русский

#### Быстро вспомнить
**Назвать триггеры, проверки, артефакт, среды и откат.**

#### Ответ на собеседовании
> На pull request запущу линтер и тесты, после слияния соберу один идентифицируемый артефакт и развёрну его в тестовой среде. После короткой проверки и нужного согласования продвину тот же артефакт в production, проконтролирую состояние и сохраню возможность отката. Отдельно уточню миграции базы и работу с секретами.

#### Подробнее
Это схема для обсуждения, а не готовый production pipeline. Источник описывает именно задание пройти по решениям от push до выпуска.

**Interview evidence / Источник задания:** [Firsthand pipeline whiteboard account](https://www.reddit.com/r/devops/comments/cvwdjo/). **Technical reference / Справка:** [GitHub Actions concepts](https://docs.github.com/en/actions/get-started/understand-github-actions).

## 7. What is the difference between Git, GitHub Actions, and GitLab CI/CD? / Чем отличаются Git, GitHub Actions и GitLab CI/CD?

### 🇬🇧 English

#### Quick recall
**Git tracks history; GitHub and GitLab host collaboration; Actions and GitLab CI/CD automate workflows.**

#### Interview answer
> Git is the version-control system. GitHub Actions is GitHub's workflow automation service. GitLab CI/CD is GitLab's pipeline system. Both automation services can run checks and deployments, but their configuration, permissions, and runners differ. I would compare concrete requirements instead of claiming one is universally better.

#### Details
GitHub is not Git, and GitLab is not GitLab CI/CD alone.

### 🇷🇺 Русский

#### Быстро вспомнить
**Git хранит историю; GitHub и GitLab дают совместную работу; Actions и GitLab CI/CD автоматизируют процессы.**

#### Ответ на собеседовании
> Git — система контроля версий. GitHub Actions — сервис автоматизации GitHub, GitLab CI/CD — система pipeline в GitLab. Обе системы запускают проверки и развёртывание, но отличаются конфигурацией, правами и исполнителями. Сравнивать их стоит по конкретным требованиям.

#### Подробнее
GitHub — не то же самое, что Git, а GitLab не сводится к CI/CD.

**Interview evidence / Источник вопроса:** [Candidate lists these exact comparisons](https://www.reddit.com/r/devops/comments/1r98h8f/juniorr_devops_interview_experience_questions_i/). **Technical references / Справка:** [GitHub Actions](https://docs.github.com/en/actions/get-started/understand-github-actions), [GitLab CI/CD](https://docs.gitlab.com/ci/).

## 8. How would you improve an existing pipeline? / Как улучшить существующий pipeline?

### 🇬🇧 English

#### Quick recall
**Read the current flow, identify risk or delay, then change one thing with a measurable result.**

#### Interview answer
> I would map triggers, dependencies, test coverage, artifact handling, approvals, and deployment verification. Then I would ask where failures or delays occur. Possible improvements include parallel independent checks, better cache use, earlier feedback, and safer deployment gates, but only when evidence supports them.

#### Details
Never optimize away a security or correctness gate just to make the pipeline green faster.

### 🇷🇺 Русский

#### Быстро вспомнить
**Разобрать текущую схему, найти риск или задержку и измерить эффект изменения.**

#### Ответ на собеседовании
> Отмечу триггеры, зависимости, тесты, хранение артефактов, согласования и проверку после выпуска. Затем выясню, где возникают ошибки и задержки. Независимые проверки можно выполнять параллельно, кеш настроить лучше, а обратную связь получать раньше, но улучшение должно решать наблюдаемую проблему.

#### Подробнее
Не следует убирать проверку безопасности или корректности только ради ускорения зелёного статуса.

**Interview evidence / Источник задания:** [Candidate reports being asked to improve a drawn pipeline](https://www.reddit.com/r/devops/comments/dxo6pt/). **Technical reference / Справка:** [GitLab pipeline efficiency](https://docs.gitlab.com/ci/pipelines/pipeline_efficiency/).

## 9. A pipeline fails intermittently. What do you investigate? / Pipeline иногда падает. Что проверите?

### 🇬🇧 English

#### Quick recall
**Find the failing job, compare runs, and test for nondeterminism.**

#### Interview answer
> I would compare successful and failed job logs, runner images, dependency versions, external services, timing, and test data. If a test is flaky, I would isolate and fix it rather than normalizing retries. I would document a reproducible symptom and the verified cause.

#### Details
Retries can reduce disruption temporarily but can also hide defects. Distinguish infrastructure failure from application-test failure.

### 🇷🇺 Русский

#### Быстро вспомнить
**Найти падающую задачу, сравнить запуски и проверить нестабильные зависимости.**

#### Ответ на собеседовании
> Сравню логи успешного и неуспешного запусков, образы runner, версии зависимостей, внешние сервисы, тайминги и тестовые данные. Нестабильный тест нужно изолировать и исправить, а не считать повторы нормой. Причину зафиксирую только после проверки.

#### Подробнее
Повторный запуск может временно помочь, но способен скрыть ошибку. Нужно отличать сбой инфраструктуры от сбоя теста.

**Interview evidence / Источник задания:** [Reported interview questions about diagnosing pipeline issues](https://www.reddit.com/r/devopsjobs/comments/1qepvk2/devops_interview_questions_recently_attended/). **Technical reference / Справка:** [GitHub Actions workflow run logs](https://docs.github.com/en/actions/how-tos/monitor-workflows/use-workflow-run-logs).

## 10. How do you ensure the integrity of a CI/CD pipeline? / Как обеспечить целостность CI/CD pipeline?

### 🇬🇧 English

#### Quick recall
**Clarify the threat, then protect source, execution, secrets, artifacts, and deployments.**

#### Interview answer
> I would first ask whether “integrity” means resisting unauthorized changes, securing dependencies, preventing secret leaks, or proving that the deployed artifact is the tested one. Then I would describe controls such as review and branch protection, least-privilege tokens, pinned dependencies, isolated runners, artifact provenance, and deployment approvals.

#### Details
No single control proves the entire pipeline safe. For documentation, spell out trust boundaries and which credentials a workflow needs.

### 🇷🇺 Русский

#### Быстро вспомнить
**Уточнить угрозу и защитить код, выполнение, секреты, артефакты и выпуск.**

#### Ответ на собеседовании
> Сначала выясню, означает ли «целостность» защиту от несанкционированных изменений, подмены зависимостей, утечки секретов или гарантию, что выпущен именно проверенный артефакт. Затем назову ревью и защиту веток, минимальные права токенов, закрепление версий зависимостей, изоляцию runner, происхождение артефакта и согласование выпуска.

#### Подробнее
Одна мера не делает весь pipeline безопасным. В документации полезно явно показать границы доверия и нужные права.

**Interview evidence / Источник вопроса:** [Candidate reports being asked this exact question](https://www.reddit.com/r/devops/comments/1988j1q/). **Technical reference / Справка:** [Secure use of GitHub Actions](https://docs.github.com/en/actions/reference/security/secure-use).
