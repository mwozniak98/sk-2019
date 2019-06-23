Zadanie 1
---------

![zadanie 1](zadanie-1.svg)

1. Zaprojektuj oraz przygotuj prototyp rozwiązania z wykorzystaniem oprogramowania ``VirtualBox`` lub podobnego. 
Zaproponuj rozwiązanie spełniające poniższe wymagania:
   * Usługodawca zapewnia domunikację z siecią internet poprzez interfejs ``eth0`` ``PC0``
   * Zapewnij komunikację z siecią internet na poziomie ``LAN1`` oraz ``LAN2``
   * Dokonaj takiego podziału sieci o adresie ``172.22.128.0/17`` aby w ``LAN1`` można było zaadresować ``500`` adresów natomiast w LAN2 ``5000`` adresów    
   * Przygotuj dokumentację powyższej architektury w formie graficznej w programie ``DIA``
   Rozwiązanie zadania:
 -------------------------------------------
 
 Konfiguracja komputera PC0
 --------------------------------
![PC0](pc0.png)


Dodatkowe polecenia użyte przy konfiguracji:

- ip addr add 172.22.254.1/23 dev enp0s8
- ip addr add 172.22.128.10/19 dev enp0s9
- ip link set enp0s3 up
- ip link set enp0s8 up
- ip link set enp0s9 up
- cat /proc/sys/net/ipv4/ip_forward
- echo 1 > /proc/sys/net/ipv4/ip_forward
- iptables --table nat --append POSTROUTING --out-interface 10.0.2.15 -j MASQUERADE
- iptables --append FORWARD --in-interface 172.22.254.1 -j ACCEPT

 Konfiguracja komputera PC1
 --------------------------------
  Polecenia użyte przy konfiguracji:
- ip addr add 172.22.254.10/23 dev enp0s3
- ip route add default 172.22.128.10

 Konfiguracja komputera PC2
 ---------------------------------
Polecenia użyte przy konfiguracji:
- ip addr add 172.22.254.200/19 dev enp0s3
- ip route add default 172.22.128.1



Rezultat końcowy potwierdzający poprawność konfiguracji
------------------------------------
![ZADA](zada.png)


Diagram w programie Dia
--------------
![DIAGRAM](exam_res.svg)
 
