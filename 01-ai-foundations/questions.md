# AI Foundations — Questions

## Ders 1 — What Is AI? (1.1)

Önce kendi cevaplarını yaz (her sorunun altına ya da ayrı bir notta). Birlikte tartıştıktan sonra sonuçları [solutions.md](solutions.md)'ye işleyeceğiz.

Zorluk: ★ temel · ★★ orta · ★★★ ileri

---

## A. Tartışma soruları

1. ★★ Bir sistem makine öğrenmesi kullanmadan yapay zekâ sistemi olabilir mi?
2. ★★★ Bir LLM tek başına akıllı ajan olarak kabul edilebilir mi? *(İpucu: [modern-approaches.md](modern-approaches.md) 5. kısımdaki kontrol listesini doldur.)*
3. ★★ Bir sistem yanlış tahminde bulunmasına rağmen rasyonel davranmış olabilir mi?
4. ★★★ Beklenen kârı maksimize eden sistem her zaman işletme için en doğru kararı mı vermiştir?
5. ★★★ [theory.md](theory.md)'deki stok problemini deterministik yazılım, makine öğrenmesi ve agentic AI mimarileriyle ayrı ayrı nasıl çözerdin? Her biri için: neden bu yaklaşım, alternatifleri, hangi koşullarda başarısız olur, üretime nasıl taşınır, maliyeti nedir?

## B. Kavram soruları (kitaptan)

6. ★ Dört yaklaşımı tanımlayan iki ekseni açıkla. Her yaklaşım için bir örnek sistem ver.
7. ★ Turing testini geçmek için gereken dört yetenek nedir? Total Turing test hangi iki yeteneği ekler?
8. ★★ AI araştırmacıları neden Turing testini geçmeye çok az emek harcadı? Kitaptaki "yapay uçuş" benzetmesini açıkla.
9. ★★ "Laws of thought" yaklaşımının iki temel sınırı nedir? Probability bunlardan hangisini çözer, hangisini çözmez?
10. ★ Çıkarım (inference) gerektirmeyen rasyonel bir eylem örneği ver.
11. ★★ Rational agent yaklaşımının diğer yaklaşımlara göre iki avantajı nedir?
12. ★★ "Standard model" nedir? Kontrol teorisi, yöneylem araştırması, istatistik ve ekonomideki karşılıklarını yaz.
13. ★★ Perfect rationality ile limited rationality arasındaki fark nedir? Perfect rationality neden yine de faydalı bir kavram?
14. ★★★ Value alignment problemi nedir? Kitaptaki satranç örneğinde makinenin şantaj yapması neden "akılsızlık" değil de hedef tanımının mantıksal sonucudur?
15. ★★★ Kitap, hedefinden emin olmayan bir makinenin neden *daha iyi* davranacağını savunuyor? Bu makinenin sergileyeceği dört davranışı say.

## C. Hesaplama soruları

[theory.md](theory.md) Bölüm 5'teki kâr tablosunu kullan. Çözümü elle yap, sonra [experiments.ipynb](experiments.ipynb) ile kontrol et.

16. ★ $p = (0{,}10;\ 0{,}40;\ 0{,}50)$ için üç stratejinin beklenen kârını hesapla. Optimal karar nedir?
17. ★★ P(Yüksek) = 0 iken, P(Düşük) hangi değerin üzerine çıkarsa **Az** sipariş optimal olur?
18. ★★ "Çok" stratejisinin düşük talepteki zararı −10.000 ₺ yerine −20.000 ₺ olsaydı, P(Orta) = 0,5 sabitken Orta/Çok karar sınırı P(Yüksek)'in hangi değerine kayardı?
19. ★★★ Şirket riskten kaçınıyor: herhangi bir senaryoda 0 ₺'nin altına düşmeyi kabul etmiyor. Bu kısıt altında Senaryo B'nin kararı değişir mi? Bu, 4. tartışma sorusuyla nasıl ilişkili?

## D. Mülakat / sistem tasarımı soruları

20. ★★ "Bizim chatbot'umuz Turing testini geçti, demek ki akıllı." Bu iddiayı teknik olarak değerlendir. *(Bağlam: Jones & Bergen, 2025.)*
21. ★★★ Bir e-ticaret öneri sisteminin hedefini **click-through rate** olarak tanımladın. Bu proxy hedef, gerçek iş hedefinden hangi yollarla sapabilir? Üretimde bunu nasıl tespit edersin?
22. ★★★ Bir üründe reasoning modelin "düşünme seviyesini" (test-time compute) hangi kriterlere göre seçersin? Bunu bir limited rationality problemi olarak formüle et.
23. ★★★ Otonom bir müşteri hizmetleri ajanı tasarlıyorsun. Kitaptaki "hedefinden emin olmayan makine" fikrini mimariye nasıl yansıtırsın? (Ne zaman insana sorar, ne zaman kendi karar verir?)
