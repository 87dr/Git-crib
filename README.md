#1. git init Сделать папку репозиторием

Например, создайте папку first-project и сделайте её Git-репозиторием: перейдите в неё с помощью команды cd и выполните git init.

$ cd ~/dev/first-project # перешли в нужную папку

$ git init # создали репозиторий

В зависимости от настроек Git может назвать начальную ветку или main, или master

Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку .git.

#2. git status
git status (от англ. status — «статус», «состояние») — показывает текущее состояние репозитория.

Команда git status выведет:
- название текущей ветки: On branch master или On branch main;
- сообщение о том, что в репозитории ещё нет коммитов: No commits yet;
- сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — nothing to commit (create/copy files and use "git add" to track).

В любой непонятной ситуации стоит посмотреть состояние (статус) репозитория, а потом решить, что делать дальше.

Состояние untracked значит, что Git ещё не хранит информацию о версиях файла и не может отследить, как он изменялся.

#3. git add

$ git add --all # подготовили к сохранению все файлы в репозитории
Добавлять файлы можно и по одному, без ключа --all.
$ git add readme.txt
$ git add . # добавить всю текущую папку

Но сохранения пока не произошло, потому что команда git add только запоминает текущее содержимое (контент) файла.

#4. git commit Выполнить коммит    

Сделать коммит можно командой git commit c ключом -m (от англ. message — «сообщение»), который присваивает коммиту сообщение.

$ git commit -m 'Мой первый коммит!' 

Сначала команда git add сообщает Git, какие именно файлы нужно сохранить и какую их версию. Затем с помощью команды git commit происходит само сохранение.

#5. git log  
Чтобы увидеть все commit, введите команду git log
Обратите внимание, что по умолчанию git log выводит коммиты в обратном хронологическом порядке — последние коммиты оказываются первыми сверху.  
Получить сокращённый лог можно с помощью команды git log с флагом --oneline. В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.
Сокращённый лог полезен, если в репозитории уже много коммитов — например, сотни или тысячи. В этом случае можно быстро найти нужный по описанию.

#6. Привязать удалённый репозиторий к локальному — git remote add  
Перейдите на страницу удалённого репозитория, выберите тип SSH и скопируйте URL. Кнопка справа позволит сделать это мгновенно.
Откройте консоль, перейдите в каталог локального репозитория и введите команду git remote add (от англ. remote — «удалённый» и add — «добавить»).

$ cd ~/dev/first-project
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
Команде необходимо передать два параметра: имя удалённого репозитория и его URL. В качестве имени используйте слово origin. А URL вы скопировали со страницы удалённого репозитория.

#7. Убедиться, что репозитории связаны, — git remote -v  

$ git remote -v
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push) 

В выводе вы должны увидеть две строчки, аналогичные тем, что показаны выше.
Флаг -v — короткая форма флага --verbose (англ. «подробный»). Он позволяет показать больше информации в выводе.

#8. git push Отправить изменения на удалённый репозиторий  
В первый раз эту команду нужно вызвать с флагом -u и параметрами origin (имя удалённого репозитория) и main или master (название текущей ветки). Флаг -u свяжет локальную ветку с одноимённой удалённой. Как вы связывали локальный и удалённый репозитории в предыдущем уроке, так же и здесь нужно дополнительно связать ветки.
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте 
                          # заменить main на master.

#8. Файл HEAD  
Файл HEAD (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним (то есть на самый новый).
Внутри HEAD — ссылка на служебный файл: refs/heads/master (или refs/heads/main в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита.
Если нужно передать последний коммит, то вместо его хеша можно просто написать слово HEAD — Git поймёт, что вы имели в виду последний коммит.
