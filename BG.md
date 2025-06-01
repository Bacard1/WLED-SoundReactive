![BANNER](/IMG/banner.png)

# 🎤🔉WLED SoundReactiv интилигентна цветомузика
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?color=ff00d8)](https://opensource.org/licenses/MIT)
![Downloads](https://img.shields.io/npm/dm/WLED-SoundReactive.svg?color=ff00d8)
[![hacs_badge](https://img.shields.io/badge/HACS-2025.5.3-orange.svg?color=ff00d8)](https://github.com/hacs/integration)

[![Home Assistant](https://img.shields.io/badge/.-HOME_ASSISTANT-blue?logo=homeassistant)](https://www.home-assistant.io/) 
[![Donate via PayPal](https://img.shields.io/badge/PayPal-DONATE-blue?logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=AAWFZVF2XCP5A)
![Script](https://img.shields.io/badge/Script-YAML-blue?logo=yaml)

[![Български](https://img.shields.io/badge/BG-ЕЗИК-gree?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg
)](BG.md)
[![Deutch](https://img.shields.io/badge/DE-SPRACHE-gree?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg
)](DE.md)
[![English](https://img.shields.io/badge/EN-LANGUAGE-gree?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg)](README.md)

WLED SoundReactive – Интелигентно аудио-реактивно осветление с ESP32

Този проект представя моята лична реализация на WLED SoundReactive с помощта на ESP32 микроконтролер. Чрез интелигентна визуализация на звука в реално време, можете да озарите помещението си в синхрон с музиката – идеално за партита, фонова светлина или просто като готин DIY проект.

Какво включва репозиторията:

YAML автоматизации за Home Assistant

Инструкции за хардуерна настройка

Конфигурационни насоки за SoundReactive WLED форк

Визуални подобрения за по-реалистичен ефект

Подходящ както за напреднали, така и за начинаещи ентусиасти в света на ESP32 и WLED.

<img align="center" src="IMG\WLED-scheme.png"  alt="WLED-scheme" width="100%" height="100%">

> [!WARNING]
> На схемата не е показана дължината на лентата или броят на диодите, понеже това не е от значение.

---

## 📦 Съдържание

- [🎤🔉WLED SoundReactiv интилигентна цветомузика](#wled-soundreactiv-интилигентна-цветомузика)
  - [📦 Съдържание](#-съдържание)
  - [💻 Хардуер:](#-хардуер)
    - [Компоненти:](#компоненти)
  - [👽 Софтуер:](#-софтуер)
    - [Инсталиране на WLED: WLED e уеб сървър за управление на NeoPixel (WS2812B, WS2811, SK6812) светодиоди или също SPI базирани чипсети, като WS2801 и APA102! Свържете ESP32 към произволен USB порт на машина с Windows/Linux/MAC за да инсталирате WLED уеб сървър.](#инсталиране-на-wled-wled-e-уеб-сървър-за-управление-на-neopixel-ws2812b-ws2811-sk6812-светодиоди-или-също-spi-базирани-чипсети-като-ws2801-и-apa102-свържете-esp32-към-произволен-usb-порт-на-машина-с-windowslinuxmac-за-да-инсталирате-wled-уеб-сървър)
    - [Конфигуриране/Настройки на WLED:](#конфигурираненастройки-на-wled)
    - [Home-Assistant integration:](#home-assistant-integration)

---

## 💻 Хардуер: 

### Компоненти:
- **ESP32 DEV:** моделът не е от много голямо значение в този проект беше използван ["ESP32 WROOM-32 Entwicklungsboard TYPE-C CH340C/ CP2102" ](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) 

<img align="center" src="IMG/ESP WROMM 32.png"  alt="ESP WROMM 32" width="35%" height="35%">

- **ESP32 Adapter:** Предимствата на този ["Terminal Adapter"](https://www.amazon.de/dp/B0CRVHJ9GB?ref=ppx_yo2ov_dt_b_fed_asin_title) са много, ето и някои от тях.:
    - Не е необходимо запояване, а всъщност е здраво и стъбилно.
    - Не се налага да програмирате ["ESP32 WROOM-32 Entwicklungsboard TYPE-C CH340C/ CP2102" ](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) на място, а след програмирането просто го поставяте.
    - Възможност за тестване с повече от един чип (докато всичко си работи можете да си поиграете с настройките върху др. чип и просто да ги размените).
    - Предотвратява допир на два пина.
    - Удобно за направата на мост между два пина.
    
    <br>

    <img align="center" src="IMG/ESP-adapter.png"  alt="ESP-adapter" width="35%" height="35%">

- **Микрофон:** [MAX9814](https://www.amazon.de/dp/B0D3X6K7BW?ref=ppx_yo2ov_dt_b_fed_asin_title) е идеалният избор за този проект, но той може да бъде заменен и с друг вид.:

    <img align="center" src="IMG/mic-MAX9814.png"  alt="mic-MAX9814" width="35%" height="35%">
 
> [!WARNING]
>  Преди да включите захранването се уверете, че кабелите водещи до микрофонът са точн, както на схемата най-горе и не контактуват помежду си. В противен случай микрофонът изгаря и става негоден за употреба. Можете да проверите това с мултицет. Четирите канала на микрофона не трябва да контактуват, ако те контактуват търсете проблемът в споиките или вече той е изгорял. 

- **Захранване:** то би могло да бъде и друго, в този проект ползвах ["vusum Schalt-LED-Netzteil, 5-V-Netzteil, Transformator"](https://de.aliexpress.com/item/1005005616440560.html?spm=a2g0o.order_list.order_list_main.4.133b5c5fQtV6NX&gatewayAdapt=glo2deu). 

    <img align="center" src="IMG/netz-teil.png"  alt="netz-teil" width="35%" height="35%">

> [!WARNING]
> Да работи на 5 волта и мощността му да не е по-малка от тази на лед лентите, които ще захранва. Както се вижда в обявата цената между 150W-350W не e много голяма. Моят съвет е да вземете максимално голямата мощност. Понеже така или иначе ще изразходва само това, което консумират LED-лентите, а не повече.:

- **LED лента:** за този проект избрах [Individually Addressable Led Strip,5m 300Pixels 5V Led](https://www.amazon.de/gp/product/B01CDTEG1O/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1).:

    <img align="center" src="IMG/LED.png"  alt="LED" width="35%" height="35%">

> [!WARNING]
> Изборът на LED лента е строго идивидуален. В моят случай ми трябваха 4 ленти по 2,3 метра и избрах две ленти по 5 метра с максимален брой диоди на нея, за да се постигне максимален ефект.

    
- **Други:** за проекта бяха нужни и [LED-конектори](https://www.amazon.de/gp/product/B094NJLKFH/ref=ppx_yo_dt_b_search_asin_image?ie=UTF8&psc=1) ,[кабели](https://www.amazon.de/gp/product/B08JTZKN4M/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1) ,[ъглови алуминеви профили](https://www.amazon.de/gp/product/B0BG8L6D8Q/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1) и [клемореди](https://de.aliexpress.com/item/1005006918394384.html?spm=a2g0o.order_list.order_list_main.151.133b5c5fQtV6NX&gatewayAdapt=glo2deu) 

    <img align="center" src="IMG/kleme.png"  alt="клемореди" width="35%" height="35%">
    <img align="center" src="IMG/LED-kuplung.png"  alt="LED-конектори" width="35%" height="35%">
    <img align="center" src="IMG/alu-profile.png"  alt="ъглови алуминеви профили" width="35%" height="35%">
    <img align="center" src="IMG/cabel.png"  alt="кабели" width="35%" height="35%">

> [!WARNING]
> Внимавайте при закупуването на [LED лентата](https://www.amazon.de/gp/product/B01CDTEG1O/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1) и  [Захранването](https://de.aliexpress.com/item/1005005616440560.html?spm=a2g0o.order_list.order_list_main.4.133b5c5fQtV6NX&gatewayAdapt=glo2deu). Трябва да работят задължително на 5 Волта, понеже и [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) работи на толкова. [Микрофонът](https://www.amazon.de/dp/B0D3X6K7BW?ref=ppx_yo2ov_dt_b_fed_asin_title) трябва да работи на 3 Волта или в този диапазон, но не и повече от 5 Волта.

## 👽 Софтуер: 

### Инсталиране на WLED: WLED e уеб сървър за управление на NeoPixel (WS2812B, WS2811, SK6812) светодиоди или също SPI базирани чипсети, като WS2801 и APA102! Свържете [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) към произволен USB порт на машина с Windows/Linux/MAC за да инсталирате WLED уеб сървър.
- [Драивър VCP Drivers:](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads) след инсталацията рестартирайте операционната система преди да продължите.
- [Флаш софтуер:](https://github.com/xyzroe/ZigStarGW-MT/releases/).: непретенциозен и лесен за употреба.
- [WEB Flash](https://tasmota.github.io/install/): удобна функция за инсталиране на "bin" файлове предоставена от Tasmota.
- [WLED уеб сървър:](https://github.com/Bacard1/Home-Assistant-Bulgaria/raw/refs/heads/main/Statik/Projekts/Home-Assistant-WLED-SoundReactive/bin/WLEDMM_0.14.0-b15.21_athom_music_esp32_4MB_M.bin)
  
> [!WARNING]
> Използвайте точно този файл, понеже е модификация и работи прекрасно с [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) и е компактивен с всички операционни системи. Не се тревожете за версията тя ще бъде подменена от мен, ако има по нова такава. 

### Конфигуриране/Настройки на WLED:
- **Настройки на Wi-Fi мрежата:** тази настройка не е задължителна, въпрос на вкус.

    <img align="center" src="IMG/GIF/WLED-Wi-Fi-config.gif"  alt="WLED-Wi-Fi-config" width="100%" height="100%">

- **Настройки на LED лентата:** пребройте точно LED диодите, по това се подразбира, че всяка една лента трябва да е с еднакъв брой диоди.

    <img align="center" src="IMG/GIF/WLED-LED-config.gif"  alt="WLED-LED-config" width="100%" height="100%">

- **Настройки на микрофонът:**

    <img align="center" src="IMG/GIF/WLED-mic-config.gif"  alt="WLED-mic-config" width="100%" height="100%">

### Home-Assistant integration: 

<a href="https://my.home-assistant.io/redirect/config_flow_start?domain=wled">
    <img align="center" src="/IMG/button ADD INTEGRATION TO.svg" alt="Още информация" width="40%" height="40%">
</a>

> [!WARNING]
> Ако "Home Assistent" ви препоръча нова версия на WLED я пропоснете. В противен случай, ще загубите опциите си за настройване на микрофон.

> [!TIP]
> Ако този проект ви е харесъл, [ТУК](https://github.com/Bacard1?tab=repositories) ще намерите още интересни гранилища направени от мен.<br>
> Ако срещате затруднения или имате въпроси не се колебайте да се свържете с мен.