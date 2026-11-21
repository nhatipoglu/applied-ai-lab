# AI Foundations — Modern Approaches

## Ders 1 — What Is AI? (1.1)

🔧 Bu dosyanın tamamı **bizim eklememiz**; kitapta yer almaz. Kitaptaki kavramlara bağlantılar 📖 ile işaretli.

Hedef: Klasik AI, makine öğrenmesi, üretken AI, akıl yürütme modelleri ve agentic AI arasındaki ilişkiyi, kitabın 1.1'de kurduğu çerçeve üzerinden okumak.

## 1. Kavram haritası

Bu terimler aynı eksende değil. Bazıları **yöntem ailesi**, bazıları **model sınıfı**, bazıları **sistem mimarisi**:

```text
Artificial Intelligence  (alan: doğru şeyi yapan ajanlar)
├── Klasik / sembolik AI       arama, mantık, planlama, CSP          (kitap Böl. 3–11)
├── Olasılıksal AI             Bayes ağları, karar teorisi, MDP      (Böl. 12–18)
└── Machine Learning           deneyimle performansı artırma         (Böl. 19–22)
    └── Deep Learning          çok katmanlı sinir ağları             (Böl. 21)
        └── Foundation models  büyük, genel amaçlı, önceden eğitilmiş
            ├── Generative AI       LLM, diffusion, multimodal
            └── Reasoning models    test anında uzun akıl yürütme

Agentic AI  →  bir model sınıfı değil, bir SİSTEM MİMARİSİ:
               model + araçlar + bellek + döngü + ortam
```

- 📖 Kitabın dipnotu (s. 1): ML, AI'ın bir alt alanıdır; bazı AI sistemleri ML kullanmaz. Örneğin bir satranç motorundaki alpha-beta araması veya bir rota planlayıcıdaki A*.
- **Foundation model** terimi Bommasani et al. (2021) tarafından popülerleştirildi: geniş veriyle önceden eğitilip birçok göreve uyarlanabilen modeller.
- **Agentic AI** bir model türü değildir. Aynı LLM, döngü ve araçlarla sarıldığında ajan olur, sarılmadığında olmaz. Bu ayrım [questions.md](questions.md) Soru 2 için önemli.

## 2. Dört yaklaşım, 2026'dan bakınca

| Yaklaşım 📖          | Modern karşılık                                                   | Not |
| -------------------- | ----------------------------------------------------------------- | --- |
| Acting humanly       | LLM tabanlı sohbet sistemleri                                     | Jones & Bergen (2025): persona prompt'u verilen GPT-4.5, üç taraflı standart Turing testinde katılımcıların %73'ünde insan olarak seçildi; bu oran gerçek insanlarınkinden yüksekti. Kitabın uyarısı geçerli: testi geçmek, "zekâ"nın ne olduğu sorusunu kapatmıyor (Böl. 27). |
| Thinking humanly     | Hesaplamalı bilişsel modeller, beyin verisinden dil çözümleme     | 📖 Kitap s. 3'teki "read minds" cümlesinin somut örneği: Tang et al. (2023), fMRI kayıtlarından sürekli dilin anlamsal içeriğini yeniden kurdu. LLM'lerin insan dil işlemenin modeli olup olmadığı açık bir tartışma. |
| Thinking rationally  | Neuro-symbolic AI, formal doğrulama                               | AlphaGeometry (Trinh et al., 2024): bir dil modeli yardımcı yapılar önerir, sembolik bir motor kesin ispatı üretir. "Laws of thought" geleneği öğrenmeyle birleşiyor. |
| Acting rationally    | RL ajanları, LLM ajanları, otonom sistemler                       | Kitabın "standard model"i hâlâ eğitim hedeflerinin omurgası (bkz. 3. kısım). |

📖 Kitabın 1.1.2'deki uyarısı LLM çağında çok güncel: *"Bu sistem görevi iyi yapıyor"* ile *"Bu sistem insan gibi düşünüyor"* iki ayrı iddiadır. LLM'lerin insan benzeri çıktı üretmesi, ikinci iddiayı kendiliğinden kanıtlamaz.

## 3. Standard model, LLM eğitimi ve value alignment

LLM eğitim hattı, 📖 standard model tablosundaki satırları sırayla kullanır:

| Aşama                         | Optimize edilen                          | Standard model satırı |
| ----------------------------- | ---------------------------------------- | --------------------- |
| Pretraining                   | Sonraki token tahmininde cross-entropy loss | İstatistik: loss minimizasyonu |
| RLHF (Christiano et al., 2017; Ouyang et al., 2022) | İnsan tercihlerinden öğrenilmiş bir reward model | Yöneylem araştırması: reward maksimizasyonu |
| RL with verifiable rewards (ör. DeepSeek-R1, 2025) | Doğruluğu otomatik kontrol edilebilen cevaplar (matematik, kod) | Reward maksimizasyonu |

**1.1.5 ile bağlantı:**

- RLHF, hedefi elle yazmak yerine **insan tercihlerinden öğrenir**. Bu, kitabın önerdiği "makine hedefimizi bilmiyor ve öğreniyor" fikrine kısmi bir adımdır.
- Ama öğrenilen reward model de bir **proxy**'dir ($\hat{U}$). Ona karşı çok güçlü optimizasyon yapılınca gerçek kalite düşmeye başlar: **reward model overoptimization** (Gao et al., 2022). Bu, kitabın satranç örneğindeki dinamiğin ölçülmüş bir hâlidir.
- **Specification gaming / reward hacking:** Ajanların hedefin harfine uyup ruhunu ihlal ettiği belgelenmiş örnekler (Krakovna et al., 2020; Amodei et al., 2016).
- **Constitutional AI** (Bai et al., 2022): İnsan etiketinin bir kısmının yerine yazılı ilkelerden üretilen AI geri bildirimi kullanmak.
- Kitabın tercih ettiği formülasyon olan **assistance games / CIRL** (Hadfield-Menell et al., 2016; Russell, 2019), belirsizliği eğitim hedefinin içine açıkça koyar. Bkz. [mathematics.md](mathematics.md) 5. kısım.

## 4. Limited rationality ve test-time compute

📖 Kitap: Perfect rationality karmaşık ortamlarda mümkün değil; hesaplama zamanı sınırlı (s. 4).

**Reasoning models** (OpenAI o1, 2024; DeepSeek-R1, 2025) bu ödünleşimi doğrudan ürün parametresine dönüştürdü: Model cevap vermeden önce değişken miktarda "düşünme" yapar. Daha fazla düşünme genellikle daha iyi cevap verir, ama gecikmeyi ve maliyeti artırır.

- Snell et al. (2024/ICLR 2025): Test anındaki hesaplamayı **problem zorluğuna göre uyarlamalı** dağıtmak, best-of-N'e göre 4 kattan fazla verim sağladı. Eşit FLOP karşılaştırmasında, küçük bir modelin ek test-time compute ile yaklaşık 14 kat büyük bir modeli geçebildiği görüldü (küçük modelin kayda değer başarı oranına sahip olduğu problemlerde).
- Bu, [mathematics.md](mathematics.md) 4. kısımdaki $\max_{c,a}\,[EU(a \mid e, c) - \text{Cost}(c)]$ probleminin pratik bir örneği. Kolay soruya az, zor soruya çok düşünmek *limited rationality*'nin ta kendisi.
- **Mühendislik sorusu:** Bir üründe "reasoning effort" seviyesini neye göre seçersin? Gecikme bütçesi, hata maliyeti, istek başına maliyet → bu bir karar teorisi problemi.

## 5. Agent tanımı ve LLM ajanları

📖 Kitap s. 3–4: Bilgisayar ajanından beklenenler. Bunu bir **kontrol listesi** olarak kullanabiliriz:

| Özellik 📖                        | Çıplak LLM (tek çağrı) | LLM + döngü + araçlar + bellek |
| -------------------------------- | ---------------------- | ------------------------------ |
| Otonom çalışma                   | ?                      | ?                              |
| Ortamı algılama                  | ?                      | ?                              |
| Uzun süre varlığını sürdürme     | ?                      | ?                              |
| Değişime uyum                    | ?                      | ?                              |
| Hedef oluşturma ve takip etme    | ?                      | ?                              |

Soru işaretlerini [questions.md](questions.md) Soru 2'yi cevaplarken sen doldur.

Literatürdeki temel yapı taşları:

- **ReAct** (Yao et al., 2023): Akıl yürütme adımlarıyla eylemleri (araç çağrıları) iç içe geçiren döngü.
- **Toolformer** (Schick et al., 2023): Modelin hangi aracı ne zaman çağıracağını kendi kendine öğrenmesi.
- Bu yapıların ayrıntılı analizi Bölüm 2'de (ajan yapıları: simple reflex, model-based, goal-based, utility-based, learning agents) yapılacak. Modern LLM ajanlarını o sınıflandırmaya yerleştireceğiz.

## Kaynaklar

Tam künyeler: [references.md](references.md).
