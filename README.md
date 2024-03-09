# Домашнее задание к занятию "Уязвимости и атаки на информационные системы" - `Громов Андрей`

---

### Задание 1

---
Какие сетевые службы в ней разрешены?

    PORT     STATE SERVICE     VERSION
    21/tcp   open  ftp         vsftpd 2.3.4
    22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
    23/tcp   open  telnet      Linux telnetd
     5/tcp   open  smtp        Postfix smtpd
    53/tcp   open  domain      ISC BIND 9.4.2
    80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
    111/tcp  open  rpcbind     2 (RPC #100000)
    139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
    445/tcp  open  netbios-ssn Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)
    1099/tcp open  java-rmi    GNU Classpath grmiregistry
    1524/tcp open  bindshell   Metasploitable root shell
    2049/tcp open  nfs         2-4 (RPC #100003)
    2121/tcp open  ftp         ProFTPD 1.3.1
    3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
    5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
    5900/tcp open  vnc         VNC (protocol 3.3)
    6667/tcp open  irc         UnrealIRCd
    8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
    8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1

---

Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)

    1. vsftpd 2.3.4 - Backdoor Command Execution (Metasploit) 
    https://www.exploit-db.com/exploits/17491
    2. smbftpd 0.96 - SMBDirList-function Remote Format String 
    https://www.exploit-db.com/exploits/4478
    3. MySQL 5.0.x - IF Query Handling Remote Denial of Service
    https://www.exploit-db.com/exploits/30020

---

### Задание 2

---

Режимы сканирования SYN, FIN, Xmas и UDP являются различными способами сканирования портов в сети.

    SYN сканирование:
        В этом режиме сканирования клиент отправляет пакет с флагом SYN на порт сервера и ожидает ответа.
        Если порт открыт, сервер отправляет пакет с флагом SYN/ACK в ответ, что указывает на готовность соединения.
        Если порт закрыт, сервер отправляет пакет с флагом RST в ответ, что указывает на отклонение соединения.

    FIN (или Xmas) сканирование:
        В этом режиме сканирования клиент отправляет пакет с флагом FIN (или сочетанием флагов FIN, URG и PSH) на порт сервера.
        Если порт закрыт, сервер должен отправить пакет с флагом RST в ответ, что указывает на отклонение соединения.
        Кроме того, возможны различные реакции сервера, такие как отсутствие ответа или отправка пакета с флагом RST/ACK или RST/URG.

    UDP сканирование:
        UDP сканирование отличается от других режимов, так как UDP является протоколом без установления соединения.
        В этом режиме клиент отправляет UDP-пакет на порт сервера и ожидает ответа.
        Если порт открыт, сервер может ответить на запрос.
        Если порт закрыт, сервер может отправить пакет с сообщением об ошибке порта в ответ.

В результате сетевого сканирования разными режимами можно определить доступность портов на удаленном сервере и его конфигурацию без установления реального соединения. Каждый режим сканирования имеет свои особенности и может быть эффективным при определенных условиях.