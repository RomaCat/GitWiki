## 1. Создание проекта и первый коммит

```bash
# Инициализируем Git репозиторий
git init

# Проверяем статус репозитория
git status
```

![[{40E98EBD-46AB-43A4-9D8C-272ABBE5B560}.png]]

```bash
# Добавляем файл в индекс
git add README.md

# Создаём первый коммит
git commit -m "Первый commint: add README.md"
```

![[{0C69CB17-AE94-42AB-8FCB-B76968A0B38D}.png]]
## 2. Добавление кода и второй коммит

```bash
# Создаём файл с кодом
index.py

# Проверяем статус
git status
```

![[{1E6127EC-E42E-4B52-BB25-10A8D3460838}.png]]

```bash
# Добавляем и коммитим новый файл
git add index.py
git commit -m "Добавлена строка Hello world"
```

## 3. Внесение изменений в существующий файл

```bash
# Изменяем код в index.py
index.py

# Смотрим изменения
git diff
```

![[{3E27FFFB-897A-4E32-BA9B-7FFA678F8F89}.png]]

```bash
# Коммитим изменения
git add index.py
git commit -m "Изменение строки"
```

## 4. Работа с ветками

```bash
# Смотрим текущие ветки
git branch
```

![[{D93F0D3D-01E2-4CCA-9931-FC22087AB066}.png]]

```bash
# Создаём новую ветку для новой функции
git branch feature/goodbye
```

![[{3F21D2B0-BB90-437E-8183-2440502D122C}.png]]

```bash
# Проверяем список веток
git branch
```

![[{3250389C-E35E-49CF-B0F9-18C94CA81C08}.png]]

```bash
# Переключаемся на новую ветку
git checkout feature/goodbye
```

![[{4B98C1A5-324F-41B1-8B91-DD9BDF965E23}.png]]

```bash
# изменяем файл в этой ветке
index.py

# Смотрим изменения
git status
```

![[{BB034EEF-5399-4022-9D7D-0B99CE4C9FE4}.png]]

```bash
# Коммитим изменения в новой ветке
git add index.js
git commit -m "Add goodbye function"
```

![[{06FCA381-3825-4275-8D86-95C63F54BB35}.png]]

```bash
# Проверяем лог
git log --oneline
```

![[{D3A977EA-AEEE-4D79-AF1B-12B672192D1D}.png]]
## 5. Слияние веток

```bash
# Возвращаемся в основную ветку
git checkout master

# Сливаем изменения из feature-ветки
git merge feature/goodbye-function
```

![[{700E74E4-173C-4639-9686-D0DF57D492EF}.png]]

## 6. Работа с конфликтами

```bash
# Смотрим на какой мы ветке
git branch
```

![[{F5063F9A-7B9A-4BC5-B001-935EC85FF236}.png]]

```bash
# Создаём новую ветку
git branch new
```

![[{E4E64630-0E0F-4233-9F7D-16F08B443BF1}.png]]

```bash
# Переключаемся на новую ветку
git checkout new
```

![[{F47479A9-F621-4735-82C2-C0D008D33096}.png]]

```bash
# Изменяем файл функцию в первой ветке
index.py

# Смотрим статус изменений
git status
```

![[{F29263E8-ED8C-4423-A344-BA430DFD8C47}.png]]

```bash
# Добавляем изменения в индекс
git add index.js
```

![[{896269CE-94F9-4B8A-AEAD-D6287E3D661C}.png]]

```bash
# Создаём коммит в первой ветке
git commit -m "Change"
```

![[{B77C3CEB-C324-4901-955E-D223105B71CB}.png]]

```bash
# Переключаемся обратно в main
git checkout master
```

![[{EC810B19-5003-4B67-8FE1-0512A1AD83ED}.png]]

```bash
# Создаём конфликтующие изменения в master
index.py

# Проверяем статус
git status
```

![[{F2BCE69F-BF4A-4AD7-8D97-F988F4CDFDF2}.png]]

```bash
# Добавляем изменения в индекс
git add index.py

# Создаём коммит в main
git commit -m "Change 2"
```

![[{EB797891-3418-4A97-8602-A39C5A888550}.png]]

```bash
# Пытаемся слить ветку new в main
git merge new
```

![[{4412086B-A90F-40E1-9715-335694C46413}.png]]

```bash
# Проверяем статус после конфликта
git status
```

![[{2B8D31ED-D663-49C3-8BA6-53D1D5A31199}.png]]

```bash
# Открываем файл и видим конфликт
cat index.js
```
![[{58457915-FC2F-451A-86D5-ADA43D290A3D}.png]]
```
<<<<<<< HEAD
print("hello world")
=======
print("sdsd")
printe("hi worled and hello world")
>>>>>>> new
```


```bash
# Решаем конфликт, выбирая нужную версию или объединяя их
# Например, делаем такую версию:
print("sdsd")
print("hello world")
 > index.py

# Проверяем изменения
git status
```

![[{8665FA30-4054-41F4-A756-E8230BEC8D9B}.png]]

```bash
# Добавляем решенный файл в индекс
git add index.py
```

![[{E806358D-1F33-43E4-A8FE-ADDD6F8F4CF2} 1.png]]

```bash
# Завершаем слияние создавая коммит
$ git commit -m "Решение слияния"
```

![[{DDF0F6B7-B407-4604-8CB0-6A741D0111A3}.png]]

```bash
# Проверяем историю
git log --oneline
```

![[{35110936-F635-47B4-A62C-3DC2F22BE20B}.png]]

```bash
# Проверяем финальное содержимое файла
cat index.py
```

![[{1985546C-4778-4CD4-A380-B378B5D70635}.png]]

```bash
# Проверяем, что все чисто
git status
```

![[{36E8A593-253C-4458-B70F-9DC3708A9E88}.png]]

## 7. Просмотр истории

```bash
# Просмотр истории коммитов с графом
git log --graph --oneline --all
```

![[{EA4AC9EF-CF22-4B39-81D4-9E197E56841A}.png]]

## 8. Работа с тегами

```bash
# Просмотр существующих тегов
git tag
```

![[{C4144E8A-DC3E-4819-8425-E73DDF74F3E6}.png]]

```bash
# Создание аннотированного тега
git tag -a v1.0 -m "Version 1.0 release"
```

![[{4B4F2A4C-994B-4CFB-BE41-77EA56082654}.png]]

```bash
# Просмотр информации о конкретном теге
git show v1.0
```

![[{3975B907-EF1E-4A13-AE29-66D4BD58312E}.png]]

```bash
# Создание легковесного тега
git tag v1.0-beta
```

![[{97B42DEB-1B7A-4750-B9B2-5DEC1DC5415B}.png]]

```bash
# Просмотр тегов с шаблоном
git tag --list "v1.*"
```

![[{5E2F02B7-D558-4EA3-9CA6-779269660AC5}.png]]

```bash
# Создание тега для определённого коммита
git tag -a v0.9 5e0eeba -m "начало"
```

![[{C9890FFB-F35C-4F91-A865-51F075EADA90}.png]]

```bash
# Удаление тега
git tag --delete v1.0-beta
```

![[{538646B1-6EA8-4DF8-BAF6-F7C616649664}.png]]

```bash
# Проверка тегов после удаления
git tag
```

![[{28FBAF21-927E-4101-B4FA-F0EF62AE599C}.png]]

```bash
# Поиск коммита по тегу
git checkout v1.0
```

![[{66F66793-D064-4411-9EA0-00F9446352F0}.png]]

```bash
# Возврат к последнему состоянию main
git checkout main
```

![[{7E59E0FD-09AC-424C-AE96-D4F01A12CAB5}.png]]

```bash
# Просмотр истории с тегами
git log --oneline --decorate
```

![[{2A610A79-7414-48EB-B92D-49DF593FF849}.png]]

## 9. Итоговая структура проекта:

```
my-project/
├── README.md
└── index.py
```

## 10. Проверка статуса в конце

```bash
git status
git log --oneline
```

![[{BB30192C-6AF3-4647-91C1-244BF29FE133}.png]]
