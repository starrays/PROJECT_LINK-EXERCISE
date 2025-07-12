# 🌱 FUNDAMENTAL – Excel & Statistik Deskriptif

Statistik deskriptif adalah fondasi analisis data yang membantu kita memahami karakteristik dan pola dalam dataset.

---

## 📊 Apa Itu Statistik Deskriptif?

Statistik deskriptif adalah metode untuk meringkas dan mendeskripsikan karakteristik utama dari dataset. Tujuannya adalah memberikan gambaran umum tentang data tanpa melakukan inferensi.

---

## 🧮 Ukuran Tendensi Sentral

### Mean (Rata-rata)
- Rumus: `=AVERAGE(range)`
- Jumlah semua nilai dibagi jumlah observasi
- Sensitif terhadap outlier

### Median
- Rumus: `=MEDIAN(range)`
- Nilai tengah setelah data diurutkan
- Lebih robust terhadap outlier

### Mode
- Rumus: `=MODE(range)`
- Nilai yang paling sering muncul
- Bisa ada lebih dari satu mode

---

## 📈 Ukuran Dispersi

### Standard Deviation
- Rumus: `=STDEV(range)`
- Mengukur seberapa tersebar data dari mean
- Semakin besar, semakin tersebar data

### Variance
- Rumus: `=VAR(range)`
- Kuadrat dari standard deviation
- Digunakan dalam perhitungan statistik lanjutan

### Range
- Rumus: `=MAX(range) - MIN(range)`
- Selisih nilai tertinggi dan terendah
- Ukuran dispersi paling sederhana

---

## 📋 Excel Functions Penting

| Function | Keterangan | Contoh |
|----------|------------|--------|
| `=AVERAGE()` | Rata-rata | `=AVERAGE(A2:A100)` |
| `=MEDIAN()` | Median | `=MEDIAN(A2:A100)` |
| `=MODE()` | Mode | `=MODE(A2:A100)` |
| `=STDEV()` | Standard deviation | `=STDEV(A2:A100)` |
| `=VAR()` | Variance | `=VAR(A2:A100)` |
| `=CORREL()` | Correlation | `=CORREL(A2:A100, B2:B100)` |
| `=QUARTILE()` | Quartile | `=QUARTILE(A2:A100, 1)` |

---

## 📊 Interpretasi Hasil

### Mean vs Median
- Jika mean > median: distribusi skewed ke kanan
- Jika mean < median: distribusi skewed ke kiri
- Jika mean ≈ median: distribusi simetris

### Standard Deviation
- SD kecil: data terkumpul di sekitar mean
- SD besar: data tersebar jauh dari mean

### Correlation
- 0.7-1.0: Korelasi kuat positif
- 0.3-0.7: Korelasi moderat positif
- -0.3-0.3: Korelasi lemah
- -0.7-(-0.3): Korelasi moderat negatif
- -1.0-(-0.7): Korelasi kuat negatif

---

## 💡 Tips Praktis

1. **Selalu cek data quality** sebelum analisis
2. **Gunakan multiple measures** untuk pemahaman lengkap
3. **Visualisasikan data** untuk insight tambahan
4. **Interpretasikan dalam konteks bisnis**

---

## 🔗 Referensi
- [Excel Statistical Functions](https://support.microsoft.com/en-us/excel)
- [Descriptive Statistics](https://www.statisticshowto.com/)
- [Business Analytics](https://www.investopedia.com/)

---

> "Statistik deskriptif adalah bahasa untuk memahami data. Kuasai ini, dan kamu akan bisa bercerita dengan angka." 