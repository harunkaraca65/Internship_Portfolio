# Gömülü Sistemler Proje Portföyü / Embedded Systems Project Portfolio

---

## 🇹🇷 Türkçe Özet

Bu depo, STM32 ve ESP32 mikrodenetleyicileri için geliştirilmiş çeşitli gömülü sistem projelerini içerir.
Aşağıda projelerin teknik özetleri ve eşleşen klasör isimleri yer almaktadır.
**Algoritma akışları, donanım konfigürasyonları ve detaylı açıklamalar için lütfen her projenin kendi klasöründeki README dosyasına bakınız.**

## 🇬🇧 English Summary

This repository contains various embedded systems projects developed for STM32 and ESP32 microcontrollers.
Technical summaries of the projects and their corresponding folder names are listed below.
**Please refer to the README file in each project's folder for algorithm flows, hardware configurations, and detailed descriptions.**

---

### 1. `DEM_ESP_UART` - ESP-IDF Asenkron UART İletişimi
**TR:**
Bu proje, ESP-IDF framework üzerinde çalışan ve UART iletişimini yöneten asenkron bir yapı sunar.
Veri alma (RX) ve veri gönderme (TX) işlemleri için birbirinden bağımsız iki FreeRTOS görevi oluşturulmuştur.
Sürekli veri dinleyen RX görevi ve periyodik gönderim yapan TX görevi sayesinde iletişim trafiği bloke edilmeden yönetilir.

**EN:**
This project presents an asynchronous structure running on the ESP-IDF framework managing UART communication.
Two independent FreeRTOS tasks are created for data reception (RX) and data transmission (TX).
Traffic is managed without blocking via the RX task that continuously listens for data and the TX task that transmits periodically.

### 2. `DEM_STM_UART` - STM32 FreeRTOS Senkron UART Yönetimi
**TR:**
STM32 mikrodenetleyicisi üzerinde FreeRTOS kullanılarak geliştirilen bu proje, UART iletişimini senkron bir yapıda ele alır.
Diğer ESP32 projesiyle karşılıklı haberleşmek ve el sıkışma (handshake) protokolünü uygulamak üzere tasarlanmıştır.
Görevler arası senkronizasyon mekanizmaları kullanılarak veri akışının güvenliği ve sıralaması sağlanır.

**EN:**
Developed using FreeRTOS on an STM32 microcontroller, this project handles UART communication in a synchronous structure.
It is designed to communicate mutually with the other ESP32 project and implement a handshake protocol.
Data flow security and ordering are ensured using inter-task synchronization mechanisms.

### 3. `DEM_MODBUS_STM_SLAVE` - STM32 Modbus RTU Slave Yazılımı
**TR:**
Bu yazılım, herhangi bir RTOS kullanmadan SysTick zamanlayıcısı ve kesmeler üzerine kurulu modüler bir Modbus RTU Slave uygulamasıdır.
Modbus protokol işleme, uygulama mantığı ve donanım sürücüleri birbirinden izole edilerek temiz bir mimari oluşturulmuştur.
Ana döngü engellemesiz (non-blocking) çalışarak sistemin sensör okuma ve iletişim görevlerini eş zamanlı yürütmesine olanak tanır.

**EN:**
This software is a modular Modbus RTU Slave application built on SysTick timer and interrupts without using any RTOS.
Modbus protocol processing, application logic, and hardware drivers are isolated from each other creating a clean architecture.
The main loop operates in a non-blocking manner allowing the system to execute sensor reading and communication tasks concurrently.

### 4. `DEM_LOW_POWER` - STM32 Düşük Güç Modları Döngüsü
**TR:**
Bu proje, STM32'nin Sleep, Stop ve Standby gibi düşük güç modlarına giriş ve çıkış süreçlerini döngüsel olarak test eder.
RTC (Gerçek Zamanlı Saat) alarmı, işlemciyi derin uyku durumlarından uyandırmak için bir tetikleyici olarak kullanılır.
Sistemin hangi modda olduğu ve güç tüketim profilleri, üzerindeki LED göstergeleri aracılığıyla izlenebilir.

**EN:**
This project cyclically tests the entry and exit processes for STM32's low-power modes such as Sleep, Stop, and Standby.
The RTC (Real-Time Clock) alarm is used as a trigger to wake the processor from deep sleep states.
The system's current mode and power consumption profiles can be monitored via onboard LED indicators.

### 5. `DEM_ADC_COMPARISON` - STM32 ADC Okuma Yöntemleri Karşılaştırması
**TR:**
Proje, STM32 ADC biriminden veri okumak için Polling, DMA Normal, DMA Circular ve Timer Trigger olmak üzere dört farklı yöntemi uygular.
Her bir yöntemin işlemci yükü üzerindeki etkisi ve veri okuma verimliliği karşılaştırmalı olarak analiz edilir.
Elde edilen veriler bellekteki tampon dizilere kaydedilerek farklı senaryolar için en uygun okuma stratejisi belirlenir.

**EN:**
The project implements four different methods for reading data from the STM32 ADC unit: Polling, DMA Normal, DMA Circular, and Timer Trigger.
The impact on processor load and data reading efficiency of each method is analyzed comparatively.
Acquired data is saved to buffer arrays in memory to determine the most suitable reading strategy for different scenarios.

### 6. `DEM_HC-SR04` - HC-SR04 Ultrasonik Mesafe Ölçümü
**TR:**
Bu uygulama, HC-SR04 sensörü ile hassas mesafe ölçümü yapmak için donanım zamanlayıcılarının Input Capture özelliğini kullanır.
Ortam sıcaklığı ADC üzerinden okunarak ses hızı hesaplamasına dahil edilir ve ölçüm sonuçları termal değişimlere göre kompanze edilir.
One Pulse Mode ile tetiklenen sensör verileri işlenerek sonuçlar UART üzerinden seri port terminaline gönderilir.

**EN:**
This application uses the Input Capture feature of hardware timers to perform precise distance measurement with the HC-SR04 sensor.
Ambient temperature is read via ADC and included in the speed of sound calculation to compensate measurement results for thermal changes.
Sensor data triggered via One Pulse Mode is processed and results are sent to the serial port terminal via UART.

### 7. `DEM_ACC_ANGLE` - STM32 LIS2DW12 Eğim Ölçer
**TR:**
Proje, LIS2DW12 ivmeölçer sensöründen I2C protokolü ile ham veri okuyarak Roll ve Pitch açılarını hesaplar.
Hesaplanan açı değerleri, ana döngüyü meşgul etmemek adına kesme tabanlı bir UART iletimi ile dış dünyaya aktarılır.
Cihazın eğim durumu belirli eşik değerlerini aştığında uyarı LED'leri aktif hale getirilerek görsel geri bildirim sağlanır.

**EN:**
The project calculates Roll and Pitch angles by reading raw data from the LIS2DW12 accelerometer sensor via the I2C protocol.
Calculated angle values are transmitted externally via interrupt-based UART transmission to avoid stalling the main loop.
Warning LEDs are activated to provide visual feedback when the device's tilt status exceeds certain threshold values.

### 8. `DEM_FREERTOS_STM` - STM32 FreeRTOS Çoklu Görev Sensör Yönetimi
**TR:**
Bu kapsamlı FreeRTOS uygulaması, ADC okuma, İvmeölçer verisi işleme, OLED ekran güncelleme ve UART iletişimi gibi görevleri eş zamanlı yönetir.
Görevler arasındaki veri transferi kuyruklar (Queues) aracılığıyla sağlanırken, paylaşılan donanım kaynakları Mutex ile korunur.
Sistem ayrıca arka planda çalışan bir yazılım zamanlayıcısı ile sensör verilerinden bağımsız görsel animasyonlar yürütür.

**EN:**
This comprehensive FreeRTOS application concurrently manages tasks such as ADC reading, Accelerometer data processing, OLED display updating, and UART communication.
Data transfer between tasks is facilitated via Queues, while shared hardware resources are protected by Mutexes.
The system also executes visual animations independent of sensor data via a software timer running in the background.

### 9. `DEM_CONNECT_WIFI` - ESP32 Wi-Fi & ThingSpeak Menü Sistemi
**TR:**
Arduino altyapısı üzerinde geliştirilen bu proje, ESP32'nin kalıcı hafızasını kullanarak Wi-Fi ve API bilgilerini saklar.
Kullanıcıya seri port üzerinden sunulan interaktif menü sayesinde otomatik bağlantı veya yeni kurulum seçenekleri sunulur.
Bağlantı sağlandığında üretilen sensör verileri, güvenli bir şekilde ThingSpeak bulut platformuna periyodik olarak gönderilir.

**EN:**
Developed on the Arduino infrastructure, this project stores Wi-Fi and API credentials using ESP32's persistent memory.
Automatic connection or new setup options are offered via an interactive menu presented to the user through the serial port.
Once connected, generated sensor data is periodically sent securely to the ThingSpeak cloud platform.

### 10. `DEM_FREERTOS_ESP` - ESP32 UART - MQTT Ağ Geçidi
**TR:**
Bu proje, STM32 gibi harici bir kaynaktan UART üzerinden gelen sensör verilerini alıp MQTT protokolüne dönüştüren bir ağ geçididir.
Gelen veriler ayrıştırılıp JSON formatına çevrildikten sonra belirlenen bir MQTT sunucusuna (Broker) yayınlanır.
Wi-Fi veya MQTT bağlantısında kopma yaşanması durumunda sistem otomatik olarak yeniden bağlanma prosedürlerini devreye sokar.

**EN:**
This project is a gateway that receives sensor data via UART from an external source like STM32 and converts it to the MQTT protocol.
Incoming data is parsed, converted to JSON format, and then published to a specified MQTT Broker.
In case of Wi-Fi or MQTT connection loss, the system automatically activates reconnection procedures.

### 11. `DEM_ESP_MQTT` - ESP-IDF Akıllı Wi-Fi ve MQTT Kurulumu
**TR:**
ESP-IDF ile geliştirilen bu güncel IoT projesi, NVS (Flash) belleği kullanarak ağ kimlik bilgilerini kalıcı olarak saklar.
Sistem açılışında kayıtlı ağlara otomatik bağlanmayı dener veya kullanıcıya interaktif bir kurulum sihirbazı sunar.
Bağlantı başarıyla kurulduğunda rastgele üretilen veriler periyodik olarak yapılandırılmış MQTT konusuna yayınlanır.

**EN:**
Developed with ESP-IDF, this current IoT project persistently stores network credentials using NVS (Flash) memory.
Upon system startup, it attempts to automatically connect to saved networks or offers an interactive setup wizard to the user.
Once the connection is successfully established, randomly generated data is periodically published to the configured MQTT topic.

### 12. `DEM_MCS_CHRONOMETER` - STM32 Master-Slave Timer Kronometre
**TR:**
Bu uygulama, iki adet donanım zamanlayıcısını (TIM3 ve TIM1) zincirleyerek mikro saniye hassasiyetinde çalışan bir kronometre oluşturur.
Master ve Slave modunda çalışan zamanlayıcılar sayesinde yazılım yükü olmadan 32-bit genişliğinde zaman takibi yapılır.
Kullanıcı butonları ile başlatma, durdurma, tur (lap) kaydı alma ve sistemi sıfırlama işlevleri bir durum makinesi ile yönetilir.

**EN:**
This application creates a microsecond-precision chronometer by chaining two hardware timers (TIM3 and TIM1).
Timers operating in Master and Slave modes allow for 32-bit wide time tracking without software overhead.
Start, stop, lap recording, and system reset functions via user buttons are managed by a state machine.