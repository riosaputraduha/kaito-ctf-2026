# Kaito CTF - What a Good Spot

- Write-Up Author: Ben Ten
- Category: Osint
- Flag: `Kaito{55.994,-3.385}`

## Challenge Description

<img src="./assets/view.jpg" alt="What a Good Spot" width="263">

Contractor was told to pick a spot with good ventilation.

They bolted a wooden shed to the side of a rail bridge, 150 feet over the water, and called it a day. Honestly? What a good spot.

Find the coordinates of this toilet.

Flag format: Kaito{lat,lon} to 3 decimal places
Example: Kaito{12.123,4.567}

## Steps to Find the Flag

1. **Analisis Forensik & Metadata Awal:** Langkah pertama yang dilakukan pada file view.jpg adalah memeriksa metadata untuk mencari potensi kebocoran lokasi menggunakan tool CLI Kali Linux. Perintah exiftool view.jpg dieksekusi, namun tidak ditemukan data koordinat GPS (*sanitized*). Pendekatan beralih ke IMINT (*Image Intelligence*).
2. **Analisis Visual (IMINT):** Identifikasi fitur arsitektur unik pada gambar, yaitu: struktur baja masif dengan sambungan paku keling (*rivets*), desain rangka tipe kantilever, dan adanya bilik kayu kecil di sisi luar lintasan. Visualisasi laut/sungai dan rumah di *background* menunjukkan lokasi pesisir atau muara.
3. **Reverse Image Search (RIS):** Untuk meminimalisir *noise* pada hasil pencarian, teknik *cropping* spesifik diterapkan pada area bilik kayu dan pola silang baja, lalu diumpankan ke *engine* Yandex Visual Search dan Google Lens. Analisis hasil pencarian (*cross-reference*) secara absolut mengarah pada **Forth Bridge**, jembatan kereta api di Firth of Forth, Skotlandia.
4. **Ekstraksi Koordinat Geospasial:** Tantangan *geolocation* sering kali menggunakan format *Decimal Degrees* (DD). Melalui Google Maps (citra satelit), sebuah pin diletakkan pada struktur utama Forth Bridge. Query koordinat pada pin tersebut mengembalikan nilai *latitude* (lintang utara) dan *longitude* (bujur barat).
5. **Parsing dan Flag Formatting:** Nilai raw koordinat dari peta disesuaikan presisinya (dipotong/dibulatkan menjadi 3 angka desimal) untuk memenuhi *pattern* yang disyaratkan oleh sistem validasi platform KAITO'S CTF. Latitude didapatkan sebagai 55.994 dan longitude -3.385. Menggabungkan nilai ini ke dalam wrapper menghasilkan final payload flag.

## Conclusion

Tantangan OSINT ini merupakan latihan geolokasi klasik yang menguji kemampuan pengumpulan informasi dari detail arsitektur suatu *landmark*. Dengan memanfaatkan *reverse image search* untuk mengenali jembatan Forth Bridge di Skotlandia, dan mengambil tiga angka desimal pertama dari koordinatnya di Google Maps, *flag* dapat ditemukan dengan akurat.

**Flag:** `Kaito{55.994,-3.385}`
