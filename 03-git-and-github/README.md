# Git for Technical Writer Interviews

A cheat sheet on core Git questions for junior and middle technical writer interviews.

It focuses on basic, practical topics that are useful for interviews and everyday Docs-as-Code workflows.

Each question contains two separate language blocks. English is the primary version and comes first:

- 🇬🇧 **English** — short interview answer, details.
- 🇷🇺 **Русский** — короткий ответ на собеседовании, подробнее.

---

## 1. What is Git and why is it used? / Что такое Git и зачем он нужен?

### 🇬🇧 English

#### Interview answer

> Git is a distributed version-control system. It records project history and helps people compare, combine, and restore versions.

#### Details

Git is commonly used for source code, but it also works very well for text-based documentation. It records not only the current state but also the history of changes.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Git — распределённая система контроля версий. Она хранит историю проекта и помогает сравнивать, объединять и восстанавливать версии.

#### Подробнее

Git чаще всего используют для исходного кода, но он отлично подходит и для текстовой документации. В отличие от обычного хранения файлов, Git показывает не только текущую версию, но и историю: что изменилось, кем и когда.

---

## 2. Git vs GitHub or GitLab / Чем Git отличается от GitHub или GitLab?

### 🇬🇧 English

#### Interview answer

> Git manages version history. GitHub and GitLab host Git repositories and add collaboration, review, and automation tools.

#### Details

Git does not require GitHub or GitLab. Other hosting options include Bitbucket and self-hosted Git servers.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Git управляет историей версий. GitHub и GitLab хранят Git-репозитории и добавляют совместную работу, ревью и автоматизацию.

#### Подробнее

Git можно использовать вообще без GitHub или GitLab. Также существуют Bitbucket и собственные Git-серверы.

---

## 3. What is a Git repository? Local vs remote / Что такое Git-репозиторий? Чем локальный отличается от удаленного?

### 🇬🇧 English

#### Interview answer

> A repository stores versioned project snapshots and history. A local repository is my copy; a remote is another repository used to exchange changes.

#### Details

A local repository can have multiple remotes. `origin` is a conventional name, not a special type. A remote can even be another directory on the same machine. The working tree is distinct from the repository data; bare repositories, commonly used on servers, have no checked-out working tree.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Репозиторий хранит версии проекта и их историю. Локальный репозиторий — моя копия, remote — другой репозиторий для обмена изменениями.

#### Подробнее

У локального репозитория может быть несколько remote. `origin` — условное имя, а не специальный тип. Remote может быть даже другим каталогом на той же машине. Рабочая директория отличается от данных репозитория; bare-репозитории, часто используемые на серверах, не имеют рабочей директории.

---

## 4. What is a commit? / Что такое commit?

### 🇬🇧 English

#### Interview answer

> A commit records a project snapshot from the staging area, with metadata and links to parent commits. Committing is local; publishing requires a push.

#### Details

A commit is best thought of as a meaningful step in project history rather than an automatic file save.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Коммит сохраняет снимок проекта из staging area, метаданные и ссылки на родительские коммиты. Коммит создаётся локально; для публикации нужен push.

#### Подробнее

Commit лучше воспринимать как осмысленный шаг в истории проекта, а не как обычное автоматическое сохранение файла. Например: `docs: clarify OAuth setup`.

---

## 5. What is a branch and why use branches? / Что такое branch и зачем нужны ветки?

### 🇬🇧 English

#### Interview answer

> A branch is a movable reference to a commit. It lets a task develop along its own line of history before integration.

#### Details

A branch name points to a commit and normally advances with each new commit. It does not copy the entire project into another directory. Uncommitted edits belong to the working tree: switching branches can carry them along or be blocked to prevent overwriting them.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Ветка — перемещаемая ссылка на коммит. Она позволяет вести отдельную линию разработки задачи до объединения изменений.

#### Подробнее

Имя ветки указывает на коммит и обычно перемещается после каждого нового коммита. Весь проект в отдельный каталог не копируется. Незакоммиченные правки принадлежат рабочей директории: при переключении они могут перейти с тобой, а при риске перезаписи Git запретит переключение.

---

## 6. What does a typical Git workflow look like? / Как выглядит обычный workflow в Git?

### 🇬🇧 English

#### Interview answer

> I would create a branch, edit and verify files, stage and commit changes, then push and open a pull request for review and merging.

#### Details

Exact rules vary by team, but `branch → edit → add → commit → push → PR → review → merge` is a common flow.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я создам ветку, изменю и проверю файлы, подготовлю коммит, отправлю изменения и открою pull request для ревью и слияния.

#### Подробнее

Конкретные правила отличаются между командами, но схема `branch → edit → add → commit → push → PR → review → merge` очень распространена.

---

## 7. Working directory, staging area, and repository / Что такое working directory, staging area и repository?

### 🇬🇧 English

#### Interview answer

> The working tree holds editable files; the staging area prepares the next snapshot; the repository stores committed history.

#### Details

A useful model is `working tree → git add → staging area → git commit → repository`. Staging captures the content at the time of `git add`; later edits need another add. `git diff` shows unstaged changes; `git diff --staged` shows what the next commit would change.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Рабочая директория содержит редактируемые файлы; staging area готовит следующий снимок; репозиторий хранит историю коммитов.

#### Подробнее

Схема: `рабочая директория → git add → staging area → git commit → репозиторий`. В staging попадает содержимое на момент `git add`; последующие правки нужно добавить снова. `git diff` показывает неподготовленные правки, `git diff --staged` — изменения будущего коммита.

---

## 8. What are merge and a pull request? / Что такое merge и pull request?

### 🇬🇧 English

#### Interview answer

> Merge integrates branch histories. A pull request is a hosting-platform proposal to review and merge changes, not a Git command.

#### Details

A pull request is a hosting-platform feature rather than a core Git command. GitLab commonly calls the equivalent a Merge Request.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Merge объединяет историю веток. Pull request — предложение проверить и объединить изменения на платформе хостинга, а не команда Git.

#### Подробнее

Pull request — функция GitHub и похожих платформ, а не отдельная базовая команда Git. В GitLab аналог обычно называется Merge Request.

---

## 9. What is a merge conflict and how do you resolve it? / Что такое merge conflict и как его решить?

### 🇬🇧 English

#### Interview answer

> A conflict means Git cannot combine changes automatically. I would resolve the intended result, verify it, stage the resolution, and complete the operation.

#### Details

Text conflicts often have markers such as `<<<<<<<`, `=======`, and `>>>>>>>`; binary and modify/delete conflicts may not. Inspect `git status`, resolve the intended result, and stage it. Complete a merge with a commit or continue a rebase with `git rebase --continue`, depending on the operation.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Конфликт означает, что Git не может автоматически объединить изменения. Я выберу правильный результат, проверю его, подготовлю разрешение конфликта и завершу операцию.

#### Подробнее

В текстовом конфликте часто есть маркеры `<<<<<<<`, `=======` и `>>>>>>>`; при конфликте бинарных файлов или изменения с удалением их может не быть. Проверь `git status`, согласуй итог и добавь его в staging. Merge завершается коммитом, rebase продолжается через `git rebase --continue`.

---

## 10. `git fetch` vs `git pull` / Чем `git fetch` отличается от `git pull`?

### 🇬🇧 English

#### Interview answer

> Fetch downloads remote updates without integrating them into my current branch. Pull fetches and then integrates, according to its options and configuration.

#### Details

Fetch normally updates remote-tracking refs such as `origin/main`, not the checked-out branch or its files. Pull then attempts integration: fast-forward, merge, or rebase according to its options. A fast-forward-only pull refuses divergent histories instead of merging them.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Fetch получает обновления без их объединения с текущей веткой. Pull получает и затем интегрирует их согласно параметрам и настройкам.

#### Подробнее

Fetch обычно обновляет remote-tracking ссылки вроде `origin/main`, а не текущую ветку и её файлы. Pull затем пытается интегрировать изменения: fast-forward, merge или rebase согласно настройкам. В режиме fast-forward-only расходящаяся история вызовет отказ, а не автоматическое слияние.

---

## 11. Merge vs rebase / Чем merge отличается от rebase?

### 🇬🇧 English

#### Interview answer

> Merge combines histories; rebase reapplies commits on a new base. Rebase can change commit IDs, so rewriting shared history requires coordination.

#### Details

A fast-forward merge moves the branch pointer without creating a merge commit. Rebase normally creates replacement commits with new IDs. Agree on the team's policy before rebasing commits that other people already use.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Merge объединяет историю; rebase повторно применяет коммиты поверх другой базы. Идентификаторы могут измениться, поэтому переписывание общей истории нужно согласовать.

#### Подробнее

При fast-forward merge указатель ветки перемещается без merge-коммита. Rebase обычно создаёт заменяющие коммиты с новыми ID. Перед переписыванием коммитов, которыми пользуются коллеги, нужно согласовать правила команды.

---

## 12. How do you undo changes? `revert`, `reset`, and `restore` / Как отменять изменения? `revert`, `reset` и `restore`

### 🇬🇧 English

#### Interview answer

> Restore restores files or unstages changes. Reset updates the index or moves HEAD, depending on its form. Revert records a new commit reversing an earlier change.

#### Details

First distinguish uncommitted edits, staged changes, and shared commits. `git restore --staged FILE` unstages without discarding working-tree edits. Path-form `git reset -- FILE` also updates the index without moving HEAD. Commit-form reset can move HEAD; `--hard` can destroy uncommitted work. Revert reverses a selected commit, not necessarily the latest, and may conflict.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Restore восстанавливает файлы или убирает изменения из staging. Reset меняет индекс или HEAD в зависимости от формы. Revert создаёт коммит с обратными изменениями.

#### Подробнее

Сначала различи незакоммиченные правки, staging и общие коммиты. `git restore --staged FILE` убирает из staging, сохраняя рабочие правки. Форма `git reset -- FILE` тоже меняет индекс, не перемещая HEAD. Reset на коммит может переместить HEAD; `--hard` способен уничтожить незакоммиченную работу. Revert отменяет выбранный, не обязательно последний коммит и может вызвать конфликт.

---

## 13. What is `.gitignore`? / Что такое `.gitignore`?

### 🇬🇧 English

#### Interview answer

> .gitignore contains patterns for files Git should normally leave untracked. It does not stop tracking files already in the repository.

#### Details

Examples of ignore patterns include `node_modules/`, `__pycache__/`, and `.DS_Store`. The file contains patterns, not the ignored files themselves. `git rm --cached FILE` can stop tracking a file in a new commit while retaining the local copy; it does not erase history. If a secret leaked, revoke or rotate it: ignore rules alone do not protect it.

### 🇷🇺 Русский

#### Ответ на собеседовании

> .gitignore содержит шаблоны файлов, которые Git обычно не должен начинать отслеживать. На уже отслеживаемые файлы это не действует.

#### Подробнее

Примеры шаблонов: `node_modules/`, `__pycache__/`, `.DS_Store`. В файле лежат шаблоны, а не сами игнорируемые файлы. `git rm --cached FILE` позволяет прекратить отслеживание новым коммитом, оставив локальный файл, но не стирает историю. При утечке секрета его нужно отозвать или заменить: одного игнорирования недостаточно.

---

## 14. How does a technical writer use Git and Docs as Code? / Как технический писатель использует Git и Docs as Code?

### 🇬🇧 English

#### Interview answer

> A writer uses Git for documentation history and diffs. Pull requests and CI add review, checks, and a controlled publishing workflow.

#### Details

Git supplies history and diffs; hosting platforms add pull requests and review interfaces. CI is configured separately. Together they can connect documentation changes to product changes and release checks.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Техписатель использует Git для истории документации и сравнения правок. Pull request и CI добавляют ревью, проверки и управляемую публикацию.

#### Подробнее

Git предоставляет историю и diff; платформы хостинга добавляют pull request и интерфейс ревью. CI настраивается отдельно. Вместе они связывают изменения документации с изменениями продукта и проверками релиза.

---

## 15. What is `git push --force` and why is it risky? / Что такое `git push --force` и почему с ним нужно быть осторожным?

### 🇬🇧 English

#### Interview answer

> Force push permits a non-fast-forward branch update. It can remove other people's commits from the branch history, so it requires care and agreement.

#### Details

`--force-with-lease` checks an expected remote ref value before replacing it. It is safer than an unconditional force, but not a guarantee: background fetches can weaken the implicit expectation based on remote-tracking refs. Force does not bypass server permissions or protected-branch rules.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Force push допускает обновление ветки не по fast-forward. Чужие коммиты могут исчезнуть из её истории, поэтому нужны осторожность и согласование.

#### Подробнее

`--force-with-lease` проверяет ожидаемое значение удалённой ссылки перед заменой. Это безопаснее безусловного force, но не гарантия: фоновый fetch может ослабить неявную проверку по remote-tracking ссылкам. Force не обходит серверные права и защиту веток.

---

## 16. What basic Git commands do you know? / Какие основные команды Git вы знаете?

### 🇬🇧 English

#### Interview answer

> The basic flow is status and diff, add, commit, then push. Fetch and pull synchronize; switch changes branches; log shows history.

#### Details

##### Main commands

| Command | What it does |
|---|---|
| `git clone <url>` | Creates a local copy of a remote repository |
| `git status` | Shows the current branch and the state of modified, staged, and untracked files |
| `git diff` | Shows unstaged changes; `--staged` compares the index with HEAD |
| `git switch <branch>` | Switches branches; `git switch -c <name>` creates and switches to a new one |
| `git add <file>` | Adds selected changes to the staging area |
| `git commit -m "message"` | Records staged changes as a new commit |
| `git pull` | Gets remote changes and integrates them into the current branch |
| `git fetch` | Downloads remote changes without modifying the current branch |
| `git push` | Sends local commits to a remote repository |
| `git merge <branch>` | Integrates the specified branch into the current branch |
| `git log` | Displays commit history |

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

#### Ответ на собеседовании

> Базовая цепочка: status и diff, add, commit, затем push. Fetch и pull синхронизируют, switch переключает ветки, log показывает историю.

#### Подробнее

##### Основные команды

| Команда | Что делает |
|---|---|
| `git clone <url>` | Создает локальную копию удаленного репозитория |
| `git status` | Показывает текущую ветку и состояние измененных, staged и untracked файлов |
| `git diff` | Показывает неподготовленные правки; `--staged` сравнивает индекс с HEAD |
| `git switch <branch>` | Переключает на другую ветку; `git switch -c <name>` создает новую и переключается на нее |
| `git add <file>` | Добавляет выбранные изменения в staging area |
| `git commit -m "message"` | Сохраняет staged changes как новый commit |
| `git pull` | Получает изменения из remote и интегрирует их в текущую ветку |
| `git fetch` | Получает новые данные из remote без изменения текущей ветки |
| `git push` | Отправляет локальные commits в remote repository |
| `git merge <branch>` | Объединяет изменения указанной ветки с текущей |
| `git log` | Показывает историю commits |

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

## References / Источники

Technical review: 2026-11-03. / Техническая проверка: 2026-11-03.

- [Pro Git: Git's model](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F), [branches](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell).
- [git reset](https://git-scm.com/docs/git-reset), [git restore](https://git-scm.com/docs/git-restore), [git revert](https://git-scm.com/docs/git-revert).
- [gitignore](https://git-scm.com/docs/gitignore), [git pull](https://git-scm.com/docs/git-pull), [git push and force-with-lease](https://git-scm.com/docs/git-push).
