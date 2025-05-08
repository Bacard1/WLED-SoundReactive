# 🎤🔉WLED SoundReactiv Intelligent Light and Sound Show
[![PayPal Donation](https://img.shields.io/badge/PayPal-Дари-синьо?logo=paypal)](https://www.paypal.com/donate/?osted_button_id=AAWFZVF2XCP5A)
![Script](https://img.shields.io/badge/logo-yaml-green?logo=yaml)
[![Български](https://img.shields.io/badge/Български-език-green?logo=translate&labelColor=gray&style=flat-square&link=https://example.com/bg)](BG.md)

The idea is to place aluminum profiles with LED strips in the corners of the room, which react to sound in parallel, not sequentially. The schematic I've made is exactly the same as how I've connected the components.

<img align="center" src="IMG\WLED-scheme.png"  alt="WLED-scheme" width="100%" height="100%">

> [!WARNING]
> The schematic does not show the length of the strip or the number of LEDs, as this is not important.

---

## 📦 Contents

- [🎤🔉WLED SoundReactiv Intelligent Light and Sound Show](#wled-soundreactiv-intelligent-light-and-sound-show)
  - [📦 Contents](#-contents)
  - [💻 Hardware:](#-hardware)
    - [Components:](#components)
  - [👽 Software:](#-software)
    - [Installing WLED:](#installing-wled)
    - [Configuring WLED:](#configuring-wled)
    - [Home-Assistant integration:](#home-assistant-integration)

---

## 💻 Hardware: 

### Components:
- **ESP32 DEV:** the model isn't very important; in this project, the ["ESP32 WROOM-32 Entwicklungsboard TYPE-C CH340C/ CP2102"](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) was used. 

<img align="center" src="IMG/ESP WROMM 32.png"  alt="ESP WROMM 32" width="35%" height="35%">

- **ESP32 Adapter:** The advantages of this ["Terminal Adapter"](https://www.amazon.de/dp/B0CRVHJ9GB?ref=ppx_yo2ov_dt_b_fed_asin_title) are many. Here are a few:
  - No soldering required, yet stable and solid.
  - You don't have to program the ["ESP32 WROOM-32 Entwicklungsboard TYPE-C CH340C/ CP2102"](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) in place—just slot it in after programming.
  - Allows testing with multiple chips (while one works, you can tweak settings on another and swap them).
  - Prevents pin shorting.
  - Convenient for bridging two pins.
    
    <br>

    <img align="center" src="IMG/ESP-adapter.png"  alt="ESP-adapter" width="35%" height="35%">

- **Microphone:** [MAX9814](https://www.amazon.de/dp/B0D3X6K7BW?ref=ppx_yo2ov_dt_b_fed_asin_title) is the ideal choice for this project, but can be replaced by other types.

    <img align="center" src="IMG/mic-MAX9814.png"  alt="mic-MAX9814" width="35%" height="35%">
 
> [!WARNING]
> Before powering on, make sure the wires going to the microphone are exactly as in the schematic above and are not touching each other. Otherwise, the microphone will burn out and become unusable. You can verify this with a multimeter. The four channels of the microphone must not short—if they do, check the solder joints or assume it's already damaged.

- **Power Supply:** You can use something else, but for this project I used ["vusum Schalt-LED-Netzteil, 5-V-Netzteil, Transformator"](https://de.aliexpress.com/item/1005005616440560.html?spm=a2g0o.order_list.order_list_main.4.133b5c5fQtV6NX&gatewayAdapt=glo2deu). 

    <img align="center" src="IMG/netz-teil.png"  alt="netz-teil" width="35%" height="35%">

> [!WARNING]
> It must operate at 5V and provide at least the power required by the LED strips. As you can see in the listing, the price difference between 150W and 350W isn't large. My advice: get the highest wattage possible. The PSU will only deliver as much as the LEDs consume—no more.

- **LED Strip:** For this project I chose [Individually Addressable Led Strip,5m 300Pixels 5V Led](https://www.amazon.de/gp/product/B01CDTEG1O/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1).

    <img align="center" src="IMG/LED.png"  alt="LED" width="35%" height="35%">

> [!WARNING]
> Choosing an LED strip is highly individual. In my case, I needed 4 strips of 2.3 meters each, so I chose two 5-meter strips with the maximum number of LEDs to achieve the strongest effect.

    
- **Other:** This project also required [LED connectors](https://www.amazon.de/gp/product/B094NJLKFH/ref=ppx_yo_dt_b_search_asin_image?ie=UTF8&psc=1), [wires](https://www.amazon.de/gp/product/B08JTZKN4M/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1), [angled aluminum profiles](https://www.amazon.de/gp/product/B0BG8L6D8Q/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1), and [terminal blocks](https://de.aliexpress.com/item/1005006918394384.html?spm=a2g0o.order_list.order_list_main.151.133b5c5fQtV6NX&gatewayAdapt=glo2deu) 

    <img align="center" src="IMG/kleme.png"  alt="клемореди" width="35%" height="35%">
    <img align="center" src="IMG/LED-kuplung.png"  alt="LED-конектори" width="35%" height="35%">
    <img align="center" src="IMG/alu-profile.png"  alt="ъглови алуминеви профили" width="35%" height="35%">
    <img align="center" src="IMG/cabel.png"  alt="кабели" width="35%" height="35%">

> [!WARNING]
> Be careful when buying the [LED strip](https://www.amazon.de/gp/product/B01CDTEG1O/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&th=1) and [power supply](https://de.aliexpress.com/item/1005005616440560.html?spm=a2g0o.order_list.order_list_main.4.133b5c5fQtV6NX&gatewayAdapt=glo2deu). They must operate at 5V, since the [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) also uses 5V. The [microphone](https://www.amazon.de/dp/B0D3X6K7BW?ref=ppx_yo2ov_dt_b_fed_asin_title) should run on 3V or within that range—but not over 5V.

## 👽 Software: 

### Installing WLED:  
WLED is a web server for controlling NeoPixel (WS2812B, WS2811, SK6812) LEDs or also SPI-based chipsets like WS2801 and APA102! Connect the [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu) to any USB port of a Windows/Linux/MAC machine to install the WLED web server.
- [VCP Drivers:](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads) reboot your system after installation.
- [Flash software:](https://github.com/xyzroe/ZigStarGW-MT/releases/): simple and easy to use.
- [WEB Flash](https://tasmota.github.io/install/): a convenient method to flash “.bin” files provided by Tasmota.
- [WLED web server binary:](https://github.com/Bacard1/Home-Assistant-Bulgaria/raw/refs/heads/main/Statik/Projekts/Home-Assistant-WLED-SoundReactive/bin/WLEDMM_0.14.0-b15.21_athom_music_esp32_4MB_M.bin)
  
> [!WARNING]
> Use this specific file, as it’s modified and works flawlessly with [ESP32](https://de.aliexpress.com/item/1005005953505528.html?spm=a2g0o.order_list.order_list_main.20.133b5c5fUUgTke&gatewayAdapt=glo2deu), and is compatible with all OSs. Don’t worry about versioning—I’ll update it if there’s a newer one. 

### Configuring WLED:
- **Wi-Fi network settings:** this is optional, a matter of preference.

    <img align="center" src="IMG/GIF/WLED-Wi-Fi-config.gif"  alt="WLED-Wi-Fi-config" width="100%" height="100%">

- **LED strip settings:** count the exact number of LEDs; each strip must have the same number.

    <img align="center" src="IMG/GIF/WLED-LED-config.gif"  alt="WLED-LED-config" width="100%" height="100%">

- **Microphone settings:**

    <img align="center" src="IMG/GIF/WLED-mic-config.gif"  alt="WLED-mic-config" width="100%" height="100%">

### Home-Assistant integration: 

<a href="https://my.home-assistant.io/redirect/config_flow_start?domain=wled">
    <img align="center" src="/IMG/button ADD INTEGRATION TO.svg" alt="Още информация" width="40%" height="40%">
</a>

> [!WARNING]
> If "Home Assistant" suggests updating WLED, skip it. Otherwise, you'll lose your microphone configuration options.

> [!TIP]
> If you liked this project, [HERE](https://github.com/Bacard1?tab=repositories) you’ll find more interesting creations by me.  
> If you have questions or need help, feel free to contact me.
