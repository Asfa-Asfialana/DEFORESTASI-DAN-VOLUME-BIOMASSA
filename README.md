# 🌲 Korelasi Deforestasi dan Volume Biomassa (2015–2024)

Analisis ini bertujuan untuk mengeksplorasi hubungan antara deforestasi dan hilangnya volume biomassa di Indonesia selama satu dekade terakhir. Fokus khusus diberikan pada wilayah Sumatera sebagai salah satu pusat tekanan deforestasi nasional. Penelitian ini dilakukan dengan pendekatan kuantitatif menggunakan Python dan visualisasi data.

---

## 🧭 Pendahuluan

### 📌 Latar Belakang

Indonesia merupakan salah satu negara dengan kawasan hutan tropis terluas di dunia, namun menghadapi tantangan serius berupa deforestasi yang masif setiap tahunnya. Aktivitas pembukaan lahan, konversi hutan untuk perkebunan, dan praktik penebangan ilegal telah menyebabkan hilangnya tutupan hutan yang berdampak besar terhadap lingkungan.

Salah satu dampak langsung dari deforestasi adalah berkurangnya **biomassa**, yaitu total massa organik yang tersimpan dalam vegetasi hidup. Biomassa ini memainkan peran penting sebagai penyerap karbon alami. Ketika pohon ditebang, karbon yang tersimpan dilepaskan ke atmosfer dan mempercepat laju perubahan iklim.

Analisis ini dilakukan untuk memahami bagaimana besarnya hubungan antara deforestasi dan hilangnya volume biomassa. Pengetahuan ini penting untuk mendukung pengambilan kebijakan berbasis bukti.

### 🎯 Tujuan Analisis

- Mengukur korelasi antara tingkat kehilangan tutupan hutan dan kehilangan volume biomassa di Indonesia (2015–2024).
- Menyediakan visualisasi data yang jelas dan informatif sebagai bukti visual hubungan tersebut.
- Memberikan informasi berbasis data yang dapat digunakan oleh berbagai pihak untuk mendukung kebijakan dan aksi lingkungan.

### 🌱 Manfaat Analisis

| Pihak         | Manfaat                                                                 |
|---------------|--------------------------------------------------------------------------|
| Pemerintah    | Landasan ilmiah untuk kebijakan konservasi dan mitigasi perubahan iklim |
| Perusahaan    | Penguatan komitmen emisi karbon dan transparansi laporan lingkungan     |
| Alam          | Perlindungan keanekaragaman hayati dan penyimpanan karbon                |
| Masyarakat    | Kesadaran lingkungan dan keterlibatan aktif dalam pelestarian hutan      |

---

## 🗂️ Pembuatan Data Set

Data yang digunakan bersumber dari [Global Forest Watch](https://data.globalforestwatch.org/) yang mencakup:
- Hilangnya tutupan hutan (tree cover loss) per tahun
- Estimasi emisi karbon dan kehilangan biomassa dalam satuan CO2e
- Spesifik untuk wilayah Sumatera dari tahun 2015–2024

Data dikompilasi dalam file `biomassa_deforestasi_sumatera.csv`.

---

## 🧪 Kode Python Analisis

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load data
df = pd.read_csv('biomassa_deforestasi_sumatera.csv')

# Korelasi
correlation = df['biomass_loss'].corr(df['tree_cover_loss'])
print(f"Korelasi antara deforestasi dan kehilangan biomassa: {correlation:.2f}")
