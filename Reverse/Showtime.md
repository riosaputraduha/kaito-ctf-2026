# Showtime

- Write-Up Author: Ben Ten
- Category: Reverse
- Flag: `KAITO{its_showtime_ladies_and_gentlemen}`

## Challenge Description

Repeating-key XOR using SHA256 hash of `_canon()` output as the key.

## Steps to Find the Flag

1. Analisis binari untuk menemukan logika algoritma enkripsi yaitu Repeating-key XOR.
2. *Reverse engineer* fungsi `_canon()` untuk melihat *output* atau *return value*-nya.
3. Gunakan *hash* SHA256 dari output fungsi `_canon()` sebagai kunci untuk mendekripsi flag.

## Conclusion

Analisis fungsi internal (`_canon()`) memungkinkan pembentukan kunci XOR melalui fungsi hash SHA256.

**Flag:** `KAITO{its_showtime_ladies_and_gentlemen}`
