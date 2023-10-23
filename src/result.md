# Операционные системы UNIX/Linux (Базовый).
## Part 1. Установить **Ubuntu 20.04 Server LTS** без графического интерфейса. (Используем программу для виртуализации - VirtualBox)

- Версия UBANTU, cat /etc/issue 


![task](///materials/task1.png)

## Part 2. Создать пользователя, отличного от пользователя, который создавался при установке. Пользователь должен быть добавлен в группу `adm`.

- Создание нового пользователя sudo useradd -G adm user1 

![res](../materials/task 2.png)

- Просмотр нового пользователя cat /etc/passwd 

![res](../materials/task 2.1.png)

## Part 3. Настройка сети ОС

- Задать название машины user-1, с помощью sudo hostname user-1

![res](../materials/task 3.1.1.png)

![res](../materials/task 3.1.2.png)

- Установка временной зоны, соответствующей моему местоположению ls /usr/share/zoneinfo
export TZ=Europe/Moscow

![res](../materials/task 3.1.3.png)

- вывести названия сетевых интерфейсов с помощью консольной команды.

![task3](../materials/task 3.png)

Интерфейс lo является локальной петлёй, имеющей IP-адрес 127.0.0.1. Она предназначена для обеспечения сетевого доступа к компьютеру.

- Получить ip адрес устройства от DHCP сервера: sudo dhclient -v

![task 3.1](../materials/task 3.1.png)

DHCP (англ. Dynamic Host Configuration Protocol — протокол динамической настройки узла) — это протокол клиента или сервера, который автоматически предоставляет узел протокола IP с его IP-адресом и другие связанные сведения о конфигурации, такие как маска подсети и шлюз по умолчанию.

- Определить и вывести на экран внешний ip-адрес шлюза (ip) curl ifconfig.me/ip и внутренний IP-адрес шлюза ip route

![out_in](../materials/task 3.2.png)

- задать статичные настройки ip, gw, dns. с помощью команды sudo vim /etc/netplan/00-installer-config.yaml

![ip](../materials/task 3.3.png)

- пропинговала хосты

![task3.3.1](../materials/task 3.3.1.png)

## Part 4 Обновление ОС

- Обновить системные пакеты до последней на момент выполнения задания версии

![update](../materials/task 4.png)

## Part 5. Использование команды **sudo**

- позволяет выполнять привилегированные команды обычным пользователям без необходимости ввода пароля суперпользователя root

- Чтоб дать возможность изменять имя хоста через другого пользователя, надо sudo usermode -a -G sudo user2 . Для переключения на второго пользователя : su user2. для переименования хоста. sudo hostname use

![task5](../materials/task 5.png)

## Part 6. Установка и настройка службы времени

- вывод информации о времени на компьютере

![task6](../materials/task 6.png)

## Part 7. Установка и использование текстовых редакторов 

- редактор **vim**. для сохранения нажать (esc :qw), для выхода без сохранения(esc :q!), поиск и замена :%s/что заменить/на что заменить/g

![vim](../materials/task 7 - vim.1.png) 
![vim](../materials/task 7 - vim.2.png)
![vim](../materials/task 7 - vim.3.png)

- редактор **nano**. для выхода с сохранением изменений (cntrl + x - yes - entr)

![nano](../materials/task 7 - nano.1.png) 

- для выхода без сохранения изменений (cntrl + x - no - entr)

![nano](../materials/task 7 - nano.2.png) 

- alt+R -поиск замена

![nano](../materials/task 7 - nano.3.png) 


- редактор **mcedit**. для выхода с сохранением изменений (нажать на 2, выйти 10), найти и заменить нажать на f4

![mcedit](../materials/task 7 - mcedit.1.png) 
![mcedit](../materials/task 7 - mcedit.2.png) 
![mcedit](../materials/task 7 - mcedit.3.png) 


## Part 8. Установка и базовая настройка сервиса **SSHD**

- установка sudo apt-get install ssh

![task8](../materials/task 8.1.png)

- автостарт службы sudo systemctl enable ssh

![task8](../materials/task 8.2.png)

- результат перенастройки службы

![task8](../materials/task 8.3.png)

- ps -C sshd

команда ps позволяет просмотреть список всех текущих процессов. 
Флаг -С - выбирать процессы по имени команды

![task8](../materials/task 8.4.png)

- для перезагрузки использвала sudo shutdown -r now

- netstat (network statistics) — утилита командной строки, выводящая на дисплей состояние TCP-соединений. Опции –t показывают активные соединения TCP, флаг –a , также будут показаны сокеты, ожидающие соединения, -n показывает сетевые адреса как числа. netstat обычно показывает адреса как символы. Этот дисплей даст вам список всех серверов, которые в настоящее время работают в вашей системе.

![netstat](../materials/task 8.png)

Proto – протокол (tcp, udp). 

Recv-Q – количество байтов, помещённых в буфер приёма TCP/IP, но не переданных приложению.

Send-Q – количество байтов, помещённых в буфер отправки TCP/IP, но не отправленных, или отправленных, но не подтверждённых 

Local Address – локальный адрес сервера. 

Foreign Address – адрес второй стороны. В обычных соединения, это адрес с которого пришло соединение. 0.0.0.0:* – значит подключаться можно с любых адресов и с любых портов. 

State – состояние подключения, или прослушивания


## Part 9.  Установка и использование утилит **top**, **htop**(перепроверить)

- установка и запуск утилиты top и htop 
uptime - 00:44:06

![thop](../materials/task 9 thop.png)

- pid процесса занимающего больше всего памяти

![pid](../materials/task 9 pid.png)

- сортировка по PERCENT_CPU

![percent](../materials/task 9 percent_cpu.png)

- сортировка по PERCENT_MEM

![mem](../materials/task 9 percent_mem.png)

- сортировка по TIME

![time](../materials/task 9 time.png)

- фильтровка для процесса sshd

![sshd](../materials/task 9 sshd.png)

- с процессом syslog, найденным, используя поиск

![suslog](../materials/task 9 syslog.png)

## part 10. Использование утилиты **fdisk**

- запустить каманду fdisk -1 
Название жесткого диска sda. Размер - 8 gib. Кол-во сектаров - 13101056. Размер swap - 6.2

![task](../materials/task 10.png)

## Part 11. Использование утилиты **df**

- размер раздела - 10218772, размер занятого пространства - 4446040, размер свободного пространства - 5232060, процент использования - 46%
тип файловой системы - /dev/mapper/ubuntu--vg-ubuntu-lv

![task](../materials/task 11.png)

## Part 12. Использование утилиты **du**
- вызов du

  ![task](../materials/task 12.png)
  
- вывод размеров папок /home

![home](../materials/task 12_home.png)

- вывод размеров папок /var
  
![var](../materials/task 12_var.png)

- вывод размеров папок /var/log
  
![var_log](../materials/task 12_var_log.png)

- Вывести размер всего содержимого в /var/log (не общее, а каждого вложенного элемента, используя *)

![all](../materials/task 12_var_log_all.png)

## Part 13. Установка и использование утилиты **ncdu**

- установка ncdu : sudo apt install ncdu 

![linux](../materials/task 13 unstall ncdu.png)

- ncdu /home = 36/0 KiB

![linux](../materials/task 13_home.png)

- ncdu /var = 369.8 MiB

![linux](../materials/task 13_var.png)

- ncdu /var/log  = 16.0 MiB
  
![linux](../materials/task 13_var_log.png)

## Part 14. Работа с системными журналами

- less /var/log/dmesg

![task14](../materials/task 14 dmesg.png)

- less /var/log/syslog

![task14](../materials/task 14 syslog.png)

- less /var/log/auth.log

![task14](../materials/task 14 auth.log.png) 

- время последней успешной авторизации - 15:28:03 
имя пользователя - laubakh 
метод входа в систему - less

## Part 15. Использование планировщика заданий **CRON**
- Используя планировщик заданий, запустите команду uptime через каждые 2 минуты

![task15](../materials/task 15_cron.png) 

- строки о выполнение задачи через каждые 2 минуты

![task15](../materials/task 15.1.png) 

- удаление всех заданий с помощью crontab -r

![task15](../materials/task 15_del.png)
