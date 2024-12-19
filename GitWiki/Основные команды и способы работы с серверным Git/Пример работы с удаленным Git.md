## 1. Начальная настройка и клонирование

```bash
# Проверяем текущие настройки Git
git config --list
```
На фото должны быть видны настройки:
```
user.name=Your Name
user.email=your.email@example.com
core.editor=vim
color.ui=auto
```

```bash
# Настраиваем имя пользователя и email, если еще не настроены
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Клонируем репозиторий
git clone https://github.com/username/repository.git
```
На фото должен быть виден процесс клонирования:
```
Cloning into 'repository'...
remote: Counting objects: 100, done.
remote: Compressing objects: 100% (80/80), done.
remote: Total 100 (delta 20), reused 90 (delta 10)
Receiving objects: 100% (100/100), 10.5 KiB | 5.24 MiB/s, done.
Resolving deltas: 100% (20/20), done.
```

```bash
# Переходим в директорию проекта
cd repository

# Проверяем статус репозитория
git status
```
На фото должен быть виден чистый статус:
```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

## 2. Работа с удаленными репозиториями

```bash
# Проверяем настроенные удаленные репозитории
git remote -v
```
На фото должен быть виден origin:
```
origin  https://github.com/username/repository.git (fetch)
origin  https://github.com/username/repository.git (push)
```

```bash
# Добавляем дополнительный удаленный репозиторий
git remote add upstream https://github.com/original-owner/repository.git

# Проверяем обновленный список удаленных репозиториев
git remote -v
```
На фото должны быть видны оба репозитория:
```
origin    https://github.com/username/repository.git (fetch)
origin    https://github.com/username/repository.git (push)
upstream  https://github.com/original-owner/repository.git (fetch)
upstream  https://github.com/original-owner/repository.git (push)
```

## 3. Создание новой ветки и внесение изменений

```bash
# Создаем новую ветку для работы
git checkout -b feature/new-feature

# Проверяем, что мы находимся в новой ветке
git branch
```
На фото должен быть виден список веток:
```
  main
* feature/new-feature
```

```bash
# Вносим изменения в файлы
echo "New feature code" > feature.txt

# Проверяем статус изменений
git status
```
На фото должен быть виден статус с новым файлом:
```
On branch feature/new-feature
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        feature.txt

nothing added to commit but untracked files present
```

## 4. Фиксация изменений

```bash
# Добавляем изменения в индекс
git add feature.txt

# Создаем коммит
git commit -m "feat: добавлен новый функционал"

# Проверяем лог
git log --oneline
```
На фото должна быть видна история коммитов:
```
a1b2c3d feat: добавлен новый функционал
e4f5g6h Initial commit
```

## 5. Синхронизация с удаленным репозиторием

```bash
# Получаем последние изменения с удаленного репозитория
git fetch origin

# Проверяем наличие новых изменений
git log HEAD..origin/main --oneline
```
На фото должны быть видны новые коммиты (если есть):
```
b2c3d4e fix: исправление бага в основной ветке
c3d4e5f docs: обновление документации
```

```bash
# Обновляем основную ветку
git checkout main
git pull origin main

# Возвращаемся в ветку с функционалом
git checkout feature/new-feature
```
На фото должен быть виден процесс обновления:
```
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
Updating e4f5g6h..c3d4e5f
Fast-forward
 docs/README.md | 2 ++
 1 file changed, 2 insertions(+)
Switched to branch 'feature/new-feature'
```

## 6. Отправка изменений в удаленный репозиторий

```bash
# Отправляем новую ветку в удаленный репозиторий
git push -u origin feature/new-feature
```
На фото должен быть виден результат отправки:
```
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'feature/new-feature' on GitHub by visiting:
remote:      https://github.com/username/repository/pull/new/feature/new-feature
remote: 
To https://github.com/username/repository.git
 * [new branch]      feature/new-feature -> feature/new-feature
Branch 'feature/new-feature' set up to track remote branch 'feature/new-feature' from 'origin'.
```

## 7. После создания Pull Request

```bash
# Вносим дополнительные изменения
echo "Additional changes" >> feature.txt

# Фиксируем изменения
git add feature.txt
git commit -m "fix: внесены правки по результатам code review"

# Отправляем обновления
git push origin feature/new-feature
```
На фото должен быть виден результат отправки изменений:
```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 288 bytes | 288.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/username/repository.git
   a1b2c3d..d4e5f6g  feature/new-feature -> feature/new-feature
```

## 8. Разрешение конфликтов

```bash
# Пытаемся слить изменения из main
git merge main
```
На фото должно быть видно сообщение о конфликте:
```
Auto-merging feature.txt
CONFLICT (content): Merge conflict in feature.txt
Automatic merge failed; fix conflicts and then commit the result.
```

```bash
# Открываем конфликтующий файл
cat feature.txt
```
На фото должен быть виден конфликт в файле:
```
<<<<<<< HEAD
New feature code
Additional changes
=======
Different changes from main
>>>>>>> main
```

```bash
# После решения конфликта
git add feature.txt
git commit -m "resolve: разрешение конфликта слияния"
git push origin feature/new-feature
```
На фото должен быть виден успешный результат:
```
[feature/new-feature h5i6j7k] resolve: разрешение конфликта слияния
 1 file changed, 2 insertions(+), 1 deletion(-)
To https://github.com/username/repository.git
   d4e5f6g..h5i6j7k  feature/new-feature -> feature/new-feature
```

## 9. Завершение работы

```bash
# Удаляем ветки
git checkout main
git pull origin main
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```
На фото должен быть виден результат очистки:
```
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
Already up to date.
Deleted branch feature/new-feature (was h5i6j7k).
To https://github.com/username/repository.git
 - [deleted]         feature/new-feature
```

## 10. Итоговое состояние

```bash
# Проверяем статус и историю
git status
git log --oneline --graph
```
На фото должен быть виден чистый статус и история с влитыми изменениями:
```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

* h5i6j7k (HEAD -> main) resolve: разрешение конфликта слияния
|\
| * d4e5f6g fix: внесены правки по результатам code review
| * a1b2c3d feat: добавлен новый функционал
|/
* e4f5g6h Initial commit
```