# Applied AI Lab

Russell & Norvig, *Artificial Intelligence: A Modern Approach* (4. baskı) üzerine kişisel çalışma laboratuvarı ve portföy.
Dil: Türkçe anlatım, teknik terimler İngilizce (kitaptaki karşılıklarıyla).

**Kitap akademik omurgamız, sınırımız değil.** Kitaptan gelen bilgi ile sonradan eklenen modern yaklaşımlar her zaman birbirinden ayrılır ve açıkça etiketlenir.

## Kaynak

- PDF: `Artificial-Intelligence-A-Modern-Approach-4th edition.pdf` (1.127 sayfa, gitignore'da; repoya eklenmez)
- Sayfa eşlemesi: **PDF sayfası = kitap sayfası + 13** (doğrulandı: Ch.1 → PDF 14, Ch.12 → 398, Ch.19 → 664)
- Okuma: `pdftotext -f <pdf_sayfa> -l <pdf_sayfa> "<pdf>" -`
- Referanslarda kitabın basılı sayfa numarası kullanılır; gerekiyorsa PDF sayfası parantez içinde verilir.
- Kitaptan uzun pasajlar kopyalanmaz; özetlenir, kısa alıntılar kaynak gösterilerek yapılır.

## Kapsam (17 bölüm)

| Kısım                           | Bölümler | Kitap sayfaları |
| ------------------------------- | -------- | --------------- |
| I. Yapay Zekânın Temelleri      | 1–2      | 1–62            |
| IV. Belirsizlik ve Akıl Yürütme | 12–18    | 385–650         |
| V. Makine Öğrenmesi             | 19–22    | 651–822         |
| VI. Dil, Algı ve Eylem          | 23–26    | 823–980         |

## Beş katmanlı çalışma sistemi → dosyalar

| Katman        | İçerik                                                   | Dosya                                   |
| ------------- | -------------------------------------------------------- | --------------------------------------- |
| 01 Refresh    | Kitaptaki teorinin tekrarı                               | `theory.md`                             |
| 02 Deep Dive  | Matematiksel temeller, algoritmalar, çıkarımlar          | `mathematics.md`                        |
| 03 Modernize  | 2020–2026 gelişmeleri ve makaleler (doğrulanmış kaynak)  | `modern-approaches.md`, `references.md` |
| 04 Apply      | Python, deneyler, gerçek dünya problemleri               | `experiments.ipynb`, `implementation/`  |
| 05 Evaluate   | Mülakat soruları, vaka analizleri, sistem tasarımı       | `questions.md`, `solutions.md`, `case-studies/` |

Kök klasörler: `research-papers/`, `case-studies/` (bölümler arası), `mathematical-notes/`, `capstone-projects/`.

## Ders akışı

- Ders = kitabın bir alt bölümü (ör. 1.1, 1.2 …). Başlıkta bölüm, kitap sayfası ve PDF sayfası yer alır. Sayfa aralıkları PDF'ten doğrulanır (ör. 1.1 = s. 1–5, plandaki 1–4 değil).
- İçerikte 📖 = kitaptan, 🔧 = bizim eklememiz etiketleri kullanılır.
- Modern kaynak künyeleri (arXiv no, yıl, yazar) çevrimiçi doğrulanır; doğrulananlar `references.md`'de ✔ ile işaretlenir.
- Referans şablonu: `01-ai-foundations/` (Ders 1.1 tamamlanmış örnek).
- Her ders bitince `README.md`'deki "Kapsam ve ilerleme" durumunu ve "Ders günlüğü" tablosunu güncelle.
- Her problemde sorulur: Neden bu algoritma? Alternatifleri? Hangi koşullarda başarısız olur? Üretime nasıl taşınır? Maliyeti?
- Gerçek dünya örnekleri tek sektöre bağlı kalmaz (finans, sağlık, lojistik, üretim, enerji, e-ticaret, yazılım, doküman işleme, robotik).
- Tartışma soruları önce kullanıcıya sorulur; çözümler kullanıcı cevap verdikten sonra `solutions.md`'ye yazılır.
- Modern konular (Foundation Models/LLM, Neuro-Symbolic AI, Agentic AI, Tool Calling, Reasoning Models, Agent Memory/Planning/Reflection, Multi-Agent Orchestration, AI Evaluation) ilgili bölümlerde `modern-approaches.md` altında işlenir.

## Teknik

- Ortam: `.venv` + `requirements.txt` (numpy, matplotlib, jupyter, ipywidgets)
- Notebook'lar VS Code Jupyter ile çalışır; sayısal sonuçlar `.md` dosyalarındaki rakamlarla tutarlı olmalı (değiştirince yeniden hesapla).
- Formüller: `$...$` ve `$$...$$` (VS Code markdown önizlemesi).
