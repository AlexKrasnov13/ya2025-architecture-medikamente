# Task1 — DFD To-Be (по методике Lucidchart)

Набор диаграмм сделан как:

1. `Level 0 (Context)`: общий поток данных по платформе.
2. `Level 1 (Process)`: отдельные диаграммы для каждого ключевого процесса.

## Level 0

1. `dfd-context-to-be.drawio`

## Level 1 (по процессам)

1. `dfd-p1-booking-to-be.drawio` — запись пациента.
2. `dfd-p2-clinical-to-be.drawio` — прием и ведение медкарты.
3. `dfd-p3-payment-to-be.drawio` — оплата услуг.
4. `dfd-p4-lab-to-be.drawio` — интеграция с лабораторией.

## Принципы нотации

1. Используются 4 элемента DFD: `External Entity`, `Process`, `Data Store`, `Data Flow`.
2. На стрелках указаны данные, а не только технологический вызов.
3. Для каждого процесса отображены операции над данными (create/read/update/validate/reconcile/tokenize).
4. Безопасность отображена как встроенные контроли потока (IAM, policy/tagging, encryption, audit).
