---
# 📋 SSD1322 SPI 256x64 5,5"
---

Link Aliexpress: 
https://pl.aliexpress.com/item/1005006049846504.html

<img width="686" height="318" alt="obraz" src="https://github.com/user-attachments/assets/cc31972f-c514-46a7-a030-3a536b05633c" />

INFO: Aby polaczyc ten ekran po SPI trzeba usunac rezystor przy P8080. Nie testowalem jeszcze tego LCD :) Na razie chinole produkuja go tylko w dwoch kolorach. Zoltym i zielonym.


---
# 📋 SSD1322 SPI 256x64 3,12"
---

<img width="712" height="267" alt="obraz" src="https://github.com/user-attachments/assets/92782975-253d-4eb8-909b-452e4c65bcbe" />


Chinile produkuja go w 4 kolorach. Z czego kolor bialy potrafi byc tanszy o 50%. Jest on czesto dodawany do Multirabatow. Z wersja V-Toma 0.8.3 wyglada zajefajnie. 

```
Oto kluczowe różnice, które musisz znać przy budowie radia:
1. Rozmiar i widoczność (PPI)

    3,12 cala: Obraz jest mniejszy, ale bardzo ostry i zwarty (wysokie zagęszczenie pikseli). Idealny, gdy patrzysz na radio z bliska (np. stoi na biurku).
    5,5 cala: To ogromny wyświetlacz. Obraz jest dwa razy większy fizycznie, ale przy tej samej liczbie pikseli stają się one "ziarniste" (widoczne gołym okiem). Jest to idealne rozwiązanie, jeśli radio stoi na regale i chcesz widzieć nazwę stacji z drugiego końca pokoju.

2. Pobór prądu (Ważne dla Twojego ESP32!)
Oba te wyświetlacze to zazwyczaj OLED na sterowniku SSD1322.

    Model 5,5" pobiera znacznie więcej prądu niż 3,12". Przy pełnym podświetleniu może to obciążać linię 3.3V Twojego ESP32-S3, co może powodować restarty lub błędy w odczycie Twojego pilota IR.
    Pamiętaj o dobrym zasilaniu (co najmniej 1A–2A dla całego układu).

3. Czy opis "256x64" jest poprawny?
Tak, to klasyczny standard dla sterownika SSD1322, który obsługuje projekt Maestro. Jeśli w Twoim kodzie masz ustawione:
#define LCD_SSD1322
...to oba wyświetlacze zadziałają bez żadnej zmiany w programie. Obraz po prostu "rozciągnie się" na większą powierzchnię w modelu 5,5".
Podsumowanie – co wybrać?

    Wybierz 3,12": Jeśli budujesz mniejsze, kompaktowe radio i zależy Ci na elegancji i ostrości napisów.
    Wybierz 5,5": Jeśli robisz duże radio "stacjonarne" (np. w stylu retro) i chcesz mieć czytelne napisy z dużej odległości.

Proponuję sprawdzić, czy model 5,5" zmieści się w Twojej obudowie – jest on naprawdę duży (około 14 cm szerokości samego szkła!).
```


INFO: W projekcie yoradio w pliku options.h znajduje sie lista obslugiwanych LCD.

```C++
/*******************************************************

The connection tables are located here https://github.com/e2002/yoradio#connection-tables
   
********************************************************/

#define DSP_DUMMY       0     // without display
#define DSP_ST7735      1     // 160x128  1.8'  or 128x128  1.44'  or 160x80   0.96'  https://aliexpress.com/item/1005002822797745.html
#define DSP_SSD1306     2     // 128x64   0.96' https://aliexpress.com/item/1005001621806398.html
#define DSP_NOKIA5110   3     // 84x48    1.6'  https://aliexpress.com/item/1005001621837569.html
#define DSP_ST7789      4     // 320x240  2.4'  https://aliexpress.com/item/32960241206.html 
#define DSP_SH1106      5     // 128x64   1.3'  https://aliexpress.com/item/32683094040.html
#define DSP_1602I2C     6     // 16x2           https://aliexpress.com/item/32305776560.html
#define DSP_SSD1306x32  7     // 128x32   0.91' https://aliexpress.com/item/32798439084.html
#define DSP_SSD1327     8     // 128x128  1.5'  https://aliexpress.com/item/1005001414175498.html
#define DSP_ILI9341     9     // 320x240  3.2'  https://aliexpress.com/item/33048191074.html
#define DSP_SSD1305     10    // 128x64   2.4'  SSD1305 and SSD1309 SPI https://aliexpress.com/item/32950307344.html
#define DSP_SH1107      11    // 128x64   1.3'  https://aliexpress.com/item/4000551696674.html
#define DSP_1602        12    // 16x2           https://aliexpress.com/item/32685016568.html
#define DSP_GC9106      13    // 160x80   0.96' (looks like ST7735S, but it's not him) https://aliexpress.com/item/32947890530.html
#define DSP_2004I2C     14    // 20x4           https://aliexpress.com/item/32783128355.html
#define DSP_2004        15    // 20x4           https://aliexpress.com/item/32783128355.html
#define DSP_SSD1305I2C  16    // 128x64   2.4'  SSD1305 and SSD1309 I2C https://aliexpress.com/item/32950307344.html
#define DSP_ILI9225     17    // 220x176  2.0'  https://aliexpress.com/item/32952021835.html
#define DSP_ST7789_240  18    // 240x240  1.3'  https://aliexpress.com/item/32996979276.html
/* !!! DSP_ST7789_240 requires further development when used in conjunction with the VS1053 module !!! See the link https://www.instructables.com/Adding-CS-Pin-to-13-LCD/ */
#define DSP_ST7796      19    // 480x320  3.5'  https://aliexpress.com/item/1005004632953455.html?sku_id=12000029911293172
#define DSP_GC9A01A     20    // 240x240  1.28' https://aliexpress.com/item/1005004069703494.html?sku_id=12000029869654615
#define DSP_ILI9488     21    // 480x320  3.5'  https://aliexpress.com/item/1005001999296476.html?sku_id=12000018365356570
#define DSP_ILI9486     22    // (Testing mode) 480x320  3.5'  https://aliexpress.com/item/1005001999296476.html?sku_id=12000018365356568
#define DSP_SSD1322     23    // 256x64   2.8'  https://aliexpress.com/item/1005003480981568.html
#define DSP_ST7920      24    // 128x64   2.6'  https://aliexpress.com/item/32699482638.html
#define DSP_ST7789_76   25    // 284x76   2.25' https://aliexpress.com/item/1005009016973081.html
#define DSP_2002        26    // 20x2           https://aliexpress.com/item/32812259852.html
#define DSP_2002I2C     27    // 20x2           https://aliexpress.com/item/32812259852.html
#define DSP_ST7789_170  28    // 320x170  1.9'  https://aliexpress.com/item/1005008723378017.html
#define DSP_CUSTOM      101   // your display
```

LCD mozna zdefiniowac w pliku myoptions.h na dwa sposoby:
```c++
#define DSP_MODEL DSP_SSD1322  // 256x64   2.8'  https://aliexpress.com/item/1005003480981568.html

#define DSP_MODEL 23  // 256x64   2.8'  https://aliexpress.com/item/1005003480981568.html
```

Teraz ponizej moj konfig z wykorzystaniem ESP32-S3 N16R8 czyli z pamiecia flash 16MB i PSRAM 8MB. Te ESP sa wg mnie najlepsze do projektow yoradio.

## 🖥️ Ekran / DSP
```c++
#define DSP_MODEL DSP_SSD1322     /* Wyświetlacz ST7789 2.25` TFT LCD 284x76 */
#define SSD1322_GRAYSCALE false
#define DSP_INVERT_TITLE false

#define TFT_DC         9            /* może być DC, RS */
#define TFT_CS         10           /* może być CS pin ( ) */
#define TFT_RST        -1           /* SPI RST pin	(-1 jeśli połączono z EN) */
#define TFT_MOSI            11              
#define TFT_SCLK            12
```

Mala sciaga PINOUT od Jacka ;)

![esp sciaga pinout](https://github.com/user-attachments/assets/6a862563-811c-444f-b9f7-e4bae5210f8a)


```
1. WYŚWIETLACZ (SPI / I2C / PARALLEL)

    SDA / DIN / MOSI / SDI / DOUT (Dane szeregowe / Master Out Slave In)
    SCL / CLK / MISO / SDO / SCK (Zegar szeregowy / Master In Slave Out)
    DC / RS / A0 (Data/Command - Wybór Dane/Komenda)
    CS / SS / CE (Chip Select - Wybór układu)
    RES / RST / RESET (Resetowanie wyświetlacza)
    BL / LED / BKL / BACKLIGHT (Podświetlenie matrycy)

2. AUDIO DAC (I2S / PCM)

    I2C_DOUT / DIN / DATA (Szeregowe dane audio)
    I2C_BCLK / BCK / BIT_CLK (Bit Clock - Zegar bitowy)
    I2C_LRC / LCK / WS / LRCLK (Word Select / Left-Right Clock)
    MCLK / SCK (Master Clock - używany w niektórych DAC-ach)
    XMT / MUTE (Wyciszenie wzmacniacza)

3. ENCODER (OBROTOWY)

    ENC_BTNR / S1 / PRAWY / CLK (Impuls obrotu A)
    ENC_BTNL / S2 / LEWY / DT (Impuls obrotu B)
    ENC_BTNB / KEY / PRZYCISK / SW (Przycisk wbudowany w enkoder)

4. KARTA SD (SPI)

    SD_CS / SD_SS (Wybór karty SD)
    SD_MOSI / SD_DI (Dane wejściowe karty)
    SD_MISO / SD_DO (Dane wyjściowe karty)
    SD_SCK / SD_CLK (Zegar karty SD)

5. OZNACZENIA NAPIĘĆ I ZASILANIA

    VCC / VIN / 3V3 / 3,3V / 5V (Zasilanie dodatnie)
    GND / MASA / 0V (Masa układu)
    EN / CH_PD / RUN (Enable - Włączenie układu ESP)
    BOOT / IO0 (Przycisk programowania / Bootowania)

6. CZUJNIK IR (PODCZERWIEŃ)

    IR / IR_DATA / RECV (Sygnał z odbiornika podczerwieni)
```


