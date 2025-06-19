# 🌲 Deforestasi dan Volume Biomassa

![transisi-hijau](https://github.com/Asfa-Asfialana/DEFORESTASI-DAN-VOLUME-BIOMASSA/blob/main/Diforestasi/transisi-hijau.png)

-----

## 🌳 Halo Sobat ETL! Selamat datang di repositori "Analisis Deforestasi & Biomassa" 🌱

Proyek ini dibuat dalam menyelesaikan week task, agar kita lebih yang peduli lingkungan dan tertarik dengan data! Di sini kita akan mengulas hubungan antara **deforestasi** dan **volume biomassa** di Indonesia dari tahun 2010 hingga 2024.

Kenapa ini penting? Karena biomassa punya potensi besar sebagai energi hijau, tapi deforestasi bisa bikin cadangan biomassa menurun drastis. Lewat analisis data dan visualisasi, kita coba cari tahu seberapa besar dampaknya, dan bagaimana data ini bisa bantu mendukung **transisi energi hijau** yang adil dan berkelanjutan.

Yuk, kita gali bareng-bareng! Semoga proyek ini bisa jadi referensi, inspirasi, atau bahkan langkah awal ide besar berikutnya untuk kita semua🌏✨


---

## 🧭 1. Pendahuluan

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

## 🗂️2. Pembuatan Data Set

Data yang digunakan dalam proyek ini adalah data sintetis yang disusun untuk mensimulasikan hubungan antara deforestasi, biomassa, ekspor kayu, dan denda ekspor ilegal di Indonesia.

Penggunaan data sintetis dilakukan karena:

- Data publik yang lengkap dan terstruktur sulit diakses, khususnya untuk rentang tahun 2010–2024.

- Beberapa data bersifat terbatas, tersebar di berbagai sumber, atau tidak tersedia secara terbuka.

namun data ini tetap mempertimbangkan beberapa hal seperti :

- Struktur dan variabel yang menyerupai data nyata, seperti tahun, deforestasi (ha), biomassa (ton/ha), denda ekspor (USD Juta) dan ekspor kayu (ton)

- Pola tren berdasarkan referensi literatur dan laporan resmi
  
- Hubungan logis antar variabel, misalnya: semakin tinggi deforestasi, semakin besar biomassa hilang dan potensi emisi.

#### 🔧 Cara Generate Data

Data dibangkitkan menggunakan Python (`pandas`, `numpy`) dengan rentang waktu tahun **2010–2024**. Berikut adalah batasan dan asumsi yang saya terapkan:

### 📌 Batasan dan Asumsi

| Variabel                 | Penjelasan                                                                 |
|--------------------------|----------------------------------------------------------------------------|
| `Deforestasi_ha`         | Dibuat dengan nilai acak antara 6.000–12.000 ha, kemudian ditambahkan tren tahunan linear (×100/tahun) untuk mensimulasikan kenaikan deforestasi. |
| `Biomassa_ton_ha`        | Dibuat dari distribusi acak `uniform` antara 100–600 ton/ha, **dengan tren menurun** agar mencerminkan degradasi biomassa akibat deforestasi. |
| `Denda_Ekspor_USD_juta` | Nilai acak 10–25 juta USD, lalu ditambah tren tetap sebesar 2 juta per tahun dari 2010, mensimulasikan kebijakan yang makin ketat. |
| `Ekspor_Kayu_ton`        | Nilai acak antara 2.000–5.000 ton, ditambah pertumbuhan 50 ton per tahun, untuk merefleksikan peningkatan permintaan dan produksi ekspor. |

#### 🧪 Kode Generate Data

```python
import pandas as pd
import numpy as np

np.random.seed(42)
years = np.arange(2010, 2025)

deforestation = np.random.randint(6000, 12000, size=15) + years*100
biomass = np.random.uniform(600, 100, size=15).round(2)  # tren menurun
export_fine = np.random.randint(10, 25, size=15) + (years - 2010)*2
timber_export = np.random.randint(2000, 5000, size=15) + (years - 2010)*50

data = pd.DataFrame({
    'Tahun': years,
    'Deforestasi_ha': deforestation,
    'Biomassa_ton_ha': biomass,
    'Denda_Ekspor_USD_juta': export_fine,
    'Ekspor_Kayu_ton': timber_export
})

print(data)
```

Berikut adalah data hasil genetare yang dihasilkan melalui kode python diatas :



---

### Analisis Korelasi dan Regresi

Sobat ETL ku, dalam analisis korelasi dan regresi aku menggunakan beberapa library yaitu Pandas, NumPy, Matplotlib, dan Seaborn untuk analisis data.

Berikut adalah kode Python yang aku gunakan :

```python
# Hitung korelasi antara deforestasi dan biomassa
corr_biomass_defor = data['Deforestasi_ha'].corr(data['Biomassa_ton_ha'])
print(f"Korelasi Deforestasi-Biomassa: {corr_biomass_defor:.2f}")
```

Dan nilai yang didapatkan dari hasil analisis korelasi deforestasi dan biomassa adalah : -0.31

```python
# Korelasi antara denda ekspor dan deforestasi
corr_fine_defor = data['Denda_Ekspor_USD_juta'].corr(data['Deforestasi_ha'])
print(f"Korelasi Denda Ekspor-Deforestasi: {corr_fine_defor:.2f}")
```

Dan hasil yang didapatkan dari hasil analisis Korelasi Denda Ekspor-Deforestasi: 0.02

```python
# Korelasi antara semua variabel
correlation_matrix = data.corr()
print("\nMatriks Korelasi:")
print(correlation_matrix)
```

Dan hasil yang didapatkan setelah melakukan analisis korelasi antara semua variabel adalah :
|                              | Tahun  | Deforestasi\_ha | Biomassa\_ton\_ha | Denda\_Ekspor\_USD\_juta | Ekspor\_Kayu\_ton |
| ---------------------------- | ------ | --------------- | ----------------- | ------------------------ | ----------------- |
| **Tahun**                    | 1.000  | -0.013          | 0.119             | 0.889                    | 0.213             |
| **Deforestasi\_ha**          | -0.013 | 1.000           | -0.306            | 0.019                    | 0.084             |
| **Biomassa\_ton\_ha**        | 0.119  | -0.306          | 1.000             | 0.189                    | 0.099             |
| **Denda\_Ekspor\_USD\_juta** | 0.889  | 0.019           | 0.189             | 1.000                    | 0.160             |
| **Ekspor\_Kayu\_ton**        | 0.213  | 0.084           | 0.099             | 0.160                    | 1.000             |
