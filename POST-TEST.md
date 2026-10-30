**1.	Lampirkan kedua script SQL kelompok Anda: (1) Query JOIN yang kompleks, dan (2) Script DDL pembentukan kolom/tabel denormalisasi beserta query panggilannya!**

jawab:
```sql
-- Menghitung total tempat/lokasi ramah lingkungan yang didaftarkan oleh setiap mitra
SELECT 
    u.user_id AS id_mitra,
    u.name AS nama_mitra,
    COUNT(l.lokasi_id) AS total_lokasi_terdaftar
FROM users u
JOIN lokasi l ON u.user_id = l.mitra_id
WHERE u.role = 'mitra'
GROUP BY u.user_id, u.name;
```
<br>

```sql
-- A. DDL: Menambahkan kolom atribut turunan (redudan) pada tabel master (users)
ALTER TABLE users 
ADD COLUMN total_lokasi_terdaftar INT DEFAULT 0;

-- B. Mengisi kolom turunan tersebut dengan data hasil agregasi dari tabel lokasi
UPDATE users u
SET total_lokasi_terdaftar = (
    SELECT COUNT(l.lokasi_id)
    FROM lokasi l
    WHERE l.mitra_id = u.user_id
);

-- C. Pembuktian: Query baca kilat (untuk dasbor) tanpa JOIN atau agregasi
SELECT 
    user_id AS id_mitra,
    name AS nama_mitra,
    total_lokasi_terdaftar
FROM users
WHERE role = 'mitra';
```

