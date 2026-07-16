## Yol Haritası Üretim Testleri — AI Studio (Gemini)

**Amaç:** Sprint 2, Story #11 "Yol haritası çıktısı üret" kapsamında, sistemin dilekçeyle birlikte kullanıcıya adım adım bir başvuru yol haritası (ne yapmalı, hangi belgeler, süreler, sonuç alınamazsa üst mercii) üretip üretemediğini doğrulamak için 3 farklı dert türüyle test yapılmıştır.

**Yöntem:** n8n entegrasyonundan önce, prompt mantığı doğrudan Google AI Studio üzerinde test edilmiştir. Her testte dert türü, doğru mercii ve örnek bir kullanıcı durumu verilerek yol haritası ürettirilmiştir.

**Not:** İlk testte (online iade) kullanıcının belirtmediği bir varsayım (sürenin 1 gün aşılmış olması) modele eklenmiştir. Durumun net verildiği 2. ve 3. testlerde bu görülmemiştir. Bu gözlem, Sprint 2'deki hafızalı soru-cevap (slot-filling) ve RAG çalışmalarının gerekliliğini doğrulamaktadır: sistem eksik bilgi aldığında varsayım üretme eğilimindedir; slot-filling bu boşluğu kullanıcıya sorarak, RAG ise çıktıyı gerçek kaynağa dayandırarak kapatacaktır.

---

## Test 1 — Online Alışveriş / Cayma-İade

**Girdi:** "15 gün önce aldığım kazağı iade etmek istiyorum ama satıcı reddediyor."

**Çıktı:**

```
1. ADIM ADIM NE YAPMALI?
1. İletişim Kayıtlarını Kontrol Edin: Satıcıya iade talebinizi ilk ne zaman
   ilettiniz? 14. gün dolmadan talep açtıysanız haklısınız. Mesajın ekran
   görüntüsünü alın.
2. Cayma Hakkınızı Hatırlatın: Satıcıya "Mesafeli Sözleşmeler Yönetmeliği
   gereği 14 günlük cayma hakkımı kullanmak istiyorum, aksi halde Tüketici
   Hakem Heyeti'ne başvuracağım" deyin.
3. Kargoya Vermeyi Deneyin: Sistemden iade kodu alabiliyorsanız ürünü hemen
   kargolayın.
4. E-Devlet Üzerinden Şikayet Edin: Satıcı reddediyorsa doğrudan Tüketici
   Hakem Heyeti'ne başvurun.

2. GEREKLİ BELGELER
- [ ] Fatura veya Satış Fişi
- [ ] Sipariş Özeti (Siparişlerim ekran görüntüsü)
- [ ] İade Talebi Ekran Görüntüsü
- [ ] Kargo Teslim Fişi

3. SÜRE / SON TARİH UYARISI
- 14 Gün Kuralı: İade hakkı teslim tarihinin ertesi başlar, 14 takvim günü sürer.
- İstisna: Satıcı cayma hakkı bilgisini yazılı vermediyse süre 1 yıla kadar uzar.
- Hafta Sonu Notu: 14. gün pazar/resmi tatile denk gelirse süre bir sonraki iş
  gününe uzar.

4. SONUÇ ALINAMAZSA (Tüketici Hakem Heyeti)
- TÜBİS'e (e-Devlet) girin, formu doldurun, belgeleri yükleyin, talebinizi yazın.
- Hakem Heyeti kararları mahkeme kararı gibidir, 3-6 ayda sonuçlanır, ücretsizdir.
```

---

## Test 2 — Kira / Depozito İadesi

**Girdi:** "Evden çıkalı 2 ay oldu, ev sahibi depozitomu geri vermiyor, hiçbir hasar da yoktu."

**Çıktı:**

```
1. ADIM ADIM NE YAPMALI?
1. Son Bir "Yazılı" Uyarı Yapın: Ev sahibine "Evi hasarsız teslim edeli 2 ay
   oldu. Depozitomu 3 gün içinde [IBAN] hesabıma yatırın, aksi halde yasal
   yollara başvuracağım" mesajı atın (delil olur).
2. Noterden İhtarname Gönderin: Ödeme yapmazsa notere gidip resmi ihtarname çekin.
3. Arabulucuya Başvurun: Adliyedeki Arabuluculuk Bürosuna gidin; kira
   uyuşmazlıklarında arabuluculuk artık zorunludur, ücretsizdir.
4. Toplantıya Katılın: Uzlaşırsanız konu kapanır, uzlaşamazsanız tutanak verilir.

2. GEREKLİ BELGELER
- [ ] Kira Sözleşmesi (depozito miktarının yazılı olduğu sayfa)
- [ ] Banka Dekontu (depozitoyu ödediğinize dair)
- [ ] Evin Teslim Fotoğrafları/Videosu
- [ ] Anahtar Teslim Tutanağı (veya mesaj kayıtları)
- [ ] Noter İhtarnamesi (gönderildiyse)

3. SÜRE / SON TARİH UYARISI
- 3 Aylık Süre: Ev sahibi dava/icra başlatmadıysa depozitoyu en geç 3 ayda iade
  etmek zorundadır; 2 ayınız dolmuş, uygun zamandasınız.
- Zamanaşımı: Depozito alacağı için 10 yıl süreniz var.

4. SONUÇ ALINAMAZSA (Sulh Hukuk Mahkemesi)
- Arabuluculuktan "anlaşamadık" tutanağıyla dava açabilirsiniz.
- Haklı çıkarsanız mahkeme masrafı, avukat ücreti ve faizi ev sahibi öder.
```

---

## Test 3 — Abonelik İptali / Haksız Tahsilat

**Girdi:** "İnternet abonemi iptal etmek istedim ama firma sürekli oyalıyor, her ay ücret kesilmeye devam ediyor."

**Çıktı:**

```
1. ADIM ADIM NE YAPMALI?
1. E-Devlet Üzerinden İptal Edin: "Abonelik Fesih Başvurusu" ile firmayı seçip
   kimlik doğrulamasıyla iptal talebinizi yapın. Firma "haberimiz yoktu" diyemez.
2. Modem ve Cihazları İade Edin: Yetkili bayiye götürüp "Cihaz Teslim Tutanağı"
   alın.
3. BTK'ya Şikayet Yazın: "BTK Tüketici Şikayet Bildirim Sistemi"ne girip durumu
   anlatın. Firmalar BTK denetiminden korktuğu için genelde 10 günde çözer.
4. Otomatik Ödemeyi İptal Edin: Bankadan bu firmaya ait otomatik ödeme talimatını
   kaldırın.

2. GEREKLİ BELGELER
- [ ] E-Devlet İptal Başvuru No / Ekran Görüntüsü
- [ ] Cihaz Teslim Tutanağı
- [ ] Haksız Kesilen Faturalar
- [ ] Müşteri Hizmetleri Kayıtları (varsa)

3. SÜRE / SON TARİH UYARISI
- 24 Saat Kuralı: Firma iptal talebinden sonra 24 saatte hizmeti durdurmalıdır.
- 7 Gün Kuralı: En geç 7 günde aboneliği sonlandırıp yazılı bilgi vermelidir.
- Fatura Kesimi: Talep sonrası kullanılan günler için ücret talep edilemez.

4. SONUÇ ALINAMAZSA (Tüketici Hakem Heyeti)
- TÜBİS üzerinden başvurup "haksız tahsil edilen paraların iadesi ve borçların
  silinmesi"ni talep edin.
- Haklı bulunursanız firma ödemek zorundadır; ödemezse icraya verebilirsiniz.
```

---

## Genel Sonuç

3 farklı dert türünde de sistem:
- Doğru mercii zincirini (ilk mercii → üst mercii) belirledi
- Somut, eyleme dönük adımlar ve gerçek prosedür bilgisi (e-Devlet/TÜBİS/BTK, yasal süreler) verdi
- Belge kontrol listesini `- [ ]` formatında üretti
- Hukuki dile yabancı bir kullanıcının anlayacağı sadelikte yazdı

Bu testler, Story #11'in "yol haritası çıktısı" bileşeninin prompt seviyesinde çalıştığını doğrular. Sonraki adım: slot-filling (eksik bilgi sorma) ve RAG ile çıktının gerçek kaynağa bağlanması.
