Наша работа 
# Часть 1: Индивидуальная работа (Основы Git)

1. **Создайте каталог проекта и инициализируйте Git**

```bash
mkdir my_first_project
cd my_first_project
git init
```

2. **Создайте файл README.md и добавьте описание**

```bash
echo "# Мой первый проект\nФИО: [Ваши ФИО]" > README.md
```

3. **Добавьте файл в индекс и сделайте первый коммит**

```bash
git add README.md
git commit -m "Initial commit. Added project description"
```

4. **Создайте и переключитесь на ветку `develop`**

```bash
git branch develop
git checkout develop
# или
git checkout -b develop
```

5. **Создайте файл `calculator.py` с простыми функциями**

```python
# calculator.py
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b
```

6. **Зафиксируйте изменения в ветке `develop`**

```bash
git add calculator.py
git commit -m "Add basic arithmetic functions"
```

7. **Вернитесь в ветку `main` и убедитесь, что файла `calculator.py` там нет**

```bash
git checkout main
ls  # убедитесь, что файла calculator.py нет
```

8. **Выполните слияние `develop` в `main`**

```bash
git merge develop
```

---

# Часть 2: Командная работа (Работа с удалённым репозиторием)

### Для Студента А:

1. **Создайте репозиторий на GitHub или GitLab** с названием `team-project-[ваша_фамилия]`.

2. **Добавьте файл `main.py`**

```python
# main.py
def main():
    print("Hello, Team!")

if __name__ == "__main__":
    main()
```

3. **Добавьте и запушьте файл**

```bash
git init
git add main.py
git commit -m "Initial commit with main structure"
git remote add origin <URL-репозитория>
git push -u origin main
```

4. **Добавьте Студента Б как collaborator через интерфейс GitHub/GitLab.**

---

### Для Студента Б:

1. **Клонируйте репозиторий**

```bash
git clone <URL-репозитория>
cd <имя_репозитория>
```

2. **Создайте новую ветку**

```bash
git checkout -b feature/ivanov
```

3. **Редактируйте `main.py`, добавляя свою функцию**

```python
# main.py
def main():
    print("Hello, Team!")

def divide(a, b):
    return a / b

if __name__ == "__main__":
    main()
```

4. **Зафиксируйте изменения и пуш**

```bash
git add main.py
git commit -m "Add divide() function"
git push -u origin feature/ivanov
```

5. **Создайте Pull Request (GitHub/GitLab) на слияние в `main`.**

---

### Для Студента А:

1. **Примет Pull Request и выполнит слияние**

```bash
# В интерфейсе GitHub/GitLab: нажмите "Merge"
```

---

### Для Студента Б:

1. **Попытка слить свой PR вызовет конфликт.**

2. **Обновите локальные данные**

```bash
git checkout main
git pull origin main
```

3. **Переключитесь в свою ветку и сделайте слияние `main` в свою ветку для разрешения конфликта**

```bash
git checkout feature/ivanov
git merge main
```

4. **Разрешите конфликт вручную в файле `main.py`, оставив обе функции**

```python
# main.py
def main():
    print("Hello, Team!")

def multiply(a, b):
    return a * b

def divide(a, b):
    return a / b

if __name__ == "__main__":
    main()
```

5. **Зафиксируйте исправления и отправьте**

```bash
git add main.py
git commit -m "Resolve merge conflict: keep both multiply and divide functions"
git push
```

6. **Завершите слияние Pull Request**

---

# Теоретические вопросы — ответы

1. **Разница между командами `git fetch` и `git pull`:**

- `git fetch` загружает изменения из удаленного репозитория, но не сливает их с текущей веткой.
- `git pull` — это сочетание `git fetch` и `git merge`, то есть загружает изменения и автоматически сливает их с текущей веткой.

2. **Для чего используется команда `git branch -a`?**

- Показывает список всех локальных и удаленных веток.

3. **Что такое "fast-forward" слияние и когда оно невозможно?**

- "Fast-forward" — это слияние, при котором текущая ветка просто перемещается вперед до новой точки без дополнительных коммитов слияния. Оно невозможно, если у обеих веток есть свои уникальные изменения, требующие создания коммита слияния.

4. **Алгоритм действий при конфликте слияния:**

- Обнаружить конфликт.
- Открыть конфликтные файлы, вручную разрешить конфликты.
- Добавить исправленные файлы (`git add`).
- Закоммитить исправления (`git commit`).
- Продолжить работу или завершить слияние.

5. **Лучшие практики именования коммитов и веток:**

- Ветки: использовать понятные имена, отражающие задачу, например, `feature/add-login`, `bugfix/fix-typo`.
- Коммиты: писать короткие, содержательные сообщения в императивной форме, например, "Добавить функцию деления", "Исправить ошибку в расчетах".

---

