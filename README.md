# 🔈 Analog Elektronik Devreler: 4-Fazlı Ses Yükseltici Devre Tasarımı

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Hardware](https://img.shields.io/badge/Hardware-Audio_Amplifier-blue)
![EDA](https://img.shields.io/badge/EDA-LTspice_%7C_KiCad-orange)

## 📖 Proje Hakkında
Bu proje, "ELE 311 - Analog Elektronik Devreler" dersi kapsamında geliştirilmiş, dört fazdan oluşan uçtan uca bir ses yükseltici (audio amplifier) tasarımıdır. Çalışma; teorik matematiksel analizleri, detaylı SPICE simülasyonlarını, fiziksel breadboard prototiplemesini ve endüstriyel üretim standartlarındaki nihai PCB tasarımını içermektedir.

Elde edilen detaylı analizler, simülasyon verileri ve test sonuçları, ilerleyen dönemde kamera kullanılmadan tamamen bilgisayar grafikleri ve metin-okuma (text-to-speech) araçlarıyla üretilecek teorik elektrik ve elektronik eğitim içeriklerine sağlam bir kaynak oluşturması amacıyla açık kaynak olarak sunulmaktadır.

---

## 🚀 Proje Fazları

### Faz 1: Ortak Emetör (Common Emitter) Katı Tasarımı
- **Amaç:** Ses sinyalini güçlendirmek adına yüksek gerilim kazancı sağlayan ilk katın tasarlanması.
- **Detaylar:** DC çalışma noktası stabilizasyonu, küçük-sinyal (AC) analizi, ve bant geçiren filtre karakteristiği için alt/üst kesim frekans hesaplamaları.
- **Kazanım:** LTspice simülasyonları (.op, .ac, .tran) ile kağıt üzerindeki analitik hesapların (%5 tolerans altında) tam uyuşumunun kanıtlanması.

### Faz 2: Emetör Takipçisi (Emitter Follower) ve Kaskat Yapı
- **Amaç:** Katlar arası yükleme etkisini önlemek için tampon (buffer) katının tasarlanması ve çok katlı kaskat yapıya (Cascade) geçiş.
- **Detaylar:** İki ortak emetör katının ardışıl bağlanması, emetör takipçisi ile empedans uyumunun sağlanması ve uygun kuplaj kapasitörlerinin seçimi.
- **Kazanım:** Sistemin gerilim kazancının hedeflenen seviyelere çıkarılması ve 20 Hz - 20 kHz ses bandı şartlarının eksiksiz karşılanması.

### Faz 3: Sınıf AB (Class AB) Güç Katı ve Gerçek Parametrelere Geçiş
- **Amaç:** 8 Ω empedanslı bir hoparlörü sürebilmek için Sınıf AB push-pull güç katı tasarımı ve ideal $\beta$ değerlerinden piyasadaki gerçek BJT'lere geçiş.
- **Detaylar:** BC546B (Giriş/Ortak Emetör), BD139-16 (Emetör Takipçisi), BD139 ve BD140 (Push-Pull Güç Katı) transistörlerinin sisteme entegrasyonu. Çapraz geçiş (crossover) distorsiyonunun 1N4148 diyot öngerilimlemesi ile yok edilmesi.
- **Kazanım:** Simülasyonlarda 65.5 dB (1883 V/V) toplam kazanç, ~2.5 W çıkış gücü ve distorsiyonsuz, lineer sinyal aktarımının elde edilmesi.

### Faz 4: Fiziksel Gerçekleme, Ölçüm ve PCB Tasarımı
- **Amaç:** Bilgisayar ortamındaki tasarımın fiziksel dünyada doğrulanması ve profesyonel bir donanıma dönüştürülmesi.
- **Detaylar:** Parazitik etkilere karşı breadboard kurulumu, osiloskop ve multimetre ölçümleri ile sistemin test edilmesi. KiCad EDA yazılımı ile iki katmanlı (Top & Bottom), termal tahliye alanlarına (Heat Sink) sahip PCB tasarımının tamamlanması.
- **Kazanım:** İdeal dışı fiziksel koşullarda 0.179 V gibi son derece düşük bir DC ofset, yüksek frekans osilasyonlarından arındırılmış temiz bir çıkış ve Design Rules Check (DRC) onaylı üretim dosyalarının çıkarılması.

---

## 🛠️ Sistem Bileşenleri

* **Giriş ve Ara Kazanç Katı:** `BC546B` (Yüksek $V_{CEO}$ dayanımı ve kararlı akım kazancı için)
* **Sürücü / Buffer Katı:** `BD139-16` (Termal kararlılık ve orta-güç dayanımı için)
* **Güç Katı (Push-Pull):** `BD139` (NPN) & `BD140` (PNP) komplementer çifti
* **Öngerilimleme:** `1N4148` hızlı anahtarlama diyotları
* **Güç Kaynağı:** $\pm15V$ Simetrik Besleme
* **Çıkış Yükü:** $8\Omega$ (Hoparlör eşdeğeri)

---

## 📊 Nihai Performans Tablosu

| Parametre | Proje Hedefi | Gerçekleşen (Fiziksel Ölçüm) |
| :--- | :--- | :--- |
| **Gerilim Kazancı ($A_v$)** | $\ge 1000$ | **1884 V/V (65.5 dB)** |
| **Çıkış Gücü (8 $\Omega$)** | $\ge 2 W$ | **2.1 W** |
| **Düşük Kesim Frekansı ($f_L$)**| $< 20 Hz$ | **17.5 Hz** |
| **Yüksek Kesim Frekansı ($f_H$)**| $\ge 20 kHz$ | **23.5 kHz** |
| **Sistem Güç Tüketimi ($P_S$)** | $< 10 W$ | **1.8 W** |
| **Giriş Empedansı ($R_{in}$)** | - | **17 k$\Omega$** |
| **DC Çıkış Ofseti** | $0 V$ (İdeal) | **0.179 V** |

---

## 🤖 Yapay Zeka Entegrasyonu & Prompt Mühendisliği
Bu proje boyunca modern yapay zeka araçları (Google Gemini & OpenAI ChatGPT), iteratif bir mühendislik danışmanı olarak sürece dahil edilmiştir. Basit soru-cevaplardan ziyade, katı "Prompt Şartnameleri" uygulanmıştır:
1. Gerçek BJT modellerinin datasheet verilerinin yorumlanması ve SPICE modellerinin (.model directive) sentetik olarak oluşturulması.
2. Sınır durum hesaplamalarında (worst-case scenario), güç tüketimi ve maksimum kırpılmasız salınım ($V_{pp}$) limitleri için matematiksel ispatların yaptırılması.
3. Breadboard prototiplemesinde karşılaşılan ısıl kaymalar, direnç tolerans sorunları ve parazitik geri beslemelerin (osilasyon) hata ayıklama (debugging) süreçlerinin yönetilmesi.

## 📝 Lisans
Bu depo, akademik proje süreçlerini belgelemek amacıyla oluşturulmuştur. Şemalar, analizler ve PCB dosyaları, eğitim ve gelişim amacıyla açık kaynak olarak kullanılabilir.
