# Пилотная методичка

### :minibus: Пути
> :memo: Путь - коротко говоря то, где расположен файл.

Представим, что у нас есть папка `foo/`, в которой есть другая папка `bar/`, в которой расположен файл `baz/`. Тогда путь для файла `baz/` будет выглядеть как `foo/bar/baz/`

В системах UNIX/Linux все пути начинаются из корневого раздела - `/`. Это не просто черточка, это указатель на вполне определённый раздел жесткого диска.

Пути бывают двух типов: абсолютные и относительные пути.
В чем же разница?

**Абсолютный путь** требует указания ПОЛНОГО перечня директорий до текущей директории. Например, нам нужна директория `log/`. Для того, чтобы получить доступ к этой директории, нам придётся записать полный её путь от корневого раздела: `/var/log`. Обрати внимание, что запись пути мы начали с `/` - корневого раздела, затем записали папку `var/`, в которой находится директорию `log/`.
 
**Относительный путь** более умный. Допустим, нам все также требуется получить доступ к файлу `log_file` в директории `/var/log/`, но сейчас мы находимся в директорию `var/`. Чтобы получить доступ к `log_file` нам достаточно указать путь `log/log_file`. Терминал знает то, в какой директорию ты сейчас находишься и достаточно указать путь, относительно текущей папки.

Домашня директорию `/home/<текущий пользователь>/` сокращается до `~/` . Допустим, ты сейчас залогинен под пользователем `Ilya` . Тогда, для тебя `~/` будет равносилен `/home/Ilya/`

Символ `.` - указывает на текущую директорию
Например, мы находимся в папке `foo/bar` . для нас папка `.` будет `foo/bar/`

Символ `..` - указывает на директорию, находящуюся на уровень выше.
Например, мы находимся в папке `foo/bar` . Для нас папка `..` будет `foo`. 

:book: Подробней про пути смотри по этой [ссылке](https://losst.ru/put-k-fajlu-v-linux)

<hr>

### :runner: Навигация по файловой системе

Для перехода по папкам используется команда `cd` (change directory - смени директорию).
Примеры использования:

 - Перейти в корневой раздел: `cd /`
 - Перейти в домашнюю директорию: `cd ~/` или `cd /home/<имя текущего
   пользователя>/`
 - Перейти в директорию `foo/bar`: `cd foo/bar`
 - Перейти в директорию `foo/`, находясь в директорию `foo/bar/`: `cd ..`
 - Перейти в директорию `foo/baz/`, находясь в директорию `foo/bar/`: `cd ../baz`

:book: Подробней по команде `cd` смотри по этой [ссылке](https://www.google.ru/search?client=ubuntu&channel=fs&q=linux+cd&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=PEVYWLCKB4KG7gS4xrHoAQ)

<hr>

### :open_file_folder: Просмотр содержимого директорий

Для просмотра содержимого директорий служит команда `ls` (От английского list - список)
Примеры использования:

 - Просмотр содержимого текущей директории: `ls`
 - Просмотр содержимого директории `/var/log/`: `ls /var/log`
 - Просмотр содержимого директори `foo/baz/`, находясь в директории `foo/bar/`: `ls ../baz/`

:book: Подробней по команде `ls` смотри по этой [ссылке](https://www.google.ru/search?client=ubuntu&channel=fs&q=linux+ls&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=3ERYWPvaHoKG7gS4xrHoAQ)

<hr>

### :pencil2: Создание файлов в консоли

Один из способов создания файлов в консоли - использование команды `touch` (прикосновение с английского)
Пример:
* `touch my_file.txt` - создаст в текущей папке пустой файл с названием `my_file.txt`
* `touch foo/another_file.txt` - создаст в папке `./foo` файл `another_file.txt`

:book: Подробней по команде `touch` смотри по этой [ссылке](https://www.google.ru/search?client=ubuntu&channel=fs&q=linux+touch&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=pkRYWLkpgobuBLjGsegB)

<hr>

### :file_folder: Создание директорий

Для создания директорий используется команда `mkdir` (make dir - сделай директорию)
Примеры:

- создать папку `foo/`: `mkdir foo`
- мы находимся в папке `foo/bar/`, создать папку `foo/baz`: `mkdir ../baz`

Если необходимо создать последовательность директорий, стоит использовать команду `mkdir` с ключем `-p`:
- мы находимся в папке в папке `foo/`, нам нужно создать директорию `foo/bar/baz/`. Используя команду без ключа -p нам пришлось бы выполнить две команды:

1. `mkdir bar/` - создаём директорию `bar/`
2. `mkdir bar/baz/` создаём директорию `baz/` в директории `bar/baz`

Используя ключ `-p` достаточно выполнить одну:
`mkdir -p bar/baz`

:book: Подробней по команде `mkdir` смотри по этой [ссылке](https://www.google.ru/search?client=ubuntu&channel=fs&q=nook+djvu&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=FV1ZWOLmJKW8zAWD3ZmYBw#newwindow=1&safe=off&channel=fs&q=linux+mkdir)

<hr>

### :balloon: Команда Echo

Выводит в консоль (на самом деле в stdout, что это такое - читай ниже) переданный ей текст.
`echo hello` выведет в консоль `hello`

Важно помнить, что есть мы хотим вывести больше одного слова, стоит использовать ковычки:
`echo "hello world\!"` выведет в консоль `hello world\!`

(\ перед восклицательным знаком - так называемое экранирование)

:book: Более полные примеры смотри по этой [ссылке](https://www.google.ru/search?client=ubuntu&channel=fs&q=linux%20echo&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=6j9YWOrzJpLHZLOMuaAE)

<hr>

### :barber: Стандартные потоки

> :memo: В средах UNIX/Linux существует такое понятие, как стандартные потоки

У каждой программы существует 3 потока данных:

 - `stdin`
 - `stdout`
 - `stderr`
 
 :book: Информацию о них можешь найти по этой [ссылке](https://habrahabr.ru/post/55136/)

<hr>

### :pencil2: Создание файлов (и наполнение их текстом) (Часть 2)

Теперь, прочев про потоки данных мы можем сделать следующее: перенаправить поток `stdout` команды `echo` в новый файл:
`echo "hello" > new_file.txt`

Открыв файл, мы увидим текст `hello`
Чтобы добавить к тексту `word`, выполним команду `echo "word" >> new_file.txt`. После выполнения этой команды содержимое файла станет 
```
hello
world
```
