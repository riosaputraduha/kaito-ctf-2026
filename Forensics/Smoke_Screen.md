# Smoke Screen

- Write-Up Author: Ben Ten
- Category: Forensics
- Flag: `KAITO{cocoon_of_smoke_gilded_escape}`

## Challenge Description

Kaito Kid escaped the rooftop inside a cocoon of smoke — one of five charges deployed that night.

Four are empty misdirection. One carries what he left behind.

## Steps to Find the Flag

1. Analisis file `cocoon_3.bin` yang berukuran 132 byte.
2. Lewati atau potong 32-byte pertama yang merupakan *header*.
3. Sisa data merupakan teks base64 yang dikompresi dengan zlib. Lakukan dekode base64 lalu dekompresi zlib (`zlib.decompress`) untuk mendapatkan flag.

## Conclusion

Flag berhasil diekstrak dengan memisahkan header dan mendekompresi payload zlib-base64 dari dalam file biner.

**Flag:** `KAITO{cocoon_of_smoke_gilded_escape}`
