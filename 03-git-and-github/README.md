# Git for Technical Writer Interviews

A cheat sheet on core Git questions for junior and middle technical writer interviews.

It focuses on basic, practical topics that are useful for interviews and everyday Docs-as-Code workflows.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — quick recall, interview answer, details.
- 🇷🇺 **Русский** — быстро вспомнить, ответ на собеседовании, подробнее.

---

## 1. What is Git and why is it used? / Что такое Git и зачем он нужен?

### 🇬🇧 English

#### Quick recall

**Git is a distributed version control system. It tracks history and helps multiple people work safely on the same project.**

#### Interview answer

> Git is a distributed version control system. It lets us track project history, create separate branches for tasks, compare versions, restore previous states, and combine work from multiple contributors.

#### Details

Git is commonly used for source code, but it also works very well for text-based documentation. It records not only the current state but also the history of changes.

### 🇷🇺 Русский

#### Быстро вспомнить

**Git — распределенная система контроля версий. Она хранит историю изменений и помогает нескольким людям безопасно работать над одним проектом.**

#### Ответ на собеседовании

> Git — это распределенная система контроля версий. С его помощью можно сохранять историю изменений проекта, создавать отдельные ветки для задач, сравнивать версии, возвращаться к предыдущим состояниям и объединять работу нескольких участников.

#### Подробнее

Git чаще всего используют для исходного кода, но он отлично подходит и для текстовой документации. В отличие от обычного хранения файлов, Git показывает не только текущую версию, но и историю: что изменилось, кем и когда.

---

## 2. Git vs GitHub or GitLab / Чем Git отличается от GitHub или GitLab?

### 🇬🇧 English

#### Quick recall

**Git is the version control system itself. GitHub and GitLab are platforms for hosting Git repositories and collaborating around them.**

#### Interview answer

> Git works locally and manages project history. GitHub and GitLab host remote Git repositories and add collaboration features such as pull or merge requests, reviews, issues, CI/CD, and access control.

#### Details

Git does not require GitHub or GitLab. Other hosting options include Bitbucket and self-hosted Git servers.

### 🇷🇺 Русский

#### Быстро вспомнить

**Git — сама система контроля версий. GitHub и GitLab — платформы, на которых можно хранить Git-репозитории и организовывать совместную работу.**

#### Ответ на собеседовании

> Git работает локально и управляет версиями проекта. GitHub и GitLab — сервисы вокруг Git: они хранят удаленные репозитории и добавляют pull или merge requests, review, issues, CI/CD и управление доступом.

#### Подробнее

Git можно использовать вообще без GitHub или GitLab. Также существуют Bitbucket и собственные Git-серверы.

---

## 3. What is a Git repository? Local vs remote / Что такое Git-репозиторий? Чем локальный отличается от удаленного?

### 🇬🇧 English

#### Quick recall

**A repository is a project managed by Git together with its history. A local repository is on your computer; a remote repository is hosted elsewhere, for example on GitHub.**

#### Interview answer

> A Git repository contains project files and their version history. I work in a local repository on my computer, while a remote repository is used to exchange changes with the team. The remote a project was cloned from is commonly named `origin`.

#### Details

A local repository can have multiple remotes. `origin` is a conventional name, not a special repository type.

### 🇷🇺 Русский

#### Быстро вспомнить

**Репозиторий — проект под управлением Git вместе с его историей. Локальный находится на компьютере, удаленный — на сервере, например GitHub.**

#### Ответ на собеседовании

> Git-репозиторий содержит файлы проекта и историю их изменений. Я работаю с локальным репозиторием на своем компьютере, а удаленный репозиторий используется для обмена изменениями с командой. Часто удаленный репозиторий, из которого проект клонировали, называется `origin`.

#### Подробнее

У одного локального репозитория может быть несколько remote. `origin` — распространенное имя, а не специальный тип репозитория.

---

## 4. What is a commit? / Что такое commit?

### 🇬🇧 English

#### Quick recall

**A commit is a saved point in Git history that records a selected set of changes.**

#### Interview answer

> A commit records staged changes in the local repository history. It has a unique identifier, author, timestamp, and commit message describing the purpose of the change.

#### Details

A commit is best thought of as a meaningful step in project history rather than an automatic file save.

### 🇷🇺 Русский

#### Быстро вспомнить

**Commit — сохраненная точка в истории Git, которая фиксирует подготовленный набор изменений.**

#### Ответ на собеседовании

> Commit фиксирует выбранные изменения в истории локального репозитория. У него есть уникальный идентификатор, автор, время и commit message, который кратко описывает смысл изменения.

#### Подробнее

Commit лучше воспринимать как осмысленный шаг в истории проекта, а не как обычное автоматическое сохранение файла. Например: `docs: clarify OAuth setup`.

---

## 5. What is a branch and why use branches? / Что такое branch и зачем нужны ветки?

### 🇬🇧 English

#### Quick recall

**A branch is a separate line of work in a repository. It allows changes to be developed independently from the main branch.**

#### Interview answer

> A branch isolates work on a specific task, such as a feature or documentation update. I can create a branch from `main`, make changes there, and merge them after review.

#### Details

Branches allow contributors to work in parallel without putting unfinished changes directly into the stable main branch.

### 🇷🇺 Русский

#### Быстро вспомнить

**Ветка — отдельная линия работы над проектом. Она позволяет делать изменения независимо от основной ветки.**

#### Ответ на собеседовании

> Branch позволяет изолировать работу над конкретной задачей, например новой функцией или обновлением документации. Я могу создать ветку от `main`, сделать изменения и после проверки объединить их с основной веткой.

#### Подробнее

Ветки позволяют нескольким людям работать параллельно и не вносить незавершенные изменения прямо в стабильный `main`.

---

## 6. What does a typical Git workflow look like? / Как выглядит обычный workflow в Git?

### 🇬🇧 English

#### Quick recall

**A common workflow is: update the repository → create a branch → edit files → `add` → `commit` → `push` → pull request → review → merge.**

#### Interview answer

> In a typical team workflow, I update the project, create a separate branch, make and verify changes, stage them, commit and push the branch. Then I open a pull request, go through review, and merge the approved changes into `main`.

#### Details

Exact rules vary by team, but `branch → edit → add → commit → push → PR → review → merge` is a common flow.

### 🇷🇺 Русский

#### Быстро вспомнить

**Обычно: получить актуальный репозиторий → создать ветку → изменить файлы → `add` → `commit` → `push` → pull request → review → merge.**

#### Ответ на собеседовании

> В обычном командном workflow я сначала получаю актуальную версию проекта, создаю отдельную ветку, меняю и проверяю файлы, добавляю нужные изменения в staging area, делаю commit и push. Затем открываю pull request, прохожу review и после одобрения изменения объединяются с `main`.

#### Подробнее

Конкретные правила отличаются между командами, но схема `branch → edit → add → commit → push → PR → review → merge` очень распространена.

---

## 7. Working directory, staging area, and repository / Что такое working directory, staging area и repository?

### 🇬🇧 English

#### Quick recall

**The working directory contains the files I am editing, the staging area contains changes selected for the next commit, and the repository contains committed history.**

#### Interview answer

> Changes first appear in the working directory. `git add` selects changes for the staging area, and `git commit` records that staged set in the local repository history.

#### Details

A useful model is: `Working directory → git add → Staging area → git commit → Repository`.

### 🇷🇺 Русский

#### Быстро вспомнить

**Working directory — файлы, которые я сейчас редактирую; staging area — изменения для следующего commit; repository — уже сохраненная история.**

#### Ответ на собеседовании

> Изменения сначала появляются в working directory. Командой `git add` я выбираю, какие из них попадут в staging area. Затем `git commit` сохраняет подготовленный набор в локальную историю репозитория.

#### Подробнее

Полезная схема: `Working directory → git add → Staging area → git commit → Repository`. Именно staging позволяет не коммитить автоматически все измененные файлы.

---

## 8. What are merge and a pull request? / Что такое merge и pull request?

### 🇬🇧 English

#### Quick recall

**Merge combines branches. A pull request is a proposal to review changes from one branch and merge them into another.**

#### Interview answer

> `git merge` combines branch histories. In team workflows, a pull request is often opened first so reviewers can inspect the diff, leave comments, request changes, run automated checks, and approve the merge.

#### Details

A pull request is a hosting-platform feature rather than a core Git command. GitLab commonly calls the equivalent a Merge Request.

### 🇷🇺 Русский

#### Быстро вспомнить

**Merge объединяет изменения веток. Pull request — предложение проверить изменения одной ветки и объединить их с другой.**

#### Ответ на собеседовании

> `git merge` объединяет историю двух веток. В командной работе перед merge часто создают pull request: коллеги смотрят diff, оставляют комментарии, просят исправления, запускаются автоматические проверки, а после одобрения изменения объединяются.

#### Подробнее

Pull request — функция GitHub и похожих платформ, а не отдельная базовая команда Git. В GitLab аналог обычно называется Merge Request.

---

## 9. What is a merge conflict and how do you resolve it? / Что такое merge conflict и как его решить?

### 🇬🇧 English

#### Quick recall

**A merge conflict occurs when Git cannot automatically decide how to combine incompatible changes.**

#### Interview answer

> A conflict often happens when two branches modify the same part of a file. Git marks the conflicting sections. I resolve it by choosing the correct final content, removing conflict markers, verifying the result, staging the file with `git add`, and completing the merge.

#### Details

A conflict is a normal collaboration situation. The important part is understanding both changes rather than blindly keeping one version.

### 🇷🇺 Русский

#### Быстро вспомнить

**Merge conflict возникает, когда Git не может автоматически решить, какие несовместимые изменения нужно сохранить.**

#### Ответ на собеседовании

> Конфликт часто возникает, когда две ветки изменили один и тот же участок файла. Git отмечает конфликтующие части. Нужно вручную определить правильный итоговый вариант, удалить конфликтные маркеры, проверить файл, выполнить `git add` и завершить merge.

#### Подробнее

Конфликт — нормальная ситуация совместной работы. В документации особенно важно не просто выбрать «свою» версию, а понять смысл обеих правок.

---

## 10. `git fetch` vs `git pull` / Чем `git fetch` отличается от `git pull`?

### 🇬🇧 English

#### Quick recall

**`git fetch` downloads remote commits and references without changing the current branch. `git pull` downloads changes and immediately integrates them.**

#### Interview answer

> `git fetch` updates information from the remote so I can inspect incoming changes first. `git pull` generally performs a fetch followed by a merge or rebase, depending on configuration.

#### Details

In short: `fetch` gets the changes; `pull` gets and integrates them.

### 🇷🇺 Русский

#### Быстро вспомнить

**`git fetch` получает информацию и commits с remote, но не меняет текущую ветку. `git pull` получает изменения и сразу интегрирует их в текущую ветку.**

#### Ответ на собеседовании

> `git fetch` обновляет данные об удаленном репозитории, поэтому я могу сначала посмотреть, что изменилось. `git pull` обычно выполняет fetch, а затем merge или rebase в зависимости от настройки.

#### Подробнее

Коротко: `fetch` — получить и посмотреть; `pull` — получить и применить к текущей ветке.

---

## 11. Merge vs rebase / Чем merge отличается от rebase?

### 🇬🇧 English

#### Quick recall

**Both integrate changes, but merge preserves the branch history while rebase reapplies commits on top of another branch and rewrites history.**

#### Interview answer

> Merge combines two lines of history and may create a merge commit. Rebase reapplies my branch commits on top of another base, creating a more linear history. Because rebase rewrites history, it should be used carefully with already shared commits.

#### Details

For a junior or middle interview, understanding this principle and the risk of rewriting shared history is usually more important than advanced rebase options.

### 🇷🇺 Русский

#### Быстро вспомнить

**Оба объединяют изменения, но merge сохраняет разветвленную историю, а rebase переносит commits поверх другой ветки и переписывает историю.**

#### Ответ на собеседовании

> Merge объединяет две линии истории и может создать merge commit. Rebase берет commits моей ветки и повторно применяет их поверх другой базы, поэтому история становится линейнее. Rebase переписывает историю, поэтому с общими уже опубликованными commits его используют осторожно.

#### Подробнее

Для junior/middle достаточно понимать принцип и главное правило: не переписывать через rebase общую историю, с которой уже работают другие люди.

---

## 12. How do you undo changes? `revert`, `reset`, and `restore` / Как отменять изменения? `revert`, `reset` и `restore`

### 🇬🇧 English

#### Quick recall

**The correct method depends on the state: `restore` for uncommitted file changes, `reset` for local history, and `revert` for safely undoing a shared commit.**

#### Interview answer

> `git restore` can discard working-directory changes or unstage files. `git reset` moves the branch pointer and can rewrite local history. `git revert` creates a new commit that reverses an earlier commit, so it is commonly used for already shared history.

#### Details

A good interview answer first asks whether the commit has already been pushed. `reset --hard` requires care because it can discard uncommitted work.

### 🇷🇺 Русский

#### Быстро вспомнить

**Способ зависит от состояния изменений: `restore` — для незакоммиченных файлов, `reset` — для локальной истории, `revert` — безопасная отмена уже опубликованного commit.**

#### Ответ на собеседовании

> `git restore` может отменить изменения в working directory или убрать файл из staging. `git reset` перемещает указатель ветки и может переписать локальную историю. `git revert` создает новый commit, который отменяет изменения предыдущего, поэтому его обычно используют для уже опубликованной общей истории.

#### Подробнее

На интервью хороший ответ начинается с уточнения: commit уже был отправлен в remote или еще нет? `reset --hard` требует осторожности, потому что может уничтожить незакоммиченные изменения.

---

## 13. What is `.gitignore`? / Что такое `.gitignore`?

### 🇬🇧 English

#### Quick recall

**`.gitignore` defines patterns for files and directories that Git should not start tracking.**

#### Interview answer

> It commonly contains temporary files, dependencies, build artifacts, IDE-specific files, and local environment files so they do not clutter the repository.

#### Details

Examples include `node_modules/`, `__pycache__/`, and `.DS_Store`. Secrets should not be committed. Adding an already tracked file to `.gitignore` does not remove it from history.

### 🇷🇺 Русский

#### Быстро вспомнить

**`.gitignore` задает правила для файлов и каталогов, которые Git не должен начинать отслеживать.**

#### Ответ на собеседовании

> В `.gitignore` обычно помещают временные файлы, зависимости, build artifacts, настройки IDE и локальные файлы окружения. Это помогает не засорять репозиторий ненужными или машинно-зависимыми файлами.

#### Подробнее

Например: `node_modules/`, `__pycache__/`, `.DS_Store`. Секреты нельзя коммитить. Если файл уже отслеживается Git, простое добавление его в `.gitignore` не удалит его из истории.

---

## 14. How does a technical writer use Git and Docs as Code? / Как технический писатель использует Git и Docs as Code?

### 🇬🇧 English

#### Quick recall

**In Docs-as-Code, documentation is stored as text-based source files and follows a development-like workflow using Git, branches, commits, pull requests, reviews, and automated checks.**

#### Interview answer

> A technical writer can edit Markdown in a Git repository, create a task-specific branch, commit the changes, and open a pull request. Developers can review technical accuracy, while CI can check links, style, or documentation builds.

#### Details

Git provides documentation version history, useful diffs and reviews, links documentation changes to product work, and makes previous states recoverable.

### 🇷🇺 Русский

#### Быстро вспомнить

**В Docs as Code документация хранится как текстовые исходники и проходит похожий на разработку workflow: Git, ветки, commits, pull requests, review и автоматические проверки.**

#### Ответ на собеседовании

> Технический писатель может редактировать Markdown в Git-репозитории, создавать отдельную ветку под задачу, делать commits и pull request. Разработчики проверяют техническую точность через review, а CI может автоматически проверить ссылки, стиль или сборку документации.

#### Подробнее

Git дает документации историю версий, удобные diff и review, возможность связать обновление docs с изменением продукта и при необходимости вернуться к предыдущему состоянию.

---

## 15. What is `git push --force` and why is it risky? / Что такое `git push --force` и почему с ним нужно быть осторожным?

### 🇬🇧 English

#### Quick recall

**`git push --force` makes the remote accept local history even when it is not a normal continuation of the remote branch. It can overwrite other people's commits.**

#### Interview answer

> Force push may be needed after history-rewriting operations such as rebase. On a shared branch it is dangerous because remote history can be replaced by the local version, potentially removing other contributors' commits from that branch.

#### Details

`git push --force-with-lease` is often safer because it checks that the remote has not changed unexpectedly. For a junior or middle interview, understanding why force push is dangerous matters more than memorizing every option.

### 🇷🇺 Русский

#### Быстро вспомнить

**`git push --force` заставляет remote принять локальную историю даже когда она не является обычным продолжением удаленной истории. Так можно перезаписать чужие commits.**

#### Ответ на собеседовании

> Force push используют после операций, которые переписывают историю, например rebase. Но на общей ветке он опасен: удаленная история может быть заменена локальной, и чужая работа станет недоступна из этой ветки. Поэтому его применяют только когда понимают последствия и правила команды.

#### Подробнее

Более безопасный вариант во многих случаях — `git push --force-with-lease`: он проверяет, что remote не изменился неожиданно с момента последнего получения данных. Для junior/middle важнее знать риск force push, чем помнить все ключи.

---

## 16. What basic Git commands do you know? / Какие основные команды Git вы знаете?

### 🇬🇧 English

#### Quick recall

**For everyday work, it is enough to understand about ten core commands for getting a repository, checking state, working with branches, recording changes, synchronizing, and merging.**

#### Interview answer

> In my everyday workflow, I commonly use `git clone`, `git status`, `git switch`, `git add`, `git commit`, `git pull`, `git fetch`, `git push`, `git merge`, and `git log`. I think it is more important to understand where each command fits into the workflow than to memorize a large command list.

#### Main commands

| Command | What it does |
|---|---|
| `git clone <url>` | Creates a local copy of a remote repository |
| `git status` | Shows the current branch and the state of modified, staged, and untracked files |
| `git switch <branch>` | Switches branches; `git switch -c <name>` creates and switches to a new one |
| `git add <file>` | Adds selected changes to the staging area |
| `git commit -m "message"` | Records staged changes as a new commit |
| `git pull` | Gets remote changes and integrates them into the current branch |
| `git fetch` | Downloads remote changes without modifying the current branch |
| `git push` | Sends local commits to a remote repository |
| `git merge <branch>` | Integrates the specified branch into the current branch |
| `git log` | Displays commit history |

#### Details

A typical documentation workflow can look like this:

```text
git clone
→ git switch -c docs/update-guide
→ edit files
→ git status
→ git add
→ git commit
→ git push
→ Pull Request
→ Review
→ Merge
```

`git pull` and `git fetch` are used for synchronization with the remote, while `git log` helps inspect history.

### 🇷🇺 Русский

#### Быстро вспомнить

**Для повседневной работы достаточно уверенно понимать примерно 10 команд: получить репозиторий, посмотреть состояние, создать ветку, подготовить и сохранить изменения, синхронизироваться и объединить работу.**

#### Ответ на собеседовании

> В повседневном workflow я чаще всего использую `git clone`, `git status`, `git switch`, `git add`, `git commit`, `git pull`, `git fetch`, `git push`, `git merge` и `git log`. Важно понимать не только синтаксис команд, но и то, на каком этапе workflow они используются.

#### Основные команды

| Команда | Что делает |
|---|---|
| `git clone <url>` | Создает локальную копию удаленного репозитория |
| `git status` | Показывает текущую ветку и состояние измененных, staged и untracked файлов |
| `git switch <branch>` | Переключает на другую ветку; `git switch -c <name>` создает новую и переключается на нее |
| `git add <file>` | Добавляет выбранные изменения в staging area |
| `git commit -m "message"` | Сохраняет staged changes как новый commit |
| `git pull` | Получает изменения из remote и интегрирует их в текущую ветку |
| `git fetch` | Получает новые данные из remote без изменения текущей ветки |
| `git push` | Отправляет локальные commits в remote repository |
| `git merge <branch>` | Объединяет изменения указанной ветки с текущей |
| `git log` | Показывает историю commits |

#### Подробнее

Типичная последовательность для документации:

```text
git clone
→ git switch -c docs/update-guide
→ edit files
→ git status
→ git add
→ git commit
→ git push
→ Pull Request
→ Review
→ Merge
```

`git pull` и `git fetch` используются для синхронизации с remote, а `git log` — чтобы посмотреть историю.

---

## Core flow / Главная схема

### 🇬🇧 English

```text
Working directory
      ↓ git add
Staging area
      ↓ git commit
Local repository
      ↓ git push
Remote repository
```

Team workflow:

```text
main → branch → edit → add → commit → push → Pull Request → Review → Merge
```

### 🇷🇺 Русский

```text
Working directory
      ↓ git add
Staging area
      ↓ git commit
Local repository
      ↓ git push
Remote repository
```

Командная работа:

```text
main → branch → edit → add → commit → push → Pull Request → Review → Merge
```
