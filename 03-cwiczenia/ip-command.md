## Zarządzanie interfejsami z wykorzystamiem programu IP

* stan interfejsu
    * interfejs up
    * interfejs down
* adresacja
    * dodaj adres
    * zmień adres
    * usuń adres
    * wyczyść adresy
* routing
    * pobierz trasę dla adresu
    
* adresacja fizyczna
    * pokaż adresy interfejsów dostępnych w sieci
    * pokaż adresy dla konkretnego interfejsu
     


### ip 

| subcommand    |  polecenie   | opis  |
| ------------- |:-------------| :---------------| 
|   ``addr``    |                               | informacje o adresacji i własnościach interfejsów |
|               |   ``ip addr``                 | informacja o wszystkich interfejsach |
|               |   ``ip addr show dev enp0s3`` | informacja o konkretnym interfejsie |
|   ``link``    |                               | zarządza i wyświetla stan wszystkich interfejsów sieciowych |
|               |   ``ip link``                 | informacja o wszystkich interfejsach |
|               |   ``ip link show dev em1``    | informacja o konkretnym interfejsie |
|               |   ``ip -s link``              | wyświetla statystyki interfejsu |
|   ``route``   |  | wyświetla i zmienia tablice routingu |
|               |   ``ip route``                | zarządzanie tablicą routingu wewnątrz jądra |
|   ``maddr``   |  | zarządza i wyświetla adresy IP multicast |
|               |   ``ip maddr``                | wyświetla informacje o multicascie dla wszystkich urządzeń |
|               |   ``ip maddr show dev em1``   | wyświetla informacje o multicascie dla konkrentego urządzenia |
|   ``neigh``   |  | pokazuje tablice ARP dla IPv4 |
|               |   ``ip neigh``                | wyświetla tablice sąsiedztwa |
|               |   ``ip neigh show dev em1``   | pokazuje pamięć podręczną ARP dla konkretnego urządzenia |
|   ``help``    |  | wyświetla listę komend i argumentów dla każdej subkomendy |
|               |   ``ip help``                 | wyświetla komendy i arguemnty subkomendy ip |
|               |   ``ip addr help``            | wyświetla komendy i arguemnty subkomendy addr |
|               |   ``ip link help``            | wyświetla komendy i arguemnty subkomendy link |
|               |   ``ip neigh help``           | wyświetla komendy i arguemnty subkomendy neigh |


### Zadanie

![zadanie 3](sieci-3.0.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem, 
   * Przetestuj połączenie poleceniem ping
   * Przetestuj połączenie z internetem
   * Sprawdź trasę dla połączeń z adresem IP z poza Twojej sieci lokalnej np. 1.1.1.1

1.1
   * Zmodyfikuj połączenia sieciowe zgodnie z poniższym schematem
   * Ponownie sprawdź trasę dla adresu z poza Twojej sieci lokalnej
  
![zadanie 3](sieci-3.1.png)

2.
   * Zainstaluj na komputerze ``PC0`` serwer ``HTTP`` np. ``nginx`` 
   * skonfiguruj program ``nginx`` tak aby wyświetlał zawartość katalogu ``/var/www``
   * przeładuj konfigurację
   * utwórz własny plik ``index.html`` zawierający tekst
   * Przetestuj komunikację z ``localhost``  wykorzystując konsolowego klienta ``HTTP``, program ``curl``
3.
   * Sprawdź który port został zarezerwowany dla komunikacji przez progrmam ``nginx``
   * np. program ``netstat``

4.
   * Przetestuj komunikację z serwerem HTTP z poziomu komputera ``PC2``
   * czy jest dostepne polecenie curl?
   * np. ``curl {adres_ip_pc_2}``
   * Wykonaj test dla połączenia na innym porcie niż ``80``, np ``curl {adres_ip_pc_2}:8080``
   * czy odpowiedź jest analogiczna jak dla testu z zadania ``2``?

5.
   * Rozbuduj sieć o kolejny komputer ``PC3`` zgodnie z diagramem
   
![zadanie 3](sieci-3.2.png)

6. 
   * Na komputerze ``PC3`` utwórzy plik index.html w katalogu ``/var/www``
   * Na komputerze ``PC3`` uruchom serwer protokołu ``HTTP`` tym razem wykorzystujac python
   * ``python3 -m http.server --directory /var/www --bind 127.0.0.1``
   * Przenieś wykonanie programu do tła ``ctrl + z`` ``bg``
   * Sprawdź połączenie wykorzystując ``curl localhost:port``
   * Sprawdź połączenie wykorzystując ``curl adres_ip:port``
   * Sprawdź zarezerwowane porty korzystając z polecenia ``netstat``
   
7. 
    * Na komputerze ``PC3`` zmodyfikuj sposób uruchamiania serwera http w taki sposób aby możliwe było wyświetlenie strony z komputerów ``PC1`` oraz ``PC2`` 
    * Przeprowadź test takiej komunikacji

8.
   * Na komputerze ``PC0`` zainstaluj i uruchom w tle program ``chat-server`` z cwiczeń 2
   * Sprawdź zarezerwowane porty korzystając z polecenia ``netstat``
   * Na komputerach ``PC1`` oraz ``PC2`` zainstaluj program ``chat-client``
   * Połącz się z serwerem dostępnym pod adresem IP ``PC0``
