---
title: Using OLED(SSD1306:SPI,128x64) by ESP32
share: false  # Show social sharing links?
view: ["3"]
date: "2019-09-20"
markup: mmark
abstruct: ""
draft: false
featured: true
categories : ["tips", "ESP32", "Electronic Kits"]
tags : ["ESP32", "Electronic Kits"]
---

## Pin Assintment

about SSD1306:SPI,128x64  

- GND  
- VCC : 3.3v (or 5v)  
- D0 : CLK  
- D1 : MOSI  
- RES : GPIO  
- DC : GPIO  
- CS : GPIO  

## Install Library

- スケッチ>ライブラリをインクルード>ライブラリを管理...
- search and install : Adafruit SSD1306 by Adafruit
- search and install : Adafruit GFX Library

## Modify Library

To match your device, select display size in Adafruit_SSD.h at Arduino/libraries/Adafruit_SSD1306

change form

``` C
   #define SSD1306_64_48
// #define SSD1306_128_64
// #define SSD1306_128_32
// #define SSD1306_96_16
```

to

``` C
// #define SSD1306_64_48
   #define SSD1306_128_64
// #define SSD1306_128_32
// #define SSD1306_96_16
```

## Use Sample Program

at ファイル>スケッチ例>Adafruit SSD1306 Wemos Mini OLED> ssd 1306_128x64_spi

Modify sample program about Pin define

## Reference

- https://circuitdigest.com/microcontroller-projects/esp32-internet-clock
- https://mobile.k05.biz/e/2018/12/ssd1306-128x64-spi.html
- https://jumbleat.com/2017/03/16/amazon_cheap_oled_2/
