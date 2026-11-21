# Applied AI Lab

Russell & Norvig'in *Artificial Intelligence: A Modern Approach* (4. baskı) kitabını omurga alan; teoriyi matematik, güncel araştırmalar, Python deneyleri ve gerçek dünya problemleriyle birleştiren kişisel bir yapay zekâ laboratuvarı.

> **Kitap akademik omurgamız, sınırımız değil.** Kitaptan gelen bilgi (📖) ile sonradan eklenen modern yaklaşımlar (🔧) her dosyada birbirinden ayrılır.

## Çalışma yöntemi

Her konu beş katmanda işlenir:

| #  | Katman        | İçerik                                                  | Dosya                                   |
| -- | ------------- | ------------------------------------------------------- | --------------------------------------- |
| 01 | **Refresh**   | Kitaptaki teorinin tekrarı                              | `theory.md`                             |
| 02 | **Deep Dive** | Matematiksel temeller, algoritmalar, çıkarımlar         | `mathematics.md`                        |
| 03 | **Modernize** | 2020–2026 gelişmeleri ve akademik makaleler             | `modern-approaches.md`, `references.md` |
| 04 | **Apply**     | Python, deneyler, gerçek dünya problemleri              | `experiments.ipynb`, `implementation/`  |
| 05 | **Evaluate**  | Teknik mülakat soruları, vaka analizleri, sistem tasarımı | `questions.md`, `solutions.md`, `case-studies/` |

Her problemde yalnızca çözüme değil, şu sorulara da cevap aranır: *Neden bu algoritma? Alternatifleri neler? Hangi koşullarda başarısız olur? Üretime nasıl taşınır? Maliyeti nedir?*

## Kapsam ve ilerleme

17 bölüm, ~650 kitap sayfası.

| Bölüm | Konu | Durum |
| ----- | ---- | ----- |
| **I. Yapay Zekânın Temelleri** (s. 1–62) | | |
| [01](01-ai-foundations/) | Introduction — AI Foundations | 🟡 1.1 tamam (sorular cevap bekliyor) |
| [02](02-intelligent-agents/) | Intelligent Agents | ⚪ |
| **IV. Belirsizlik ve Akıl Yürütme** (s. 385–650) | | |
| [12](12-quantifying-uncertainty/) | Quantifying Uncertainty | ⚪ |
| [13](13-probabilistic-reasoning/) | Probabilistic Reasoning | ⚪ |
| [14](14-probabilistic-reasoning-over-time/) | Probabilistic Reasoning over Time | ⚪ |
| [15](15-probabilistic-programming/) | Probabilistic Programming | ⚪ |
| [16](16-making-simple-decisions/) | Making Simple Decisions | ⚪ |
| [17](17-making-complex-decisions/) | Making Complex Decisions | ⚪ |
| [18](18-multiagent-decision-making/) | Multiagent Decision Making | ⚪ |
| **V. Makine Öğrenmesi** (s. 651–822) | | |
| [19](19-learning-from-examples/) | Learning from Examples | ⚪ |
| [20](20-learning-probabilistic-models/) | Learning Probabilistic Models | ⚪ |
| [21](21-deep-learning/) | Deep Learning | ⚪ |
| [22](22-reinforcement-learning/) | Reinforcement Learning | ⚪ |
| **VI. Dil, Algı ve Eylem** (s. 823–980) | | |
| [23](23-natural-language-processing/) | Natural Language Processing | ⚪ |
| [24](24-deep-learning-for-nlp/) | Deep Learning for NLP | ⚪ |
| [25](25-computer-vision/) | Computer Vision | ⚪ |
| [26](26-robotics/) | Robotics | ⚪ |

⚪ başlanmadı · 🟡 devam ediyor · ✅ tamamlandı

### Ders günlüğü

| Ders | Konu | Kitap s. | Öne çıkanlar |
| ---- | ---- | -------- | ------------ |
| [1.1](01-ai-foundations/theory.md) | What Is AI? | 1–5 | Dört yaklaşım, standard model, limited rationality, value alignment · [Expected utility simülasyonu](01-ai-foundations/experiments.ipynb) |

## Modern konular

Kitabın ötesinde, ilgili bölümlerde işlenecek güncel başlıklar:

- Foundation Models ve Large Language Models
- Neuro-Symbolic AI
- Agentic AI ve otonom sistemler
- Tool Calling ve Function Calling
- Reasoning Models ve test-time compute
- Agent Memory, Planning ve Reflection
- Multi-Agent Orchestration
- AI Evaluation ve güvenilirlik

## Uygulama alanları

Problemler tek bir sektöre bağlı kalmaz:

| Sektör         | Örnek problem                               |
| -------------- | ------------------------------------------- |
| Finans         | Belirsiz veriler altında kredi risk analizi |
| Sağlık         | Olasılıksal karar destek sistemleri         |
| Lojistik       | Dinamik rota optimizasyonu                  |
| Üretim         | Arıza tahmini ve anomali tespiti            |
| Enerji         | Tüketim tahminleme ve optimizasyon          |
| E-ticaret      | Öneri sistemleri ve talep tahmini           |
| Yazılım        | Otonom yazılım geliştirme ajanları          |
| Doküman işleme | Multimodal bilgi çıkarımı ve doğrulama      |
| Robotik        | Belirsiz ortamlarda karar verme             |

## Repo yapısı

```text
applied-ai-lab/
├── 01-ai-foundations/          # Her bölüm aynı yapıda:
│   ├── theory.md               #   01 Refresh
│   ├── mathematics.md          #   02 Deep Dive
│   ├── modern-approaches.md    #   03 Modernize
│   ├── references.md
│   ├── experiments.ipynb       #   04 Apply
│   ├── implementation/
│   ├── questions.md            #   05 Evaluate
│   ├── solutions.md
│   └── case-studies/
├── 02-intelligent-agents/
├── 12-quantifying-uncertainty/ … 26-robotics/
├── research-papers/            # Okunan makaleler ve notlar
├── case-studies/               # Bölümler arası vaka analizleri
├── mathematical-notes/         # Ortak matematik notları
└── capstone-projects/          # Birden çok bölümü birleştiren projeler
```

## Kurulum

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Notebook'lar Jupyter veya VS Code (Jupyter eklentisi) ile açılır. Formüller `.md` dosyalarında `$...$` / `$$...$$` ile yazılır; VS Code markdown önizlemesi ve GitHub bunları render eder.

## Kaynak

Russell, S., & Norvig, P. (2021). *Artificial Intelligence: A Modern Approach* (4th ed.). Pearson.
Kitabın kendisi telif hakkı nedeniyle bu repoda **yer almaz**; içerik özet, yorum ve kısa alıntılardan oluşur.
