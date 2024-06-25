# Домашнее задание к занятию "`Уязвимости и атаки на информационные системы`" - `Сайфиев Денис`
---

### Задание 1
скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/ .

Это типичная ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину с помощью nmap .

пытаемся найти уязвимости, в которых происходит эта виртуальная машина.

Сами уязвимости можно найти на сайте https://www.exploit-db.com/ .

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

Какие сетевые службы в ней разрешены?
Какие уязвимости обнаружены вами? (список со ссылками: достаточно трёх уязвимостей)
Примите ответ в свободной форме.

### Решение 1

#### 1. Разрешенные сетевые службы
```
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
53/tcp   open  domain      ISC BIND 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
111/tcp  open  rpcbind     2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login?
514/tcp  open  shell       Netkit rshd
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
5900/tcp open  vnc         VNC (protocol 3.3)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
```
 #### 2. Обнаруженные уязвимости

 https://www.exploit-db.com/exploits/17491
 https://www.exploit-db.com/exploits/15449
 https://www.exploit-db.com/exploits/16922

### Задание 2
Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.

### Решение 2

```
SELECT *
FROM payment
WHERE payment_date  BETWEEN '2005-06-15' and '2005-06-19'
AND amount > 10;
```
![Решение 2](https://github.com/DenioSa/SQL-1/blob/9177d277bc0c450eec274b9fc3e9af13ecb02aab/img/2.bmp)`

### Задание 3
Получите последние пять аренд фильмов.

### Решение 3

```
SELECT *  
FROM rental   
ORDER by rental_date DESC 
LIMIT 5;
```
![Решение 3](https://github.com/DenioSa/SQL-1/blob/9177d277bc0c450eec274b9fc3e9af13ecb02aab/img/3.bmp)`

### Задание 4
Одним запросом получите активных покупателей, имена которых Kelly или Willie.

Сформируйте вывод в результат таким образом:

все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
замените буквы 'll' в именах на 'pp'.

### Решение 4

```
SELECT LOWER(REPLACE(first_name, 'LL', 'pp')) 
FROM customer
WHERE first_name LIKE 'Willie' OR first_name  LIKE 'Kelly';
```
![Решение 4](https://github.com/DenioSa/SQL-1/blob/9177d277bc0c450eec274b9fc3e9af13ecb02aab/img/4.bmp)`


