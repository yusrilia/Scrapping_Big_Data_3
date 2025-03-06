# Latar Belakang
Dalam analisis keuangan, berita ekonomi memainkan peran penting dalam memahami sentimen pasar dan tren industri. IQPlus menyediakan berita keuangan yang harus diolah melalui proses ingestion menggunakan web scraping dengan tools seperti BeautifulSoup atau Selenium. Data yang diekstrak berupa teks tidak terstruktur, sehingga memerlukan pembersihan dan strukturisasi sebelum disimpan dalam database seperti MongoDB atau Elasticsearch. Penyimpanan ini memungkinkan pencarian cepat dan analisis lebih lanjut, seperti sentimen analisis dan identifikasi tren pasar.

# **Web Scraping IQPlus dengan Selenium**  

Proses web scraping dari IQPlus menggunakan **Selenium** memerlukan beberapa tahapan untuk mengambil data berita dengan aman dan efisien. Berikut adalah alur kerjanya:  

### **1. Inisialisasi Selenium**  
- Install pustaka yang diperlukan:  
  ```bash
  pip install selenium beautifulsoup4
  ```  
- Tentukan **driver browser** (misalnya, **ChromeDriver** atau **GeckoDriver**).  
- Atur opsi Selenium agar berjalan tanpa tampilan GUI (headless mode) jika diperlukan.  

### **2. Akses Halaman Utama IQPlus**  
- Buka situs IQPlus menggunakan Selenium.  
- Tunggu hingga elemen utama halaman dimuat sepenuhnya menggunakan **WebDriverWait**.  

### **3. Navigasi dan Pengambilan Data Berita**  
- Identifikasi daftar berita menggunakan XPath atau **CSS Selector**.  
- Loop melalui daftar berita untuk mengambil:  
  - **Judul berita**  
  - **Tanggal publikasi**  
  - **Ringkasan berita**  
  - **URL detail berita**  

### **4. Navigasi ke Halaman Detail Berita**  
- Klik setiap berita atau akses langsung halaman detailnya.  
- Ambil **isi lengkap berita** menggunakan BeautifulSoup atau metode Selenium seperti `.text`.  

### **5. Penyimpanan Data**  
- Format data dalam bentuk JSON atau dictionary:  
  ```json
  {
    "judul": "Judul Berita",
    "tanggal": "YYYY-MM-DD",
    "ringkasan": "Ringkasan singkat...",
    "isi": "Isi lengkap berita...",
    "url": "https://iqplus.info/..."
  }
  ```
- Simpan data ke **MongoDB**, **CSV**, atau **JSON file**.  

### **6. Error Handling dan Logging**  
- Gunakan **try-except** untuk menangkap error saat mengambil data.  
- Buat mekanisme retry jika scraping gagal karena keterlambatan loading halaman.  
- Simpan log scraping untuk analisis lebih lanjut.  

### **7. Automasi dan Scheduling (Opsional)**  
- Gunakan **scheduler (cron job / Windows Task Scheduler)** untuk scraping secara berkala.  
- Pastikan scraping tidak melanggar **robots.txt** dan batasan akses situs IQPlus.  
