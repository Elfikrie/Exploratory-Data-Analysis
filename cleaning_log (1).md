# Cleaning Log

Dataset: bedtime_screen_sleep_debt.csv  
Baris mentah: 8600 -> baris bersih: 8500  

| # | Langkah | Baris terdampak | Alasan |
|---|---|---|---|
| 1 | Buang spasi awal dan akhir kolom teks | 500.0 | Spasi tersembunyi memecah groupby dan melambungkan nunique |
| 2 | Seragamkan sleep_debt_category | 0.0 | Huruf dan spasi oleh kode; sinonim dan salah ketik diputuskan manual lalu dicatat di peta |
| 3 | Hapus duplikat persis | 100.0 | Seluruh kolom identik; satu baris disimpan |
| 4 | Buang baris tanpa user_id | 0.0 | Kunci utama kosong tidak dapat ditelusuri kembali ke sumber |
| 5 | total_sleep_hours <= 0 menjadi kosong | 5.0 | Belum jelas retur atau salah input; barisnya masih berguna untuk kolom lain |
| 6 | Konversi bedtime_phone_minutes ke numerik (buang satuan 'min') | 51.0 | Kolom bertipe teks karena sebagian nilai berformat '<angka> min'; diekstrak angkanya dengan regex dan diubah ke float agar bisa dihitung |