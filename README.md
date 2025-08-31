# Analisis Kesehatan Ibu & Anak Kota Tangerang Selatan 2022
cleaning, EDA, dengan dukungan IBM Granite/watsonx.ai (Colab + Slides).

📌 Tujuan
Menghasilkan dataset terintegrasi tingkat kecamatan untuk indikator: tenaga gizi, stunting, malnutrisi, anemia, ASI eksklusif, imunisasi, pelayanan ibu hamil/bayi/balita, dan indikator terkait lainnya.

##🧩 Ringkasan Metodologi
1) **Normalisasi**: deteksi header `Kecamatan`, bersihkan kolom kosong/`Unnamed`, normalisasi desimal (`,`→`.`), persen → 0–100.  
2) **Merging**: *outer join* di `Kecamatan`, prefix nama kolom berdasar file/sheet untuk hindari tabrakan.  
3) **Validasi**: persen out-of-range di-*neutralize* (`NaN`), drop baris agregat **Total/Jumlah/Kecamatan**.  
4) **Skoring**: hitung `PRIORITY_SCORE` dari stunting, imunisasi, ASI, layanan Ibu/Bayi/Balita, dan tenaga gizi.  

## 📦 Output Utama
- `data/master_dataset_clean.csv` — dataset gabungan siap analisis.  
- `data/priority_ranking.csv` — peringkat kecamatan berdasar `PRIORITY_SCORE`.  

## 🤖 Penggunaan AI (Granite)
- **Digunakan**: membuat *caption/insight* pendek dari payload (Top-N) dan **menghasilkan kode `matplotlib`** dari `DATA + SPEC`.  
- **Tidak Digunakan**: pembersihan data atau perhitungan skor.  

## 🚀 Cara Pakai (Colab)
1. Klik **Open in Colab** di atas.  
2. Upload ZIP sumber ke sel “ingest”, jalankan sel **clean & merge**, lalu **compute PRIORITY_SCORE**.  
3. Jalankan sel **Granite Visuals** untuk membuat grafik otomatis dan **Tanya AI** untuk caption.


## Catatan
- Perubahan: pembersihan persen, normalisasi angka, penyatuan indikator.
- Keterbatasan: data 2022, tingkat agregasi kecamatan.
