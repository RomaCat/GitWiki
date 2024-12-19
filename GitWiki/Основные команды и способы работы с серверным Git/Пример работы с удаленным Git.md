## 1. Начальная настройка и клонирование

```bash
# Клонируем репозиторий
git clone https://github.com/username/repository.git
```

![[{DA4A87B1-F7A8-4C74-9998-4D34A1FDD74F}.png]]

```bash
# Переходим в директорию проекта
cd repository

# Проверяем статус репозитория
git status
```

![[{C7BDE752-AC17-4B98-9AC8-8392A290ECEB}.png]]
## 2. Создание новой ветки и внесение изменений

```bash
# Создаем новую ветку для работы
git checkout -b feature/new-feature

# Проверяем, что мы находимся в новой ветке
git branch
```

![[{E60BF739-ECD2-4807-8FB7-6B8701218047}.png]]

```bash
# Вносим изменения в файлы
echo "New feature code" > feature.txt

# Проверяем статус изменений
git status
```

![[{EC504ABA-ED48-424E-BF8C-F78375620B12}.png]]
## 4. Фиксация изменений

```bash
# Добавляем изменения в индекс
git add feature.txt

# Создаем коммит
git commit -m "feat: добавлен новый функционал"

# Проверяем лог
git log --oneline
```

![[{8465798C-7783-4C17-BB27-A4E9051C206D}.png]]
## 5. Синхронизация с удаленным репозиторием

```bash
# Получаем последние изменения с удаленного репозитория
git fetch origin

# Проверяем наличие новых изменений
git log HEAD..origin/main --oneline
```

![[{BEAE9F2A-D219-4712-A625-B3F5A3DC0952}.png]]

```bash
# Обновляем основную ветку
git checkout main
git pull origin main

# Возвращаемся в ветку с функционалом
git checkout feature/new-feature
```

![[{BDA9C12B-8093-4ED3-98B4-DEDC717F739D}.png]]
## 6. Отправка изменений в удаленный репозиторий

```bash
# Отправляем новую ветку в удаленный репозиторий
git push -u origin feature/new-feature
```

![[{580CAABA-AB1A-4FEE-8DAE-BD3A540B1068}.png]]

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

![[{B35B9023-6EC6-4CEB-A453-F9ABC1B98E6F}.png]]

## 8. Разрешение конфликтов

```bash
# Пытаемся слить изменения из main
git merge main
```

![[{FFC2777B-7109-499B-B8E8-E8FC02C8AAC2}.png]]

```bash
# Открываем конфликтующий файл
cat feature.txt
```

![[{5EBA5233-8DC5-4630-8625-03FD09919079}.png]]

```bash
# После решения конфликта
git add feature.txt
git commit -m "resolve: разрешение конфликта слияния"
git push origin feature/new-feature
```

![[{A3E4847F-1DC9-495D-923F-B89624CE0027}.png]]

## 9. Завершение работы

```bash
# Удаляем ветки
git checkout main
git pull origin main
git branch -d feature/new-feature
git push origin --delete feature/new-feature
```

![[{7D46380F-19A2-4FDB-9102-F0FD242060CB}.png]]

## 10. Итоговое состояние

```bash
# Проверяем статус и историю
git status
git log --oneline --graph
```
