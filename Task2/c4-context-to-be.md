# Task2 — C4 Context (To-Be)

## 1. Внешние акторы

1. Пациент (web/mobile).
2. Сотрудник ресепшена.
3. Медицинский специалист.
4. Лаборатория (внешний API-контрагент).
5. Legacy 1C-контур (бухгалтерия/склад через адаптер).

## 2. Контекстная архитектура системы

Системная граница `Medikamente Platform` содержит:

1. `Личный кабинет пациента`.
2. `Портал ресепшена`.
3. `CRM & Scheduling`.
4. `Clinical Records Service`.
5. `Billing / Payment Gateway`.
6. `Lab Integration API`.
7. `IAM / ABAC`.
8. `Consent & Policy Service`.
9. `Data Classification & Tagging`.
10. `Tokenization / Pseudonymization`.
11. `Data Platform (BI/ML)`.
12. `Audit / SIEM`.
13. `Retention & Deletion Orchestrator`.
14. `Privacy Gate in CI/CD`.

## 3. Ключевые взаимодействия

1. Пациент через `ЛК` управляет записью и просматривает только свои анализы/назначения/документы.
2. `ЛК` обращается в `CRM & Scheduling` (запись) и `Clinical Records Service` (клинические данные).
3. Врач работает в `Clinical Records Service`.
4. `Clinical Records Service` отправляет заказ в `Lab Integration API`, получает результаты и сохраняет их в клинический контур.
5. `Lab Integration API` выполняет внешний обмен с `Laboratory` по ограниченным контрактам.
6. `Billing / Payment Gateway` интегрирован с legacy 1С через выделенный адаптер.

## 4. Privacy by Design блоки

1. `IAM / ABAC` — контроль доступа по роли, контексту и цели.
2. `Consent & Policy Service` — проверка legal basis/purpose до доступа/обмена.
3. `Data Classification & Tagging` — обязательная маркировка чувствительных данных.
4. `Tokenization / Pseudonymization` — подготовка данных для BI/ML.
5. `Retention & Deletion Orchestrator` — контроль срока хранения и удаление.
6. `Privacy Gate in CI/CD` — автоматическая проверка релизов по tagged data policy.
7. `Audit / SIEM` — аудит доступа и алертинг аномалий.

## 5. Аналитический слой

1. Данные из операционных сервисов поступают в `Tokenization / Pseudonymization`.
2. В `Data Platform (BI/ML)` попадают подготовленные (обезличенные) данные по умолчанию.
3. Доступ к аналитике ограничен политиками и контролируется аудитом.

## 6. Проверка соответствия целям бизнеса

1. Лабораторная API-интеграция встроена в клинический процесс и не изолирована.
2. Пациент имеет доступ в ЛК не только к записи, но и к анализам/назначениям.
3. Добавлены обязательные privacy-by-design компоненты, требуемые Task2.
4. Добавлен отдельный аналитический слой с privacy-контролями.
