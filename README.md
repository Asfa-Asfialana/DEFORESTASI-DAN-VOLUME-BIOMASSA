# 🌲 Deforestasi dan Volume Biomassa

![FOREST](https://github.com/Asfa-Asfialana/DEFORESTASI-DAN-VOLUME-BIOMASSA/blob/main/Diforestasi/FOREST.gif)

-----

## 🌳 Halo Sobat ETL! Selamat datang di repositori "Analisis Deforestasi & Biomassa" 🌱

Proyek ini dibuat dalam menyelesaikan week task, agar kita lebih yang peduli lingkungan dan tertarik dengan data! Di sini kita akan mengulas hubungan antara **deforestasi** dan **volume biomassa** di Indonesia dari tahun 2010 hingga 2024.

Kenapa ini penting? Karena biomassa punya potensi besar sebagai energi hijau, tapi deforestasi bisa bikin cadangan biomassa menurun drastis. Lewat analisis data dan visualisasi, kita coba cari tahu seberapa besar dampaknya, dan bagaimana data ini bisa bantu mendukung **transisi energi hijau** yang adil dan berkelanjutan.

Yuk, kita gali bareng-bareng! Semoga proyek ini bisa jadi referensi, inspirasi, atau bahkan langkah awal ide besar berikutnya untuk kita semua🌏✨


---

## 🧭 Pendahuluan

#### 📌 Latar Belakang

Perubahan iklim global dan tingginya emisi gas rumah kaca telah mendorong dunia untuk melakukan transisi energi hijau, yaitu peralihan dari energi fosil ke energi ramah lingkungan seperti tenaga surya, angin, dan biomassa. Namun, pemanfaatan biomassa harus disertai pengelolaan hutan yang berkelanjutan. Jika tidak, justru akan mempercepat deforestasi dan memperburuk kerusakan lingkungan.

Indonesia sebagai negara dengan hutan tropis terbesar ketiga di dunia memiliki peran strategis dalam menjaga keseimbangan ekosistem dan mendukung transisi hijau. Sayangnya, laju deforestasi di Indonesia masih tinggi, terutama akibat ekspansi perkebunan, kebakaran hutan, dan penebangan ilegal.

Dengan memahami hubungan antara deforestasi dan penurunan volume biomassa, kita bisa:

- Menyusun kebijakan energi dan kehutanan yang lebih bijak

- Memberikan rekomendasi solusi untuk menjaga hutan sekaligus mendukung energi bersih

1. Deforestasi
   
Deforestasi adalah proses penghilangan hutan secara permanen untuk keperluan lain seperti pertanian, perkebunan, pemukiman, atau pertambangan. Kegiatan ini menyebabkan berkurangnya tutupan pohon alami, yang berdampak pada hilangnya keanekaragaman hayati, meningkatnya emisi karbon, dan terganggunya siklus air serta iklim global.

2. Biomassa
   
Biomassa adalah materi organik yang berasal dari makhluk hidup, seperti tanaman, kayu, limbah pertanian, atau alga. Biomassa bisa dimanfaatkan sebagai sumber energi terbarukan karena dapat dibakar atau diolah menjadi bioenergi (biofuel, biogas, dll).

#### 🎯 Tujuan Analisis

- Mengukur korelasi antara tingkat kehilangan tutupan hutan dan kehilangan volume biomassa di Indonesia (2015–2024).
- Menyediakan visualisasi data yang jelas dan informatif sebagai bukti visual hubungan tersebut.
- Memberikan informasi berbasis data yang dapat digunakan oleh berbagai pihak untuk mendukung kebijakan dan aksi lingkungan.

#### 🌱 Manfaat Analisis

| Pihak         | Manfaat                                                                 |
|---------------|--------------------------------------------------------------------------|
| Pemerintah    | Landasan ilmiah untuk kebijakan konservasi dan mitigasi perubahan iklim |
| Perusahaan    | Penguatan komitmen emisi karbon dan transparansi laporan lingkungan     |
| Alam          | Perlindungan keanekaragaman hayati dan penyimpanan karbon                |
| Masyarakat    | Kesadaran lingkungan dan keterlibatan aktif dalam pelestarian hutan      |

---

### 🗂️ Pembuatan Data Set

Kali ini data yang saya gunakan adalah data sintetis yang berdasarkan pola umum deforestasi dan biomassa di Indonesia untuk keperluan simulasi analisis.

Data dikompilasi dalam file `deforestasi-dan-biomassa.csv`.

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
