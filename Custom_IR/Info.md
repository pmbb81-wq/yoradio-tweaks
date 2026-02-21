---
                                                               📋 CUSTOM IR CODES 📻
                                                   ```Modyfikacja pod wlasne kody do pilota.```
---

1. Edytujemy plik Controls.cpp
   
![c1](https://github.com/user-attachments/assets/3e5e8335-2324-4845-b683-e369308a086e)


2. Pomiedzy #enif a for wkleimy nasz kod do zmapowania kodow pilota :) THX for Marcin za nakierowanie na poprawne tory :)
   
<img width="799" height="477" alt="obraz" src="https://github.com/user-attachments/assets/f1012fb3-6466-45b4-82d1-99bac77a85a9" />

3. Ponizej kod wykorzystany do wlaczania lub wylaczania pogody.
```C++
if (irResults.value == 0x202E817)

              {
               Serial.println("weather off");
                config.setShowweather(0);
                irrecv.resume(); // Przygotowanie na kolejny sygnał
                return;
              }

              if (irResults.value == 0x20218E7)

              {
               Serial.println("weather on");
                config.setShowweather(1);
                irrecv.resume(); // Przygotowanie na kolejny sygnał
                return;
              }
```
4. Kody 0x202E817 i 0x20218E7 sa oczywiscie z mojego pilota :) Aby odczytac kod pilota musimy wejsc w ustawienia na stronie www i wybrac opcje IR Recorder.

<img width="505" height="369" alt="obraz" src="https://github.com/user-attachments/assets/aadf6943-09d6-4819-bc7a-f798e034e8df" />

5.Wchodzimy w IR RECORDER aby odczytac interesujacy nasz kod pilota. W tym przypadku dla klawisza 0. Mozemy jak widac dodac obsluge do 3 pilotow.

<img width="701" height="691" alt="obraz" src="https://github.com/user-attachments/assets/ac8ec343-ff54-4da9-8d56-994dbb9db48d" />

6. Ja uzywam takiego pilota z aliexpress i teraz pokaze przyklad na przypisaniu kodu do czerwonego guziczka :)

 <img width="1698" height="777" alt="obraz" src="https://github.com/user-attachments/assets/3da47551-8647-4bc6-90f7-d6874481ea0e" />

 7. Musiny jak juz wiemy wejsc na ta strone gdzie sa odczytywane kody pilota i zapisac go sobie. Kod z mojego pilota to: 202B24D

 8. Tworzymy jakis kod dla tego przycisku.
```C++
if (irResults.value == 0x202B24D)

              {
               Serial.println("Restart ESP");
                ESP.restart();
                irrecv.resume(); // Przygotowanie na kolejny sygnał
                return;
              }
```

9.Kompilujemy nasz kod i sprawdzamy jak dziala ;)

10.Sprawdzamy teraz taki kod:
```C++
if (irResults.value == 0x20242BD) // kolejny przycisk

              {
              Serial.println("ESP Info...\n");
                
              Serial.printf("------------------------- \n");

              Serial.printf("--- SYSTEM INFO ---\n");
Serial.printf("Chip Model: %s | Rev: %u | Cores: %u\n", ESP.getChipModel(), ESP.getChipRevision(), ESP.getChipCores());
Serial.printf("SDK Ver: %s | Core Ver: %s\n", ESP.getSdkVersion(), ESP.getCoreVersion());
Serial.printf("CPU Freq: %u MHz | Cycle Count: %u\n", ESP.getCpuFreqMHz(), ESP.getCycleCount());
Serial.printf("Flash Size: %u bajtow | Speed: %u MHz | Mode: %u\n", ESP.getFlashChipSize(), ESP.getFlashChipSpeed() / 1000000, ESP.getFlashChipMode());
Serial.printf("Sketch Size: %u | Free Heap: %u bajtow\n", ESP.getSketchSize(), ESP.getFreeHeap());
Serial.printf("PSRAM Size: %u | Free PSRAM: %u\n", ESP.getPsramSize(), ESP.getFreePsram());
Serial.printf("Sketch MD5: %s\n", ESP.getSketchMD5().c_str());
Serial.printf("-------------------\n");


              irrecv.resume(); // Przygotowanie na kolejny sygnał
                return;
              }
```






W logu pokaza sie takie informacje:
```C++
------------------------- 
--- SYSTEM INFO ---
Chip Model: ESP32-S3 | Rev: 2 | Cores: 2
SDK Ver: v5.5.2-249-gf56bea3d1f | Core Ver: 3.3.6
CPU Freq: 240 MHz | Cycle Count: 3145914382
Flash Size: 16777216 bajtow | Speed: 80 MHz | Mode: 0
Sketch Size: 2159888 | Free Heap: 127544 bajtow
PSRAM Size: 8388608 | Free PSRAM: 7402024
Sketch MD5: 4c52befaee51a5d79eb121460e08cb7c
```





















