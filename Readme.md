# Инструкция для работы с Git и удалёнными репозиториями

## Что такое Git?
Git - это одна из реализаций распределённых систем контроля версий, имеющая как и локальные, так и удалённые репозитории. Является самой популярной реализацией систем контроля версий в мире.
## Подготовка репозитория
Для создание репозитория необходимо выполнить команду *git init*  в папке с репозиторием и у Вас создатся репозиторий (появится скрытая папка .git).

## Создание коммитов

### Git add
Для добавления измений в коммит используется команда *git add*. Чтобы использовать команду *git add* напишите *git add <имя файла>*

### Просмотр состояния репозитория
Для того, чтобы посмотреть состояние репозитория используется команда *git status*. Для этого необходимо в папке с репозиторием написать *git status*, и Вы увидите были ли измения в файлах, или их не было.

### Создание коммитов
Для того, чтобы создать коммит(сохранение) необходимо выполнить команду *git commit*. Выполняется она так: *git commit -m "<сообщение к коммиту>*. Все файлы для коммита должны быть ***ДОБАВЛЕНЫ*** и сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

## Перемещение между сохранениями
Для того, чтобы перемещаться между коммитами, используется команда *git checkout*. Используется она в папке с репозиторием следующим образом: *git checkout <номер коммита>*.

    **Пример** `PS D:\Юля\geek brains\Контроль версий\git_seminar> git checkout 750e`

* Для возврата к последнему коммиту ветки нужно использовать команду *git checkout master*.

    **Пример** `PS D:\Юля\geek brains\Контроль версий\git_seminar> git checkout master`


## Журнал изменений
Для того, чтобы посмтреть все сделанные изменения в репозитории, используется команда *git log*. Для этого достаточно выполнить команду *git log* в папке с репозиторием. Для каждого коммита есть свой идентификационный номер. Чтобы переходить от коммита к коммиту достаточно ввести 4 первые символа к команде checkout.



## Ветки в Git

Ветка - это набор commit, которые идут друг за другом. У ветки есть название, основную ветку чаще всего называют master . Если говорить простыми словами, то ветка master - это наш проект.
Другие ветки - это отдельное место для реализации нового функционала или исправление багов (ошибок) нашего проекта. То есть, с отдельной веткой вы делаете что угодно, а затем сливаете эти изменения в основную ветку master.

Чтобы посмотреть сколько у нас на данный момент веток и какая из них текущая (в которой мы работаем) набираем команду *git branch*. Новые ветки создаем из ветки master. Для этого достаточно команду просто применить в папке с репозиторием. 


### Создание ветки

Для того, чтобы создать ветку, используется команда *git branch*. Делается это следующим образом в папке с репозиторием: *git branch <название новой ветки>*.

Чтобы перейти от одной ветки к другой - *git checkout < name>*.

## Слияние веток

Когда нас черновик полностью устраивает, мы можем перенести эту ветку в master. Для того чтобы дабавить ветку в текущую ветку используется команда *git merge <name branch>*. Команду выполняем из той ветки, в которую нужно перенести наш черновик. 



## Удаление веток
Если ветка - черновик больше не нужна, то можем ее удалить. 
Для удаления ветки ввести команду "git branch -d 'name branch'"

## Работа с удаленными репозиториями
Работа с удаленными репозиториями - это работа с репозиториями, которые находятся не на нашем компьютере.

[GitHub](https://github.com/ "ссылка на сайт") - это сервис компании microsoft, который позволяет интегрироваться с программой git и настроить удаленную работу с вашем репозиторием. Это самый популярный на данный момент сервис, но не единственный. Для полноценной работы на GitHub необходимо пройти регистрацию на сайте.

![Git vs GitHub](Untitled.png)

### Перенос удаленного репозитория к себе на компьютер.
Чтобы перенести(скопировать) удаленный репозиторий к себе на компьютер нужно сначала найти нужную папку на gitHub, нажать на кнопку code и скопировать адрес. Например, <https://github.com/ilnar-geekbrains/version_control_lection_3.git>.

Далее заходим в программу git и пишем команду *git clone <https://github.com/ilnar-geekbrains/version_control_lection_3.git>*. Теперь репозиторий в программе git!

Чтобы переместиться в загруженную папку(поменять директорий) нужно набрать команду ***cd имя скаченной папки .***

### Перенос локального репозитория в удаленный

Создаем новый репозиторий на gitHub, имя может быть любое. Далее gitHub предлагает 3 варианта:

![три варианта действий](Untitled2.png)

Сейчас нас интересует вариант 2. Для этого мы копируем адрес нового репозитория и выполняем следующие команды у себя в git:

1. *git remote add origin <https://github.com/YuliaShurygina/test.git>*  - мы говорим программе, что у нас появляется новый удаленный репозиторий, связываем локальный репозиторий с удаленным. origin - название удаленного репозитория.
2. *git branch -M main* - указываем какая ветка основная

3. *git push -u origin main* - отправляем то, что в локальном репозитории в интернет. push -  направлять (протолкнуть) все, что мы сделали на удаленный репозиторий.

Некоторые нюансы:

* Если отправляем впервые, то нужно пройти авторизацию.
* Для того, чтобы дать доступ другому нужно скопировать ссылку из code и чтобы была надпись public.

### Синхронизация локального репозитория с удаленным

Для синхронизации локального репозитория с удаленным используется команда *git pull origin master* (тянуть). Эта команда позволяет скачать все из текущего репозитория и автоматически сделать merge с нашей версией.

### Участие в стороннем проекте
