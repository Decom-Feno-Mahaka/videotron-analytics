# Panduan Menjalankan Prototype Videotron Analytics

Proyek purwarupa ini terdiri dari tiga komponen utama yang saling terhubung:
1. **Mock Dashboard (Frontend Solid.js)**
2. **Simple Backend (Node.js/Express) API**
3. **Sample AI Generator (Python)**

Untuk menjalankan keseluruhan antarmuka secara *live*, ikuti langkah-langkah di bawah ini. Disarankan Anda membuka **3 tab terminal** terpisah agar lebih mudah mengelolanya.

## 1. Menjalankan Backend API
Terminal Pertama: Mengaktifkan server Node.js untuk menghimpun data dan melayani API ke antarmuka.

```bash
cd "@prototype/simple-backend"
npm install    # Menginstal dependensi (Express, CORS) jika belum
node server.js # Menjalankan server pada port http://localhost:3000
```

## 2. Mengaktifkan Generator AI Data (Python)
Terminal Kedua: Menjalankan skrip Python yang berperan menyimulasikan tangkapan kamera analitik dan mengirim (POST) ke Backend.

```bash
cd "@prototype/sample-ai"
# Aktifkan virtual environment (wajib dilakukan agar pip berjalan lancar)
source venv/bin/activate     

pip install requests         # Skrip ini butuh paket 'requests' untuk HTTP call
python3 mock_detector.py     # Menjalankan pembuaya aktivitas simulasi
```
*(Skrip ini akan secara proaktif melontarkan data pendeteksian acak ke `localhost:3000`)*

## 3. Menjalankan Dashboard Interaktif (Frontend)
Terminal Ketiga: Merender antarmuka gaya *Behance Neon* menggunakan Solid.js & Vite.

```bash
cd "@prototype/mock-dashboard"
npm install       # Menginstal dependensi framework & chart.js
npm run dev       # Mengaktifkan dev server Vite (biasanya di http://localhost:5173)
```

Setelah ketiganya berjalan, buka **http://localhost:5173** di peramban (browser) Anda. 
Anda akan melihat data pada *Pie Charts*, Angka Audiens, dan Animasi Grafik yang bergerak interaktif secara real-time!
