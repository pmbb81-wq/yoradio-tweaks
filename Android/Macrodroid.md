

Link do aplikacji do play store:

https://play.google.com/store/apps/details?id=com.arlosoft.macrodroid&hl=pl

Sterowanie yoradiem telefonem w nowym wymiarze. Tego nie zrobicie przez www ani inna metode. 

Opis robie na moim telefonie. Xiaomi 11T PRO. Na innych nie mam pojecia jak beda opcje. Musicie sami to obczaic.

Okz zalozmy,ze macie juz zainstalowany Macrodroid. Musicie znac IP radyjka :)

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
Moj przykladowy ip http://192.168.8.103/?vol
```

Odznaczamy Sledz przekierowania.

Klikamy w gornym prawym rogu [v] ptaszka czyli zapisujemy.
Testujemy nasze makro :)

Dla volume down wybieramy volm

Lista komend z githuba:
## POST/GET
---
http://<yoradioip>/?command
---
start           : start 
> Dziala jako przycisk PLAY

stop            : stop
> Dziala jako przycisk STOP

toggle          : start/stop
> Dziala jako przycisk PLAY<->STOP. Mozna przypisac do jednego klawisza.

prev            : previous station
> Poprzednia stacja

next            : next station
> Nastepna stacja

volm            : volume down one step
> Zciszenie o wartosc ustawiona na stronie www.

volp            : volume up one step
> Podglosnienie o wartosc ustawiona na stronie www

vol=x           : set volume to x (0-254)
> Ustawienie glosnosci na wartosc od 0 do 254. Gdzie 254 to 100% glosnosci.

trebble=x&middle=x&bass=x : equalizer, x from -16 to 16 (three parameters together)
> Ustawienia equalizera od -16 do 16. Gdzie 0 to srodek. Chcemy wiecej basu? Ustawiamy np 16 :)

ballance=x      : balance, x from -16 to 16
> Ustawienie balansu. Zero to srodek czyli dwa glosniki graja tak samo.

playstation=x
> Odtwarza stacje x. Np 5 itp. Zalezy ile stacji mamy w playliscie.

play=x          : start playback of station number x
>Odtwarza stacje x. Np 5 czy tam 10 :)
> Przyklad: http:192.168.8.103/?play=1 (pierwsza stacja z playlisty)
>
dspon=x         : display on/off, x=0 - off, x=1 - on
> Wlacza lub wylacza ekran naszego radyjka.
> Przyklad: http:192.168.8.103/?dspon=0 (Wylaczenie ekranu)

dim=x           : display brightness x=(0-100) (if supported)
> Ustawia jasnosc ekranu jezeli wykorzystujemy pin PWM i mamy go zdefiniowanego. Jezeli LCD to obsluguje.
> Przyklad: http:192.168.8.103/?dim=50 (Przyciemnie ekran lcd o 50%)

sleep=x&after=y : sleep for x minutes after y minutes
> Usypia nasze radyjko przez sleep=x po czasie after=y.

sleep=x         : sleep for x minutes right now
> Usypia nasze radyjko natychmiast

reset           : reset settings to default
? Ustawia ustawienia domyslne naszego radyjka


