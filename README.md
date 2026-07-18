# **Takım İsmi**

YZTA Grup 8

# Ürün İle İlgili Bilgiler

## Takım Elemanları

- Enise Cömet: Scrum Master — Hat A (AI/Orkestrasyon, dilekçe üretimi)
- Ahmet Kavruk: Product Owner — Bilgi Tabanı & İçerik
- Aleyna Tandoğan: Developer — Hat A (AI/Orkestrasyon, sınıflandırma)
- İlayda Yılmaz: Developer — Hat B (Frontend)
- Himmet Can Umutlu: Developer — Hat C (Veri & QA)

## Ürün İsmi

**Hak Pusulası**

## Ürün Açıklaması

- Hak Pusulası, vatandaşın günlük dille anlattığı bir derdi (iade, abonelik iptali, kira, komşu, kamu hizmeti şikâyeti vb.) alıp; hangi mercie, hangi belgelerle, hangi süre içinde başvuracağını belirleyen çok-ajanlı bir yapay zekâ asistanıdır. Kullanıcıya resmi üslupta hazır bir dilekçe ve adım adım yol haritası üretir.

## Ürün Özellikleri

- Yazılı ve sesli giriş
- Otomatik dert sınıflandırma ve doğru mercie yönlendirme
- Eksik bilgiyi soran çok adımlı, hafızalı ajan
- RAG destekli resmi dilekçe / ihtarname / başvuru metni üretimi
- Adım adım yol haritası + belge kontrol listesi + süre uyarısı
- Çıktı öncesi otomatik eksiklik doğrulaması

## Hedef Kitle

- Tüketici uyuşmazlığı yaşayanlar (online iade, ayıplı mal, abonelik iptali)
- Kiracılar ve ev sahipleri
- Kamu hizmetinden şikâyetçi olan vatandaşlar
- Hukuki dile yabancı, yaşlı veya düşük okuryazarlıktaki kullanıcılar

## Kullanılan Teknolojiler

- **Arayüz:** Lovable / Netlify
- **Orkestrasyon:** n8n (local)
- **Yapay Zekâ:** Google Gemini
- **Bilgi Tabanı:** Google Sheets
- **Veritabanı:** Supabase

## Product Backlog URL

[GitHub Projects Board](https://github.com/users/enisecmt/projects/1)

> **Sorumluluk Reddi:** Bu uygulama hukuki tavsiye vermez. Ürettiği metinler bilgilendirme amaçlı taslaklardır; resmi işlemler öncesi yetkili bir uzmana danışılması önerilir.

---

# Sprint 1

- **Sprint Notları:** Sprint hedefimiz, kullanıcının günlük dille yazdığı bir derdi alıp doğru mercii belirleyen ve resmi bir dilekçe üreten, uçtan uca çalışan temel bir MVP ortaya çıkarmaktır. (19 Haziran – 5 Temmuz)

- **Sprint içinde tamamlanması tahmin edilen puan:** 39

- **Puan tamamlama mantığı:** Story'ler Fibonacci yöntemiyle (1, 2, 3, 5, 8) puanlanmıştır. Her story'nin puanı, sprint toplam puanının (39) yarısından azdır ve seçilen story'lerin toplamı sprint kapasitesini aşmamaktadır.

- **Backlog düzeni ve Story seçimleri:** Backlog'umuz ilk yapılacak story'lere göre düzenlenmiştir. Sprint başına tahmin edilen puanı geçmeyecek şekilde sıradan seçimler yapılmaktadır. Story başına çıkan tahmin puanı, toplam puanın yarısından az tutulmuştur.

  Story'ler yapılacak işlere (task'lere) bölünmüştür. Görevler her story issue'sunun içinde checklist olarak takip edilmektedir; "Story" etiketli kartlar GitHub Projects board'unda yer almaktadır.

- **Daily Scrum:** Daily Scrum toplantılarının zamansal sebeplerden ötürü WhatsApp üzerinden yazılı yapılmasına karar verilmiştir. Detaylı günlük kayıtlar: [Sprint 1 Daily Scrum Notları](ProjectManagement/Sprint1Documents/DailyScrumMeetingNotesSprint1.pdf)

- **Sprint board update:**
  ![Sprint 1 Board](ProjectManagement/Sprint1Documents/sprint1-board.png)
  ![Sprint 1 Board Güncelleme](ProjectManagement/Sprint1Documents/sprint1-board2.png)

- **Ürün Durumu:** Ekran görüntüleri:

  **Arayüz (Lovable + Netlify):**
  ![Giriş Ekranı](ProjectManagement/Sprint1Documents/arayuz-1-giris.png)
  ![Kategori Seçimi](ProjectManagement/Sprint1Documents/arayuz-2-kategori.png)
  ![Girdi Ekranı](ProjectManagement/Sprint1Documents/arayuz-3-girdi.png)
  ![Analiz Ekranı](ProjectManagement/Sprint1Documents/arayuz-4-analiz.png)
  ![Netlify - Girdi](ProjectManagement/Sprint1Documents/arayuz-netlify-girdi.png)
  ![Netlify - Kategori](ProjectManagement/Sprint1Documents/arayuz-netlify-kategori.png)

  **Bilgi Tabanı (Google Sheets):**
  ![Bilgi Tabanı 1](ProjectManagement/Sprint1Documents/bilgi-tabani.png)
  ![Bilgi Tabanı 2](ProjectManagement/Sprint1Documents/bilgi-tabani2.png)

  **Dilekçe Üretim Testleri (AI Studio):**
  ![Online İade Testi](ProjectManagement/Sprint1Documents/dilekce-test-1-onlineiade.png)
  ![Tüketici Hakem Heyeti Testi](ProjectManagement/Sprint1Documents/dilekce-test-2-hakemheyeti.png)
  ![Abonelik İptali Testi](ProjectManagement/Sprint1Documents/dilekce-test-3-abonelik.png)

  **Sınıflandırma Testleri:**
  ![Sınıflandırma Testi 1](ProjectManagement/Sprint1Documents/sınıflandırma-testi.png)
  ![Sınıflandırma Testi 2](ProjectManagement/Sprint1Documents/sınıflandırma-testi2.png)
  ![Sınıflandırma Testi 3](ProjectManagement/Sprint1Documents/sınıflandırma-testi3.png)
  ![Sınıflandırma Testi 4](ProjectManagement/Sprint1Documents/sınıflandırma-testi4.png)

  **n8n + Gemini Uçtan Uca Bağlantı Testi:**
  ![n8n Webhook Testi](ProjectManagement/Sprint1Documents/n8n-webhook-test.png)

- **Sprint Review:**

  Sprint 1 boyunca ürünün tüm temel bileşenleri ayrı ayrı geliştirildi ve doğrulandı:
  - Bilgi tabanı (6 dert türü + mercii/mevzuat/süre bilgileri) Google Sheets'te oluşturuldu.
  - Dilekçe üretim prompt'u AI Studio üzerinde 3 farklı dert türüyle test edildi, tutarlı ve kaliteli sonuçlar alındı.
  - Dert sınıflandırma prompt'u geliştirildi ve test edildi; kullanıcı metnini doğru kategoriye atayabiliyor.
  - n8n ile Gemini API arasındaki bağlantı (webhook → Gemini → cevap) başarıyla kuruldu ve doğrulandı.
  - Arayüz (Lovable + Netlify) 3 adımlı akışla (kategori seçimi → sorun girdisi → sonuç) tasarlandı ve yayınlandı.
  - Veri yapısı (Supabase) kuruldu, bilgi tabanı içeriğiyle entegre edildi, test senaryoları hazırlandı.

  **Alınan kararlar:**
  - Bileşenlerin birbirine bağlanması (arayüzün n8n akışına canlı bağlanması) Sprint 2'nin başına taşınmıştır. Sebep: n8n şu an local ortamda çalışmaktadır ve arayüz (Netlify üzerinde canlı) local adrese ulaşamamaktadır; bu bağlantı için gerekli çözüm (genel erişime açma) Sprint 2'de uygulanacaktır.
  - Bilgi tabanındaki 6 dert türünün tamamı için gerçek dilekçe şablon metinleri Sprint 2'de tamamlanacaktır; öncelik en sık kullanılan kategorilere verilmiştir.
  - Sınıflandırma akışının n8n içinde bilgi tabanıyla (mercii/mevzuat eşleştirmesi) tam entegrasyonu Sprint 2'ye taşınmıştır.
  - n8n barındırma kararı (Cloud/self-host) Sprint 2 başında netleştirilecektir.

  **Sprint Review katılımcıları:** Ahmet Kavruk, Enise Cömet, Aleyna Tandoğan, İlayda Yılmaz, Himmet Can Umutlu

- **Sprint Retrospective:**
  - İyi giden: AI Studio üzerinden hızlı prototipleme sayesinde n8n kurulumu beklenmeden prompt kalitesi (dilekçe üretimi ve sınıflandırma) erken doğrulandı; bu, riskin erken görülmesini sağladı.
  - İyi giden: Ekip üyeleri birbirinden bağımsız alanlarda (bilgi tabanı, arayüz, veri yapısı) paralel ilerleyebildi, birbirini beklemek zorunda kalmadı.
  - Zorlanılan: Gemini API kurulumunda beklenmeyen bir kota sorunu (limit: 0 hatası) zaman kaybettirdi; bu, ekip kontrolünde olmayan bir platform sorunuydu.
  - Zorlanılan: Local geliştirme ortamının (n8n) canlı arayüzle bağlantısı planlanandan daha geç fark edilen bir teknik detaydı.
  - Sonraki sprintte değiştirilecek: Entegrasyon adımları (servisler arası bağlantı) sprint başında, ayrı geliştirmeden önce planlanacak.
  - Sonraki sprintte değiştirilecek: Altyapı kurulumlarına (API, hesap, bağlantı testleri) daha fazla tampon süre ayrılacak.
  - Sonraki sprintte değiştirilecek: Tahmin puanları sprint planlamada daha gerçekçi gözden geçirilecek.

---

# Sprint 2

- **Sprint Notları:** Sprint 2 hedefimiz, ürünü temel MVP'den akıllı asistana taşımaktır: hafıza (eksik bilgiyi kullanıcıya sorma), RAG (dilekçeyi gerçek mevzuata dayandırma), çok-ajan orkestrasyon, sesli giriş ve adım adım yol haritası çıktısı. (6 – 19 Temmuz 2026)

- **Sprint içinde tamamlanması tahmin edilen puan:** 53

- **Puan tamamlama mantığı:** Story'ler Fibonacci yöntemiyle (5, 8) puanlanmıştır. Her story'nin puanı, sprint toplam puanının (53) yarısından azdır ve seçilen story'lerin toplamı sprint kapasitesini aşmamaktadır.

- **Backlog düzeni ve Story seçimleri:** Sprint 1'de yarım kalan işler (şablon metinleri, mercii eşleştirme, uçtan uca test) Sprint 2 story'lerine taşınmıştır. Bu sprintte yapay zekâ katmanları (hafıza, RAG, çok-ajan, ses) öncelik almaktadır. Görevler her story issue'sunun içinde checklist olarak takip edilmektedir.

- **Çalışma prensibi:** n8n Cloud'un 14 günlük denemesi final teslimine (2 Ağustos) denk gelecek şekilde Sprint 3 başında aktive edilecektir. Bu nedenle Sprint 2 boyunca tüm ajan mantığı local n8n ve AI Studio üzerinde geliştirilip manuel olarak test edilmektedir; canlı arayüz-backend bağlantısı Sprint 3'e planlanmıştır.

- **Daily Scrum:** [Sprint 2 Daily Scrum Notları](ProjectManagement/Sprint2Documents/DailyScrumMeetingNotesSprint2.pdf)

- **Sprint board update:**
  ![Sprint 2 Board 1](ProjectManagement/Sprint2Documents/sprint2-board-1.png)
  ![Sprint 2 Board 2](ProjectManagement/Sprint2Documents/sprint2-board-2.png)
  ![Sprint 2 Board Güncel 1](ProjectManagement/Sprint2Documents/sprint2-board-3.png)
  ![Sprint 2 Board Güncel 2](ProjectManagement/Sprint2Documents/sprint2-board-4.png)
  ![Sprint 2 Board Güncel 3](ProjectManagement/Sprint2Documents/sprint2-board-5.png)

- **Ürün Durumu:** Ekran görüntüleri ve testler:

  **Arayüz v2 (Lovable):**
  ![Giriş](ProjectManagement/Sprint2Documents/arayuz-v2-giris.png)
  ![Kategori Seçimi](ProjectManagement/Sprint2Documents/arayuz-v2-kategori.png)
  ![Sorun Yazma](ProjectManagement/Sprint2Documents/arayuz-v2-sorun.png)
  ![Sesli Giriş](ProjectManagement/Sprint2Documents/arayuz-v2-sesli-giris.jpeg)
  ![Diyalog (Soru-Cevap)](ProjectManagement/Sprint2Documents/arayuz-v2-diyalog.png)
  ![Dilekçe Çıktısı 1](ProjectManagement/Sprint2Documents/arayuz-v2-dilekce.png)
  ![Dilekçe Çıktısı 2](ProjectManagement/Sprint2Documents/arayuz-v2-dilekce2.png)
  ![Yol Haritası Ekranı](ProjectManagement/Sprint2Documents/arayuz-v2-yolharitasi.png)
  ![Geçmiş Talepler](ProjectManagement/Sprint2Documents/arayuz-v2-gecmis.png)

  **Hafızalı Diyalog (n8n + Supabase):**
  Kullanıcı bir konuşma başlatıp eksik bilgi verdiğinde sistem soruyor, cevapları hatırlıyor ve tam çıktı üretiyor. Akış local n8n üzerinde Supabase'e bağlı olarak çalışmaktadır.
  ![n8n Tüm Node'lar Çalışıyor](ProjectManagement/Sprint2Documents/hafiza-n8n-tum-node-yesil.png)
  ![n8n Geçmiş Okundu](ProjectManagement/Sprint2Documents/hafiza-n8n-gecmis-okundu.png)
  Workflow dosyası: [Hak_Pusulasi_Hafizali_Diyalog.json](ProjectManagement/Sprint2Documents/Hak_Pusulasi_Hafizali_Diyalog.json)

  **RAG (Bilgi Tabanına Dayalı Üretim) + Çok-Ajan Orkestrasyonu:**
  Sistem, kullanıcının derdini sınıflandırdıktan sonra Supabase'deki bilgi tabanından ilgili kategorinin doğrulanmış bilgisini (yetkili merci, süre, gerekli belgeler) otomatik çekip dilekçe ve yol haritası üretimine kaynak olarak vermektedir. Böylece çıktı, modelin ezberine değil gerçek bilgi tabanına dayanır. Akış, farklı görevlere sahip AI bileşenlerinin (sınıflandırıcı → bilgi getirici → dilekçe/yol haritası yazarı) tek bir zincirde koordineli çalıştığı çok-ajan yapısındadır.

  ![RAG - Çok-Ajan Zinciri (Tüm Node'lar)](ProjectManagement/Sprint2Documents/rag-tum-node-yesil.png)
  ![RAG - Bilgi Tabanından Veri Çekme](ProjectManagement/Sprint2Documents/rag-bilgi-getir-cikti.png)
  ![RAG - Bilgi Birleştirme](ProjectManagement/Sprint2Documents/rag-bilgi-birlestir-cikti.png)
  ![RAG - Dilekçe Çıktısı 1](ProjectManagement/Sprint2Documents/rag-dilekce-cikti.png)
  ![RAG - Dilekçe Çıktısı 2](ProjectManagement/Sprint2Documents/rag-dilekce-cikti2.png)

  Farklı kategorilerde (Online Alışveriş, Kira, Abonelik, Bilgi Edinme) yapılan RAG testleri: [rag-testleri.md](ProjectManagement/Sprint2Documents/rag-testleri.md)

  Güncel workflow (hafıza + RAG): [Hak_Pusulasi_Hafizali_RAG.json](ProjectManagement/Sprint2Documents/Hak_Pusulasi_Hafizali_RAG.json)

  **Prompt Testleri (AI Studio):**
  ![Slot-Filling (Eksik Bilgi Sorma)](ProjectManagement/Sprint2Documents/slot-filling-test.png)
  ![Hafızalı Diyalog Testi 1](ProjectManagement/Sprint2Documents/hafiza-diyalog-test1.png)
  ![Hafızalı Diyalog Testi 2](ProjectManagement/Sprint2Documents/hafiza-diyalog-test2.png)
  Yol haritası üretim testleri: [yol-haritasi-testleri.md](ProjectManagement/Sprint2Documents/yol-haritasi-testleri.md)

- **Sprint Review:** <!-- Sprint sonunda doldurulacak -->
  Alınan kararlar:
  Sprint Review katılımcıları:

- **Sprint Retrospective:** <!-- Sprint sonunda doldurulacak -->
  -

---

# Sprint 3

---
