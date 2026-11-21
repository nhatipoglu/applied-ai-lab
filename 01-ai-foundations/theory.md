# AI Foundations — Theory

## Ders 1 — What Is AI?

*Bölüm 1.1 | Kitap sayfa 1–4 | PDF sayfa 14–17 (bölümün başlangıcı)*

## 1. Yapay zekâyı nasıl tanımlıyoruz?

Russell ve Norvig, yapay zekâyı iki temel eksen üzerinden ele alıyor:

- İnsan davranışına benzerlik ve rasyonellik.
- Düşünme ve eyleme geçme.

Bu iki eksenden dört farklı yapay zekâ yaklaşımı ortaya çıkıyor:

|                | **İnsan gibi**                                  | **Rasyonel**                                       |
| -------------- | ----------------------------------------------- | -------------------------------------------------- |
| **Düşünme**    | Thinking Humanly — *cognitive modeling*         | Thinking Rationally — *laws of thought*            |
| **Eylem**      | Acting Humanly — *Turing test*                  | Acting Rationally — *rational agent*               |

*Kitaptaki dört temel yaklaşımın kavramsal gösterimi (Artificial Intelligence: A Modern Approach, 4th ed.).*

Kitabın ana omurgasını özellikle **Rational Agent Approach** oluşturuyor. Yani insanı taklit etmekten ziyade, mevcut bilgi ve koşullar altında en iyi beklenen sonucu elde etmek.

## 2. Klasik yaklaşımın modern AI ile ilişkisi

Aşağıdaki karşılaştırma kitabın birebir içeriği değil, bizim eklediğimiz modern mühendislik perspektifidir.

| Yaklaşım            | Modern uygulamalar             |
| ------------------- | ------------------------------ |
| Thinking Humanly    | Cognitive architectures        |
| Acting Humanly      | Conversational AI, LLM         |
| Thinking Rationally | Symbolic AI, theorem proving   |
| Acting Rationally   | Agentic AI, autonomous systems |

Bu yaklaşımlar birbirini dışlamaz. Modern bir yapay zekâ sistemi dördünün de özelliklerini taşıyabilir.

## 3. Matematiksel perspektif

Rasyonel bir ajanın belirsizlik altında karar vermesini genel olarak şöyle ifade edebiliriz:

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

Bu matematiksel yaklaşımı 12, 13, 16 ve 17. bölümlerde çok daha ayrıntılı inceleyeceğiz.

## 4. İlk gerçek dünya problemimiz

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

| Sipariş | Beklenen kâr                                         |
| ------- | ---------------------------------------------------- |
| Az      | 0,2·10.000 + 0,5·8.000 + 0,3·3.000 = **6.900 ₺**     |
| Orta    | 0,2·4.000 + 0,5·15.000 + 0,3·12.000 = **11.900 ₺** ✅ |
| Çok     | 0,2·(−10.000) + 0,5·10.000 + 0,3·25.000 = **10.500 ₺** |

Rasyonel karar: **Orta sipariş**.

**Senaryo B — Yüksek talep olasılığı artarsa** (Düşük %13, Orta %52, Yüksek %35):

| Sipariş | Beklenen kâr     |
| ------- | ---------------- |
| Az      | 6.510 ₺          |
| Orta    | 12.520 ₺         |
| Çok     | **12.650 ₺** ✅  |

Rasyonel karar: **Çok sipariş**.

Olasılıklardaki küçük bir kayma optimal kararı değiştirebiliyor. Bu simülasyonu [experiments.ipynb](experiments.ipynb) içinde olasılıkları değiştirerek tekrar edebilirsin. Buradaki sistemin karar verebilmesi için bir LLM veya sinir ağı kullanması zorunlu değil.

## 5. İlk akademik tartışma sorularımız

Bunları hemen cevaplamıyoruz. Önce kendi değerlendirmeni yap, ardından [solutions.md](solutions.md) ile karşılaştır.

1. Bir sistem makine öğrenmesi kullanmadan yapay zekâ sistemi olabilir mi?
2. Bir LLM tek başına akıllı ajan olarak kabul edilebilir mi?
3. Bir sistem yanlış tahminde bulunmasına rağmen rasyonel davranmış olabilir mi?
4. Beklenen kârı maksimize eden sistem her zaman işletme için en doğru kararı mı vermiştir?
5. Yukarıdaki stok problemini deterministik yazılım, makine öğrenmesi ve Agentic AI mimarileriyle ayrı ayrı nasıl çözerdin?

Özellikle beşinci soru bizim için önemli. Çünkü çalışmamız boyunca **hangi problem için hangi yapay zekâ yaklaşımının tercih edilmesi gerektiğini** öğrenmek, algoritmaların kendisini öğrenmek kadar önemli olacak.
