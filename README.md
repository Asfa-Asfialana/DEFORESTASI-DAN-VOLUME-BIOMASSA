# 🌲 Korelasi Deforestasi dan Volume Biomassa

![FOREST](https://github.com/Asfa-Asfialana/DEFORESTASI-DAN-VOLUME-BIOMASSA/blob/main/Diforestasi/FOREST.gif)

-----
Halo sobat ETL ku dimanapun berada, repositori kali ini berisi weektask yang mengambil kasus Deforestasi dan Volume Biomassa. 

Analisis ini bertujuan untuk membantu upaya Indonesia dalam Transisi Hijau. Hasil analisis ini diharapkan mampu digunakan untuk mendorong kebijakan berkelanjutan, memantau emisi, dan memastikan penggunaan sumber daya yang tidak merusak lingkungan.

---

## 🧭 Pendahuluan

### 📌 Latar Belakang

Perubahan iklim global dan tingginya emisi gas rumah kaca telah mendorong dunia untuk melakukan transisi energi hijau, yaitu peralihan dari energi fosil ke energi ramah lingkungan seperti tenaga surya, angin, dan biomassa. Namun, pemanfaatan biomassa harus disertai pengelolaan hutan yang berkelanjutan. Jika tidak, justru akan mempercepat deforestasi dan memperburuk kerusakan lingkungan.

Indonesia sebagai negara dengan hutan tropis terbesar ketiga di dunia memiliki peran strategis dalam menjaga keseimbangan ekosistem dan mendukung transisi hijau. Sayangnya, laju deforestasi di Indonesia masih tinggi, terutama akibat ekspansi perkebunan, kebakaran hutan, dan penebangan ilegal.

Dengan memahami hubungan antara deforestasi dan penurunan volume biomassa, kita bisa:

- Menganalisis dampaknya terhadap emisi karbon dan krisis iklim

- Menyusun kebijakan energi dan kehutanan yang lebih bijak

- Memberikan rekomendasi solusi untuk menjaga hutan sekaligus mendukung energi bersih

1. Deforestasi
Deforestasi adalah proses penghilangan hutan secara permanen untuk keperluan lain seperti pertanian, perkebunan, pemukiman, atau pertambangan. Kegiatan ini menyebabkan berkurangnya tutupan pohon alami, yang berdampak pada hilangnya keanekaragaman hayati, meningkatnya emisi karbon, dan terganggunya siklus air serta iklim global.

2. Biomassa
Biomassa adalah materi organik yang berasal dari makhluk hidup, seperti tanaman, kayu, limbah pertanian, atau alga. Biomassa bisa dimanfaatkan sebagai sumber energi terbarukan karena dapat dibakar atau diolah menjadi bioenergi (biofuel, biogas, dll).

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
