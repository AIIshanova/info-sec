---
# Front matter
lang: ru-RU
title: "Лабораторная работа №3"
subtitle: "Дискреционное разграничение прав в Linux. Два пользователя."
author: "Ишанова А.И. группа НФИ-02-19"

# Formatting
toc-title: "Содержание"

# Pdf output format
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: false # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей.

# Теоретическое введение

Дискреционное разграничение доступа — управление доступом субъектов к объектам на основе списков управления доступом или матрицы доступа. Также используются названия дискреционное управление доступом, контролируемое управление доступом и разграничительное управление доступом. [2]

# Выполнение лабораторной работы

1. Пропускаем шаги с учетной записью guest и берем пользователя со второй лабораторной работы.
2. Создаем пользователя guest2. (@fig:001)

![Создание новой учетнойй записи и добавление в группу](1.png){ #fig:001 width=70%}

3. Осущиствляем вход в записи на разных консолях. Для обоих пользователей командой pwd определили директории, в которой они находятся. (@fig:002, @fig:003)

![Определение директории, в которой находится guest](2.png){ #fig:002 width=70%}

![Определение директории, в которой находится guest2](3.png){ #fig:003 width=70%}

4. Получаем информацию о пользователях через консоль. (@fig:004, @fig:005)

![Информация о пользователе guest](4.png){ #fig:004 width=70%}

![Информация о пользователе guest2](5.png){ #fig:005 width=70%}

5. Получаем информацию из файла /etc/group. (@fig:006)

![Информация о группах, в которых состоят guest и guest2](6.png){ #fig:006 width=70%}

6. От имени пользователя guest2 регистреум пользователя guest2 в группе guest. (@fig:007)

![Регистрация guest2 в группу guest](7.png){ #fig:007 width=70%}

7. От имени пользователя guest изменяем права директории /home/guest, разрешив все действия для пользователей группы. (@fig:008)

![Изменение прав директории /home/guest](8.png){ #fig:008 width=70%}

8. Заполняем таблицу "Установленные права и разрешённые действия для групп".

|Права директории|Права файла|Создание файла|Удаление файла|Запись в файл|Чтение файла|Смена директории|Просмотр файлов в директории|Переименование файла|Смена атрибутов файла|
|:-------: |:------:| :------:| :------:| :------:| :------:| :------:| :------:| :------:| :------:|
| d(000) | 000 | - | - | - | - | - | - | - | - |
| d(000) | 010 | - | - | - | - | - | - | - | - |
| d(000) | 020 | - | - | - | - | - | - | - | - |
| d(000) | 030 | - | - | - | - | - | - | - | - |
| d(000) | 040 | - | - | - | - | - | - | - | - |
| d(000) | 050 | - | - | - | - | - | - | - | - |
| d(000) | 060 | - | - | - | - | - | - | - | - |
| d(000) | 070 | - | - | - | - | - | - | - | - |
| d(010) | 000 | - | - | - | - | + | - | - | - |
| d(010) | 010 | - | - | - | - | + | - | - | - |
| d(010) | 020 | - | - | - | - | + | - | - | - |
| d(010) | 030 | - | - | - | - | + | - | - | - |
| d(010) | 040 | - | - | - | - | + | - | - | - |
| d(010) | 050 | - | - | - | - | + | - | - | - |
| d(010) | 060 | - | - | - | - | + | - | - | - |
| d(010) | 070 | - | - | - | - | + | - | - | - |
| d(020) | 000 | - | - | - | - | - | - | - | - |
| d(020) | 010 | - | - | - | - | - | - | - | - |
| d(020) | 020 | - | - | - | - | - | - | - | - |
| d(020) | 030 | - | - | - | - | - | - | - | - |
| d(020) | 040 | - | - | - | - | - | - | - | - |
| d(020) | 050 | - | - | - | - | - | - | - | - |
| d(020) | 060 | - | - | - | - | - | - | - | - |
| d(020) | 070 | - | - | - | - | - | - | - | - |
| d(030) | 000 | + | + | - | - | + | - | + | + |
| d(030) | 010 | + | + | - | - | + | - | + | + |
| d(030) | 020 | + | + | + | - | + | - | + | + |
| d(030) | 030 | + | + | + | - | + | - | + | + |
| d(030) | 040 | + | + | - | + | + | - | + | + |
| d(030) | 050 | + | + | - | + | + | - | + | + |
| d(030) | 060 | + | + | + | + | + | - | + | + |
| d(030) | 070 | + | + | + | + | + | - | + | + |
| d(040) | 000 | - | - | - | - | - | - | - | - |
| d(040) | 010 | - | - | - | - | - | - | - | - |
| d(040) | 020 | - | - | - | - | - | - | - | - |
| d(040) | 030 | - | - | - | - | - | - | - | - |
| d(040) | 040 | - | - | - | - | - | - | - | - |
| d(040) | 050 | - | - | - | - | - | - | - | - |
| d(040) | 060 | - | - | - | - | - | - | - | - |
| d(040) | 070 | - | - | - | - | - | - | - | - |
| d(050) | 000 | - | - | - | - | + | + | - | - |
| d(050) | 010 | - | - | - | - | + | + | - | - |
| d(050) | 020 | - | - | - | - | + | + | - | - |
| d(050) | 030 | - | - | - | - | + | + | - | - |
| d(050) | 040 | - | - | - | - | + | + | - | - |
| d(050) | 050 | - | - | - | - | + | + | - | - |
| d(050) | 060 | - | - | - | - | + | + | - | - |
| d(050) | 070 | - | - | - | - | + | + | - | - |
| d(060) | 000 | - | - | - | - | - | - | - | - |
| d(060) | 010 | - | - | - | - | - | - | - | - |
| d(060) | 020 | - | - | - | - | - | - | - | - |
| d(060) | 030 | - | - | - | - | - | - | - | - |
| d(060) | 040 | - | - | - | - | - | - | - | - |
| d(060) | 050 | - | - | - | - | - | - | - | - |
| d(060) | 060 | - | - | - | - | - | - | - | - |
| d(060) | 070 | - | - | - | - | - | - | - | - |
| d(070) | 000 | + | + | - | - | + | + | + | + |
| d(070) | 010 | + | + | - | - | + | + | + | + |
| d(070) | 020 | + | + | + | - | + | + | + | + |
| d(070) | 030 | + | + | + | - | + | + | + | + |
| d(070) | 040 | + | + | - | + | + | + | + | + |
| d(070) | 050 | + | + | - | + | + | + | + | + |
| d(070) | 060 | + | + | + | + | + | + | + | + |
| d(070) | 070 | + | + | + | + | + | + | + | + |

9. Заполняем таблицу "Минимальные права для совершения операций от имени пользователей
входящих в группу".

| Операция | Минимальные права на директорию| Минимальные права на файл |
|:---------------:|:---------------:|:---------------:|
| Создание файла | 030 | 000 |
| Удаление файла | 030 | 000 |
| Чтение файла | 030 | 040 |
| Запись в файл | 030 | 020 |
| Переименование файла | 030 | 000 |
| Создание поддиректории | 030 | 000 |
| Удаление поддиректории | 030 | 000 |

# Вывод

В ходе выполнения лабораторной работы был создан новый пользователь, были заполнены таблицы “Установленные права и разрешённые действия для групп” и "Минимальные права для совершения операций от имени пользователей
входящих в группу” и получены навыки разграничения доступа в ОС Linux.

# Библиография

1. Методические материалы курса.
2. Wikipedia: Избирательное управление доступом. (URL: https://ru.wikipedia.org/wiki/%D0%98%D0%B7%D0%B1%D0%B8%D1%80%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE%D0%B5_%D1%83%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5_%D0%B4%D0%BE%D1%81%D1%82%D1%83%D0%BF%D0%BE%D0%BC)
