# WS-02: Problem Statement

> **Bab 2 — Problem Formulation & System Context**

---

## Ringkasan Materi

### Problem Formation Model

Masalah riset melewati 5 tahap transformasi. Melompat langsung dari Reality ke Variable adalah kesalahan paling umum.

```
Reality → Observed Issue (Symptom) → Diagnosed Problem (Root Cause)
→ Researchable Problem (Scoped) → Measurable Variable (Operationalized)
```

### Topic ≠ Problem ≠ Research Problem

| Level | Contoh | Status |
|-------|--------|--------|
| **Topik** | Keamanan IoT | Terlalu luas, tidak bisa diuji |
| **Problem** | MQTT tidak terenkripsi | Spesifik tapi belum riset |
| **Research Problem** | Belum ada studi membandingkan overhead TLS 1.3 vs DTLS pada MQTT di IoT RAM < 64KB | Bisa dirancang eksperimennya |

### Symptom vs Root Cause

Apa yang diamati (gejala) ≠ mengapa terjadi (akar masalah). Gunakan **5 Whys** atau **Fishbone Diagram** untuk menggali.

Contoh: "User meninggalkan checkout" (symptom) → "Waktu loading > 8 detik karena API call sequential" (root cause).

### System Thinking

Setiap masalah riset TI harus terikat pada komponen sistem: **Input → Process → Output → Outcome → Constraints → Stakeholders**.

### Problem Quality Check

Masalah riset yang layak harus memenuhi 5 kriteria:
- **Clarity** — Satu orang membaca akan paham
- **Measurability** — Ada metrik kuantitatif
- **Relevance** — Penting untuk domain
- **Testability** — Bisa gagal (falsifiable)
- **Impact** — Ada kontribusi jika terjawab

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Menyelesaikan masalah (*solve*) | Memahami dan membuktikan (*understand & prove*) |
| Masalah | Bug, error, fitur belum ada | Gap dalam pengetahuan |
| Scope | Selesaikan semua yang perlu | Batasi agar bisa dibuktikan |
| Output | Working system | Evidence, paper, replicable findings |

### Istilah Penting

- **Problem Statement** — Formulasi tertulis: konteks sistem + gap + dampak + justifikasi
- **System Context** — Deskripsi lengkap: input, proses, output, outcome, constraints, stakeholders
- **Problem Drift** — Masalah "bermutasi" dari pendahuluan ke metodologi karena statement awal tidak presisi
- **Solution-First Thinking** — Memulai dari solusi tanpa masalah yang jelas — berbahaya dalam riset
- **Operational Definition** — Definisi variabel yang cukup jelas agar peneliti lain bisa mengukur hal yang sama

---

## Template A.2 — Problem Statement Builder

```
PROBLEM STATEMENT BUILDER

Domain & Konteks
  Domain   : Keamanan jaringan / machine learning
  Konteks  : Deteksi anomali trafik jaringan menggunakan SMOTE dan Random Forest

System Context
  Input       : Dataset trafik jaringan (normal & anomali)
  Process     : Preprocessing data - SMOTE - training model Random Forest
  Output      : Hasil prediksi + nilai akurasi, precision, recall, F1-score
  Outcome     : Model deteksi anomali dengan performa tinggi
  Constraints : Dataset terbatas, data tidak selalu mencerminkan kondisi nyata
  Stakeholders: Peneliti, praktisi keamanan jaringan

Fenomena → Problem
  Fenomena yang diamati             : Penggunaan SMOTE meningkatkan performa model deteksi anomali
  Gejala (symptom) yang terukur     : Nilai akurasi, precision, recall, dan F1-score meningkat setelah SMOTE
  Masalah yang didiagnosis          : SMOTE menghasilkan data sintetis yang mengubah distribusi data asli
  Masalah riset (researchable)      : Belum diketahui apakah peningkatan performa model setelah SMOTE benar-benar valid atau hanya akibat distorsi data
  Variabel yang terukur             : Akurasi,Precision, Recall,F1-score,Perbandingan performa (dengan vs tanpa SMOTE)

Problem Quality Check
  [v] Clarity — Apakah satu orang membaca akan paham?
  [v] Measurability — Apakah ada metrik kuantitatif?
  [v] Relevance — Apakah penting untuk domain?
  [v] Testability — Apakah bisa gagal?
  [v] Impact — Apakah ada kontribusi jika terjawab?

Problem Statement (1 paragraf):
Penggunaan SMOTE dalam deteksi anomali jaringan sering dilaporkan dapat meningkatkan performa model, yang ditunjukkan melalui kenaikan nilai akurasi, precision, recall, dan F1-score. Namun, berdasarkan analisis sebelumnya, SMOTE berpotensi menimbulkan distorsi karena menghasilkan data sintetis yang dapat mengubah distribusi data asli. Hal ini menimbulkan pertanyaan apakah peningkatan performa tersebut benar-benar mencerminkan kondisi nyata atau hanya akibat perubahan data. Oleh karena itu, penelitian ini bertujuan untuk mengevaluasi pengaruh penggunaan SMOTE terhadap keandalan model deteksi anomali dengan membandingkan performa model sebelum dan sesudah penerapan SMOTE menggunakan metrik yang sama.

## Latihan 1 — Deteksi anomali jaringan dengan SMOTE

Pilih satu topik di bidang TI yang diminati. Transformasikan melalui 5 tahap Problem Formation Model.

**Topik awal:** ________________________________________

| Tahap | Hasil |
|-------|-------|
| Reality | Model digunakan untuk deteksi anomali jaringan |
| Observed Issue (Symptom) | Performa meningkat setelah SMOTE |
| Diagnosed Problem (Root Cause) | Data berubah karena SMOTE |
| Researchable Problem | Belum jelas apakah performa meningkat itu valid |
| Measurable Variable | Akurasi, precision, recall, F1-score |

**Apakah terjebak solution-first thinking?** [ ] Ya / [v] Tidak
> Jika ya, kembali ke tahap mana? ________________________

---

## Latihan 2 — System Context Decomposition

Gambarkan konteks sistem dari masalah riset di Latihan 1.

| Komponen | Deskripsi |
|----------|----------|
| Input | Dataset trafik jaringan |
| Process | SMOTE + training model |
| Output | Hasil prediksi & metrik |
| Outcome | Model lebih akurat |
| Constraints | Dataset terbatas |
| Stakeholders | Peneliti & praktisi |

**Komponen mana yang paling relevan dengan masalah riset?** Process,karena masalah ada di SMOTE

---

## Latihan 3 — Problem Quality Check

Evaluasi problem statement yang sudah dibuat menggunakan 5 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Clarity | 5 | jelas fokus ke SMOTE |
| Measurability | 5 | pakai matriks jelas |
| Relevance | 5 | penting di ML |
| Testability | 5 | bisa dibandingkan |
| Impact | 4 | berguna untuk validasi metode |

**Skor total:** 24 / 25

**Problem statement versi final (1 paragraf):**
SMOTE memang bisa meningkatkan performa model deteksi anomali, tapi karena menghasilkan data buatan, ada kemungkinan hasil tersebut tidak mencerminkan kondisi nyata. Oleh karena itu, penelitian ini dilakukan untuk mengecek apakah peningkatan performa tersebut benar-benar valid atau hanya efek dari perubahan data.
---

## Refleksi

> Bandingkan "masalah" yang biasa ditemui saat coding (bug, error) dengan masalah riset. Apa perbedaan fundamental dalam cara mendefinisikan dan mendekati keduanya?

**Jawaban:**
> Masalah saat coding biasanya jelas dan langsung kelihatan, misalnya error, bug, atau fitur yang nggak jalan. Cara ngatasinnya juga langsung: cari penyebabnya di kode terus diperbaiki sampai sistem jalan normal.

> Sedangkan masalah riset itu nggak selalu kelihatan jelas. Kita harus nyari dulu akar masalahnya, bahkan kadang harus mempertanyakan apakah masalahnya memang benar ada atau cuma asumsi. Di riset juga nggak langsung nyari solusi, tapi lebih ke memahami masalah dan membuktikan dengan data apakah suatu klaim itu benar atau nggak.
