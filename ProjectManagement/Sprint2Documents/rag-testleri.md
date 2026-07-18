## RAG (Bilgi Tabanına Dayalı Üretim) Testleri — n8n + Supabase

**Amaç:** Sprint 2 kapsamında, sistemin kullanıcının derdini sınıflandırdıktan sonra Supabase'deki `bilgi_tabani` tablosundan ilgili kategorinin doğrulanmış bilgisini (yetkili merci, başvuru süresi, gerekli belgeler) otomatik çekip dilekçe/yol haritası üretimine kaynak olarak verdiğini doğrulamak.

**Yöntem:** Vektörsüz RAG. Sınıflandırma bileşeni kategoriyi 6 sabit değerden birine atar; "Bilgi Getir" node'u bu kategoriyle Supabase `bilgi_tabani` tablosundan ilgili satırı çeker; "Bilgi Birleştir" node'u bu doğrulanmış bilgiyi dilekçe üretim prompt'una "DOĞRULANMIŞ BİLGİ TABANI" olarak ekler. Böylece çıktı, modelin ezberine değil gerçek bilgi tabanına dayanır.

**Not:** Vektör araması ve embedding kullanılmamıştır. Bilgi tabanı küçük ve kategoriler net olduğu için, sınıflandırmanın bulduğu kategoriyle doğrudan tablo eşleştirmesi hem yeterli hem daha güvenilirdir (yanlış belge getirme riski yoktur).

Aşağıdaki 4 farklı kategoride yapılan testlerde, her seferinde sınıflandırma kategoriyi tabloyla eşleşecek şekilde belirledi ve "Bilgi Getir" ilgili satırı sorunsuz çekti.

---

### Test 1 — Online Alışveriş

**Girdi:** "Trendyol'dan aldığım kazağı iade etmek istiyorum, satıcı reddediyor."

**Sınıflandırma kategorisi:** Online Alışveriş

**Bilgi tabanından çekilen (RAG):**
- Yetkili merci: Satıcı
- Başvuru süresi: Satıcıya göre
- Gerekli belgeler: Fatura
- (İlgili alt kategoriler: Cayma Hakkı, İade Talebinin Reddedilmesi)

**Sonuç:** Dilekçe çıktısında gerekli belgeler arasında "fatura" ilk sırada yer aldı; yol haritası TÜBİS / Tüketici Hakem Heyeti sürecine yönlendirdi. Çıktı bilgi tabanıyla tutarlı.

---

### Test 2 — Kira

**Girdi:** "Ev sahibim depozitomu geri vermiyor, evden çıkalı 2 ay oldu."

**Sınıflandırma kategorisi:** Kira

**Bilgi tabanından çekilen (RAG):**
- Yetkili merci: Kiracı
- Başvuru süresi: Duruma göre
- Gerekli belgeler: Kira sözleşmesi, Deliller
- (İlgili alt kategoriler: Kira Borcu, Sözleşmeye Aykırılık)

**Sonuç:** Sınıflandırma, dava öncesi arabuluculuk zorunluluğunu (7036 sayılı Kanun) doğru belirtti; birincil ve alternatif merciler (Arabuluculuk, Sulh Hukuk Mahkemesi) tutarlı geldi.

---

### Test 3 — Abonelik

**Girdi:** "İnternet aboneliğimi iptal etmek istedim ama firma sürekli oyalıyor."

**Sınıflandırma kategorisi:** Abonelik

**Bilgi tabanından çekilen (RAG):**
- Yetkili merci: Hizmet Sağlayıcı
- Başvuru süresi: Sözleşmeye göre
- Gerekli belgeler: Sözleşme
- (İlgili alt kategoriler: İptal Talebi, İptalin Reddedilmesi — BTK)

**Sonuç:** Sistem e-Devlet üzerinden fesih sürecini ve sonuç alınamazsa Tüketici Hakem Heyeti'ni doğru sıraladı; ilgili yönetmeliğe atıf yaptı.

---

### Test 4 — Bilgi Edinme Hakkı

**Girdi:** "Belediyeden bilgi talep ettim ama cevap vermiyorlar."

**Sınıflandırma kategorisi:** Bilgi Edinme Hakkı

**Bilgi tabanından çekilen (RAG):**
- Yetkili merci: İlgili Kamu Kurumu
- Başvuru süresi: Sınır yok
- Gerekli belgeler: Yok
- (İlgili alt kategoriler: Bilgi Talebi, Bilgi Verilmemesi — BEDK)

**Sonuç:** Sınıflandırma 4982 sayılı Bilgi Edinme Hakkı Kanunu'na ve 15 iş günlük yanıt süresine atıf yaptı; alternatif merci olarak Bilgi Edinme Değerlendirme Kurulu'nu (BEDK) belirtti.

---

## Genel Sonuç

4 farklı kategoride de:
- Sınıflandırma, kategoriyi bilgi tabanıyla eşleşecek şekilde doğru belirledi
- "Bilgi Getir" node'u Supabase'den ilgili satırı sorunsuz çekti (hiçbir testte boş dönmedi)
- Doğrulanmış bilgi (merci, süre, belgeler) dilekçe/yol haritası üretimine kaynak olarak aktarıldı
- Çıktılar, ilgili mevzuata ve bilgi tabanındaki verilere tutarlı biçimde dayandı

Bu testler, RAG akışının (bilgi tabanına dayalı, doğrulanmış üretim) farklı dert türlerinde tutarlı çalıştığını göstermektedir. Ekran görüntülü örnek (Online Alışveriş) için Ürün Durumu bölümündeki RAG görsellerine bakınız.
