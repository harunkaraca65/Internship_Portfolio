# Gömülü Sistemler Proje Portföyü / Embedded Systems Project Portfolio

---

## 🇹🇷 Türkçe Özet

Bu depo, STM32 ve ESP32 mikrodenetleyicileri için geliştirilmiş çeşitli gömülü sistem projelerini içerir.
Tüm projeler **'Demedukit'** eğitim ve geliştirme kartı esas alınarak gerçekleştirilmiştir.
Aşağıda projelerin teknik özetleri ve ilgili depo (repository) isimleri yer almaktadır.
**Algoritma akışları, donanım konfigürasyonları ve detaylı açıklamalar için lütfen ilgili deponun içindeki README dosyasına bakınız.**

## 🇬🇧 English Summary

This repository contains various embedded systems projects developed for STM32 and ESP32 microcontrollers.
All projects are implemented based on the **'Demedukit'** education and development board.
Technical summaries of the projects and their corresponding repository names are listed below.
**Please refer to the README file within the respective repository for algorithm flows, hardware configurations, and detailed descriptions.**

---

### 1. `DEM_ACC_ANGLE`
**TR:**
Bu proje, LIS2DW12 ivmeölçer sensöründen I2C protokolü ile ham veri okur.
Okunan verilerden Roll ve Pitch açılarını hesaplar.
Hesaplanan açı değerleri, ana döngüyü meşgul etmemek adına kesme tabanlı bir UART iletimi ile dış dünyaya aktarılır.
Cihazın eğim durumu belirli eşik değerlerini aştığında uyarı LED'leri aktif hale getirilir.

**EN:**
This project reads raw data from the LIS2DW12 accelerometer sensor via the I2C protocol.
It calculates Roll and Pitch angles from the read data.
Calculated angle values are transmitted externally via interrupt-based UART transmission to avoid stalling the main loop.
Warning LEDs are activated when the device's tilt status exceeds certain threshold values.

🔗 **Repo:** [harunkaraca65/DEM_ACC_ANGLE](https://github.com/harunkaraca65/DEM_ACC_ANGLE)

---

### 2. `DEM_ADC_COMPARISON`
**TR:**
Proje, STM32 ADC biriminden veri okumak için dört farklı yöntemi karşılaştırır.
Polling, DMA Normal, DMA Circular ve Timer Trigger yöntemlerini uygular.
Her bir yöntemin işlemci yükü üzerindeki etkisi analiz edilir.
Elde edilen veriler bellekteki tampon dizilere kaydedilerek en uygun okuma stratejisi belirlenir.

**EN:**
The project compares four different methods for reading data from the STM32 ADC unit.
It implements Polling, DMA Normal, DMA Circular, and Timer Trigger methods.
The impact of each method on processor load is analyzed.
Acquired data is saved to buffer arrays in memory to determine the most suitable reading strategy.

🔗 **Repo:** [harunkaraca65/DEM_ADC_COMPARISON](https://github.com/harunkaraca65/DEM_ADC_COMPARISON)

---

### 3. `DEM_UART`
**TR:**
Bu depo, UART iletişimi üzerine kurulu iki ilişkili projeyi (STM32 ve ESP32) barındırır.
**ESP32 Tarafı:** ESP-IDF üzerinde çalışan asenkron bir yapı sunar; RX ve TX işlemleri için bağımsız FreeRTOS görevleri kullanır.
**STM32 Tarafı:** FreeRTOS üzerinde çalışan senkron bir yapı sunar ve ESP32 ile "El Sıkışma" (Handshake) protokolü yürütür.
İki proje birbiriyle haberleşerek veri akışını ve senkronizasyonu test eder.

**EN:**
This repository hosts two related projects (STM32 and ESP32) based on UART communication.
**ESP32 Side:** Presents an asynchronous structure on ESP-IDF; uses independent FreeRTOS tasks for RX and TX operations.
**STM32 Side:** Presents a synchronous structure on FreeRTOS and executes a "Handshake" protocol with the ESP32.
The two projects communicate with each other to test data flow and synchronization.

🔗 **Repo:** [harunkaraca65/DEM_UART](https://github.com/harunkaraca65/DEM_UART)

---

### 4. `DEM_HC-SR04`
**TR:**
Bu uygulama, HC-SR04 sensörü ile hassas mesafe ölçümü yapar.
Donanım zamanlayıcılarının Input Capture özelliğini kullanır.
Ortam sıcaklığı ADC üzerinden okunarak ses hızı hesaplamasına dahil edilir.
Ölçüm sonuçları termal değişimlere göre kompanze edilerek UART üzerinden gönderilir.

**EN:**
This application performs precise distance measurement with the HC-SR04 sensor.
It uses the Input Capture feature of hardware timers.
Ambient temperature is read via ADC and included in the speed of sound calculation.
Measurement results are compensated for thermal changes and sent via UART.

🔗 **Repo:** [harunkaraca65/DEM_HC-SR04](https://github.com/harunkaraca65/DEM_HC-SR04)

---

### 5. `DEM_LOW_POWER`
**TR:**
Bu proje, STM32'nin düşük güç modlarına (Sleep, Stop, Standby) giriş ve çıkış süreçlerini test eder.
RTC (Gerçek Zamanlı Saat) alarmı, işlemciyi derin uyku durumlarından uyandırmak için tetikleyici olarak kullanılır.
Döngüsel olarak değişen güç modları ve sistem durumu LED göstergeleri ile izlenir.

**EN:**
This project tests the entry and exit processes for STM32's low-power modes (Sleep, Stop, Standby).
The RTC (Real-Time Clock) alarm is used as a trigger to wake the processor from deep sleep states.
Cyclically changing power modes and system status are monitored via LED indicators.

🔗 **Repo:** [harunkaraca65/DEM_LOW_POWER](https://github.com/harunkaraca65/DEM_LOW_POWER)

---

### 6. `DEM_THINKSPEAK`
**TR:**
Arduino altyapısı üzerinde geliştirilen bu proje, ESP32 için bir IoT menü sistemidir.
Kalıcı hafızayı (Preferences) kullanarak Wi-Fi ve API bilgilerini saklar.
Seri port üzerinden sunulan interaktif menü ile otomatik bağlantı veya yeni kurulum seçenekleri sunar.
Bağlantı sağlandığında sensör verilerini ThingSpeak bulut platformuna gönderir.

**EN:**
Developed on the Arduino infrastructure, this project is an IoT menu system for ESP32.
It stores Wi-Fi and API credentials using persistent memory (Preferences).
Offers automatic connection or new setup options via an interactive menu presented through the serial port.
Sends sensor data to the ThingSpeak cloud platform once connected.

🔗 **Repo:** [harunkaraca65/DEM_THINKSPEAK](https://github.com/harunkaraca65/DEM_THINKSPEAK)

---

### 7. `DEM_MQTT`
**TR:**
ESP-IDF ile geliştirilen bu güncel IoT projesi, NVS (Flash) belleği kullanarak ağ bilgilerini saklar.
Sistem açılışında kayıtlı ağlara otomatik bağlanmayı dener veya kullanıcıya interaktif bir kurulum sihirbazı sunar.
Bağlantı başarıyla kurulduğunda rastgele üretilen veriler yapılandırılmış MQTT konusuna yayınlanır.

**EN:**
Developed with ESP-IDF, this current IoT project stores network credentials using NVS (Flash) memory.
Upon startup, it attempts to automatically connect to saved networks or offers an interactive setup wizard to the user.
Once the connection is established, randomly generated data is published to the configured MQTT topic.

🔗 **Repo:** [harunkaraca65/DEM_MQTT](https://github.com/harunkaraca65/DEM_MQTT)

---

### 8. `DEM_FREERTOS`
**TR:**
Bu depo, hem STM32 hem de ESP32 için gelişmiş FreeRTOS uygulamalarını içerir.
**STM32 Tarafı:** ADC, İvmeölçer, OLED ekran ve UART görevlerini yöneten çoklu görev (multitasking) sensör sistemidir; Mutex ve Kuyruk yapılarını kullanır.
**ESP32 Tarafı:** STM32'den UART ile gelen veriyi alıp JSON formatına çeviren ve MQTT üzerinden sunucuya ileten bir "Ağ Geçidi" (Gateway) yazılımıdır.
İki proje birleşerek uçtan uca (STM32 -> ESP32 -> Bulut) bir IoT sistemini oluşturur.

**EN:**
This repository contains advanced FreeRTOS applications for both STM32 and ESP32.
**STM32 Side:** A multitasking sensor system managing ADC, Accelerometer, OLED display, and UART tasks; utilizes Mutex and Queue structures.
**ESP32 Side:** A "Gateway" software that receives data via UART from STM32, converts it to JSON, and transmits it via MQTT.
The two projects combine to form an end-to-end (STM32 -> ESP32 -> Cloud) IoT system.

🔗 **Repo:** [harunkaraca65/DEM_FREERTOS](https://github.com/harunkaraca65/DEM_FREERTOS)

---

### 9. `DEM_MCS_CHRONOMETER`
**TR:**
Bu uygulama, iki adet donanım zamanlayıcısını (Master-Slave) zincirleyerek mikro saniye hassasiyetinde çalışan bir kronometre oluşturur.
Zamanlayıcıların donanımsal zincirlenmesi sayesinde yazılım yükü olmadan 32-bit genişliğinde zaman takibi yapılır.
Başlatma, durdurma, tur (lap) kaydı alma ve sistemi sıfırlama işlevleri bir durum makinesi ile yönetilir.

**EN:**
This application creates a microsecond-precision chronometer by chaining two hardware timers (Master-Slave).
Hardware chaining allows for 32-bit wide time tracking without software overhead.
Start, stop, lap recording, and system reset functions are managed by a state machine.

🔗 **Repo:** [harunkaraca65/DEM_MCS_CHRONOMETER](https://github.com/harunkaraca65/DEM_MCS_CHRONOMETER)

---

### 10. `DEM_MODBUS`
**TR:**
Bu yazılım, RTOS kullanmadan SysTick ve kesmeler üzerine kurulu modüler bir Modbus RTU Slave uygulamasıdır.
Protokol işleme, uygulama mantığı ve donanım sürücüleri birbirinden izole edilmiştir.
Ana döngü engellemesiz (non-blocking) çalışarak sensör okuma ve iletişim görevlerini eş zamanlı yürütür.

**EN:**
This software is a modular Modbus RTU Slave application built on SysTick and interrupts without using RTOS.
Protocol processing, application logic, and hardware drivers are isolated from each other.
The main loop operates in a non-blocking manner to execute sensor reading and communication tasks concurrently.

🔗 **Repo:** [harunkaraca65/DEM_MODBUS](https://github.com/harunkaraca65/DEM_MODBUS)

---