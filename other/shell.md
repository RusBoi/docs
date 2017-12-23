`cut`
```bash
cut -d <delimeter> -f <field/byte num> <filename|->
```
* `-b` : вместо полей используй байты
* `-s` : не выводи строки, где не было разделителей

___
`paste`
```bash
paste <filename1> <filename2>
```
* `-d <delimeter>` : использовать другой разделитель (не '\t') 
___
`join`
```bash
join <filename1> <filename2|->
```
* `-i` : ignore case
* `-j` <num of field> : use this field for both files
* `-1` <num of field> : use this field for first files
* `-2` <num of field> : use this field for second files
___
`tail`
```bash
tail <filename>
```
* `-n <line_count>` : only last `n` lines
___
`head`
```bash
head <filename>
```
* `-c <line_count>` : onl first `n` lines
___
`tr`
```bash
tr <charset1> <charset2>
```
Заменяет символы из `charset1` на соответствующие символы из `charset2`. Читают и выводят с `STDIN`/`STDOUT`

* `-d` : не заменяй, а только удали символы из `charset1`
```bash
tr "[:lower:]" "[:upper:]" < name.txt
```
___

`uniq`
```bash
uniq <filename>
```
Удаляет соседние повторяющиеся строки

* `-u` : отобразить только строки, которые в исходном файле не повторялись
* `-d`, `--repeated` : отобразить только строки, которые в исходном файле повторялись
___

`sort`
```bash
sort <filename>
```
Сортируем строки файла в порядке алфавита
___

`strings`
```bash
strings <filename>
```
Выводят только печатаемые строки файла
___

`find`
```bash
find <path> <expression>
```
        
* `-name <filename>` : `True` если имена файлов совпадают
* `-wholename <filename>` :  `True` если путь+имя файлов совпадают
* `--regex <regex>` : 
* `-exec <command>` : всегда `True`; исполняет команду (`{}` - filename, after command - `\;`) 
* `-print` : всегда `True`; печатает полное имя файла
* `-[a|c|m][time|min] n` : `True` если файл был `[accessed|changeg|modified]` `n` `[дней|минут]` назад
* `-ls` : всегда `True`; печатает файл в формате `ls -l`
* `-type <file_type>` : `True` если тип файла совпадает с заданным 
* `-perm <perm_code>` : `True` если права доступа к файлу совпадает с заданными 
* `-size <size>с?` : `True` если размер совпадает с заданным (в 512 байтный блоках или байтах)
* `-follow` : всегда `True`; `find` переходит по ссылкам 
* `-depth` : всегда `True`; обход в глубину
* `-maxdepth`
* `-mindepth`
* `-prune` : всегда `True`; обрывает цепочку 

`-a, -o, !, ()` - `and`, `or`, `not`, группировка соответственно
___

`grep`
```bash
grep <pattern> <filename|->
```
* `-o` : выводить только совпавшую подстроку
* `-c` : вывести количество вхождений 
* `-r` : искать строку во всех файлах в указанной папке
* `-h` : при использовании ключа -r не будут выводится имена файлов
* `-i` : ignore case
* `-n` : выводит номер строки, в которой содержится искомая подстрока
* `-l` : вывести имена файлов, которые содержат искомую строку (имеет смысл, только вместе с ключом `-r` или при спользовании wildcard'ов)
* `-L` : высести имена файлов, которые не содержат искомую строку (имеет смысл, только вместе с ключом `-r` или при спользовании wildcard'ов) 
* `-m <count>` : вывести только первые `count` вхождений
* `-v` : выдает строки, не содержащих подстроку
* `-w` : искать подстроку только как отдельное слово
* `-A <n>` : вывести `n` строк перед вхождением
* `-B <n>` : вывести `n` строк после вхождения
* `-C <n>` : вывести n строк вокруг вхождения
* `-P` : perl style regex

___

`zip`
```bash
zip [options] <archive_filename|-> <filename|->
```

* `-r` : рекурсивно добавить файлы из указанной директории
* `-d <filename>` : удалить файл из архива
* `-x <filename>` : не добавлять файлы, удовлетворяющие данному фильтру, в архив
* `-1` : быстрый режим
* `-9` : лучшее зжатие
* `-u <filename>` : обновить указанные файлы в архиве
* `-f <filename>` : обновить указанный файл, только если он был изменен


`unzip`
```bash
unzip <archive_filename> [<filename_to_extract>] : разархивировать архив
```
* `-d <path>` : извлечь в другую папку
___
`tar`
```bash
tar <command> -f <tar_filename> [files]
```
Комманды: 

* `-r`, `--append` : добавить файлы к архиву
* `-t`, `--list` : показать содержимое .tar
* `-c`, `--create` : создать .tar
* `-u`, `--update` : добавить файлы, если их еще нет
* `-x`, `--extract` : распокавать .tar
* `--delete` : удалить файлы из .tar

Опции

* `-f <tar_filename>` : указатель на файл .tar
* `-C <path>` : поменять путь
* `-v` : verbose
* `-j`, `--bzip` : using bzip2
* `-z`, `--gzip` : using gzip
___
`gzip`
```bash
gzip <filenames>
```

gzip file (can't gzip whole folders, only single files). File will be overwritten `<filename>.gz`

* `-r` : recursive zipping of each file in directory (not whole directory) 
* `-c` : .gz file go to `STDOUT`, not file system
* `-d` : decompress (`gunzip`)
* `-v` : verbose
___

`dd`
```bash
dd if=<input_file> of=<output_file>
```
* `bs=<block_size>` : количество байт в одном блоке
* `status=progress` : показывать статус
* `count=<n>` : количество блоков для копирования
```bash
dd if=/dev/sda2 of=hdd.img bs=128K
```
___
AWK, SED, DU, WC, DIFF, DF






