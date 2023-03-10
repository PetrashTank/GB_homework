# Инструкция для работы с Git и удалёнными репозиториями

## Что такое Git?
![logo](/image1.jpeg)
Git - это одна из реализаций распределённых систем контроля версий, имеющая как и локальные, так и удалённые репозитории. Является самой популярной реализацией систем контроля версий в мире.

Git — это набор консольных утилит, которые отслеживают и фиксируют изменения в файлах (чаще всего речь идет об исходном коде программ, но вы можете использовать его для любых файлов на ваш вкус). Изначально Git был создан Линусом Торвальдсом при разработке ядра Linux. Однако инструмент так понравился разработчикам, что в последствии, он получил широкое распространение и его стали использовать в других проектах. С его помощью вы можете сравнивать, анализировать, редактировать, сливать изменения и возвращаться назад к последнему сохранению. Этот процесс называется контролем версий.

Для чего нужен GIT? 
* Чтобы отследить изменения, произошедшие с проектом, со временем. Проще говоря, мы можем посмотреть как менялись файлы программы, на всех этапах разработки и при необходимости вернуться назад и что-то отредактировать. 

* GIT Полезен при одновременной работе нескольких специалистов, над одним проектом. Без Гита случится коллапс, когда разработчики, скопировав весь код из главной папки и сделав с ним задуманное, попытаются одновременно вернуть весь код обратно.

## Подготовка репозитория
Для создание репозитория необходимо выполнить команду *git init*  в папке с репозиторием и у Вас создаться репозиторий (появится скрытая папка .git)

### **Перед работой с Git**
Чтобы быть подкованным, необходимо понимать о чем мы вообще говорим, поэтому нужно составить Git-словарик с основными понятиями(список пополняемый).

Итак: 

**Репозиторий** — директория проекта, который отслеживается Git. В директории хранится проект, история изменений и мета-информация проекта (в скрытой директории .git).

**Индекс** — хранилка, где лежат имена файлов и их изменения, которые должны быть в следующем коммите. По факту индекс — просто файл. В индекс файлы сами не попадают, их нужно явно добавлять при помощи git add.

**Коммит** (commit) — это фиксация изменений в истории проекта (изменения, которые внесены в индекс). Коммит хранит изменённые файлы, имя автора коммита и время, в которое был сделан коммит. Кроме того, каждый коммит имеет уникальный идентификатор, который позволяет в любое время к нему откатиться. Можно считать коммит этакой точкой сохранения.

**Ветка** (branch) — последовательность коммитов. По сути — ссылка на последний коммит в этой ветке. Ветки не зависят друг от друга — можно вносить изменения в одну, и они не повлияют на другую (если вы явно этого не попросите). 

Необходимо задать или изменить имя пользователя. Это можно сделать с помощью команды git config. Новое имя будет автоматически отображаться в последующих коммитах. 
## Создание коммитов

- ### Git add
Для добавления измений в коммит используется команда *git add*. Чтобы использовать команду *git add* напишите *git add <имя файла>*

- ### Просмотр состояния репозитория
Для того, чтобы посмотреть состояние репозитория используется команда *git status*. Для этого необходимо в папке с репозиторием написать *git status*, и Вы увидите были ли измения в файлах, или их не было.

- ### Создание коммитов
Для того, чтобы создать коммит(сохранение) необходимо выполнить команду *git commit*. Выполняется она так: *git commit -m "<сообщение к коммиту>*. Все файлы для коммита должны быть ***ДОБАВЛЕНЫ*** и сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

## Перемещение между сохранениями
Для того, чтобы перемещаться между коммитами, используется команда *git checkout*. Используется она в папке с репозиторием следующим образом: *git checkout <номер коммита>*

## Журнал изменений
Для того, чтобы посмтреть все сделанные изменения в репозитории, используется команда *git log*. Для этого достаточно выполнить команду *git log* в папке с репозиторием

## Ветки в Git
 Под веткой принято понимать независимую последовательность коммитов в хронологическом порядке. Однако конкретно в Git реализация ветки выполнена как указатель на последний коммит в рассматриваемой ветке. После создания ветки уже новый указатель ссылается на текущий коммит.

Имя основной ветки Git-проекта по умолчанию — master (однако зачастую бывает main, например, в GitHub), она появляется сразу при инициализации репозитория. Эта ветка ничем не отличается от остальных и также ее можно переименовать, но по договоренности master принято считать главной веткой в проекте.

**Создание ветки**


Команда git branch — главный инструмент для работы с ветвлением. С ее помощью можно добавлять новые ветки, перечислять и переименовывать существующие и удалять их.

Делается это следующим образом в папке с репозиторием: *git branch <название новой ветки>*
Если вы планируете переместиться на другую ветку, в том числе только что созданную, необходимо написать **checkout**:

*git chechout <название уже созданной ветки>*


## Слияние веток

Ветвление позволяет разделять рабочий процесс, оптимизировать тестирование и написание нового кода. Однако после того, как разработчик убедился, что написанный им кусок кода готов и его можно отправить к остальной части итоговой версии, удобно переместить его в основную ветку. Такой подход дает возможность получить к концу разработки проекта целый продукт в одном месте.


Для этого в Git предусмотрено слияние — перенос изменений с одной ветки на другую. Однако сливаемая ветка (под этим определением мы подразумеваем ветку, у которой берем изменения для «вливания» их в другую ветвь) никак не меняется и остается в прежнем состоянии. Такие преобразования мы получаем, применив git merge.


Для того чтобы дабавить ветку в текущую ветку используется команда *git merge <name branch>*

## Удаление веток
Для удаления ветки ввести команду "git branch -d 'name branch'"

|Команда         | Описание |
|----------------|--------------|
|git init        | Инициализация репозитория|
|git add .| Добавление файла|
|git status| Проверка статуса репозитория|
|git commit -m "любое сообщение"|Внесение изменений однострочным сообщением или через редактор|
|git log -p| Просмотр истории коммитов с изменениями|
|git diff|Просмотр изменений до коммита|
|git checkout| Отмена подготовленных и неподготовленных изменений|
|git branch | Просмотр списка веток|


### Работа с удаленными репозиториями

**GitHub** - это облачная платформа для хостинга IT-проектов и совместной разработки, под капотом которой находится популярная система контроля версий Git, а также полноценная социальная сеть для разработчиков.

Здесь можно найти кучу open-source-проектов на разных языках и поучаствовать в них, разместить своё портфолио с примерами кода, чтобы приложить ссылку к резюме, подглядывать в открытых проектах интересные архитектурные решения, смотреть, как опытные разработчики пишут код, и скачивать огромное количество полезных в разработке и бесплатных инструментов для разработки. Кстати, некоторые умельцы умудряются собирать в GitHub целые библиотеки — книг и статей, а не программистские либы.


**Удаленный репозиторий** – это версии нашего проекта, сохраненные на удаленном сервере. Доступ к репозиторию на таком сервере может осуществляться по интернету или по локальной сети.
*Удаленный репозиторий* – полноценный репозиторий, ничем не отличающийся от локального. У удаленного репозитория есть собственные ветки, собственный указатель HEAD, своя история коммитов и так далее.

Если мы подключим удаленный репозиторий к своему локальному, то у нас появятся копии всех ссылочных объектов удаленного репозитория. 

Перед началом работы с удаленными репозиториями, необходимо:

1. Создать аккаунт на сайте *GitHub*
2. Создать свой собственный репозиторий
3. Далее система GitHub подскажет что нужно делать: 
  * git remote add origin <путь удаленного репозитория, скопированного с GitHub>
  * git branch -M main 
  * git push -u origin main
4. С помощью команды *git push* - мы отправляем изменения в удаленный репозиторий, к которому ранее "подключились"
5. С помощью команды *git pull* - мы загружаем изменения с GitHub
6. Чтобы получить возможность скопировать удаленный репозиторий с любого аккаунта пользователя на GitHub, необходима кнопка *fork*, с ее помощью можно скопировать репозиторий себе и в дальнейшем его редактировать.
7. С помощью команды *git clone* - мы можем скопировать репозиторий с GitHub себе на локальный компьютер.
8. **Обязательно** нужно создать собственную ветку **со своими** изменениями
9. Далее нужно отправить изменения на GitHub
10. После того, как мы подгрузили свои изменения, мы можем отправить их любому позьзователю. 
