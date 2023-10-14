# Привет, дорогой друг

## В этой статье ты найдешь всю необходимую информацию для работы с Git и GitHub

### *Данная статья предназначена для пользователей Windows

---

### Что такое Git?

**Git** - это консольная утилита, для отслеживания и ведения истории изменения файлов, в твоем проекте. Чаще всего его используют для кода, но можно и для других файлов. Например, для картинок - полезно для дизайнеров.
С помощью **Git-a** ты можешь откатить свой проект до более старой версии, сравнивать, анализировать или сливать свои изменения в репозиторий.
Репозиторием называют хранилище твоего кода и историю его изменений.

---

### Установка Git

Т.к. Git - консольное приложение, значит оно требует установки.
Скачать Git можно на официальном сайте приложения. [Скачать Git](https://git-scm.com/download/win)

Открываем скачанный файл и следуем инструкции установки.

- Проверь чтоб в списке устанавливаемых программ стояла галочка напротив пункта Git Bash Here — это позволит открывать консоль с Git в любой папке.

---

### Настройка Git

Запусти программу **Git Bash**.
Сделать это можно двумя способами:

1. можно ввести название программы в окно поиска на панели задач;
2. а можно открыть директорию, в которую был установлен Git. Обычно это директория *C:\Program Files\Git\bin*. Перейди в *bin* и запустите файл *bash.exe*.

Перед тобой откроется командная строка (тоже интерфейс, только текстовый).

Сейчас ты работаешь в одиночку, но в дальнейшем может понадобиться использовать Git в команде. Чтобы участникам проекта было понятно, кто и какие изменения вносил, нужно представиться и указать имя пользователя и адрес электронной почты.

Ты можешь указать любую электронную почту и любое имя. Сделать это можно с помощью команды `$ git config` (от англ. configuration — «конфигурация», «настройка») с ключом `--global` (англ. «глобальный»). При этом не имеет значения, в какой директории ты находишься прямо сейчас: вызов `$ git config --global` сработает везде.
В качестве значения `user.name` нужно указать своё имя или никнейм. Для настройки параметра `user.email` указывают электронную почту.

`$ git config --global user.name "User Namovich"` # имя или ник нужно написать латиницей и в кавычках.

`$ git config --global user.email username@yandex.ru` # здесь нужно указать свой настоящий email.

Все глобальные настройки Git хранит в файле `.gitconfig` в домашней директории. Команда запишет в этот файл указанные имя и почту. Чтобы убедиться в этом, можно вызвать команду для чтения файлов `$ cat ~/.gitconfig`.
Другой способ проверки — вывести содержимое файла конфигурации Git той же командой `$ git config` с флагом `--list` (англ. «список»).
`$ git config --list`
В ответ командная строка покажет текущие значения настроек:

- `user.name=Username`;
- `user.email=username@yandex.ru`.

### Работа в Git Bash

В окне программы ты увидишь ```USER_NAME@HOST_NAME MINGW64```.
Вместо `USER_NAME` будет указано твое имя пользователя, а вместо `HOST_NAME` — имя компьютера.
Символ доллара ($) — он означает, что программа ждёт твоих команд.
После каждой команды необходимо нажать клавишу Enter. В Git можно писать сразу несколько команд, но их следует разделять двумя операндами `&&`. Пример `$ mkdir newProject && touch Readme.txt`.

У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх `(↑)` и вниз `(↓)`.
Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать `Tab`. Если файл или папка есть в текущей директории, командная строка допишет путь сама.

*В командную строку нельзя вставить текст из буфера обмена с помощью привычного сочетания Ctrl+V. На Windows (в Git Bash) для этого используется сочетание `Ctrl+Shift+V` (у меня это `Shift+Ins`). Также можно нажать правую кнопку мыши и выбрать пункт Paste (англ. «вставить») в выпадающем меню.*

#### Создание директории (папки) твоего проекта

Выбери удобное тебе место на компьютера для хранения проекта. Теперь для него нужно создать директорию.

- Чтобы создать директорию в правильном месте, для начала необходимо перейти перейти в нужный раздел.
Узнать, где ты сейчас, поможет команда `$ pwd`.
По умолчанию ты будешь находиться в домашней директории `/c/Users/%USERNAME%`.
Для перехода в папку, где будет создана директория проекта используй команду `$ cd`. Пример: `$ cd D:/project/`.

`$ cd ..` — перейди на уровень выше, в родительскую папку. Пример: был в *D:/Download/Games*, выполнил команду `cd ..` и оказался в *D:/Download*;

Cимвол `~` — обозначение домашней директории. С его помощью можно быстро оказаться в домашней директории командой `$ cd ~` - *C:/Users/Fadesunrise*.

Чтобы создать новую директорию используй `$ mkdir`. Пример: `$ mkdir new-project`.

Чтобы удалить директорию используй команду `$ rm dir`.
Если в папке находятся в файлы, то используй команду `$ rm -r`. Команда удалит все файлы в папке и саму папку.

Готово! Ты создал место, где будет храниться твой проект.

Пока в нем пусто и давай это исправим: создадим первый файл, который будет называться `README.txt`.
За создание новый файлов отвечает команда `$ touch`. Пример: `$ touch README.txt`. Перед этим убедись, что ты находишься в правильной директории командой `$ pwd`.

`$ ls` — покажет файлы и папки, находящиеся в той папке в которой находишься.
`$ ls -a` — покажет также скрытые файлы и папки, названия которых начинаются с символа `.`.

Удалить файл можно командой `$ rm`. Пример: `$ rm README.txt`.
Команда `$ mv *название файла* *место, куда перемещаем*` отвечает за перемещение. Пример: находясь в директории необходимого файла `$ mv  Readme.txt D:/project`

Посмотреть содержимое файла можно с помощью команды `$ cat`. Пример: `$ cat Readme.txt` или даже `$ cat D:/project/Readme.txt`.

### Отлично! Теперь инициализируем папку как **Git репозиторий**

Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно сделать **Git-репозиторием**.
Для этого следует переместиться в неё и ввести команду `$ git init`.
Пример: переходим в папку проекта `$ D:/project/` и вводим `$ git init` (создали репозиторий Git).
`$ git init` выведет сообщение вида `Initialized empty Git repository in <*ваша папка с проектом*>/.git/` (англ. «инициализирован пустой Git-репозиторий в <*ваша папка*>/.git/»). В подпапке .git Git будет хранить всю служебную информацию.
Команда `$ git init` — одна из редко применяемых, ведь репозиторий создаётся один раз, а пользоваться им можно сколько угодно долго.

Если ты случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку .git.
`$ cd <папка с репозиторием>` # перешли в папку
`$ rm -rf .git` # удалили подпапку .git

Разберём подробнее, что такое `-rf`:

1. ключ `-r` (от англ. recursive — «рекурсивно») позволяет удалять папки вместе с их содержимым;
2. ключ `-f` (от англ. force — «заставить») избавит тебя от вопросов вроде «Вы точно хотите удалить этот файл? А этот? И этот тоже?».

## Если удалить .git, то вся история проекта будет стёрта без возможности восстановления — останется только последняя версия файлов

`$ git status` показывает текущее состояние репозитория.
Команда `$ git status` выведет:

1. название текущей ветки: `On branch master` или `On branch main`;
2. сообщение о том, что в репозитории ещё нет коммитов: `No commits yet`;
3. сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — `nothing to commit (create/copy files and use "git add" to track)`.

Также **Git** сообщит, что в папке проекта есть *untracked files* (от англ. track — «следить», untracked — «неотслеженный», «неотслеживаемый») — ещё не отслеживаемые файлы.

Состояние `untracked` значит, что Git ещё не хранит информацию о версиях файла и не может отследить, как он изменялся.
Сейчас в папке есть файл. Мы хотим отслеживать его состояние, поэтому можем использовать команду `$ git add Readme.txt` или `$ git add --all`.
`$ git add --all` позволяет подготовить к сохранению все файлы в репозитории.

Также можно добавить текущую папку целиком — в этом случае все файлы в ней тоже будут добавлены. Обратиться к текущей папке в Bash позволяет точка (.).
`$ git add .` # добавить всю текущую папку.

Выполни `$ git status` и проверь в каком состоянии файл.
Он будет отмечен зеленым.
Теперь внеси изменения в README.txt с помощью любого текстового редактора. Например, напиши "Мой первый Git проект" и сохрани.
Снова выполни `$ git status`. Теперь твой файл отмечен красным. Это значит, что изменения не были сохранены и необходимо снова выполнить команду `$ git add`.

**`$ git add` только запоминает текущее содержимое (контент) файла.**

Команда `git add` не сохраняет содержимое файлов в репозитории. Само сохранение, или фиксацию состояния файлов, называют коммитом (от англ. commit — «совершать», «фиксировать»). «Сделать коммит» значит сохранить текущую версию файла.

### Делаем первый коммит

Сделать коммит можно командой `git commit` c ключом `-m` (от англ. message — «сообщение»), который присваивает коммиту сообщение.

*Обычно в таком сообщении поясняется, в чём именно состояли изменения. Это как заметки на полях: благодаря им проще читать и понимать текст. Сообщение коммита выполняет те же функции — улучшает понимание и упрощает навигацию. Оно пишется после ключа `-m` в кавычках.*

`$ git commit -m ‘Создал файл README.txt, в которо будут описаны некоторые интрукции или напоминания.’`
После нажатия `Enter` текущая версия файлов будет сохранена в репозитории с сообщением *Создал файл README.txt, в которо будут описаны некоторые интрукции или напоминания.*.
***Коммит должен говорить о происходящих изменениях, чтобы читатели смогли увидеть разницу или понять, какая работа была произведена.***

Команда `$git commit` выведет информацию о коммите.
`[master (root-commit) baa3b6e]` значит:
коммит был в ветке `master`;
`root-commit` — это самый первый, или «корневой» (англ. root), коммит в ветке, у следующих коммитов такой надписи не будет;
`baa3b6e` — сокращённый идентификатор коммита (подробнее об этом мы ещё расскажем).
`1 files changed, 1 insertion(+)` значит:

- изменились два файла (readme.txt и todo.txt);
- одна строка была добавлена (1. Пройти пару уроков по Git.).
Строки вида `create mode 100644 README.txt` — это более подробная информация о новых (добавленных в Git) файлах.
- `create` (англ. «создать») говорит, что файл был создан. Если бы файл был удалён, на этом месте было бы слово delete (англ. «удалить»).
- `mode 100644` сообщает, что это обычный файл. Также возможны варианты `100755` для исполняемых файлов (например, что-нибудь.exe) и `120000` для файлов-ссылок в Linux. Файлы-ссылки не содержат данных сами по себе, а только ссылаются на другие файлы — как «ярлыки» в Windows.

Сначала команда `git add` сообщает **Git**, какие именно файлы нужно сохранить и какую их версию. Затем с помощью команды `git commit` происходит само сохранение.

Внеси изменения в файл `README.txt`, выполни `$ git add`, а затем `$git commit`.
Теперь посмотрим историю коммитов с помощью команды `$ git log`

До этого момента ты использовал Git локально: сейчас проект first-project хранится только на твоем компьютере.

### Теперь у нас есть Git проект, но его еще никто не видит, т.к. он локальный и находится только на твоем ПК. Сделаем так, чтоб твои друзья или сотрудники имели к нему доступ, а также видели какие изменения ты вносишь. В этом нам поможет GitHub

---

## Git Hub

**GitHub** — платформа для хранения IT-проектов и совместной работы над ними с использованием Git. По сути, это сайт, куда можно загрузить файлы своего проекта для обмена с другими людьми.

Можно создавать проекты разных типов:

1. приватный — только для тебя;
2. командный — только для членов команды;
3. публичный — будет виден всем.

**Git** и **GitHub** — это два разных проекта, которые развиваются независимо друг от друга.
Git:

- консольный инструмент для работы с локальными и удалёнными репозиториями;
- проект с открытым исходным кодом.

GitHub:

- платформа для размещения удалённых репозиториев;
- принадлежит компании Microsoft.

Кроме GitHub, есть и другие платформы для командной работы. Например, GitLab и Bitbucket, которые тоже позволяют работать с Git. У каждой из этих платформ свои особенности и дополнительная функциональность:

- GitLab можно развернуть в виде сервера в приватной сети;
- Bitbucket — продукт компании Atlassian, поэтому он легко интегрируется с другими инструментами этой компании, такими как Jira.

## Создаем удаленный репозиторий на GitHub

1. Зайди в свой профиль по ссылке `https://github.com/username`, где `username` — имя, которое ты указал при регистрации;
2. Создай репозиторий. Для этого перейди на вкладку `Repositories` (англ. «репозитории»), а затем нажми на зелёную кнопку `New` (англ. «новый») справа;
3. Назови его `first-project`. Название удалённого репозитория необязательно должно совпадать с именем папки проекта у тебя на компьютере. Но чтобы не путаться, будем называть их одинаково.
Другие поля пока не понадобятся. Смело нажимай на зелёную кнопку `Create repository` (англ. «создать репозиторий») внизу;
4. Осталось связать удалённый репозиторий с локальным, который уже есть на твоем компьютере. GitHub предоставляет для этого инструкцию `(пункт …or push an existing repository from the command line)`.

Но прежде, чтобы упростить работу с GitHub и сделать её более безопасной, ты научишься генерировать SSH-ключи (от англ. Secure Shell — «безопасная оболочка»).

### Генерируем SSH-ключ

Когда компьютеры обмениваются данными в сети, они следуют сетевым протоколам (англ. network protocols) — правилам обмена данными между компьютерами.

Один из наиболее распространённых сетевых протоколов — SSH (от англ. Secure Shell Protocol). Он обеспечивает безопасный обмен данными в сети. С помощью этого протокола можно получать данные с удалённого компьютера или отправлять их на него. Трафик шифруется, поэтому протокол безопасен.

SSH использует пару ключей для обеспечения безопасности — публичный и приватный:

- Приватный ключ (англ. private key) хранится только на твоем компьютере и не должен передаваться кому-либо ещё. Он используется для расшифровки данных.
- Публичный ключ (англ. public key) доступен всем и используется для шифрования данных. Они могут быть расшифрованы парным приватным ключом.

Только ты можешь расшифровать данные с помощью приватного ключа, но любой владелец публичного ключа может их для тебя зашифровать. Эти два ключа связаны и образуют SSH-пару. В будущем ты наверняка будешь использовать их для взаимодействия с GitHub и другими удалёнными серверами.

### Проверка наличия SSH-ключа

Прежде чем генерировать SSH-ключи, убедись, что у тебя их ещё нет. По умолчанию директория с SSH-ключами находится в домашней директории пользователя. Перейди в неё - `$ cd ~`.

Обычно SSH-ключи находятся в директории `.ssh/`. Проверить наличие этой директории и файлов в ней можно с помощью команды `$ ls -la .ssh/`.

Если папка пустая или её нет, всё в порядке.
Если есть файлы с похожими названиями, SSH-ключи уже создавались:

- id_dsa.pub;
- id_ecdsa.pub;
- id_ed25519.pub;
- id_rsa.pub.
Если ты не создавал эти файлы, удали их все.

### Инструкция по генерации SSH-ключа

Для генерации SSH-пары можно использовать команду ssh-keygen. Открой терминал и введите следующую команду:
`$ ssh-keygen -t ed25519 -C "электронная почта, к которой привязан твой аккаунт на GitHub"`

Используй электронную почту, к которой привязан твой GitHub-аккаунт.

Если видишь сообщение об ошибке, то, скорее всего, твоя система не поддерживает алгоритм шифрования `ed25519`. Ничего страшного: используй другой алгоритм:
`$ ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан твой аккаунт на GitHub"`.

После ввода отобразится такое сообщение:

> Generating public/private rsa key pair. # сгенерированы публичный и приватный ключи.

Укажи место хранения ключей. Простой вариант — сделать домашний каталог пользователя путём по умолчанию. Для этого нажмите Enter.

> Enter a file in which to save the key (C:\Users\<имя_пользователя>\.ssh\):`[Press enter]`

Теперь в указанной директории появится пара ключей.

Программа запросит кодовую фразу (англ. passphrase) для доступа к SSH-ключу. Вы можете оставить поле пустым. Для этого нажмите Enter, а затем ещё раз Enter для подтверждения.

> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]

Теперь осталось проверить, что ключи действительно сгенерировались. Для этого вызови команду `ls -a ~/.ssh`.

На экране должны появиться два файла — один с расширением .pub, другой — без. Файл в .pub — публичный, им можно делиться с веб-сайтами или коллегами. Файл без расширения .pub — приватный. Ни в коем случае не передавайте его никому!

## Привязываем SSH-ключ к GitHub

После выполнения команды `ssh-keygen` в директории `~/.ssh` будет создано два файла: `id_ed25519` и `id_ed25519.pub` (или `id_rsa` и `id_rsa.pub` — в зависимости от того, какой алгоритм использовал):

- id_ed25519/id_rsa — приватный ключ (файл без .pub в конце). Ни в коем случае не копируйте его и не делитесь им.
- id_ed25519.pub/id_rsa.pub — публичный ключ (на это указывает расширение .pub).

Скопируй содержимое файла с публичным ключом в буфер обмена.

Скопировать содержимое ключа в буфер обмена:
`$ clip < ~/.ssh/id_rsa.pub`
Для ed25519:
`$ clip < ~/.ssh/id_ed25519.pub`

Далее:

1. переходим на GitHub и выберите пункт **Settings** в меню аккаунта;
2. в меню слева нажми на пункт **SSH and GPG keys**;
3. в открывшейся вкладке выбери **New SSH key**;
4. в поле **Title** напиши название ключа. Например, *Personal key*;
5. в поле **Key type** (англ. «тип ключа») должно быть Authentication Key (англ. «ключ аутентификации»);
6. в поле **Key** скопируйте ваш ключ из буфера обмена;
7. нажмите на кнопку **Add SSH key**;
8. проверь правильность ключа с помощью команды `$ ssh -T git@github.com`.

Если это первый раз, когда ты используешь Git, чтобы поделиться проектом на GitHub, появится похожее предупреждение:

"The authenticity of host 'github.com (140.82.121.4)' can't be established. ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU. This key is not known by any other names. Are you sure you want to continue connecting (yes/no/[fingerprint])?"

Это предупреждение сообщает, что ты никогда не соединялся с сервером GitHub. Поэтому Git не может гарантировать, что сервер является тем, за кого он себя выдаёт.

Для подтверждения подлинности сервер генерирует и публикует ключи SHA256.

Ты можешь проверить ключи GitHub [по этой ссылке](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints).

Если ключ в предупреждении совпадает с тем, что ты видишь на сайте, значит, сервер является действительным. Введи `yes`, чтобы продолжить. Ты увидишь приветствие на экране:

"Hi %ВАШ_АККАУНТ%! You've successfully authenticated, but GitHub does not provide shell access."

Теперь твой ключ привязан к GitHub. Если ты установил кодовую фразу для SSH-ключа, её нужно будет вводить для работы с репозиторием.

## Связываем локальный и удалённый репозитории

Сейчас у тебя есть локальный репозиторий first-project, который хранится на твоем компьютере, и удалённый репозиторий на GitHub. Ты сгенерировал SSH-ключ для безопасной работы и теперь готовы связать удалённый репозиторий с локальным.

Перейди на страницу удалённого репозитория, выбери тип SSH и скопируйте URL. Кнопка справа позволит сделать это мгновенно.

Открой консоль, перейди в каталог локального репозитория и введи команду git remote add (от англ. remote — «удалённый» и add — «добавить»).
`$ cd ~/dev/first-project`
`$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git`
Команде необходимо передать два параметра: имя удалённого репозитория и его URL. В качестве имени используй слово origin. А URL ты скопировал со страницы удалённого репозитория.

Отлично: ты связал локальный репозиторий с удалённым. Осталось убедиться, что всё работает, с помощью следующей команды `$ git remote -v`.
В выводе ты должен увидеть две строчки:
> origin    <git@github.com>:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
> origin    <git@github.com>:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)

Флаг `-v` — короткая форма флага `--verbose` (англ. «подробный»). Он позволяет показать больше информации в выводе.

## Синхронизируем локальный и удалённый репозитории

Ты зарегистрировался на GitHub, сгенерировал SSH-ключ и привязал локальный репозиторий к удалённому. Самое сложное позади. Теперь разберём, как выкладывать свои правки на удалённый репозиторий. Но сначала немного о ветках.

**Основная ветка.**

Мы упоминали, что каждый коммит сохраняет актуальное состояние файлов. Сами же коммиты хранятся в ветках (англ. branch).

Ветка всегда начинается от одного из коммитов.

В репозитории может существовать сразу несколько веток — параллельных историй изменений. Также они могут соединяться друг с другом.

Самая первая ветка в репозитории появляется автоматически и называется `main` (англ. «основная») или `master`. Её имя нужно указывать при отправке коммитов на удалённый репозиторий или при получении их из него.

### Отправить изменения на удалённый репозиторий

Мы уже прошли весь «цикл коммита»: подготовили файлы с помощью `git add`, закоммитили их с комментарием командой `git commit -m`. Осталось загрузить содержимое локального репозитория на GitHub. За это отвечает команда `git push` (от англ. push — «толкать»).

В первый раз эту команду нужно вызвать с флагом `-u` и параметрами `origin` (имя удалённого репозитория) и `main` или `master` (название текущей ветки). Флаг `-u` свяжет локальную ветку с одноимённой удалённой.

`$ git push -u origin main`

При взаимодействии с удалёнными репозиториями Git выводит в консоль отладочную информацию: количество объектов (файлов), которые отправляются на сервер, информацию о прогрессе сжатия и записи и так далее.

Если ты указывал кодовую фразу при настройке SSH-ключей, её нужно будет ввести.

Зайди в репозиторий `first-project` на GitHub. Ты увидишь, что в репозитории появились файлы с изменениями.

В дальнейшем при работе с удалённым репозиторием флаг `-u` можно опустить и писать просто `git push`.

## Работа с графическим интерфейсом GitHub

Нажми на кнопку `commit` в правой части страницы, чтобы просмотреть все коммиты в репозитории. Откроется окно с коммитами и их авторами.
**Сообщение коммита в репозитории тоже является ссылкой.**

Перейди по ссылке, кликни на текст последнего коммита над репозиторием — так ты сможешь увидеть все изменения, которые были внесены в репозиторий в этом коммите.

Чтобы увидеть наглядно проделай следующие шаги:

1. открой проект `first-project` и создайте в нём файл `task.txt` с помощью `touch`;
2. открой файл `task.txt` в текстовом редакторе и внесите любые изменения. Затем сохраните и закрой файл;
3. сделай коммит и синхронизируйте изменения с удалённым репозиторием `$ git push`;
4. воспользуйся интерфейсом GitHub, чтобы посмотреть твой последний коммит. Для этого нажми на имя коммита.

---

### Что делать, если надо откатить изменения?

#### 1. Если через `git add` добавил лишний файл

Допустим, ты создал или изменил какой-то файл и добавил его в список «на коммит» (staging area) с помощью `git add`, но потом передумал включать его туда. Убрать файл из staging поможет команда `git restore --staged <file>`

В терминале это будет выглядеть примерно так:

```bash
$ touch example.txt # создали ненужный файл
$ git add example.txt # добавили его в staged

$ git status # проверили статус
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   example.txt

$ git restore --staged example.txt
$ git status # проверили статус

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        example.txt

no changes added to commit (use "git add" and/or "git commit -a")
# файл example.txt из staged вернулся обратно в untracked
```

Вызов `git restore --staged example.txt` перевёл `example.txt` из `staged` обратно в `untracked`.
Чтобы «сбросить» все файлы из staged обратно в `untracked/modified`, можно воспользоваться командой `git restore --staged .`: она сбросит всю текущую папку.

#### «Откатить» коммит

Иногда нужно «откатить» то, что уже было закоммичено, то есть вернуть состояние репозитория к более раннему. Для этого используют команду `git reset --hard <commit hash>`

```bash
$ git log --oneline # хеш можно найти в истории
7b972f5 (HEAD -> master) style: добавить комментарии, расставить отступы
b576d89 feat: добавить массив Expenses и цикл для добавления трат # вот сюда и вернёмся
4b58962 refactor: разделить analyzeExpenses() на countSum() и saveExpenses()

$ git reset --hard b576d89
# теперь мы на этом коммите
HEAD is now at b576d89 feat: добавить массив Expenses и цикл для добавления трат
```

Теперь коммит `b576d89` стал последним: вся дальнейшая разработка будет вестись от него. Файл также вернулся к тому состоянию, в котором был в момент этого коммита. А коммит `7b972f5` Git просто удалил. Это можно проверить, снова запросив лог. Он покажет следующее.

```bash
$ git log --oneline
b576d89 (HEAD -> master) feat: добавить массив Expenses и цикл для добавления трат
4b58962 refactor: разделить analyzeExpenses() на countSum() и saveExpenses()
```

#### «Откатить» изменения, которые не попали ни в staging, ни в коммит

Может быть так, что ты случайно изменили файл, который не планировал. Теперь он отображается в `Changes not staged for commit` (`modified`). Чтобы вернуть всё «как было», можно выполнить команду `git restore <file>`.

```bash
# случайно изменили файл example.txt
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
          modified:   example.txt

$ git restore example.txt
$ git status
On branch main
nothing to commit, working tree clean
```

Изменения в файле «откатятся» до последней версии, которая была сохранена через `git commit` или `git add`.

#### Просмотр изменений в файле на этапе подготовки (коммита)

При работе с Git часто нужно узнать, что конкретно изменится или уже изменилось после того или иного коммита. Вот примеры таких ситуаций:

- Ты собираешься сделать коммит, но хочешь проверить (или перепроверить), какие именно изменения в него попадут.
- Вчера твой коллега сделал коммит с сообщением `small fix` (англ. «небольшое исправление»), после чего тесты проекта начали «падать». Чтобы разобраться в ситуации, нужно посмотреть, что изменилось в этом коммите.

Всё это позволяет делать команда `git diff` (от англ. difference — «отличие», «разница»).

Проверим локигу данной команды:

1. создай файл `example.txt`, наполни его любой информацией и сохрани;
2. подготовь его командами `git add` и `git commit`;
3. теперь внеси изменения в `example.txt`;
4. введи команду `git diff`.

Команда `git diff` выведет:

```bash
diff --git a/example.txt b/example.txt
index 901da07..ac459e1 100644
--- a/example.txt
+++ b/example.txt
@@ -1,2 +1,2 @@
 Теремок стоит, и в нём:
-никого нет
+Мышка-норушка
```

Самое важное `git diff` выводит в конце:

- красный цвет строки никого нет значит, что эта строка была удалена;
- зелёный цвет строки Мышка-норушка значит, что она была добавлена.

Не все консоли умеют выводить цвета, поэтому строки помечаются не только цветом, но и знаком `-` или `+`. Минус — это удалённые строки, плюс — это добавленные.
Коротко разберём остальные строки вывода команды:
Первые две строки (`diff --git a/... b/...` и `index 901da07..ac459e1 100644`) — это низкоуровневая техническая информация.
Строки `--- a/example.txt` и `+++ b/example.txt` говорят, что дальше будет выведен результат сравнения файлов `a/example.txt` и `b/example.txt` — исходной и текущей версий.
Строка `@@ -1,2 +1,2 @@` сообщает, какие строки файла попали в сравнение. Выражение `1,2` (неважно, с плюсом или с минусом) говорит, что были использованы две строки, начиная с первой. Если бы было, например, написано `+15,7`, это значило бы, что в сравнении участвуют 7 строк, начиная с 15-й.

Выражение со знаком минус (`-1,2`) относится к «оригинальной» версии файла (`a/example.txt`), а со знаком плюс (`+1,2`) — к «изменённой» (`b/example.txt`).

#### Просмотр изменений после команды git add и git commit

В данном случае необходимо будет использовать команду `git diff --staged`.

Пример:

1. создали файл;
2. выполнили `git add`, или `git add` + `git commit`;
3. смотрим изменения команддой `git diff --staged`.

#### Сравнить изменения в файле сравнив коммиты

Чтобы узнать какие изменения проиходили в файле в определенный период (например, между самым первым и самым последним) cледует прибегнуть к команде git diff и указать эти самые коммиты.

`git diff 5fa9653 acba029`

- `5fa9653` - самый первый коммит
- `5fa9653` - самый последний (новый). Вместо хеша последнего коммита можно написать `HEAD`, т.к. он передает последний коммит.

Пример: `git diff 5fa9653 HEAD`

#### Откат (шпаргалка)

- Команда `git restore --staged <file>` переведёт файл из staged обратно в modified или untracked.
- Команда `git reset --hard <commit hash>` «откатит» историю до коммита с хешем `<hash>`. Более поздние коммиты потеряются!
- Команда `git restore <file>` «откатит» изменения в файле до последней сохранённой (в коммите или в staging) версии.

### Шпаргалка. Начало работы с Git

#### Инициализация репозитория

`git init` (от англ. initialize, «инициализировать») — инициализируй репозиторий.

#### Синхронизация локального и удалённого репозиториев

`git remote add origin https://github.com/YandexPracticum/first-project.git` (от англ. remote, «удалённый» + add, «добавить») — привяжи локальный репозиторий к удалённому с URL <https://github.com/YandexPracticum/first-project.git>;

`git remote -v` (от англ. verbose, «подробный») — проверь, что репозитории действительно связались;

`git push -u origin main` (от англ. push, «толкать») — в первый раз загрузи все коммиты из локального репозитория в удалённый с названием `origin`.

`git push` (от англ. push, «толкать») — загрузи коммиты в удалённый репозиторий после того, как он был привязан с помощью флага `-u`.

#### Подготовка файла к коммиту

- `git add todo.txt` (от англ. add, «добавить») — подготовь файл todo.txt к коммиту;

- `git add --all` (от англ. add, «добавить» + all, «всё») — подготовь к коммиту сразу все файлы, в которых были изменения, и все новые файлы;

- `git add .` — подготовь к коммиту текущую папку и все файлы в ней.

#### Создание и публикация коммита

- `git commit -m` "Комментарий к коммиту." (от англ. commit, «совершать», фиксировать» + message, «сообщение») — сделай коммит и оставь комментарий, чтобы было проще понять, какие изменения сделаны;
- `git push` (от англ. push, «толкать») — добавь изменения в удалённый репозиторий.

#### Просмотр информации о коммитах

- `git log` (от англ. log, «журнал [записей]») — выведи подробную историю коммитов;
- `git log --oneline` (от англ. log, «журнал [записей]» + oneline, «одной строкой») — покажи краткую информацию о коммитах: сокращённый хеш и сообщение.

#### Просмотр состояния файлов

- `git status` (от англ. status, «статус», «состояние») — покажи текущее состояние репозитория.
Добавление изменений в последний коммит
- `git commit --amend --no-edit` (от англ. amend, «исправить») — добавь изменения к последнему коммиту и оставь сообщение прежним;
- `git commit --amend -m "Новое сообщение"` — измени сообщение к последнему коммиту на Новое сообщение.

#### «Откат» файлов и коммитов

- `git restore --staged hello.txt` (от англ. restore, «восстановить») — переведи файл hello.txt из состояния staged обратно в untracked или modified;
- `git restore hello.txt` — верни файл hello.txt к последней версии, которая была сохранена через git commit или git add;
- `git reset --hard b576d89` (от англ. reset, «сброс», «обнуление» + hard, «суровый») — удали все незакоммиченные изменения из staging и «рабочей зоны» вплоть до указанного коммита.

#### Просмотр изменений

git diff (от англ. difference, «отличие», «разница») — покажи изменения в «рабочей зоне», то есть в modified-файлах;
git diff a9928ab 11bada1 — выведи разницу между двумя коммитами;
git diff --staged — покажи изменения, которые добавлены в staged-файлах.

**Ну вот и все!**

Теперь ты способен выкладывать свои Git проекты на GitHub.

Пройти подробный и полный курс можно на [Яндекс Практикум](https://practicum.yandex.ru/referrals/?ref_code=gAAAAABkvS8-4d5FUdBnXzzd8LfyyVN7i38Vkv6cJG7xsoPfminiAY6CJ2MIqjps1o0azi_AgrLAzWcawMZWHpvb3V_oOzRNbQ%3D%3D).

Желаю удачи!
