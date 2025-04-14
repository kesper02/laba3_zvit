# Звіт до роботи

## Тема:
Автоматизація тестування Python-коду з використанням GitHub Actions

## Мета роботи:
Ознайомитись з GitHub Actions та створити CI/CD Workflow для автоматичного тестування коду та отримання звіту про покриття тестами.

---

## Виконання роботи

### Завдання 1: Створення Workflow через шаблон
- Створено Workflow на основі Python application
- Додано крок для запуску `lab.py`

### Завдання 2: Запуск вручну та за розкладом
- Додано `workflow_dispatch` для ручного запуску
- Додано `cron`-тригер на вибраний день тижня о 17:00

```yaml
on:
  workflow_dispatch:
  schedule:
    - cron: '0 17 * * 2'  # кожного вівторка
```

### Завдання 3: Два воркфлоу файли
- Створено `manual.yml` та `scheduled.yml`
- У вкладці Actions відображено обидва Workflow

![workflow list](pictures/workflows_list.png)

### Завдання 4: Два jobs у одному Workflow
```yaml
jobs:
  job_one:
    name: Run first Job
    runs-on: ubuntu-latest
    steps:
      - name: First
        run: echo "First"
  job_two:
    name: Run Second Job
    runs-on: ubuntu-latest
    steps:
      - name: Second
        run: echo "Second"
```
![jobs result](pictures/jobs_result.png)

### Завдання 5: Умовне виконання
```yaml
- name: Send greeting
  run: echo "Hello ${{ github.event.inputs.name }}"
  if: github.event.inputs.name != 'Executer'
```

### Бадж з статусом Workflow
```md
![Manual workflow](https://github.com/username/repo/actions/workflows/manual.yml/badge.svg)
```

### Тестування та звіт покриття
- Встановлено `pytest` та `coverage`
- Створено крок для створення тестового звіту
- Завантажено звіт на codecov.io
- Додано badge із codecov

---

## Висновок:
- Що зроблено: створено GitHub Actions CI/CD, тести, звіт покриття
- Чи досягнуто мети: так
- Які нові знання: GitHub Actions, cron-розклад, coverage
- Чи виникли складнощі: виникали помилки з виконанням pytest та імпортом модулів
- Чи сподобався формат: так
- Побажання: додати порядок CI/CD з використанням secrets, artifacts та release-збірок

