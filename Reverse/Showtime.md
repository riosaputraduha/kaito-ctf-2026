# Showtime

- Write-Up Author: Ben Ten
- Category: Reverse
- Flag: `KAITO{its_showtime_ladies_and_gentlemen}`

## Challenge Description

Before he was Kaito Kid, Kaito Kuroba headlined Ekoda High's magic club. Every show, a volunteer is "randomly" chosen from the audience. Every show, Aoko Nakamori walks on stage.

It's showtime. The randomness is part of the act.

## Steps to Find the Flag

1. Analisis script `showtime.py` untuk menemukan fungsi `_canon()`, yang menghasilkan string konstan (tidak terpengaruh oleh *seed* dari *user*).
2. Temukan bahwa string konstan tersebut akan diproses melalui fungsi hash `hashlib.sha256(canon)`.
3. Gunakan bentuk mentah (*raw bytes*) dari hasil hash SHA-256 tersebut sebagai kunci *Repeating-key XOR* untuk mendekripsi file `program.enc`.
4. Lakukan XOR antara isi `program.enc` dengan *raw digest* SHA-256 tadi untuk mendapatkan flag utuh.

## Conclusion

Sistem pemilihan *volunteer* memiliki enkripsi yang tersembunyi namun statis, menggunakan hasil raw SHA-256 dari output fungsi internal `_canon()` sebagai kunci XOR. Mengetahui relasi ini memungkinkan kita untuk memulihkan pesan rahasia di dalam `program.enc`.

**Flag:** `KAITO{its_showtime_ladies_and_gentlemen}`
