---
                                                 🇲🇨 Autor kc-dev.pl 🇲🇨
                                                  ##VOLUME MOD 0-100%
---

# 📋 OPIS:
Podmień te pliki z /src/core/
Oraz wrzuć przez Web UI http://twoje-ip/webboard pliki z katalogu /data/www/ (wystarczą tylko te dwa pliki)

Co zrobiłem:
Nie obyło się bez poważniejszego grzebania, bo oprócz poprawnego zmieniania przez Web UI dodałem procentową zmianę głośności i możliwość ustawienia kroku procentowego podczas zmiany przyciskiem lub encoderem. Bez tego nie było by to komfortowe.
Teraz można ustawiać kroki co ile procent zmienia się głośność czyli np. jedno wciśnięcie przycisku to zwiększenie głośności o 5%

Możesz to też sobie konfigurować w pliku wyoptions.h poprzez dodanie zmiennej
#define VOLUME_STEP_PERCENT 5 // Domyślnie 5 to 5% (wtedy nie musisz dodawać tego kodu) ale możesz np. ustawić 10 i będzie co 10% albo 1 i będzie co 1%

Ustaw sobie jeszcze w myoptions.h to (usunie to ramkę wokół i pasek lepiej wygląda podczas zmiany głośności):
#define COLOR_VOLBAR_OUT          0,   0,  0


![modvolok](https://github.com/user-attachments/assets/0f47397e-e732-45aa-b9b0-673983fb30be)



