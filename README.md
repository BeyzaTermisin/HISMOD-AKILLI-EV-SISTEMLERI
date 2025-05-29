# HISMOD – Akıllı Ev Güvenlik ve Afet Simülasyon Sistemi

**HISMOD**, Deneyap Kart 1A ile geliştirilen, çoklu sensör destekli bir **akıllı ev güvenlik ve afet farkındalık sistemidir**. Yangın, gaz kaçağı, deprem gibi tehlikeleri erken aşamada tespit ederek kullanıcıyı uyarır. Sistem aynı zamanda **simülasyon temelli farkındalık yaratmayı** amaçlayarak, kullanıcıların bu tehlikelere karşı hazırlıklı olmasını sağlar.

---

## 📌 Proje Amacı

Türkiye gibi afet riski yüksek ülkelerde, bireysel farkındalık ve önlem alma alışkanlığı oldukça düşüktür. HISMOD bu soruna düşük maliyetli, yerel üretimle geliştirilen, kolay kurulabilen bir donanım çözümü sunar:

- � Real-time **tehlike algılama**
- 🔔 Kullanıcıyı **görsel ve işitsel** olarak bilgilendirme
- 🧠 Bireylerde **afet bilinci** oluşturma
- 🎮 Eğitim ve tatbikat amacıyla **simülasyon yapabilme**

---

## 🔩 Donanım Bileşenleri

| Bileşen | Açıklama |
|---------|----------|
| **Deneyap Kart 1A** | ESP32 tabanlı, yerli geliştirilmiş mikrodenetleyici kart |
| **Gaz Sensörü (MQ-9)** | LPG, metan ve karbon monoksit tespiti |
| **Alev Sensörü** | Yangın kaynaklı alevin optik algılanması |
| **Deprem Sensörü (SW-420)** | Titreşim ve sarsıntı algılama |
| **Ultrasonik Sensör (HC-SR04)** | Hareket, yaklaşma ve mesafe algılama |
| **Buzzer** | Tehlike durumlarında sesli uyarı |

---

## 🚀 Sistem Özellikleri

- ✅ **Çoklu Sensör İzleme**: Sensör verileri belirli aralıklarla okunur
- ✅ **Durum Algılama Mantığı**: Eşik değerleri aşıldığında tehlike tipi belirlenir
- ✅ **Interrupt Tabanlı Algılama**: SW-420 deprem sensörü için hızlı tepki
- ✅ **Seri Port Gözlem**: Tüm olaylar Arduino IDE üzerinden anlık olarak takip edilir
- ✅ **Dinamik Uyarı Sistemi**: Her tehlike tipi için farklı sesli uyarı ve konsol çıktısı

---

## 🧠 Sistem Mantığı

Sistem, belirli bir döngüde sensörlerden veri alır. Eşik değerler aşıldığında aşağıdaki mantık çalışır:

```cpp
if (gazDegeri > gazEsik) {
  Serial.println("🚨 GAZ KAÇAĞI ALGILANDI!");
  buzzerUyar();
}
if (alevAlgilandi()) {
  Serial.println("🔥 ALEV ALGILANDI!");
  buzzerUyar();
}
if (depremAlgilandi()) {
  Serial.println("🌍 DEPREM ALGILANDI!");
  buzzerUyar();
}
---

## 🔌 Bağlantı Şeması

### Fritzing Devre Şeması
![Devre Bağlantıları](images/hismod-schema.png)


> ⚠️ **Önemli Not:**  
> Deneyap Kart 3.3V logic seviyesi kullanır. 5V sensörler için:
> - Logic level converter kullanın
> - Veya direnç ile voltaj bölücü devre yapın

---

💻 Yazılım Kurulumu (Arduino IDE)
Gerekli Adımlar:
Arduino IDE (1.8.x veya 2.x) sürümünü indirin

ESP32 kart tanımını ekleyin:

Dosya > Tercihler > Ek Kart Yönetici URL'leri

https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json ekleyin

Araçlar > Kart > Kart Yöneticisi → esp32 → Espressif Systems

Araçlar > Kart > Deneyap Kart 1A seçin

hismod.ino dosyasını açın

Uygun portu seçin ve karta yükleyin

Serial Monitor üzerinden 9600 baud ile çalıştırın

📜 Lisans
Bu proje MIT lisansı altında dağıtılmaktadır. Detaylar için LICENSE dosyasını inceleyebilirsiniz.



