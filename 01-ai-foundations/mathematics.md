# AI Foundations — Mathematics

## Ders 1 — What Is AI? (1.1)

Kitap 1.1'de formül vermiyor; bu dosyadaki formalizasyon 🔧 **bizim eklememiz**. Amaç, 1.1'deki sözel kavramları (rational agent, standard model, limited rationality, value alignment) ileriki bölümlerde kullanılacak matematiksel dile bağlamak.

## 1. Rational agent: en iyi beklenen sonuç

Kitabın tanımı: *"A rational agent is one that acts so as to achieve the best outcome or, when there is uncertainty, the best expected outcome."* (s. 4)

**Belirsizlik yoksa** (durum $s$ biliniyor):

$$
a^* = \arg\max_{a \in A} U(a, s)
$$

**Belirsizlik varsa** (yalnızca gözlem $e$ biliniyor):

$$
EU(a \mid e) = \sum_{s \in S} P(s \mid e)\, U(a, s), \qquad a^* = \arg\max_{a \in A} EU(a \mid e)
$$

Bu, Bölüm 16'daki **maximum expected utility (MEU)** ilkesidir. $P(s \mid e)$'nin nasıl hesaplanacağı Bölüm 12–14'ün, $U$'nun nasıl tanımlanacağı Bölüm 16'nın, zaman içinde art arda kararlar Bölüm 17'nin konusu.

## 2. Standard model: tek bir optimizasyon kalıbı

Kitap, "standard model"in dört alanda aynı yapıda olduğunu söylüyor. Formel olarak hepsi aynı kalıp, yalnızca işaret ve isim farklı:

| Alan                 | Optimizasyon                                          | Not                        |
| -------------------- | ----------------------------------------------------- | -------------------------- |
| Ekonomi / AI         | $\max_a \; \mathbb{E}[U]$                             | utility                    |
| Yöneylem araştırması | $\max_\pi \; \mathbb{E}\big[\sum_t \gamma^t R_t\big]$ | reward toplamı (Bölüm 17, 22) |
| İstatistik           | $\min_\delta \; \mathbb{E}[L(\theta, \delta(x))]$     | loss = −utility            |
| Kontrol teorisi      | $\min_u \; \int c(x_t, u_t)\, dt$                     | cost = −utility            |

$L = -U$ veya $c = -U$ alınırsa hepsi $\arg\max \mathbb{E}[U]$ hâline gelir. Bu yüzden ileride göreceğimiz algoritmaların büyük kısmı, bu tek problemin farklı varsayımlar altındaki çözümleridir.

## 3. Stok problemi: matris formu

[theory.md](theory.md) Bölüm 5'teki problemde $|A| = 3$, $|S| = 3$:

$$
U = \begin{bmatrix} 10.000 & 8.000 & 3.000 \\ 4.000 & 15.000 & 12.000 \\ -10.000 & 10.000 & 25.000 \end{bmatrix},
\qquad
p = \begin{bmatrix} P(\text{Düşük}) \\ P(\text{Orta}) \\ P(\text{Yüksek}) \end{bmatrix}
$$

Tüm eylemlerin beklenen faydası tek bir matris-vektör çarpımıdır:

$$
\mathbf{EU} = U p, \qquad a^* = \arg\max_i \, (Up)_i
$$

Senaryo A, $p = (0{,}2;\ 0{,}5;\ 0{,}3)$: $\mathbf{EU} = (6.900;\ 11.900;\ 10.500)$ → **Orta**.

### 3.1 Karar sınırları doğrusaldır

İki eylem arasındaki fark $p$'nin doğrusal bir fonksiyonudur:

$$
EU(\text{Orta}) - EU(\text{Çok}) = 14.000\,p_1 + 5.000\,p_2 - 13.000\,p_3
$$

Bu ifadenin sıfır olduğu yer bir **karar sınırıdır**. Olasılıklar $p_1 + p_2 + p_3 = 1$ koşulunu sağladığından, $p$ bir üçgen (**probability simplex**) üzerinde yaşar; karar sınırları bu üçgeni düz çizgilerle bölgelere ayırır. Her bölgede tek bir eylem optimaldir.

- **Senaryo B kontrolü:** $p = (0{,}13;\ 0{,}52;\ 0{,}35)$ → $1.820 + 2.600 - 4.550 = -130$. Fark negatif, yani Çok, Orta'dan 130 ₺ daha iyi (12.650 − 12.520). ✓
- **$p_2 = 0{,}5$ sabit, $p_3 = h$, $p_1 = 0{,}5 - h$:** $9.500 - 27.000h = 0 \Rightarrow h^* = 9.500 / 27.000 \approx 0{,}352$.

### 3.2 "Az sipariş" ne zaman optimal?

$$
EU(\text{Az}) - EU(\text{Orta}) = 6.000\,p_1 - 7.000\,p_2 - 9.000\,p_3
$$

$p_3 = 0$ iken $p_2 = 1 - p_1$ yazılırsa: $13.000\,p_1 > 7.000 \Rightarrow p_1 > 0{,}538$.

Yani Az sipariş, düşük talep olasılığı **%54'ü aşmadıkça** hiçbir zaman optimal değil. Yüksek talep olasılığı arttıkça bu eşik daha da yükselir.

> **Mühendislik yorumu:** Karar sınırına yakın bölgelerde ($p \approx$ sınır) tahmin modelindeki küçük hatalar kararı değiştirir. Sınırdan uzak bölgelerde ise kaba bir tahmin bile yeterlidir. Bu, *tahmin doğruluğuna ne kadar yatırım yapmalıyız?* sorusunun nicel cevabıdır (Bölüm 16: **value of information**).

## 4. Limited rationality: hesaplamanın da maliyeti var

Perfect rationality, hesaplama süresini bedava varsayar. Gerçekte düşünmek zaman alır ve zaman da faydayı etkiler. Basit bir model:

$$
a^* = \arg\max_{a} \Big[ EU(a \mid e) \Big] \quad \longrightarrow \quad
(c^*, a^*) = \arg\max_{c,\, a} \Big[ EU(a \mid e, c) - \text{Cost}(c) \Big]
$$

Burada $c$ harcanan hesaplama miktarıdır (arama derinliği, örnekleme sayısı, düşünme token'ı…). Daha fazla hesaplama daha iyi bir eylem bulma olasılığını artırır ama gecikme ve maliyet de getirir. Bu dengenin klasik incelemesi **metareasoning** ve **bounded optimality**'dir (Bölüm 5 ve 17). Modern karşılığı: [modern-approaches.md](modern-approaches.md), test-time compute.

## 5. Value alignment: proxy hedef ve gerçek hedef

Gerçek (insan) fayda fonksiyonu $U^*$, makineye verdiğimiz hedef $\hat{U}$ olsun. Makine şunu çözer:

$$
\hat{a} = \arg\max_a \hat{U}(a)
$$

Problem: Genel olarak $\hat{a} \neq \arg\max_a U^*(a)$, ve optimizasyon gücü arttıkça $\hat{U}$ ile $U^*$'ın *ayrıştığı* köşelere gitme eğilimi artar.

**Örnek: otonom araç.** Gerçek hedefin kabaca şöyle olduğunu varsayalım:

$$
U^*(v) = -\,T(v) \;-\; \lambda_1\,\text{Risk}(v) \;-\; \lambda_2\,\text{Konfor kaybı}(v)
$$

Proxy hedef "en kısa sürede var" ise $\hat{U}(v) = -T(v)$, yani $\lambda_1 = \lambda_2 = 0$. Optimum: mümkün olan en yüksek hız. Proxy hedef "mutlak güvenlik" ise $\hat{U} = -\text{Risk}$; optimum: $v = 0$, garajda kal. Kitaptaki iki uç tam olarak bu iki eksik tanımdır.

**Kitabın önerdiği formülasyon:** Makine $U^*$'ı bilmiyor, onu bir parametre $\theta$ üzerinden belirsiz kabul ediyor:

$$
a^* = \arg\max_a \sum_{\theta} P(\theta \mid e)\; U(a;\, \theta)
$$

Bu, yukarıda 1. kısımdaki MEU formülünün *aynısıdır*. Tek fark, belirsizliğin dünyanın durumu $s$ üzerinde değil, **insanın tercihleri** $\theta$ üzerinde olması. Buradan şu sonuçlar doğal olarak çıkar:

- $P(\theta \mid e)$ geniş (belirsiz) ise geri dönüşü olmayan eylemler beklenen fayda açısından cezalandırılır → **temkinli davranış**.
- İnsana soru sormak $e$'yi zenginleştirir ve $P(\theta \mid e)$'yi daraltır → **izin isteme / soru sorma** bir bilgi toplama eylemi olarak rasyoneldir.
- İnsanın "dur" demesi $\theta$ hakkında bilgi taşır → **insan kontrolüne boyun eğmek** rasyoneldir.

Bu çerçeve literatürde **assistance game** / **cooperative inverse reinforcement learning (CIRL)** olarak geçer (Hadfield-Menell et al., 2016; Bölüm 18 ve 1.5).
