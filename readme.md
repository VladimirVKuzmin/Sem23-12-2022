# Инструкция по работе с Git

## Что такое Git

***Git*** - самая популярна реализация распределенной системы контроля версий (вверсионность поддерживается и на сервере и у каждого клиента). Самой распространенной реализацией ***Git*** является (GitHub)[https://github.com]

## Подготовка репозитория

Для создания репозитория используется команда *git init*. Для этого необходимо открыть в терминале папку с будущем репозиторием и написать git init


## Создание коммитов

### Добавление файлов к коммиту
Для добавления файла к новому коммиту используется команда *git add*. Используется она следующим образом: в терминале с папкой-репозиторием пишем git add <название файла>.

### Создание коммита
Для создание новой фиксации(коммита) используется команда git commit. Для этого в терминале с папкой-репозиторием пишем *git commit -m "<сообщение к коммиту>*. Сообщение к коммиту писать ОБЯЗАТЕЛЬНО!!!


## Перемещение между коммитами

## Журнал изменений
Для просмотра истории изменений используется команда *git log*. Для этого в терминале с папкой-репозиторием необходимо написать *git log*

## Перемещение между коммитами

Для перемещения на другую фиксацию(коммит) используется команда *git checkout*. Для этого необходимо, как показано в прошлом пункте, в журнале изменений найти необходимый коммит и его хеш(номер), после чего в терминале с папкой-репозиторием надо написать *git checkout <хеш коммита>*. После выполнения этой команды мы попадаем в состояние **detached head**, в котором никакие следующие коммиты сохраняться не будут. Для выхода из этого состояния необходимо написать *git checkout master*.


## Ветки в Git

### Создание веток в гит
Для создание новой ветки используется команда *git branch*. Для этого в терминале с папкой-репозиторием необходимо написать *git branch <название ветки>*.


### Просмотр списка веток
Для просмотра списка веток используется команда *git branch*. Для этого в терминале с папкой-репозиторием необходимо написать *git branch*. Выделенная зелёным со звёздочкой ветка - это ветка, в данный момент на которой мы находимся.

### Перемещение между ветками
Для перехода на другую ветку используется команда *git checkout*. Для этого в терминале с папкой-репозиторием необходимо написать *git checkout <название ветки>*. Такая ветка должна существовать.


## Слияние веток и разрешение конфликтов

Команда *git merge* используется для слияния веток.
Обычно, *git merge* используется таким образом:
*git checkout master* - переключились на ветку master, далее *git merge <название ветки, которую хотим слить>* - сделали слияние текущей ветки (master) с <веткой,  которую хотим слить>. При этом <веткой  которую хотим слить> не меняется, меняется только master. Другими словами, изменения, сделанные в <ветке, которую хотим слить>, "вливаются" в master
Какие действия происходят при слиянии, в документации толком не указывается. Поэтому нужно уточнить, что при команде *git merge <ветка>*, Git автоматически создаст "коммит слияния". То есть, Git не только изменит содержимое рабочего каталога, применяя вливаемые изменения, но и создаст "завершающий" коммит слияния. Таким образом, после слияния не нужно делать коммит, чтобы "зафиксировать" слияние.

### Разрешение конфликтов

После запуска выполнения слияния веток коммитов, если возник конфликт слияния, то слияние будет приостановлено до разрешения конфликта.

Место конфликта слияния будет обозначено в файле следующим образом 



*<<<<<<< HEAD (Current Change)*

Окончание места конфликта в файле обозначено так:

*>>>>>>> new-branch (Incoming Change)*

Между этими обозначениями показаны два варианта кода в файле: 1) из текущей ветки (на которую указывает указатель «HEAD», эта ветка называется «master», и 2) из ветки с названием «new-branch», из которой вливаем изменения в ветку «master». Эти два варианта кода отделены друг от друга следующим обозначением:

Для завершения слияния веток нужно выбрать один из этих вариантов кода. В принципе, это можно сделать вручную, но в редакторе «VS Code» имеется функция, которая называется «CodeLens». Эта функция предоставляет подсказки программисту прямо в коде программы.

В данном случае функция «CodeLens» выведет над местом конфликта четыре подсказки в виде ссылок:

* –Accept Current Change [выбрать вариант текущей ветки];
* – Accept Incoming Change [выбрать вариант ветки, из которой идет слияние];
* – Accept Both Changes [оба варианта останутся в файле друг под другом];
* – Compare Changes [открывает дополнительное окно-вкладку со сравнением двух версий файла, похожее на редактор разниц].

## Удаление веток
Удаление локальной ветки
Чтобы удалить локальную ветку в Git нужно выполнить команду *git branch -d* <назание ветки>:

git branch -d mybranch

Обратите внимание на то, что ветка, которую вы удаляете, не должна быть вашей текущей веткой, в которой вы работаете, иначе отобразится ошибка вида:
*error: Cannot delete branch ’mybranch’ checked out at ’/path/to*
Поэтому, если вам нужно удалить текущую ветку, то сначала нужно переключиться на какую-либо другую ветку, а только потом выполнять удаление.

## 
