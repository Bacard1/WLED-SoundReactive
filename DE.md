![BANNER](/IMG/banner.png)  

# 🎤🔉 WLED SoundReaktiv intelligente Farbmusik  
[![Home Assistant](https://img.shields.io/badge/🏠_Home_Assistant-41BDF5?logo=homeassistant)](https://www.home-assistant.io/) [![Donate via PayPal](https://img.shields.io/badge/PayPal-Donate-blue?logo=paypal)](https://www.paypal.com/donate/?hosted_button_id=AAWFZVF2XCP5A)  
![Script](https://img.shields.io/badge/logo-yaml-green?logo=yaml)  
[![Български](https://img.shields.io/badge/BG_Български-език-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg)](BG.md)  
[![Deutsch](https://img.shields.io/badge/DE_Deutsche-Sprache-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/de)](DE.md)  
[![English](https://img.shields.io/badge/EN_English-language-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/en)](README.md)  

WLED SoundReactive – Intelligente audio-reaktive Beleuchtung mit ESP32  

Dieses Projekt stellt meine persönliche Implementierung von WLED SoundReactive mit dem ESP32-Mikrocontroller vor. Durch intelligente Echtzeit-Audio-Visualisierung können Sie Ihren Raum im Takt der Musik beleuchten – perfekt für Partys, Hintergrundbeleuchtung oder einfach als cooles DIY-Projekt.  

Was das Repository beinhaltet:  

- YAML-Automatisierungen für Home Assistant  
- Anleitungen zur Hardware-Konfiguration  
- Konfigurationsanleitungen für den SoundReactive-WLED-Fork  
- Visuelle Verbesserungen für einen realistischeren Effekt  

Geeignet für fortgeschrittene und beginnende Enthusiasten in der Welt von ESP32 und WLED.  

<img align="center" src="IMG\WLED-scheme.png" alt="WLED-scheme" width="100%" height="100%">  

> [!WARNING]  
> Die Schaltung zeigt nicht die Länge des LED-Streifens oder die Anzahl der Dioden, da dies irrelevant ist.  

---  

## 📦 Inhalt  

- [🎤🔉 WLED SoundReaktiv intelligente Farbmusik](#-wled-soundreaktiv-intelligente-farbmusik)
	- [📦 Inhalt](#-inhalt)
	- [💻 Hardware](#-hardware)
		- [Komponenten:](#komponenten)
	- [👽 Software](#-software)
		- [Installation von WLED:](#installation-von-wled)
		- [Konfiguration von WLED:](#konfiguration-von-wled)
		- [Home Assistant Integration:](#home-assistant-integration)

---  

## 💻 Hardware  

### Komponenten:  
- **ESP32 DEV:** Das Modell ist nicht entscheidend. In diesem Projekt wurde ["ESP32 WROOM-32 Entwicklungsboard TYPE-C CH340C/ CP2102"](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) verwendet.  

<img align="center" src="IMG/ESP WROMM 32.png" alt="ESP WROMM 32" width="35%" height="35%">  

- **ESP32 Adapter:** Die Vorteile dieses ["Terminal Adapters"](https://www.amazon.de/dp/B0CRVHJ9GB?ref=ppx_yo2ov_dt_b_fed_asin_title) sind vielfältig:  
  - Kein Löten erforderlich, stattdessen feste Steckverbindungen.  
  - Der ["ESP32 WROOM-32 Entwicklungsboard TYPE-C CH340C/ CP2102"](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) muss nicht vor Ort programmiert werden, sondern kann nach der Programmierung einfach eingesetzt werden.  
  - Möglichkeit zum Testen mit mehreren Chips (während alles funktioniert, können Sie Einstellungen auf einem anderen Chip vornehmen und einfach austauschen).  
  - Verhindert Kurzschlüsse zwischen Pins.  
  - Praktisch für Brücken zwischen Pins.  

  <br>  

  <img align="center" src="IMG/ESP-adapter.png" alt="ESP-adapter" width="35%" height="35%">  

- **Mikrofon:** [MAX9814](https://www.amazon.de/dp/B0D3X6K7BW?ref=ppx_yo2ov_dt_b_fed_asin_title) ist die ideale Wahl für dieses Projekt, kann aber auch durch andere Modelle ersetzt werden.  

  <img align="center" src="IMG/mic-MAX9814.png" alt="mic-MAX9814" width="35%" height="35%">  

> [!WARNING]  
> Stellen Sie vor dem Einschalten sicher, dass die Kabel zum Mikrofon korrekt verlegt sind, wie im Schaltplan oben gezeigt, und keinen Kontakt zueinander haben. Andernfalls kann das Mikrofon beschädigt werden. Überprüfen Sie dies mit einem Multimeter. Die vier Kanäle des Mikrofons dürfen keinen Kontakt haben. Falls doch, überprüfen Sie die Lötstellen oder ob das Mikrofon bereits defekt ist.  

- **Stromversorgung:** Eine andere Stromversorgung ist möglich. In diesem Projekt wurde ["vusum Schalt-LED-Netzteil, 5-V-Netzteil, Transformator"](https://de.aliexpress.com/item/1005005616440560.html?spm=a2g0o.order_list.order_list_main.4.133b5c5fQtV6NX&gatewayAdapt=glo2deu) verwendet.  

  <img align="center" src="IMG/netz-teil.png" alt="netz-teil" width="35%" height="35%">  

> [!WARNING]  
> Die Stromversorgung muss mit 5 Volt arbeiten, und ihre Leistung sollte nicht geringer sein als die der LED-Streifen, die sie versorgt. Wie in der Anzeige zu sehen ist, ist der Preisunterschied zwischen 150W und 350W nicht groß. Mein Rat ist, die höchstmögliche Leistung zu wählen, da sie nur das verbraucht, was die LED-Streifen benötigen, und nicht mehr.  

- **LED-Streifen:** Für dieses Projekt wurde [Individuell ansteuerbarer LED-Streifen, 5m 300Pixel 5V LED](https://www.amazon.de/gp/product/B01CDTEG1O/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1) gewählt.  

  <img align="center" src="IMG/LED.png" alt="LED" width="35%" height="35%">  

> [!WARNING]  
> Die Wahl des LED-Streifens ist sehr individuell. In meinem Fall benötigte ich 4 Streifen à 2,3 Meter und wählte zwei 5-Meter-Streifen mit der maximalen Anzahl an Dioden für den besten Effekt.  

- **Sonstiges:** Für das Projekt wurden auch [LED-Steckverbinder](https://www.amazon.de/gp/product/B094NJLKFH/ref=ppx_yo_dt_b_search_asin_image?ie=UTF8&psc=1), [Kabel](https://www.amazon.de/gp/product/B08JTZKN4M/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1), [aluminium Winkelprofile](https://www.amazon.de/gp/product/B0BG8L6D8Q/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1) und [Klemmen](https://de.aliexpress.com/item/1005006918394384.html?spm=a2g0o.order_list.order_list_main.151.133b5c5fQtV6NX&gatewayAdapt=glo2deu) benötigt.  

  <img align="center" src="IMG/kleme.png" alt="Klemmen" width="35%" height="35%">  
  <img align="center" src="IMG/LED-kuplung.png" alt="LED-Steckverbinder" width="35%" height="35%">  
  <img align="center" src="IMG/alu-profile.png" alt="aluminium Winkelprofile" width="35%" height="35%">  
  <img align="center" src="IMG/cabel.png" alt="Kabel" width="35%" height="35%">  

> [!WARNING]  
> Achten Sie beim Kauf des [LED-Streifens](https://www.amazon.de/gp/product/B01CDTEG1O/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1) und der [Stromversorgung](https://de.aliexpress.com/item/1005005616440560.html?spm=a2g0o.order_list.order_list_main.4.133b5c5fQtV6NX&gatewayAdapt=glo2deu). Sie müssen unbedingt mit 5 Volt arbeiten, da auch der [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) mit dieser Spannung betrieben wird. Das [Mikrofon](https://www.amazon.de/dp/B0D3X6K7BW?ref=ppx_yo2ov_dt_b_fed_asin_title) muss mit 3 Volt oder in diesem Bereich arbeiten, aber nicht mehr als 5 Volt.  

## 👽 Software  

### Installation von WLED:  
WLED ist ein Webserver zur Steuerung von NeoPixel (WS2812B, WS2811, SK6812) LEDs oder SPI-basierten Chipsätzen wie WS2801 und APA102! Verbinden Sie den [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) mit einem beliebigen USB-Port eines Windows/Linux/MAC-Computers, um den WLED-Webserver zu installieren.  

- [VCP-Treiber:](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads) Starten Sie das Betriebssystem nach der Installation neu, bevor Sie fortfahren.  
- [Flash-Software:](https://github.com/xyzroe/ZigStarGW-MT/releases/): Unkompliziert und einfach zu bedienen.  
- [WEB Flash](https://tasmota.github.io/install/): Praktische Funktion zum Installieren von "bin"-Dateien, bereitgestellt von Tasmota.  
- [WLED-Webserver:](https://github.com/Bacard1/Home-Assistant-Bulgaria/raw/refs/heads/main/Statik/Projekts/Home-Assistant-WLED-SoundReactive/bin/WLEDMM_0.14.0-b15.21_athom_music_esp32_4MB_M.bin)  

> [!WARNING]  
> Verwenden Sie genau diese Datei, da es sich um eine Modifikation handelt, die perfekt mit dem [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) funktioniert und mit allen Betriebssystemen kompatibel ist. Machen Sie sich keine Sorgen um die Version, sie wird von mir aktualisiert, falls eine neuere verfügbar ist.  

### Konfiguration von WLED:  
- **Wi-Fi-Netzwerkeinstellungen:** Diese Einstellung ist optional und Geschmackssache.  

  <img align="center" src="IMG/GIF/WLED-Wi-Fi-config.gif" alt="WLED-Wi-Fi-config" width="100%" height="100%">  

- **LED-Streifen-Einstellungen:** Zählen Sie die LED-Dioden genau. Jeder Streifen sollte die gleiche Anzahl an Dioden haben.  

  <img align="center" src="IMG/GIF/WLED-LED-config.gif" alt="WLED-LED-config" width="100%" height="100%">  

- **Mikrofon-Einstellungen:**  

  <img align="center" src="IMG/GIF/WLED-mic-config.gif" alt="WLED-mic-config" width="100%" height="100%">  

### Home Assistant Integration:  

<a href="https://my.home-assistant.io/redirect/config_flow_start?domain=wled">  
    <img align="center" src="/IMG/button ADD INTEGRATION TO.svg" alt="Weitere Informationen" width="40%" height="40%">  
</a>  

> [!WARNING]  
> Wenn "Home Assistant" eine neuere Version von WLED vorschlägt, lehnen Sie diese ab. Andernfalls verlieren Sie die Mikrofon-Einstellungsoptionen.  

> [!TIP]  
> Wenn Ihnen dieses Projekt gefallen hat, finden Sie [HIER](https://github.com/Bacard1?tab=repositories) weitere interessante Repositories von mir.  
> Bei Fragen oder Problemen zögern Sie nicht, mich zu kontaktieren.