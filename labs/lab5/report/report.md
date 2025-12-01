---
## Front matter
title: Лабораторная работа
subtitle: Номер 5
author: "Кобзев Д. К."

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: /home/dkkobzev/pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: Liberation Serif
romanfont: Liberation Serif
sansfont: Liberation Sans
monofont: Liberation Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9

## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью данной работы является построение простейших моделей сети на базе коммутатора и маршрутизаторов FRR и VyOS в GNS3, анализ трафика посредством Wireshark.

# Выполнение лабораторной работы

Запускаем GNS3 VM и GNS3. Создаем новый проект.
 
В рабочей области GNS3 размещаем коммутатор Ethernet и два VPCS.

Изменяем название устройства, включив в имя устройства имя моей учётной записи.

Соединяем VPCS с коммутатором (Рис. 12.1).

![Топология простейшей сети в GNS3](image/1.png){height=60%}

Задаем IP-адреса 192.168.1.11 в сети 192.168.1.0/24. Сохраняем конфигурацию. Аналогичным образом задаем IP-адрес 192.168.1.12 для PC-2.

Проверяем работоспособность соединения между PC-1 и PC-2 с помощью
команды ping (Рис. 12.2).

![Задание IP-адреса и сохранение конфигурации VPCS в GNS3](image/2.png){height=60%}

![Задание IP-адреса и сохранение конфигурации VPCS в GNS3](image/3.png){height=60%}

Запускаем на соединении между PC-1 и коммутатором анализатор трафика. В проекте GNS3 стартуем все узлы.

В терминале PC-2 делаем по одному эхо-запросу в ICMP-моде, в UDP-моде и TCP-моде к узлу PC-1 (Рис. 12.4).

![Эхо-запросы к узлу PC-1](image/4.jpg){height=60%}

Смотрим полученную информацию в Wireshark (Рис. 12.5), (Рис. 12.6).

![Полученная в Wireshark информация](image/5.png){height=60%}

![Полученная в Wireshark информация](image/6.png){height=60%}

Создаем новый проект. В рабочей области GNS3 размещаем VPCS, коммутатор Ethernet и маршрутизатор FRR. Изменяем отображаемые названия устройств. Включаем захват трафика на соединении между коммутатором и маршрутизатором. Запускаем все устройства проекта. Открываем консоль всех устройств проекта (Рис. 12.7).

![Топология простейшей сети с маршрутизатором в GNS3](image/7.png){height=60%}

Настраиваем IP-адресацию для интерфейса узла PC1 (Рис. 12.8).

![Настройка IP-адресации для интерфейса узла PC1](image/8.png){height=60%}

Настраиваем IP-адресацию для интерфейса локальной сети маршрутизатора.

Проверяем конфигурацию маршрутизатора и настройки IP-адресации (Рис. 12.9).

![Настройка IP-адресации](image/9.png){height=60%}

Проверяем подключение. Узел PC1 успешно отправляет эхо-запросы на адрес маршрутизатора 192.168.1.1 (Рис. 12.10).

![Проверка подключения](image/10.png){height=60%}

В окне Wireshark анализируем полученную информацию (Рис. 12.11), (Рис. 12.12).

![Полученная информация в Wireshark](image/11.png){height=60%}

![Полученная информация в Wireshark](image/12.png){height=60%}

Создаем новый проект. В рабочей области GNS3 размещаем VPCS, коммутатор Ethernet и маршрутизатор VyOS. Изменяем отображаемые названия устройств. Включаем захват трафика на соединении между коммутатором и маршрутизатором. Запускаем все устройства проекта (Рис. 12.13).

![Топология простейшей сети с маршрутизатором в GNS3](image/13.png){height=60%}

Настраиваем IP-адресацию для интерфейса узла PC1 (Рис. 12.10).

![Настройка IP-адресации](image/14.png){height=60%}

Настройте маршрутизатор VyOS. Переходим в режим конфигурирования. Изменяем имя устройства. Задаем IP-адрес на интерфейсе eth0. Смотрим внесённые в конфигурацию изменения. Применяем изменения в конфигурации и сохраняем саму конфигурацию. Смотрим информацию об интерфейсах маршрутизатора. Выходим из режима конфигурирования (Рис. 12.15).

![Настройка маршрутизатора VyOS](image/15.png){height=60%}

Проверяем подключение. Узел PC1 успешно отправляет эхо-запросы на адрес маршрутизатора 192.168.1.1 (Рис. 12.16).

![Проверка подключения](image/16.png){height=60%}

В окне Wireshark анализируем полученную информацию (Рис. 12.17), (Рис. 12.18).

![Полученная информация в Wireshark](image/17.png){height=60%}

![Полученная информация в Wireshark](image/18.png){height=60%}

# Выводы

В результате выполнения лабораторной работы мною были построены простейшие модели сети на базе коммутатора и маршрутизаторов FRR и VyOS в GNS3, анализ трафика посредством Wireshark.

# Список литературы{.unnumbered}
