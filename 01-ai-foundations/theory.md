# AI Foundations — Theory

## Ders 1 — What Is AI?

*Bölüm 1.1 | Kitap sayfa 1–5 | PDF sayfa 14–18*

> **Etiketler:** 📖 = kitaptan, 🔧 = bizim eklediğimiz modern / mühendislik perspektifi.

## 1. Yapay zekâyı nasıl tanımlıyoruz? 📖

Russell ve Norvig, yapay zekâyı iki temel eksen üzerinden ele alıyor:

- **İnsan vs. rasyonel:** Zekâyı insan performansına benzerlikle mi, yoksa soyut ve formel bir ölçüt olan **rationality** ("doğru şeyi yapmak") ile mi tanımlıyoruz?
- **Düşünce vs. davranış:** Zekâ içsel düşünme süreçlerinin mi, yoksa dışarıdan gözlenen davranışın mı özelliği?

Bu iki eksenden dört farklı yapay zekâ yaklaşımı ortaya çıkıyor:

|                | **İnsan gibi**                                  | **Rasyonel**                                       |
| -------------- | ----------------------------------------------- | -------------------------------------------------- |
| **Düşünme**    | Thinking Humanly — *cognitive modeling*         | Thinking Rationally — *laws of thought*            |
| **Eylem**      | Acting Humanly — *Turing test*                  | Acting Rationally — *rational agent*               |

İnsan benzeri zekâ arayışı kısmen psikolojiyle bağlantılı **ampirik** bir bilimdir. Rasyonalist yaklaşım ise matematik ve mühendisliği birleştirir; istatistik, kontrol teorisi ve ekonomiyle bağlantılıdır.

Kitaptaki iki dipnot önemli:

- **AI ≠ Machine Learning.** Makine öğrenmesi, deneyimle performansı artırmayı inceleyen bir *alt alandır*. Bazı AI sistemleri yetkinliğe ML ile ulaşır, bazıları ulaşmaz.
- "Rasyonel" demek insanların "irrasyonel" olduğu anlamına gelmez; yalnızca insan kararlarının her zaman matematiksel olarak mükemmel olmadığını kabul eder.

## 2. Dört yaklaşım ayrıntılı 📖

### 1.1.1 Acting humanly — Turing test

Turing (1950), "Makineler düşünebilir mi?" sorusunun felsefi belirsizliğinden kaçınmak için bir düşünce deneyi önerdi: Yazılı sorular soran bir sorgulayıcı, cevapların insandan mı bilgisayardan mı geldiğini ayırt edemiyorsa bilgisayar testi geçer.

Testi geçmek için gereken yetenekler:

| Yetenek                         | Amaç                                       |
| ------------------------------- | ------------------------------------------ |
| Natural language processing     | İnsan diliyle iletişim                     |
| Knowledge representation        | Bildiğini ve duyduğunu saklamak            |
| Automated reasoning             | Soruları cevaplamak, yeni sonuç çıkarmak   |
| Machine learning                | Yeni durumlara uyum, örüntü yakalama       |

**Total Turing test** fiziksel etkileşimi de içerir ve iki yetenek daha ister: **computer vision + speech recognition** (algı) ve **robotics** (nesne manipülasyonu, hareket). Bu altı disiplin AI'ın büyük kısmını oluşturur.

Yine de araştırmacılar testi geçmeye az emek harcadı; zekânın *altında yatan ilkeleri* anlamayı daha önemli buldular. Kitabın benzetmesi: "Yapay uçuş", mühendisler kuşları taklit etmeyi bırakıp rüzgâr tünellerini ve aerodinamiği incelemeye başlayınca başarıldı.

### 1.1.2 Thinking humanly — Cognitive modeling

Bir programın insan gibi düşündüğünü söylemek için insanların nasıl düşündüğünü bilmek gerekir. Üç yol var:

1. **Introspection:** Kendi düşüncelerimizi akarken yakalamaya çalışmak.
2. **Psychological experiments:** Bir insanı eylem hâlinde gözlemlemek.
3. **Brain imaging:** Beyni eylem hâlinde gözlemlemek.

Örnek: Newell ve Simon'ın **GPS (General Problem Solver)** programı (1961). Amaçları yalnızca problemi doğru çözmek değil, programın akıl yürütme adımlarının *sırasını ve zamanlamasını* insanlarınkiyle karşılaştırmaktı. **Cognitive science** bu çizgide AI modellerini psikolojinin deneysel teknikleriyle birleştirir.

Modern yazarlar iki iddiayı birbirinden ayırır: "Bu algoritma görevi iyi yapıyor" ile "Bu algoritma insan performansının iyi bir modeli". Bu ayrım hem AI'ın hem de cognitive science'ın daha hızlı gelişmesini sağladı.

### 1.1.3 Thinking rationally — "Laws of thought"

Aristoteles'in **syllogism**'leri, doğru öncüllerden her zaman doğru sonuç üreten argüman kalıplarıdır ("Sokrates bir insandır; bütün insanlar ölümlüdür → Sokrates ölümlüdür"). Bu çizgi **logic** alanını başlattı. 1965'e gelindiğinde programlar, mantıksal gösterimle tanımlanmış çözülebilir her problemi *prensipte* çözebiliyordu. Bu programların üzerine akıllı sistemler kurmayı hedefleyen geleneğe **logicist** gelenek denir.

İki sınır:

1. **Kesin bilgi gerektirir.** Satrancın kurallarını bildiğimiz gibi siyasetin ya da savaşın kurallarını bilmiyoruz. Bu boşluğu **probability** teorisi doldurur: belirsiz bilgiyle titiz akıl yürütme.
2. **Rasyonel düşünce, davranış üretmez.** Bunun için bir *rasyonel eylem* teorisine ihtiyaç var.

### 1.1.4 Acting rationally — Rational agent

**Agent**, eylemde bulunan şeydir (Latince *agere*, "yapmak"). Bilgisayar ajanlarından beklenenler: otonom çalışmak, ortamı algılamak, uzun süre varlığını sürdürmek, değişime uyum sağlamak, hedef oluşturup peşinden gitmek.

> **Rational agent:** En iyi sonuca, belirsizlik varsa **en iyi beklenen sonuca** ulaşacak şekilde davranan ajan.

Doğru çıkarım (inference) rasyonelliğin *yollarından biridir*, ama tek yolu değildir. Örneğin sıcak sobadan elini refleksle çekmek, uzun uzun düşünüp karar vermekten genellikle daha başarılıdır.

Rational agent yaklaşımının iki avantajı:

1. "Laws of thought" yaklaşımından **daha geneldir**, çünkü doğru çıkarım rasyonelliğe ulaşmanın mekanizmalarından yalnızca biridir.
2. **Bilimsel gelişime daha uygundur.** Rasyonellik standardı matematiksel olarak iyi tanımlıdır; bu tanımdan geriye doğru giderek onu *kanıtlanabilir şekilde* sağlayan ajan tasarımları türetilebilir.

**Standard model:** AI, ajana verdiğimiz bir hedefe (objective) göre "doğru şeyi yapan" ajanları inceler. Aynı paradigma başka alanlarda da hâkimdir:

| Alan                | Karşılığı                                    |
| ------------------- | -------------------------------------------- |
| Kontrol teorisi     | Controller bir **cost function**'ı minimize eder |
| Yöneylem araştırması | Policy, **ödüllerin toplamını** maksimize eder |
| İstatistik          | Decision rule bir **loss function**'ı minimize eder |
| Ekonomi             | Karar verici **utility**'yi maksimize eder   |

**Limited rationality:** Karmaşık ortamlarda *perfect rationality* (her zaman tam optimal eylem) mümkün değildir; hesaplama maliyeti çok yüksektir. Limited rationality, bütün hesaplamaları yapmaya zaman yokken uygun davranmaktır (Bölüm 5 ve 17). Yine de mükemmel rasyonellik, teorik analiz için iyi bir başlangıç noktasıdır.

### 1.1.5 Beneficial machines

Standard model, makineye **eksiksiz tanımlanmış bir hedef** verdiğimizi varsayar. Satranç veya en kısa yol gibi yapay görevlerde hedef görevin içinde gelir. Gerçek dünyada ise hedefi eksiksiz ve doğru tanımlamak giderek zorlaşır.

- **Otonom araç:** Hedef "güvenle varmak" mı? Mutlak güvenlik garajda kalmayı gerektirir. İlerleme ile risk arasındaki ödünleşim (tradeoff) nasıl kurulacak? Diğer sürücüleri ne kadar rahatsız edebilir? Yolcuyu sarsmamak için ivmelenmeyi ne kadar yumuşatmalı?
- **Value alignment problem:** Makineye koyduğumuz hedefin gerçek tercihlerimizle uyumlu olması problemi. Laboratuvarda hatalı hedef kolayca düzeltilir: sistemi sıfırla, hedefi düzelt, tekrar dene. Gerçek dünyada çalışan bir sistemde bu artık mümkün değildir. Sistem ne kadar zekiyse, yanlış hedefin sonuçları o kadar ağırdır.
- **Satranç örneği:** Satranç tahtasının ötesinde akıl yürütüp eylemde bulunabilen bir makine, kazanma şansını artırmak için rakibini hipnotize etmeye, şantaj yapmaya veya ek hesaplama gücünü ele geçirmeye çalışabilir. Bunlar "akılsız" davranışlar değildir; *kazanmayı tek hedef olarak tanımlamanın* mantıksal sonucudur.

Kitabın önerdiği yeni formülasyon: Makine **bizim** hedeflerimizi izlemeli, ama bu hedeflerin ne olduğundan **zorunlu olarak emin olmamalı**. Hedefi tam bilmediğini bilen bir makinenin temkinli davranmak, izin istemek, gözlem yoluyla tercihlerimizi öğrenmek ve insan kontrolüne boyun eğmek için bir nedeni vardır. Nihai amaç **provably beneficial** ajanlardır (Bölüm 1.5'te tekrar ele alınacak).

## 3. Klasik yaklaşımın modern AI ile ilişkisi 🔧

| Yaklaşım            | Modern uygulamalar             |
| ------------------- | ------------------------------ |
| Thinking Humanly    | Cognitive architectures        |
| Acting Humanly      | Conversational AI, LLM         |
| Thinking Rationally | Symbolic AI, theorem proving   |
| Acting Rationally   | Agentic AI, autonomous systems |

Bu yaklaşımlar birbirini dışlamaz. Modern bir yapay zekâ sistemi dördünün de özelliklerini taşıyabilir. Ayrıntılar: [modern-approaches.md](modern-approaches.md).

## 4. Matematiksel perspektif 🔧

Kitap 1.1'de formül vermiyor. Aşağıdaki ifade, "en iyi beklenen sonuç" tanımının formel hâlidir ve Bölüm 16'daki **maximum expected utility** ilkesinin önizlemesidir:

$$
a^* = \arg\max_{a \in A} \sum_{s \in S} P(s \mid e)\, U(a, s)
$$

| Sembol          | Anlamı                           |
| --------------- | -------------------------------- |
| $A$             | Olası eylemler                   |
| $S$             | Olası dünya durumları            |
| $e$             | Mevcut gözlemler                 |
| $P(s \mid e)$   | Gözlemlere bağlı durum olasılığı |
| $U(a, s)$       | Eylemin ilgili durumdaki faydası |
| $a^*$           | Optimal eylem                    |

Bu yaklaşımı 12, 13, 16 ve 17. bölümlerde çok daha ayrıntılı inceleyeceğiz. Türetmeler ve geometrik yorum: [mathematics.md](mathematics.md).

## 5. İlk gerçek dünya problemimiz 🔧

Bir e-ticaret şirketinin stok yönetiminden sorumlu bir AI sistemi tasarladığımızı düşünelim.

Sistem gelecek ayın talebini tahmin ediyor:

- Düşük talep: %20 olasılık
- Orta talep: %50 olasılık
- Yüksek talep: %30 olasılık

Üç farklı sipariş stratejisi var. Aşağıdaki hipotetik tablo her stratejinin net kârını gösteriyor.

### Expected Utility — Karar simülasyonu

| Sipariş | Düşük     | Orta     | Yüksek   |
| ------- | --------- | -------- | -------- |
| Az      | 10.000 ₺  | 8.000 ₺  | 3.000 ₺  |
| Orta    | 4.000 ₺   | 15.000 ₺ | 12.000 ₺ |
| Çok     | -10.000 ₺ | 10.000 ₺ | 25.000 ₺ |

**Senaryo A — Temel tahmin** (Düşük %20, Orta %50, Yüksek %30):

| Sipariş | Beklenen kâr                                           |
| ------- | ------------------------------------------------------ |
| Az      | 0,2·10.000 + 0,5·8.000 + 0,3·3.000 = **6.900 ₺**       |
| Orta    | 0,2·4.000 + 0,5·15.000 + 0,3·12.000 = **11.900 ₺** (optimal) |
| Çok     | 0,2·(−10.000) + 0,5·10.000 + 0,3·25.000 = **10.500 ₺** |

Rasyonel karar: **Orta sipariş**.

**Senaryo B — Yüksek talep olasılığı artarsa** (Düşük %13, Orta %52, Yüksek %35):

| Sipariş | Beklenen kâr          |
| ------- | --------------------- |
| Az      | 6.510 ₺               |
| Orta    | 12.520 ₺              |
| Çok     | **12.650 ₺** (optimal) |

Rasyonel karar: **Çok sipariş**.

Olasılıklardaki küçük bir kayma optimal kararı değiştirebiliyor. P(Orta) %50'de sabitken karar sınırı P(Yüksek) ≈ %35,2'dir. Bu simülasyonu [experiments.ipynb](experiments.ipynb) içinde olasılıkları değiştirerek tekrar edebilirsin. Buradaki sistemin karar verebilmesi için bir LLM veya sinir ağı kullanması zorunlu değil.

## 6. Tartışma soruları

Tartışma, kavram ve mülakat soruları: [questions.md](questions.md). Önce kendi cevaplarını yaz, sonra birlikte tartışıp [solutions.md](solutions.md)'ye işleyelim.
