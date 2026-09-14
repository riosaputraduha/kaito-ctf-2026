# The Jackal's Alias

- Write-Up Author: Ben Ten
- Category: Web
- Flag: `Kaito{bl1nd_j50nqu3ry_byp455_v14_b00l34n_4r1thm3t1c}`

## Challenge Description

Blind NoSQL/JSON boolean-based injection bypassing a numeric filter utilizing `array("a", "a") | size()` as an arithmetic integer representation.

## Steps to Find the Flag

1. Identifikasi kerentanan *Blind NoSQL/JSON boolean-based injection*.
2. Karena filter angka (numeric filter) memblokir karakter angka (digit), buat nilai angka dengan menggunakan aritmetika panjang array (misal `array("a", "a") | size()` sebagai angka `2`).
3. Lakukan kueri boolean-based *bruteforce* pada panjang karakter dan isi karakter hingga keseluruhan flag berhasil dibaca.

## Conclusion

Meskipun ada filter numerik ketat, pemanfaatan ukuran array (*size/length*) memungkinkan injeksi NoSQL/JSON dan ekstraksi flag secara *blind*.

**Flag:** `Kaito{bl1nd_j50nqu3ry_byp455_v14_b00l34n_4r1thm3t1c}`
