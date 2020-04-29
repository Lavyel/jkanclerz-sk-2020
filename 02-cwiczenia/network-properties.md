## Ustawianie parametrów sieci

### Zadania

0. Z wykorzystaniem dowolnych systemów operacyjnych na których potrafisz uruchomić interpreter ``python`` oraz oprogramowania virtualbox odwzoruj poniższy schemat sieci:

![alt text][network]

[network]: ./network.png "Logo Title Text 2"

1. na 1 z komputerów zainstaluj i uruchom program ``server.py`` dostępne pod adresem ``https://github.com/jkanclerz/client-server-chat``
2. na 2 z komputerów zainstaluj i uruchom program ``client.py`` dostępne pod adresem ``https://github.com/jkanclerz/client-server-chat``
3. Manipulując konfiguracją sieci na poziomie virtualbox, uruchom serwer czatu, oraz udostępnij go na wybranym porcie oraz adresie tak aby istniała możliwość połączenia przez inne osoby w obrębie pracowni
4. Zainstaluj oprogramowanie serwera HTTP ``nginx`` lub innego, skonfiguruj plik index.html wg instrukcji, sprawdź dostępność strony z wykorzystaniem dowolnego klienta protokołu ``HTTP`` z różnych konfiguracji IP
5. Posługując się programami tj: ``netstat`` lub ``lsof`` sprawdź na jakich portach zostały uruchomione serwery czatu czy HTTP

Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 10.0.15.4 | ip addr add 10.0.15.4/24 dev eth0 |
| MASKA  | /24 (255.255.255.0) | |
|   |  | |
| PC 2  |  | |
| IP - address  | 10.0.15.6 | ip addr add 10.0.15.6/24 dev eth0 |
| MASKA  | /24 (255.255.255.0 )| |


### Weryfikacja połączenia

#### Polecenie

ping 10.0.15.4

ping 10.0.15.6

#### Efekt

Między koputerami wirtualnymi jest połączenie.



Statyczna konfiguracja parametrów połączenia
Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 192.168.10.10 | ip addr add 192.168.10.10/24 dev eth0 |
| MASKA  | 255.255.255.0 | |
|   |  | |
| PC 2  |  | |
| IP - address  | 192.168.10.11 | ip addr add 192.168.10.11/17 dev eth0 |
| MASKA  | 255.255.128.0 | |
| PC 2  |  | |
| IP - address  | 172.16.100.100 | ip addr add 172.16.100.100/16 dev eth0 |
| MASKA  | 255.255.0.0 | |

### Weryfikacja połączenia

#### Polecenia
ping 192.168.10.11

ping 192.168.10.

ping 172.16.100.100

#### Efekty
Próba połączenia się powiodła.

Próba połączenia się powiodła.

Próba połączenia się nie powiodła.


### Nowa statyczna konfiguracja 

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  |  | ip addr add 168.1.0.200/24 dev eth0 |
| MASKA  |  | |
|   |  | |
| PC 2  |  | |
| IP - address  |  | ip addr add 168.1.0.201/24 dev eth0 |
| MASKA  |  | |

Weryfikacja połączenia

Polecenie
ping 168.1.0.200
ping 168.1.0.201

Efekt
Próba połączenia się powiodła.
Próba połączenia się powiodła.

### Utrwalenie konfiguracji
Dlaczego? Jak? Co? :)

Konfiguracja jest utrwalana poprzez modyfikację pliku z konfiguracją sieci. Dzięki utrwaleniu, konfiguracja jest zachowana również po wyłączeniu maszyn.

### Warto wiedzieć

-------------------------
| Parametr | wartość |
| ------------- |:-------------:|
| Lokalizacja pliku z konfiguracją sieci| etc/network/interfaces |
| UP -> Wyłączenie interfejsu sieciowego| ip link set eth1 down |
| DOWN -> Włączenie interfejsu sieciowego| ip link set eth1 up |
| Sprawdzenie obecnych parametrów | vi etc/network/interfaces |
| lista wszystkich interfejsów | ip addr show |
| Które interfejsy jakie porty słuchają | netstat |

