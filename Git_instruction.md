![Logo](git-logo.jpeg)
# Работа с Git
## 1. Проверка наличия установленного Git
В терминале выполнить команду `git version`.

Выделение в блок 
```
ввести три знака обратный
```
Если Git установлен,  появится сообщение с информацией о версии программы. иначе будет сообщение об ошибке.
## 2. Установка Git
Загрушаем последнюю версию Git c сайта  https://git-scm.com/downloads. Устанавливаем с настройками по умолчанию. 
## 3. Настройка Git

 При первом использовании Git необходимо представиться. Для этого нужно ввести в терминале две команды:
 ```sql
 git config --global user.name «Ваше имя английскими буквами» 
 git config --global user.email ваша почта@example.com
 ```
## 4. Инициализация репозитория

Репозиторий Git — это виртуальное хранилище проекта. В нем можно хранить версии кода для доступа по мере необходимости.

Команда git init создает новый репозиторий Git, данная команда обычно выполняется первой в рамках нового проекта.

Команду git init выполняют только один раз для первоначальной настройки нового репозитория. 

Для инициализации репозитария введите в терминале команду 
>git init

Создастся специальная скрытая папка для Git.

## 5. Запись изменений в репозитарий.

Команда позволяющая узнать текущее состояние.
>git status

Команда подготавливает изменения к фиксации, указывается команда с именем файла.
>git add "имя файла"

Для создания комментария используем данную команду, в скобках указываем текст комментария. После данной операции сохраняется текущее состояние. Команда сохраняет (фиксирует) в репозитории изменения.
>git commit -m "текст"

## 6. Просмотр изменений.
Перечисляет коммиты, сделанные в репозитории в обратном к хронологическому порядке — последние коммиты находятся вверху.
Для просмотра истории всех сохранений используется команда
>git log

Команда git log --oneline выдает краткий список изменений в одну строку.

## 7. Для просмотра разницы между файлами
Команда git diff используется для вычисления разницы между любыми двумя Git деревьями.
Она показывает изменения которые внесесны в файл после последней фиксации.
>git diff

Для визуализации используется разная подстветка.
При запуске команды git diff, нам выведется в консоль красным что мы удалили, а зеленым что добавили.

## 8. Перемещение между сохранениями
При просмотре истории всех сохраненных коммитов мы можем перейти к предыдущему состоянию или к любому изменению по истории. 
Для этого используем команду git checkout в "<>" указываем либо полное название коммита, либо первые 4-7 первых симоволов. 
>git checkout

Для возврата к актуальноме состоянию используем команду git checkout master. 

## 9.  Игнорирование файлов
Для того что бы исключить из отслеживания в репозитории определенные файлы или папки необходимо создать файл ***.gitignore*** в корне проекта. В этот файл добавляются файлы и директории, которые надо игнорировать. Как только .gitignore создан и в него добавлен какой-то файл или директория, игнорирование заработает автоматически. Все новые файлы, попадающие под игнорирование, не отобразятся в выводе команды git status.

Для того что бы не перечеслять все файлы имеющих одно расширение, можно заменить название на символ (*) и оставить расширение через точку: *.jpeg. Тогда буду игнорироваться все файлы с данным расширением.

## 10. Создание веток в Git

Текущая ветка будет отмечена (*) звездочкой. 

Создать ветку можно командой 
>git branch <имя новой ветки>

В результате создается новый указатель на текущий commit.

Ветка в Git - это простой перемещаемый указатель на один из commit. Обычно это последний в цепочке commit. 
По умолчанию имя основной ветки в Git - master. 
Список веток в репозитории можно посмотреть с помощью команды git branch.

Для переключения на существующую ветку выполните команду 
>git checkout. 

Команда git checkout -b. Команда git checkout умеет создавать ветки и сразу переключаться на них. Это намного удобнее, чем выполнять два этих действия по отдельности. Поэтому данный способ является более предпочтительным, так как задействует только одну команду git checkout со специальным ключом -b . 

## 11. Слияние веток и разрешение конфликтов
Для слияния выбранной ветки с текущей нужно переключиться на ветку, в которую вы хотите включить изменения, и выполнить команду.

>git merch <название выбранной ветки>

Команда git merge выполняет слияние отдельных направлений разработки, созданных с помощью команды git branch, в единую ветку.

Если вы изменили одну и ту же часть одного и того же файла по-разному в двух объединяемых ветках, Git не сможет их объединить,  вы получите сообщение о конфликте слияния. Git не создал коммит слияния автоматически. Он остановил процесс до тех пор, пока вы не разрешите конфликт. Чтобы в любой момент после появления конфликта увидеть, какие файлы не объединены, вы можете запустить git status. Всё, где есть неразрешённые конфликты слияния, перечисляется как неслитое. 
Чтобы разрешить конфликт, придётся выбрать один из вариантов, либо объединить содержимое по-своему.
Разрешив каждый конфликт во всех файлах, запустите git add для каждого файла, чтобы отметить конфликт как решённый. Добавление файла в индекс означает для Git, что все конфликты в нём исправлены.
После выхода из инструмента слияния Git спросит об успешности процесса. Если вы ответите утвердительно, то он добавит файл в индекс, чтобы отметить его как разрешенный. Теперь можно снова запустить git status, чтобы убедиться в отсутствии конфликтов.
Если это вас устраивает и вы убедились, что все файлы, где были конфликты, добавлены в индекс — выполните команду git commit для создания коммита слияния. 

## 12. Удаление ветки

Удалить ветку можно параметром branch с добавлением флага -d и указанием имени ветки. 
> git branch -d

Если вы завершили работу над веткой и объединили её с основной, можно её удалить без потери истории. Однако, если выполнить команду удаления до слияния — в результате появится сообщение об ошибке. Этот защитный механизм предотвращает потерю доступа к файлам.

Для принудительного удаления ветки используется флаг -D с заглавной буквой. В этом случае ветка будет удалена независимо от текущего статуса, без предупреждений.

Если в ветке присутствуют несмерженные изменения или незапушенные коммиты, флаг -d не позволит удалить такую локальную ветку.
Это связано с тем, что эти коммиты нигде более не отслеживаются, и Git защищает вас от случайной потери этих данных.

## 13. Работа с удаленными репозитариями

Команда ***git fetch*** связывается с удалённым репозиторием и забирает из него все изменения, которых у вас пока нет и сохраняет их локально.

Команда ***git pull*** работает как комбинация команд git fetch и git merge, т. е. Git вначале забирает изменения из указанного удалённого репозитория, а затем пытается слить их с текущей веткой.



![Logo](Theend.jpeg)