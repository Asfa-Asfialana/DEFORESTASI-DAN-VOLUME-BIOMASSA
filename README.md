# 🌲 Deforestasi

![transisi-hijau](https://github.com/Asfa-Asfialana/DEFORESTASI-DAN-VOLUME-BIOMASSA/blob/main/Diforestasi/transisi-hijau.png)

-----

## 🌳 Halo Sobat ETL! Selamat datang di repositori "Analisis Deforestasi" 🌱

Proyek ini dibuat dalam menyelesaikan week task, agar kita lebih peduli lingkungan dan tertarik dengan data! Di sini kita akan mengulas hubungan antara **deforestasi** di Indonesia dari tahun 2010 hingga 2024.

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

- Mengukur korelasi antara Deforestasi-biomassa, denda-ekspor kayu
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

## 3. Analisis Korelasi dan Regresi

#### 1. Analisis Korelasi

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


#### 2. Analisis Regresi

Setelah melakukan analisis korelasi, kemudia kita lanjut menganalisis regresi. Kode python yang digunakan dalam analisis ini adalah :

```
from sklearn.linear_model import LinearRegression

# Regresi Denda Ekspor vs Deforestasi
X = data[['Denda_Ekspor_USD_juta']]
y = data['Deforestasi_ha']
model = LinearRegression().fit(X, y)

print(f"Koefisien Regresi: {model.coef_[0]:.2f}")
print(f"Intercept: {model.intercept_:.2f}")
print(f"R-squared: {model.score(X, y):.2f}")

# Prediksi
predicted = model.predict(X)
```

Dan berikut hasil analisis regresi yang kita dapatkan dari data generate sebelumnya ;

- Koefisien Regresi: 4.57

- Intercept: 211211.68

- R-squared: 0.00

## 📚 4. Penjelasan

#### 1. Korelasi Deforestasi - Biomassa

Secara ekologis, biomassa hutan adalah jumlah total materi organik hidup dalam ekosistem hutan—terutama pohon dan tumbuhan yang menyimpan karbon. Deforestasi adalah proses kehilangan tutupan pohon alami secara permanen, baik karena aktivitas manusia maupun sebab alam.

Dalam teori ekologi:

“Semakin tinggi tingkat deforestasi, maka semakin rendah cadangan biomassa, karena pohon yang ditebang membawa karbon dan biomassa keluar dari ekosistem.” (Malhi et al., 2014; FAO, 2010)

Namun hubungan ini tidak selalu linier atau kuat, karena dipengaruhi banyak faktor eksternal dan kebijakan. Beberapa faktor yang menyebabkan deforestasi adalah :

- Faktor Ekonomi : pertambangan, pengalihan fungsi lahan menjadi perkebunan atau pertanian, pembangunan infarstruktur dll
  
- Faktor Sosial : Konflik agraria, perpindahan penduduk, kurangnya kesadaran lingkungan
  
- Faktor Pemerintah : Hukum yang lemah, Kebijakan yang memicu eksploliasi, dan kurangnya program konservasi.

Dalam analisis korelasi ini saya menggunakan batasan nilai korelasi Cohen’s Convention (1988). Cohen menyarankan:

0.10 = kecil (small)

0.30 = sedang (medium)

0.50 = besar (large)

Berikut hasil visualisasi data yang saya tampilkan dari hasil analisis korelasi deforestasi dan biomassa.

![korelasi deforestasi-biomassa](https://github.com/Asfa-Asfialana/DEFORESTASI-DAN-VOLUME-BIOMASSA/blob/main/Diforestasi/korelasi%20deforestasi-biomassa.png)

**Keterangan:**
- Setiap titik merepresentasikan satu tahun pengamatan.
- Terlihat pola bahwa saat deforestasi meningkat, nilai biomassa cenderung menurun.
- Hasil perhitungan korelasi adalah **-0.31**, menunjukkan hubungan **negatif lemah** antara keduanya.

Berikut adalah penjelasan ilmiahnya dari hasil analisis yang didapatkan :

1. Menurut FAO (2010), jenis dan intensitas penebangan menentukan seberapa banyak biomassa yang hilang. Jadi mungkin saja hanya penebangan selektif (selective logging) hanya menghilangkan sebagian pohon bernilai komersial, sedangkan vegetasi lain masih menyimpan cadangan biomassa.

2. Menurut Gibbs et al. (2007), distribusi biomassa sangat bervariasi tergantung jenis ekosistem hutan. Jadi mungkin deforestasi terjadi di hutan dengan cadangan biomassa rendah, maka dampaknya terhadap total biomassa tidak besar.

3. Penurunan biomassa juga bisa disebabkan oleh faktor non-deforestasi, seperti:

- Musim kemarau ekstrem

- Kebakaran hutan alami

- Hama dan penyakit

#### 2. Korelasi Denda Ekspor Kayu Illegal - Jumlah Ekspor Kayu

Secara kebijakan, **denda atas ekspor kayu ilegal** dimaksudkan sebagai alat pengendali deforestasi. Dalam teori hukum lingkungan dan ekonomi hijau:

> "Peningkatan sanksi finansial terhadap pelaku ilegal logging seharusnya memberikan efek jera, mengurangi insentif eksploitasi, dan pada akhirnya menurunkan laju deforestasi."
> — *CIFOR, 2020; FAO, 2010*

Namun, efektivitas kebijakan ini sangat tergantung pada:

* Konsistensi penegakan hukum
* Keterbukaan pasar ekspor
* Kekuatan aktor swasta dan politik

* Korelasi antara **Denda Ekspor (USD juta)** dan **Deforestasi (ha)**:
  `r = 0.02` → **sangat lemah, hampir tidak ada hubungan**

* Visualisasi hubungan:

![korelasi denda-jumlah](https://github.com/Asfa-Asfialana/DEFORESTASI-DAN-VOLUME-BIOMASSA/blob/main/Diforestasi/korelasi%20denda-jumlah.png)

📎 *Garis tren datar dan interval kepercayaan lebar menunjukkan bahwa kenaikan denda tidak diikuti perubahan deforestasi yang konsisten.*

Beberapa faktor yang memungkinkah hal ini terjadi adalah :

1. Banyak pelaku tidak membayar denda atau mendapat sanksi ringan saja (WALHI, 2022).
2. Denda hanya dikenakan pada pelanggaran, bukan pada ekspor legal yang juga bisa menimbulkan deforestasi.
3. Permintaan global kayu, konversi lahan sawit, tambang, dan infrastruktur lebih berdampak terhadap deforestasi

> Korelasi yang hampir nol menunjukkan bahwa **denda ekspor tidak efektif secara langsung dalam menekan deforestasi** dalam data ini. Upaya menurunkan deforestasi memerlukan kebijakan yang lebih menyeluruh: moratorium izin, peningkatan pengawasan, hingga insentif konservasi untuk masyarakat dan pelaku industri.

#### 3. HeatMap Korelasi

Nah sobat ETL langkah selanjutnya sebelum masuk ke analisis regresi adalah kita akan melihat hubungan antara deforestasi, biomassa, dan kebijakan ekspor. Melihat bagaimana setiap variabel saling memengaruhi satu sama lain. 

![matrikskorelasi](https://github.com/Asfa-Asfialana/DEFORESTASI-DAN-VOLUME-BIOMASSA/blob/main/Diforestasi/matrikskorelasi.png)

Dari hasil visualisasi data diatas maka dapat kita lihat bahwa 

1. Tahun – Denda_Ekspor_USD_juta berkorelasi sebesar  0.89 : Kuat positif → tren kenaikan denda setiap tahun
2. Deforestasi_ha – Biomassa_ton_ha berkorelasi sebesar –0.31 : Lemah-negatif → deforestasi cenderung mengurangi biomassa
3. Denda_Ekspor – Deforestasi berkorelasi sebesar 0.019 : Hampir nol → tidak berkaitan secara langsung
4. Ekspor_Kayu – Denda berkorelasi sebesar 0.16 : Sangat lemah positif
5. Deforestasi – Ekspor_Kayu berkorelasi sebesar 0.084  : Tidak signifikan    

#### 4. Analisis Regresi

Dari hasil analisis korelasi maka proyek ini dilanjutkan untuk analisis regresi. Analisis ini penting untuk melihat seberapa pengaruh variabel denda_ekspor dengan deforestasi. 
Meskipun Korelasi sangat lemah, tapi regresi bisa mengevaluasi kegagalan kebijakan: apakah denda menjadi solusi efektif atau tidak efektif.
Dari hasil analisis berdasarkan generate data yang telah dilakukan, maka hasil uji regresi adalah :
```
Koefisien Regresi: 4.57
Intercept: 211211.68
R-squared: 0.00
```
Dapat dilihat bahwa hasil uji regresi sangat lemah yang memungkin beberapa alasan yang menjadi penyebabnya :
1. Penegakan Denda Tidak Efektif, Banyak kasus denda tidak dibayar, tidak ditindaklanjuti, atau jumlahnya kecil dibanding keuntungan ekonomi dari ekspor kayu ilegal. Menurut WALHI (2022): "Hanya 8% pelaku ilegal logging dikenai sanksi hukum tegas."
2. Data denda hanya mencakup pelanggaran yang terdeteksi → padahal banyak kasus tidak tercatat
3. Data bersifat sintetis


## Implementasi Kebijakan

Berdasarkan hasil analisis regresi dan korelasi yang menunjukkan bahwa **denda ekspor tidak berpengaruh signifikan terhadap deforestasi, maka **implementasi kebijakan yang lebih menyeluruh dan multisektor** sangat diperlukan.

#### 🏛️ 1. **Sektor Pemerintah**

* Perkuat sistem penegakan hukum agar **denda tidak hanya simbolis**, tetapi benar-benar menimbulkan efek jera.
* Gunakan mekanisme **pengawasan berbasis satelit dan AI** (seperti GFW, FLEGT) untuk deteksi dini dan transparansi pelanggaran.
* Denda yang meningkat progresif + black list ekspor

📚 *Contoh implementasi kebijakan yang bisa dicontoh : 

- [Vietnam–EU VPA/FLEGT overview (Vietnam Briefing)](https://www.vietnam-briefing.com/news/eu-deforestation-regulations-vietnam.html)
  
- [Forest Trends: Vietnam Timber Legality Assurance (Decree 102/2020)](https://www.forest-trends.org/publications/vietnam-timber-legality-risk-dashboard/)


#### 🧑‍🌾 2. **Masyarakat Lokal dan Komunitas Adat**

* Memberi kompensasi kepada masyarakat yang menjaga hutan.
* Percepat legalisasi hak kelola hutan untuk masyarakat adat dan lokal.
* Dampaknya: hutan dikelola secara berkelanjutan → lebih tahan terhadap tekanan deforestasi.


#### 🏢 3. **Sektor Swasta dan Industri**

* Wajibkan seluruh perusahaan mengikuti **Sistem Verifikasi Legalitas Kayu (SVLK)** secara ketat.
* Diberi insentif ekspor hanya untuk pelaku bersertifikat.
* Gunakan sumber kayu dari **Hutan Tanaman Industri (HTI)** dan bukan dari konversi hutan alam.
* Terapkan prinsip **No Deforestation, No Peat, No Exploitation (NDPE)**
* Libatkan swasta dalam proyek **reforestasi dan rehabilitasi DAS** sebagai bagian dari tanggung jawab sosial perusahaan (CSR).

## 5. Kesimpulan

Dalam upaya pemerintah melakukan transisi energi hijau memang tidak mudah dan akan selalu menemukan tantangan. Kita exo techno leader sebagai generasi muda memegang peran penting dalam menjaga keberlanjutan hutan dan lingkungan. Melalui analisis sederhana ini, meskipun menggunakan data sintetis, kita telah menunjukkan bahwa data dapat menjadi alat kritis untuk memahami deforestasi, biomassa, dan efektivitas kebijakan. Studi ini tidak hanya menjadi contoh teknis, tetapi juga membuka ruang untuk riset lebih lanjut dengan data nyata sebagai fondasi perubahan kebijakan berbasis bukti.

💡 SEMANGAT SOBAT ETL, SEMOGA RISET SEDERHANA KITA MENJADI LANGKAH UNTUK PERUBAHAN YANG LEBIH BESAR DI MASA DEPAN !
