# Identifikasi, Ingestion, dan Penyimpanan Data Saham
## Anggota
- Mochamad Zidan Rusdhiana (2305464)
- Muhammad Daffa Ma'arif (2305771)
- Yusrilia Hidayanti (2306828)
- Ismail Fatih Raihan (2307840)
- Hafsah Hamidah (2311474)
- Yahyo Abdullozoda (2313368)

## Latar Belakang
Dalam analisis keuangan, data laporan keuangan dan berita pasar memainkan peran penting dalam memahami pergerakan pasar saham. **Yahoo Finance (yfinance)**, **IDX (Bursa Efek Indonesia)**, dan **IQPlus** menyediakan berbagai data penting yang digunakan untuk analisis pasar saham. Proses pengumpulan data dilakukan menggunakan teknik seperti API, XML parsing, dan web scraping, yang kemudian disimpan dalam MongoDB untuk analisis lebih lanjut.

## Sumber Data
### 1. **yfinance**
- **Sumber Data**: Data diperoleh dari Yahoo Finance menggunakan library `yfinance`.
- **Jenis Data yang Disediakan**:
  - **Harga Saham**: Harga pembukaan (Open), tertinggi (High), terendah (Low), dan penutupan (Close).
  - **Volume Perdagangan**: Jumlah saham yang diperdagangkan dalam periode tertentu.
  - **Data Tambahan**: Informasi mengenai dividen, stock splits, serta data historis dan statistik keuangan lainnya.
- **Keunggulan**:
  - Data historis lengkap dan dapat diunduh melalui API.
  - Tersedia dalam format Pandas DataFrame yang mudah digunakan.
  - Mudah diintegrasikan dengan Python untuk analisis lebih lanjut.

### 2. **IDX (Bursa Efek Indonesia)**
- **Sumber Data**: Website resmi IDX yang menyediakan laporan keuangan dalam format XBRL/XML.
- **Jenis Data yang Disediakan**:
  - **Data Perusahaan Tercatat**: Profil dan kinerja perusahaan yang terdaftar di BEI.
  - **Laporan Keuangan dan Tahunan**: Laporan keuangan yang dapat diunduh dalam format XBRL/XML.
  - **Data Perdagangan Saham**: Data harga saham dan volume transaksi.
- **Keunggulan**:
  - Menyediakan data resmi yang sangat kredibel dan mendetail mengenai perusahaan yang terdaftar di BEI.
  - Format XBRL yang memungkinkan analisis mendalam.

### 3. **IQPlus**
- **Sumber Data**: Layanan berita keuangan yang menyediakan informasi terkait pasar modal dan ekonomi.
- **Jenis Data yang Disediakan**:
  - **Berita Pasar Modal**: Update terkini terkait perusahaan yang terdaftar di BEI dan pengaruhnya terhadap harga saham.
  - **Laporan Keuangan dan Kinerja Perusahaan**: Informasi laba rugi, arus kas, dan neraca keuangan.
  - **Sinyal Pasar dan Rekomendasi Saham**: Analis memberikan rekomendasi beli, jual, atau tahan untuk saham tertentu.
- **Keunggulan**:
  - Menyediakan berita real-time yang membantu investor merespons pergerakan pasar dengan cepat.
  - Tersedia dalam format yang mudah diakses melalui website dan aplikasi mobile.

## Proses Pengumpulan Data
### 1. **Pengambilan Data yfinance**
   Data diambil menggunakan **API yfinance** untuk mendapatkan data historis saham dalam format JSON atau DataFrame. Data ini mencakup informasi seperti harga saham, volume perdagangan, dan data fundamental lainnya.

### 2. **Pengunduhan dan Parsing Data IDX**
   Data laporan keuangan diambil dari situs **IDX** dalam format XML/XBRL. Menggunakan **Selenium** dan **BeautifulSoup**, kita melakukan pengunduhan file `instance.zip`, mengekstrak data, dan mengonversinya ke format yang dapat digunakan.

### 3. **Web Scraping IQPlus**
   Berita pasar dan laporan keuangan diambil menggunakan **Selenium** untuk melakukan scraping pada halaman IQPlus. Berita terkait saham dan ekonomi diambil, kemudian data yang diperoleh diproses dan disimpan dalam format yang sesuai.

## Penyimpanan Data di MongoDB
Semua data yang diperoleh dari **yfinance**, **IDX**, dan **IQPlus** kemudian disimpan dalam **MongoDB**. MongoDB dipilih karena kemampuannya dalam menyimpan data yang tidak terstruktur dan memungkinkan akses yang cepat untuk query data besar.

## Struktur MongoDB
- **Koleksi yfinance**: Menyimpan data saham dalam format JSON, termasuk harga saham, volume, dan data lainnya.
- **Koleksi IDX**: Menyimpan laporan keuangan perusahaan dalam format JSON.
- **Koleksi IQPlus**: Menyimpan berita dan analisis terkait pasar modal dalam format JSON.

## Instruksi Penggunaan
1. **Instalasi Dependensi**:
   Pastikan Python dan pip sudah terinstall. Kemudian install dependensi yang dibutuhkan:
   ```bash
   pip install selenium beautifulsoup4 requests pymongo yfinance xmltodict
