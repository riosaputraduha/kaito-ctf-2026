# Pandora

- Write-Up Author: Ben Ten
- Category: Crypto
- Flag: `KAITO{pandora_holds_the_kuroba_legacy}`

## Challenge Description

Toichi Kuroba spent his life searching for the Pandora gem. After his death, Kaito inherited more than a stage name — he inherited sealed research.

A letter, a catalog entry, and an encrypted file are all that remain.

## Steps to Find the Flag

1. Ketahui bahwa payload terenkripsi menggunakan AES-256-GCM dengan ukuran 66-byte.
2. Lakukan serangan *dictionary bruteforce* untuk mencari kunci rahasia.
3. Kunci ditemukan dari hash SHA256(`toichi:pandora:gem`). Lakukan dekripsi AES untuk mendapatkan flag.

## Conclusion

Bruteforce kombinasi string kunci berhasil menemukan kunci SHA256 yang benar untuk dekripsi AES-256-GCM.

**Flag:** `KAITO{pandora_holds_the_kuroba_legacy}`
