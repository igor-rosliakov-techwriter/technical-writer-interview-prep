# Kubernetes for Technical Writer Interviews

Five fundamentals and five troubleshooting scenarios. English comes first;
Russian follows. Technical explanations were reviewed against Kubernetes
documentation on 2026-11-03. The readiness exercise in question 9 was
reverified; several earlier interview-source links were inaccessible and
are marked unverified. Do not present those questions as confirmed transcripts.

Пять базовых вопросов и пять сценариев диагностики. Технические объяснения
сверены с документацией Kubernetes 2026-11-03. Задание о readiness в
вопросе 9 подтверждено повторно; недоступные старые источники отмечены.
Их формулировки нельзя выдавать за подтверждённые вопросы интервью.

---

**General questions / Общие вопросы**

## 1. What does Kubernetes do? / Зачем нужен Kubernetes?

### 🇬🇧 English

#### Interview answer

> Kubernetes manages containerized workloads toward a declared desired state. It schedules Pods and supports scaling, rollouts, and recovery from failures.

#### Details

It does not build container images or make an unhealthy application correct. Documentation must say what the cluster manages and what the application owner must configure.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Kubernetes управляет контейнеризированными нагрузками согласно заданному состоянию. Он размещает Pod, поддерживает масштабирование, обновление и восстановление после сбоев.

#### Подробнее

Kubernetes не собирает образы и не исправляет ошибки самого приложения. В документации важно отделять ответственность кластера от настроек приложения.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/kubernetes/comments/1twmuse/). **Technical reference / Справка:** [Kubernetes overview](https://kubernetes.io/docs/concepts/overview/).

## 2. How do a Pod, Deployment, and Service differ? / Чем различаются Pod, Deployment и Service?

### 🇬🇧 English

#### Interview answer

> A Pod runs one or more closely coupled containers. A Deployment manages replicated Pods; a Service provides a stable way to reach eligible backends.

#### Details

Do not call a Service a container or a Deployment a server. A Deployment is usually for stateless workloads; other controllers exist for different needs.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Pod запускает один или несколько тесно связанных контейнеров. Deployment управляет копиями Pod, Service предоставляет стабильный способ обращения к подходящим экземплярам.

#### Подробнее

Service — не контейнер, а Deployment — не сервер. Для других типов нагрузок существуют иные контроллеры.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/kubernetes/comments/1eial2s/). **Technical references / Справка:** [Pods](https://kubernetes.io/docs/concepts/workloads/pods/), [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/), [Services](https://kubernetes.io/docs/concepts/services-networking/service/).

## 3. What are a cluster, node, and control plane? / Что такое кластер, узел и control plane?

### 🇬🇧 English

#### Interview answer

> A cluster includes a control plane and nodes. The control plane coordinates desired state and scheduling; nodes run Pods.

#### Details

This is a conceptual map, not a claim that every cluster has identical topology. Managed Kubernetes can hide much of the control plane from users.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Кластер состоит из control plane и узлов. Control plane управляет желаемым состоянием и размещением, узлы выполняют Pod.

#### Подробнее

Реальная топология зависит от установки. В управляемом Kubernetes пользователь может не иметь прямого доступа к компонентам control plane.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/kubernetes/comments/1twmuse/). **Technical reference / Справка:** [Kubernetes components](https://kubernetes.io/docs/concepts/overview/components/).

## 4. How does a Service find Pods? / Как Service находит Pod?

### 🇬🇧 English

#### Interview answer

> Usually, a Service selects Pods by labels. EndpointSlices describe its backends; readiness and port configuration affect whether traffic reaches the application.

#### Details

Services can also exist without selectors, so “always” would be inaccurate. Check namespace, selector, Pod labels, readiness, and `port` versus `targetPort` when documenting a route.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Обычно Service выбирает Pod по меткам. EndpointSlice описывает конечные точки; готовность и настройки портов влияют на доставку трафика приложению.

#### Подробнее

Service бывает и без селектора. При проверке смотрим namespace, метки, готовность Pod, а также `port` и `targetPort`.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/devops/comments/198zj1m/). **Technical reference / Справка:** [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/).

## 5. What are ConfigMaps, Secrets, and probes? / Что такое ConfigMap, Secret и пробы?

### 🇬🇧 English

#### Interview answer

> ConfigMaps hold non-sensitive configuration; Secrets hold sensitive values. Readiness gates normal Service traffic, liveness detects when to restart, and startup allows initialization time.

#### Details

Base64 is encoding, not encryption. Secret storage needs encryption-at-rest configuration and restricted access; never paste real credentials into examples. ConfigMap values injected as environment variables do not refresh automatically: recreate the Pods to pick up new values.

A failed readiness probe normally removes a Pod from regular Service traffic without restarting it; special Service settings can override this. Startup probes delay liveness and readiness until startup succeeds. Repeated startup or liveness failures can cause a restart according to policy.

### 🇷🇺 Русский

#### Ответ на собеседовании

> ConfigMap хранит обычные настройки, Secret — чувствительные данные. Readiness регулирует обычный трафик Service, liveness определяет необходимость перезапуска, startup даёт время на запуск.

#### Подробнее

Base64 — кодирование, не шифрование. Для Secret нужны настройки шифрования при хранении и ограничения доступа; реальные ключи в примерах недопустимы. Значения ConfigMap в переменных окружения не обновляются автоматически: для новых значений Pod пересоздают.

Неуспешная readiness-проба обычно исключает Pod из обычного трафика Service, но не перезапускает его; особые настройки Service могут менять это поведение. Startup-проба откладывает liveness и readiness до успешного запуска. Повторные ошибки startup или liveness могут привести к перезапуску согласно политике.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/kubernetes/comments/1h2it1f/). **Technical references / Справка:** [ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/), [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/), [Probes](https://kubernetes.io/docs/concepts/workloads/pods/probes/).

---

**Practice scenarios; see source status / Сценарии: см. статус источника**

## 6. Explain how this Service manifest reaches Pods. / Объясните, как этот Service направляет запросы к Pod.

### 🇬🇧 English

#### Interview answer

> I would trace namespace, selector, Pod labels, endpoints, and targetPort. Valid YAML alone does not prove that the application is reachable.

#### Details

If the task gives no manifest, ask for it rather than inventing labels or port numbers.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я проверю namespace, селектор, метки Pod, конечные точки и targetPort. Корректный YAML сам по себе не доказывает доступность приложения.

#### Подробнее

Если манифест не дан, лучше запросить его, а не придумывать метки и порты.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/devops/comments/198zj1m/). **Technical reference / Справка:** [Services](https://kubernetes.io/docs/concepts/services-networking/service/).

## 7. A Pod is failing. Where do you start? / Pod не работает. С чего начнёте?

### 🇬🇧 English

#### Interview answer

> I would check Pod status, events, and container logs. For a restarted container, I would also inspect its previous logs before choosing a fix.

#### Details

Use `kubectl get pod NAME -n NS`, `kubectl describe pod NAME -n NS`, and `kubectl logs NAME -n NS -c CONTAINER`. Add `--previous` for the previous terminated container instance. Replace placeholders with actual names. A restart is not a universal fix; separate symptoms, checks, causes, and corrective actions.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я проверю статус Pod, события и логи контейнера. После перезапуска также посмотрю предыдущие логи, прежде чем выбирать исправление.

#### Подробнее

Команды: `kubectl get pod NAME -n NS`, `kubectl describe pod NAME -n NS`, `kubectl logs NAME -n NS -c CONTAINER`. Ключ `--previous` показывает логи предыдущего завершённого экземпляра контейнера. Подставь реальные имена. Перезапуск не универсален: разделяй симптомы, проверки, причины и действия.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/kubernetes/comments/1eial2s/). **Technical reference / Справка:** [Debug running Pods](https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/).

## 8. A Deployment's container crash-loops after an environment change. What do you check? / Контейнер после смены переменной окружения постоянно перезапускается. Что проверить?

### 🇬🇧 English

#### Interview answer

> I would compare the changed configuration with previous logs and startup requirements. If users are affected, I would coordinate recovery to a verified working configuration.

#### Details

`CrashLoopBackOff` means a delay between repeated container restarts, not a root cause. Check configuration, application errors, OOM termination, and probes. A wrong Service port alone does not normally crash the process. Deployment rollback does not restore a separately edited ConfigMap or Secret.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я сопоставлю изменённую конфигурацию с предыдущими логами и требованиями запуска. Если затронуты пользователи, согласую восстановление проверенной рабочей конфигурации.

#### Подробнее

`CrashLoopBackOff` означает задержку между повторными перезапусками, а не конкретную причину. Проверь конфигурацию, ошибки приложения, OOM и пробы. Неверный порт Service сам по себе обычно не завершает процесс. Откат Deployment не восстановит отдельно изменённый ConfigMap или Secret.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/kubernetes/comments/1r19nhi/). **Technical references / Справка:** [Pod lifecycle](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/), [Deployment rollback](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#rolling-back-a-deployment).

## 9. A Deployment was applied but Pods are not ready. What do you inspect? / Deployment применён, но Pod не готовы. Что проверить?

### 🇬🇧 English

#### Interview answer

> I would inspect rollout status, ReplicaSets, Pod events, and readiness. Scheduling, image pulling, startup, and readiness failures require different checks.

#### Details

Useful commands include `kubectl rollout status deployment/NAME`, `kubectl describe deployment NAME`, and `kubectl describe pod NAME`.

In the linked interviewer's exercise, readiness runs `stat /tmp/ready`; the Pod stays unready while that file is missing. This question broadens that specific exercise into a troubleshooting approach; it is not a verbatim prompt.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Я проверю rollout, ReplicaSet, события Pod и readiness. Ошибки размещения, скачивания образа, запуска и готовности требуют разных проверок.

#### Подробнее

Полезны `kubectl rollout status deployment/NAME`, `kubectl describe deployment NAME` и `kubectl describe pod NAME`.

В задании интервьюера по ссылке readiness выполняет `stat /tmp/ready`: пока файла нет, Pod не готов. Здесь конкретное задание расширено до подхода к диагностике; это не дословный вопрос.

**Interview evidence / Источник задания:** [Interviewer describes a readiness-probe exercise](https://www.reddit.com/r/kubernetes/comments/1ka02oz/). **Technical reference / Справка:** [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/).

## 10. How would you explain a rolling update and rollback? / Как объяснить поэтапное обновление и откат?

### 🇬🇧 English

#### Interview answer

> A rolling update gradually replaces old Pods. A Deployment rollback restores an earlier Pod template, not external database or configuration changes.

#### Details

Avoid promising zero downtime without checking capacity, probes, application behavior, and database compatibility.

### 🇷🇺 Русский

#### Ответ на собеседовании

> Rolling update постепенно заменяет старые Pod. Откат Deployment возвращает прежний шаблон Pod, но не внешние изменения базы или конфигурации.

#### Подробнее

Нельзя обещать отсутствие простоя без проверки ресурсов, проб, поведения приложения и совместимости схемы данных.

**Earlier source, not reverified / Старый источник, не подтверждён повторно (2026-11-03):** [Previously cited page / Ранее указанная страница](https://www.reddit.com/r/kubernetes/comments/1twmuse/). **Technical reference / Справка:** [Updating a Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment).
