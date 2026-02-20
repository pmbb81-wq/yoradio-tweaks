

Link do aplikacji do play store:

https://play.google.com/store/apps/details?id=com.arlosoft.macrodroid&hl=pl

Sterowanie yoradiem telefonem w nowym wymiarze. Tego nie zrobicie przez www ani inna metode. 

Opis robie na moim telefonie. Xiaomi 11T PRO. Na innych nie mam pojecia jak beda opcje. Musicie sami to obczaic.

Ok, zalozmy,ze macie juz zainstalowany Macrodroid. Musicie znac IP radyjka :)

Tworzymy pierwsze makro. 

#**VOL_UP**
------

Mamy trzy opcje.
- [x] Wyzwalacze
- [X] Akcje
- [x] Ograniczenia

W wyzwalaczu klikamy znaczek plusa +

Wybieramy Dzialanie uzytkownika

Wybieramy przycisk glosnosci

Wybieramy opcje Uzywac uslugi ulatwienia dostepu

Wybieramy Do gory

Wybieramy Zachowaj poprzednie ustawienia glosnosci


Tak to wyglada:
-fotka tutaj-

Teraz w Akcje klikamy znak plusa +

Wybieramy interakcje internetowe 

Wybieramy Zadanie HTTP 

W Metoda zadania ustawiamy POST 

W adresie URL dla ustawienia glosnosci piszemy tak: 

Moj przykladowy ip:
```python
Moj przykladowy ip http://192.168.8.103/?volp
```

Odznaczamy Sledz przekierowania.

Klikamy w gornym prawym rogu [v] ptaszka czyli zapisujemy.
Testujemy nasze makro :)

Dla volume down wybieramy volm

Lista komend z githuba:
## POST/GET
---
http://xxx.xxx.xxx.xxx/?command
---
start           : start 
> Dziala jako przycisk PLAY
>  Przyklad: http:192.168.8.103/?start 

stop            : stop
> Dziala jako przycisk STOP
>  Przyklad: http:192.168.8.103/?stop

toggle          : start/stop
> Dziala jako przycisk PLAY<->STOP. Mozna przypisac do jednego klawisza.
>  Przyklad: http:192.168.8.103/?toggle

prev            : previous station
> Poprzednia stacja
>  Przyklad: http:192.168.8.103/?prev 

next            : next station
> Nastepna stacja
>  Przyklad: http:192.168.8.103/?next

volm            : volume down one step
> Zciszenie o wartosc ustawiona na stronie www.
>  Przyklad: http:192.168.8.103/?volm

volp            : volume up one step
> Podglosnienie o wartosc ustawiona na stronie www
> Przyklad: http:192.168.8.103/?volp

vol=x           : set volume to x (0-254)
> Ustawienie glosnosci na wartosc od 0 do 254. Gdzie 254 to 100% glosnosci.

trebble=x&middle=x&bass=x : equalizer, x from -16 to 16 (three parameters together)
> Ustawienia equalizera od -16 do 16. Gdzie 0 to srodek. Chcemy wiecej basu? Ustawiamy np 16 :)
>  Przyklad: http:192.168.8.103/?trebble=0&middle=0&bass=16

ballance=x      : balance, x from -16 to 16
> Ustawienie balansu. Zero to srodek czyli dwa glosniki graja tak samo.
>  Przyklad: http:192.168.8.103/?ballance=16

playstation=x
> Odtwarza stacje x. Np 5 itp. Zalezy ile stacji mamy w playliscie.
> trebble=x&middle=x&bass=x
> Przyklad: http:192.168.8.103/?playstation=8

play=x          : start playback of station number x
> Odtwarza stacje x. Np 5 czy tam 10 :)
> Przyklad: http:192.168.8.103/?play=1 (pierwsza stacja z playlisty)

dspon=x         : display on/off, x=0 - off, x=1 - on
> Wlacza lub wylacza ekran naszego radyjka.
> Przyklad: http:192.168.8.103/?dspon=0 (Wylaczenie ekranu)

dim=x           : display brightness x=(0-100) (if supported)
> Ustawia jasnosc ekranu jezeli wykorzystujemy pin PWM i mamy go zdefiniowanego. Jezeli LCD to obsluguje.
> Przyklad: http:192.168.8.103/?dim=50 (Przyciemnie ekran lcd o 50%)

sleep=x&after=y : sleep for x minutes after y minutes
> Usypia nasze radyjko przez sleep=x po czasie after=y.
> Przyklad: http:192.168.8.103/?sleep=60&after=5

sleep=x         : sleep for x minutes right now
> Usypia nasze radyjko natychmiast
> > Przyklad: http:192.168.8.103/?sleep=60

reset           : reset settings to default
? Ustawia ustawienia domyslne naszego radyjka
> Przyklad: http:192.168.8.103/?reset
> 
---
>                          NIE UDUKOMENTOWANE KOMENDY Z PLIKU COMMANDHANDLER.CPP
---
## 🌐 WebSocket / UI
1. clearspiffs
- [ ] Nie testowane jeszcze :)

2. invertdisplay
- [x] Odwraca kolory - Bialo czarny lub Czarno Bialy.

Przyklad: ```http://192.168.8.102/?invertdisplay=1```

Przyklad: ```http://192.168.8.102/?invertdisplay=0```

3. numplaylist
- [x] Wlacza lub wylacza numerowanie stacji radiowych w playliscie na LCD. Thx dla lechuu-st za poprawienie :)

Przyklad: ```http://192.168.8.102/?numplaylist=1``` Wlacza numerki stacji.

Przyklad: ```http://192.168.8.102/?numplaylist=0``` Wylacza numerki stacji. Widoczne tylko na www.

4. flipscreen
- [x] Obraca ekran LCD 180 stopni.

Przyklad: ```http://192.168.8.102/?flipscreen=0```

Przyklad: ```http://192.168.8.102/?flipscreen=1```

5. brightness
- [x] Regulacja jasnosci ekranu. Info aka lechuuu-st: Dziala tylko na ekranach TFT, na oledach nie. LCD musi miec PIN BL i byc podlaczony i zdefiniowany w myoptions.h Zakres jasnosci odbywa sie od 0 do 255.

Przyklad: ```http://192.168.8.102/?brightness=127``` 50% jasnosci ekranu.

Przyklad: ```http://192.168.8.102/?brightness=0``` Ekran calkowicie sciemniony.

Przyklad: ```http://192.168.8.102/?brightness=255``` Ekran swieci na maxa 100%.

6. contrast
- [ ] Nie dziala na OLEDZIE. Nie wiem jak w wypadku TFT. Do przetestowania :)

Przyklad: ```http://192.168.8.102/?contrast=127``` 50% kontrastu.

Przyklad: ```http://192.168.8.102/?contrast=255``` 100%... 

7. volsteps
- [x] Zmienia zakres przeskakiwania glosnosci o dany zakres.Domyslnie jest 1.

Przyklad: ```http://192.168.8.102/?volsteps=5``` Skok glosnosci o 5 jednostek.

Przyklad: ```http://192.168.8.102/?volsteps=10``` Skok glosnosci o 10 jednostek.

8. irtlp
- [x] Tolerancja dla odbiornika IRDA.Domyslnie jest 35

Przyklad: ```http://192.168.8.102/?irtlp=50``` Tolerancja ustawiona na 50.

Przyklad: ```http://192.168.8.102/?irtlp=35``` Tolerancjaustawiona na 35.Domyslna.

9. showweather
- [x] Pokazuje badz ukrywa pasek z pogoda.

Przyklad: ```http://192.168.8.102/?showweather=0``` Wylacza pasek pogody.

Przyklad: ```http://192.168.8.102/?showweather=1``` Wlacza pasek pogody.

10. reboot lub boot
- [x] Restartuje nasze ESP :)

Przyklad: ```http://192.168.8.102/?reboot=1``` Resetuje nasz ESP.

Przyklad: ```http://192.168.8.102/?boot=1``` Resetuje nasz ESP.

11. format
- [ ] Formatuje nasze ESP :) Dla odwaznych xD Ja tego nie testuje xD

Przyklad: ```http://192.168.8.102/?format=1``` Formatuje nasz ESP.

12. reset
- [x] Resetuje nasze ESP :) Przywraca domyslne ustawienia na www. Usywa tez API key od pogody.

Przyklad: ```http://192.168.8.102/?reset=1``` Resetuje nasz ESP.

13. vumeter
- [x] Wlacza lub wylacza pasek audio VU Meter.

Przyklad: ```http://192.168.8.102/?vumeter=1``` Wlacza pasek VU.

Przyklad: ```http://192.168.8.102/?vumeter=0``` Wylacza pasek VU.

14. vumeter
- [x] Wlacza lub wylacza pasek audio VU Meter.

Przyklad: ```http://192.168.8.102/?vumeter=1``` Wlacza pasek VU.

Przyklad: ```http://192.168.8.102/?vumeter=0``` Wylacza pasek VU.









    # 📋 Komendy obsługiwane w `CommandHandler::exec` (yoRadio)
     
    ## 🎶 Odtwarzanie i sterowanie playerem
     
    | Komenda | Parametr | Opis |
    |----------|----------|------|
    | `start` | — | Uruchamia odtwarzanie ostatniej stacji |
    | `stop` | — | Zatrzymuje odtwarzanie |
    | `toggle` | — | Przełącza między play/stop |
    | `prev` | — | Przechodzi do poprzedniej stacji |
    | `next` | — | Przechodzi do następnej stacji |
    | `volm` | — | Zmniejsza głośność o krok |
    | `volp` | — | Zwiększa głośność o krok |
    | `play` / `playstation` | `<id>` | Odtwarza stację o numerze `<id>` |
    | `vol` | `<0–254>` | Ustawia głośność |
    | `submitplaylist` | — | Zatrzymuje player |
     
    ---
     
    ## ⚙️ Konfiguracja systemowa
     
    | Komenda | Parametr | Opis |
    |----------|----------|------|
    | `reset` | — | Resetuje konfigurację (lokalnie) |
    | `balance` | `<value>` | Ustawia balans audio |
    | `mode` | `<mode>` | Zmienia tryb (SD/STREAM) |
    | `clearspiffs` | — | Czyści SPIFFS i resetuje tryb |
    | `telnet` | `<0/1>` | Włącza/wyłącza Telnet |
    | `watchdog` | `<0/1>` | Konfiguruje watchdog |
    | `smartstart` | `<0/1/2>` | Ustawia tryb smartstart |
     
    ---
     
    ## 🌐 WebSocket / UI
     
    | Komenda | Opis |
    |----------|------|
    | `getindex` | Pobiera indeks stacji |
    | `getsystem` | Informacje systemowe |
    | `getscreen` | Snapshot UI |
    | `gettimezone` | Ustawienia strefy |
    | `getcontrols` | Stan kontrolek |
    | `getweather` | Dane pogodowe |
    | `getactive` | Lista aktywnych elementów |
    | `newmode` | Zmienia tryb i odświeża UI |
     
    ---
     
    ## 🖥️ Ekran / DSP
     
    | Komenda | Parametr | Opis |
    |----------|----------|------|
    | `dspon` | `0/1` | Włącza/wyłącza wyświetlacz |
    | `dim` | `<0–100>` | Ustawia jasność |
    | `invertdisplay` | `0/1` | Odwraca ekran |
    | `brightness` | `<value>` | Jasność DSP |
    | `screenon` | `<0/1>` | Włącza ekran |
    | `contrast` | `<value>` | Ustawia kontrast |
    | `screensaverenabled` | `0/1` | Włącza wygaszacz |
    | `screensavertimeout` | `<sec>` | Timeout wygaszacza |
    | `screensaverblank` | `<0/1>` | Czarny ekran w wygaszaczu |
    | `screensaverplayingenabled` | `0/1` | Wygaszacz podczas odtwarzania |
    | `screensaverplayingtimeout` | `<sec>` | Timeout wygaszacza przy play |
     
    ---
     
    ## 📅 Czas / SNTP
     
    | Komenda | Parametr | Opis |
    |----------|----------|------|
    | `tzh` | `<hours>` | Godzina strefy |
    | `tzm` | `<minutes>` | Minuty strefy |
    | `sntp1` | `<server>` | Serwer SNTP 1 |
    | `sntp2` | `<server>` | Serwer SNTP 2 |
    | `timeint` | `<sec>` | Interwał synchronizacji |
    | `timeintrtc` | `<sec>` | Interwał RTC |
     
    ---
     
    ## 🌦️ Pogoda
     
    | Komenda | Parametr | Opis |
    |----------|----------|------|
    | `showweather` | `0/1` | Włącza pogodę |
    | `lat` | `<str>` | Szerokość geograficzna |
    | `lon` | `<str>` | Długość geograficzna |
    | `key` | `<str>` | Klucz API |
    | `wint` | `<value>` | Interwał odświeżania |
     
    ---
     
    ## 🔌 Sieć / System
     
    | Komenda | Parametr | Opis |
    |----------|----------|------|
    | `softap` | `<value>` | Opóźnienie SoftAP |
    | `mdnsname` | `<str>` | Nazwa mDNS |
    | `rebootmdns` | — | Restart i zmiana hosta |
    | `reboot` / `boot` | — | Restart ESP32 |
    | `format` | — | Format SPIFFS i restart |
     
    ---
     
    ## 🛠️ IR
     
    | Komenda | Parametr | Opis |
    |----------|----------|------|
    | `irbtn` | `<value>` | Ustawia przycisk IR |
    | `chkid` | `<value>` | ID kanału IR |
    | `irclr` | `<value>` | Czyści kod IR |
     
    ---
     
    ## 🔊 Audio
     
    | Komenda | Parametr | Opis |
    |----------|----------|------|
    | `audioinfo` | `<0/1>` | Pokazuje informacje audio |
    | `vumeter` | `<0/1>` | Włącza VU-meter |
    | `snuffle` | `true/false` | Tryb snuffle |
    | `sdpos` | `<value>` | Pozycja SD |



| Left columns  | Right columns |
| ------------- |:-------------:|
| left foo      | right foo     |
| left bar      | right bar     |
| left baz      | right baz     |


Jakis teks [[{{   fgfd]]}}  ```blablabla``` 
