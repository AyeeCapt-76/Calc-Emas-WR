# 📊 KR Marketplace Calculator - Integration Guide

## Overview
Implementasi kalkulasi KR (Konversi Rupiah) dengan formula berbeda untuk **Shopee** dan **TikTok**.

---

## 🔢 Formula Perhitungan

### Shopee (6.5% charge):
```
KR Shopee = (Modal - Modal × 6.5%) / (Harga Emas per Gram × Kadar%)
```

### TikTok (Dynamic charge):
```
Jika Modal < Rp 1.300.000:
  KR TikTok = (Modal - Modal × 13%) / (Harga Emas per Gram × Kadar%)

Jika Modal ≥ Rp 1.300.000:
  KR TikTok = (Modal - Modal × 9.5%) / (Harga Emas per Gram × Kadar%)
```

---

## 📦 File Components

### 1. **kr-implementation-guide.html**
File HTML yang sudah dibuat berisi:
- UI component untuk KR tab
- JavaScript calculator logic
- Real-time calculation & comparison

**Cara menggunakan:**
1. Copy seluruh konten `<div id="page-kr">...</div>` 
2. Paste di dalam element yang menampilkan KR tab di `index.html`
3. Pastikan localStorage `hargaEmas` sudah tersedia

---

## 🔗 Integration Steps

### Step 1: Temukan KR Page Section
Di `index.html`, cari atau tambahkan:
```html
<div id="page-kr" class="pg" style="display: none;">
  <!-- KR Page Content -->
</div>
```

### Step 2: Replace dengan New Implementation
Copy entire content dari `kr-implementation-guide.html` dan replace section di atas.

### Step 3: Ensure Dependencies
Pastikan sudah ada:
- ✅ localStorage untuk `hargaEmas`
- ✅ CSS classes sudah di-define di `index.html` (`.kr-input`, `.kr-result-card`, dll)
- ✅ Theme support (dark/light mode)

### Step 4: Test
1. Navigate ke KR tab
2. Input modal: `5000000`
3. Pilih kadar: `75K`
4. Hasil harus muncul untuk Shopee dan TikTok

---

## 📊 Contoh Output

### Input:
- Modal: **Rp 5.000.000**
- Kadar: **75K** (0.75)
- Harga/Gram: **Rp 700.000**

### Output Shopee (6.5%):
```
Charge: Rp 325.000 (6.5%)
Diterima: Rp 4.675.000
Gram: 8.905 gr
```

### Output TikTok (13%):
```
Charge: Rp 650.000 (13%)
Diterima: Rp 4.350.000
Gram: 8.286 gr
```

### Comparison:
```
💡 Shopee lebih untung +0.619 gr (7.46% lebih banyak)
```

---

## 🎛️ Features

### ✅ Real-time Calculation
- Input modal → otomatis hitung semua hasil

### ✅ Kadar Selection
- Button: 75K, 80K, 90K, 99K
- Click untuk switch kadar

### ✅ Dynamic TikTok Charge
- < Rp 1.3M: **13%** charge
- ≥ Rp 1.3M: **9.5%** charge
- ⚠️ Warning muncul saat dekat threshold

### ✅ Comparison Info
- Tampilkan marketplace mana yang lebih untung
- Selisih gram dan persen

### ✅ Dark/Light Theme Support
- Menggunakan CSS variables dari index.html
- Auto switch sesuai theme user

---

## 🔧 Customization

### Change Shopee Charge Rate:
Di JavaScript, ubah:
```javascript
chargeRate = 0.065; // Ubah angka ini
```

### Change TikTok Threshold:
```javascript
if (modal >= 1300000) { // Ubah angka 1.3 juta
  chargeRate = 0.095; // Charge ≥ threshold
} else {
  chargeRate = 0.13;  // Charge < threshold
}
```

### Change Kadar Options:
Di HTML, modifikasi:
```html
<button class="kr-tier-pill active" data-kadar="75">...</button>
<!-- Ubah data-kadar value -->
```

---

## 💾 LocalStorage Integration

Script otomatis mengambil harga emas dari:
```javascript
const stored = localStorage.getItem('hargaEmas');
```

Pastikan nilai sudah disimpan sebelumnya di tempat lain di aplikasi Anda.

---

## 🐛 Troubleshooting

### Q: Hasil menunjukkan "-"
**A:** 
- Pastikan input modal > 0
- Check localStorage `hargaEmas` tersedia
- Buka browser console untuk error messages

### Q: Charge TikTok tidak berubah
**A:** 
- Cek input modal harus ≥ atau < Rp 1.300.000
- Warning hanya muncul di range 1.2M - 1.4M

### Q: CSS styling tidak terlihat
**A:** 
- Pastikan semua `.kr-*` classes di-define di `<style>` index.html
- Check no CSS conflicts dengan page lain

---

## 📝 Notes

- Semua nilai gram di-round ke 3 desimal
- Semua nilai rupiah di-format dengan separator titik (id-ID locale)
- Harga emas diambil dari localStorage setiap kali page dimuat
- Kalkulasi otomatis trigger saat input/kadar berubah

---

## 🚀 Next Steps

1. ✅ Copy `kr-implementation-guide.html` content
2. ✅ Integrate ke KR tab di `index.html`
3. ✅ Test semua features
4. ✅ Deploy!

Selamat! KR calculator Anda sekarang support marketplace berbeda! 🎉
