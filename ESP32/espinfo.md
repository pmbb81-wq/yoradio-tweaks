---
                                          📋 ESP32-S3-N16R8
---
Plytka kupiona na aliexpress: https://pl.aliexpress.com/item/1005010071582851.html

  <img width="425" height="182" alt="obraz" src="https://github.com/user-attachments/assets/b2941932-f48c-4f9b-97b3-3dc4ee2dfe7f" />



Taka plytka ESP32-S3-N16R8 posiada dwie kostki. Jedna to kosc flash czyli np 16MB a druga to kosc PSRAM jak na zdjeciu ponizej. Nie trzeba rozcinac swojej plytki :)

<img width="837" height="510" alt="obraz" src="https://github.com/user-attachments/assets/b62c8245-96a1-42b8-8112-8ef2672be0fb" />

Ponizej caly artykul o PSRAM :)

https://www.upesy.com/blogs/tutorials/get-more-ram-on-esp32-with-psram#

---
# 📋 PlatformIO
---
Warto dodac tutaj pare informacji o ustawieniu pod plytke ESP32-S3-N16R8 jak powinna wygladac standardowe ustawienie dla PlatformIO.

UWAGA! Ponizej moje ustawienia pod plytke ESP32-S3-N16R8 z wykorzystaniem partition.csv
```C++
[env:esp32-s3-devkitc1-n8r2]
;Arduino Release v3.3.3 based on ESP-IDF v5.5.1.251017
platform = https://github.com/pioarduino/platform-espressif32/releases/download/55.03.33/platform-espressif32.zip
board = esp32-s3-devkitc1-n8r2
framework = arduino


; Ustawienia plytki
board_build.flash_mode = qio
board_build.psram_type = opi
board_build.memory_type = qio_opi      ; 
board_upload.maximum_size = 8388608    ; 4MB = 4194304 16MB = 16777216 32MB = 33554432
board_upload.flash_size = 8MB                 ; 4,8,16,32 
board_build.extra_flags = -DBOARD_HAS_PSRAM     ; 


board_build.partitions = partition.csv
board_build.filesystem = spiffs

upload_protocol = esptool



; Taktowanie CPU 240Mhz
board_build.f_cpu = 240000000L


; Biblioteki
lib_deps = 
    adafruit/Adafruit GFX Library@^1.12.3


; Monitorowanie portu USB
monitor_speed = 115200
upload_speed = 921600
upload_port = COM17  ;nasz port com do ktorego podpielismy ESP.
monitor_rts = 0
monitor_dtr = 0
```

Jak wyglada taki plik partitions.csv dla plytki N16R8? Wynik ponizej:

```CSV
# Name,   Type, SubType, Offset,  Size, Flags
nvs,      data, nvs,     0x9000,  0x5000,
otadata,  data, ota,     0xe000,  0x2000,
app0,     app,  ota_0,   0x10000, 0x330000,
app1,     app,  ota_1,   0x340000,0x330000,
spiffs,   data, spiffs,  0x670000,0x180000,
coredump, data, coredump,0x7F0000,0x10000,
```

ESP32-S3-N4R2
```CSV
# Name,   Type, SubType, Offset,   Size,     Flags
nvs,      data, nvs,     0x9000,   0x5000,
otadata,  data, ota,     0xe000,   0x2000,
app0,     app,  ota_0,   0x10000,  0x190000,
app1,     app,  ota_1,   0x1A0000, 0x190000,
spiffs,   data, spiffs,  0x330000, 0xC0000,
coredump, data, coredump,0x3F0000, 0x10000,
```

ESP32-S3-N8R4
```CSV
# Name,   Type, SubType, Offset,   Size,     Flags
nvs,      data, nvs,     0x9000,   0x5000,
otadata,  data, ota,     0xe000,   0x2000,
app0,     app,  ota_0,   0x10000,  0x330000,
app1,     app,  ota_1,   0x340000, 0x330000,
spiffs,   data, spiffs,  0x670000, 0x180000,
coredump, data, coredump,0x7F0000, 0x10000,
```

Rodzaje i przyklady partycji:

board_build.partitions = min_spiffs.csv 

board_build.partitions = huge_app.csv

board_build.partitions = default.csv

---
MYOPTIONS.h
---
#define DEF_SPI_FREQ         

80000000UL  //Ustawia predkosc odswierzania LCD














