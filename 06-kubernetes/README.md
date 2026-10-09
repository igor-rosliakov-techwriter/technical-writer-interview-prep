# Kubernetes for Technical Writer Interviews

Five reusable questions and five published interview scenarios. English comes first; Russian is a separate support block. The scenario wording is condensed from candidate/interviewer reports, not presented as a verbatim transcript. These reports mostly concern engineering or DevOps roles, so answer at a technical writer's level: explain the mechanism, read a manifest, and know what to verify.

---

**General questions / Общие вопросы**

## 1. What does Kubernetes do? / Зачем нужен Kubernetes?

### 🇬🇧 English

#### Quick recall
**Kubernetes coordinates containerized workloads across a cluster.**

#### Interview answer
> It lets a team declare the desired state of an application, such as how many replicas should run. Controllers work to bring the actual state toward that declaration. Kubernetes also supports service discovery, rollout, and recovery from some failures.

#### Details
It does not build container images or make an unhealthy application correct. Documentation must say what the cluster manages and what the application owner must configure.

### 🇷🇺 Русский

#### Быстро вспомнить
**Kubernetes управляет контейнерными приложениями в кластере.**

#### Ответ на собеседовании
> Команда задаёт желаемое состояние приложения, например число копий. Контроллеры стараются привести фактическое состояние к заданному. Платформа также помогает обнаруживать сервисы, обновлять приложения и восстанавливаться после части сбоев.

#### Подробнее
Kubernetes не собирает образы и не исправляет ошибки самого приложения. В документации важно отделять ответственность кластера от настроек приложения.

**Interview evidence / Источник вопроса:** [Interviewer reports asking about Kubernetes concepts](https://www.reddit.com/r/kubernetes/comments/1twmuse/). **Technical reference / Справка:** [Kubernetes overview](https://kubernetes.io/docs/concepts/overview/).

## 2. How do a Pod, Deployment, and Service differ? / Чем различаются Pod, Deployment и Service?

### 🇬🇧 English

#### Quick recall
**A Pod runs containers; a Deployment manages Pods; a Service provides a stable way to reach backends.**

#### Interview answer
> A Pod is the smallest deployable compute object. A Deployment describes and updates a set of Pods through ReplicaSets. A Service abstracts access to matching backends, commonly Pods, even when individual Pods are replaced.

#### Details
Do not call a Service a container or a Deployment a server. A Deployment is usually for stateless workloads; other controllers exist for different needs.

### 🇷🇺 Русский

#### Быстро вспомнить
**Pod запускает контейнеры, Deployment управляет Pod, Service даёт стабильный способ доступа.**

#### Ответ на собеседовании
> Pod — минимальная единица запуска. Deployment задаёт и обновляет набор Pod через ReplicaSet. Service скрывает изменчивость отдельных Pod и направляет обращения к подходящим экземплярам.

#### Подробнее
Service — не контейнер, а Deployment — не сервер. Для других типов нагрузок существуют иные контроллеры.

**Interview evidence / Источник вопроса:** [Interviewer reports asking this exact comparison](https://www.reddit.com/r/kubernetes/comments/1eial2s/). **Technical references / Справка:** [Pods](https://kubernetes.io/docs/concepts/workloads/pods/), [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/), [Services](https://kubernetes.io/docs/concepts/services-networking/service/).

## 3. What are a cluster, node, and control plane? / Что такое кластер, узел и control plane?

### 🇬🇧 English

#### Quick recall
**A cluster contains nodes; the control plane manages cluster state; worker nodes run workloads.**

#### Interview answer
> The control plane exposes the API, stores cluster state, schedules work, and runs controllers. Worker nodes run Pods using a container runtime and node components. The distinction helps locate whether a problem is in configuration, scheduling, or application runtime.

#### Details
This is a conceptual map, not a claim that every cluster has identical topology. Managed Kubernetes can hide much of the control plane from users.

### 🇷🇺 Русский

#### Быстро вспомнить
**Кластер состоит из узлов; control plane управляет состоянием, рабочие узлы запускают приложения.**

#### Ответ на собеседовании
> Control plane предоставляет API, хранит состояние кластера, планирует размещение и запускает контроллеры. На рабочих узлах выполняются Pod. Это разделение помогает понять, где искать проблему: в конфигурации, размещении или приложении.

#### Подробнее
Реальная топология зависит от установки. В управляемом Kubernetes пользователь может не иметь прямого доступа к компонентам control plane.

**Interview evidence / Источник вопроса:** [Interview report mentions control-plane questions](https://www.reddit.com/r/kubernetes/comments/1twmuse/). **Technical reference / Справка:** [Kubernetes components](https://kubernetes.io/docs/concepts/overview/components/).

## 4. How does a Service find Pods? / Как Service находит Pod?

### 🇬🇧 English

#### Quick recall
**Usually through label selectors and ready endpoints.**

#### Interview answer
> A Service commonly selects Pods whose labels match its selector. Kubernetes maintains EndpointSlices for those backends, and traffic goes to eligible endpoints. If a selector or target port is wrong, the Service may exist while requests still fail.

#### Details
Services can also exist without selectors, so “always” would be inaccurate. Check namespace, selector, Pod labels, readiness, and `port` versus `targetPort` when documenting a route.

### 🇷🇺 Русский

#### Быстро вспомнить
**Обычно через селекторы меток и доступные конечные точки.**

#### Ответ на собеседовании
> Service обычно выбирает Pod по совпадению меток с селектором. Kubernetes поддерживает EndpointSlice с адресами подходящих экземпляров. Неверный селектор или порт может оставить Service существующим, но недоступным для запросов.

#### Подробнее
Service бывает и без селектора. При проверке смотрим namespace, метки, готовность Pod, а также `port` и `targetPort`.

**Interview evidence / Источник вопроса:** [Candidate reports a Service-manifest interview question](https://www.reddit.com/r/devops/comments/198zj1m/). **Technical reference / Справка:** [Kubernetes Service](https://kubernetes.io/docs/concepts/services-networking/service/).

## 5. What are ConfigMaps, Secrets, and probes? / Что такое ConfigMap, Secret и пробы?

### 🇬🇧 English

#### Quick recall
**ConfigMaps hold non-secret configuration; Secrets hold sensitive values; probes report container health or readiness.**

#### Interview answer
> A ConfigMap can supply configuration without rebuilding an image. A Secret is the dedicated API object for sensitive values, but still requires access controls and encryption-at-rest decisions. Readiness controls whether a Pod receives Service traffic; liveness can trigger a container restart; startup protects slow-starting containers.

#### Details
Base64 in a Secret manifest is encoding, not encryption. Never paste real credentials into examples.

### 🇷🇺 Русский

#### Быстро вспомнить
**ConfigMap хранит обычную конфигурацию, Secret — чувствительные значения, пробы проверяют состояние контейнера.**

#### Ответ на собеседовании
> ConfigMap позволяет менять настройки без пересборки образа. Secret предназначен для чувствительных данных, но сам по себе не отменяет контроля доступа и защиты при хранении. Readiness влияет на получение трафика, liveness может перезапустить контейнер, startup учитывает долгий запуск.

#### Подробнее
Base64 в манифесте Secret — кодирование, не шифрование. В примерах нельзя публиковать реальные ключи.

**Interview evidence / Источник вопроса:** [Interview discussion of Secrets and Pod networking](https://www.reddit.com/r/kubernetes/comments/1h2it1f/). **Technical references / Справка:** [ConfigMaps](https://kubernetes.io/docs/concepts/configuration/configmap/), [Secrets](https://kubernetes.io/docs/concepts/configuration/secret/), [Probes](https://kubernetes.io/docs/concepts/configuration/liveness-readiness-startup-probes/).

---

**Published scenarios / Опубликованные ситуации**

## 6. Explain how this Service manifest reaches Pods. / Объясните, как этот Service направляет запросы к Pod.

### 🇬🇧 English

#### Quick recall
**Trace selector → Pod labels → eligible endpoints → target port.**

#### Interview answer
> I would first identify the Service's namespace, type, selector, and ports. Then I would compare the selector to Pod labels, inspect the endpoints, and confirm that `targetPort` reaches the application's listening port. A valid YAML file alone does not prove connectivity.

#### Details
If the task gives no manifest, ask for it rather than inventing labels or port numbers.

### 🇷🇺 Русский

#### Быстро вспомнить
**Идём по цепочке: селектор → метки Pod → доступные адреса → целевой порт.**

#### Ответ на собеседовании
> Сначала посмотрю namespace, тип Service, селектор и порты. Затем сверю селектор с метками Pod, проверю конечные точки и порт, который слушает приложение. Корректный YAML ещё не доказывает доступность сервиса.

#### Подробнее
Если манифест не дан, лучше запросить его, а не придумывать метки и порты.

**Interview evidence / Источник задания:** [Candidate describes a Service-manifest question](https://www.reddit.com/r/devops/comments/198zj1m/). **Technical reference / Справка:** [Services](https://kubernetes.io/docs/concepts/services-networking/service/).

## 7. A Pod is failing. Where do you start? / Pod не работает. С чего начнёте?

### 🇬🇧 English

#### Quick recall
**Status, events, logs, then the relevant manifest and dependencies.**

#### Interview answer
> I would inspect `kubectl get pod`, `kubectl describe pod`, and `kubectl logs`; for a restarted container I would check `kubectl logs --previous`. Events can reveal scheduling or image-pull problems, while logs often reveal application startup errors. I would test one hypothesis at a time.

#### Details
Do not prescribe a restart as the universal fix. In user docs, separate symptoms, checks, likely causes, and corrective actions.

### 🇷🇺 Русский

#### Быстро вспомнить
**Статус, события, логи, затем манифест и зависимости.**

#### Ответ на собеседовании
> Посмотрю `kubectl get pod`, `kubectl describe pod` и `kubectl logs`. Если контейнер уже перезапускался, проверю `kubectl logs --previous`. События часто показывают ошибки размещения или скачивания образа, а логи — ошибки запуска приложения. Проверять буду по одной гипотезе.

#### Подробнее
Перезапуск — не универсальное решение. В документации нужно разделять симптомы, проверки, причины и действия.

**Interview evidence / Источник задания:** [Interviewer reports a failing-Pod troubleshooting prompt](https://www.reddit.com/r/kubernetes/comments/1eial2s/). **Technical reference / Справка:** [Debug running Pods](https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/).

## 8. A Deployment's container crash-loops after an environment change. What do you check? / Контейнер после смены переменной окружения постоянно перезапускается. Что проверить?

### 🇬🇧 English

#### Quick recall
**Compare the new configuration with logs and the last working revision.**

#### Interview answer
> I would inspect Pod events and previous-container logs, verify the environment variable's name and source, and check whether the app can start with that value. If the rollout is harming users, I would coordinate a rollback to a known-good revision while investigating the change.

#### Details
The reported exercise used a bad environment variable or port. Do not claim every `CrashLoopBackOff` is caused by one of these; it is a restart-backoff symptom.

### 🇷🇺 Русский

#### Быстро вспомнить
**Сравнить новую конфигурацию, логи и последнюю рабочую версию.**

#### Ответ на собеседовании
> Проверю события и логи предыдущего запуска контейнера, имя и источник переменной окружения, затем поведение приложения с этим значением. Если обновление ломает сервис, согласую откат на рабочую ревизию и продолжу разбор причины.

#### Подробнее
В опубликованном задании причина была в переменной окружения или порте. Но `CrashLoopBackOff` — симптом повторных неудачных запусков, а не название конкретной причины.

**Interview evidence / Источник задания:** [Interviewer describes a crash-looping Deployment exercise](https://www.reddit.com/r/kubernetes/comments/1r19nhi/). **Technical references / Справка:** [Pod lifecycle](https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/), [Deployment rollback](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#rolling-back-a-deployment).

## 9. A Deployment was applied but Pods are not ready. What do you inspect? / Deployment применён, но Pod не готовы. Что проверить?

### 🇬🇧 English

#### Quick recall
**Check desired versus available replicas, then Pod state and events.**

#### Interview answer
> I would inspect the Deployment rollout, its ReplicaSet, and the Pods it owns. A Pod might be Pending because it cannot be scheduled, fail image pull, crash, or run but fail readiness. Each state points to a different next check; the Deployment's existence does not mean the application is serving traffic.

#### Details
Useful commands include `kubectl rollout status deployment/NAME`, `kubectl describe deployment NAME`, and `kubectl describe pod NAME`.

### 🇷🇺 Русский

#### Быстро вспомнить
**Сверить нужное и доступное число реплик, затем изучить Pod и события.**

#### Ответ на собеседовании
> Посмотрю статус обновления Deployment, его ReplicaSet и созданные Pod. Pod может не разместиться, не скачать образ, завершаться с ошибкой или работать, но не проходить readiness. Для каждого случая следующий шаг разный; существование Deployment не означает, что приложение принимает трафик.

#### Подробнее
Полезны `kubectl rollout status deployment/NAME`, `kubectl describe deployment NAME` и `kubectl describe pod NAME`.

**Interview evidence / Источник задания:** [Candidate describes a not-ready Deployment manifest exercise](https://www.reddit.com/r/kubernetes/comments/1ka02oz/). **Technical reference / Справка:** [Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/).

## 10. How would you explain a rolling update and rollback? / Как объяснить поэтапное обновление и откат?

### 🇬🇧 English

#### Quick recall
**A rolling update gradually replaces Pods; a rollback returns to an earlier Deployment revision.**

#### Interview answer
> A Deployment can create a new ReplicaSet and replace old Pods gradually, constrained by its rollout strategy. I would watch progress and readiness, then use rollout history and rollback if the new revision is faulty. I would also explain what a rollback does not undo, such as external data changes.

#### Details
Avoid promising zero downtime without checking capacity, probes, application behavior, and database compatibility.

### 🇷🇺 Русский

#### Быстро вспомнить
**Поэтапное обновление постепенно заменяет Pod, откат возвращает прежнюю ревизию Deployment.**

#### Ответ на собеседовании
> Deployment может создать новую ReplicaSet и постепенно заменить старые Pod в соответствии со стратегией обновления. Я буду следить за статусом и готовностью, а при ошибке воспользуюсь историей ревизий и откатом. Важно отдельно учитывать изменения внешних данных, которые откат Deployment не отменяет.

#### Подробнее
Нельзя обещать отсутствие простоя без проверки ресурсов, проб, поведения приложения и совместимости схемы данных.

**Interview evidence / Источник вопроса:** [Interview report includes rolling-update questions](https://www.reddit.com/r/kubernetes/comments/1twmuse/). **Technical reference / Справка:** [Updating a Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment).
