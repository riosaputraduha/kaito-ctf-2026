# Heist Notice

- Write-Up Author: Ben Ten
- Category: Stego
- Flag: `KAITO{tonights_target_is_the_moonlight_sonata}`

## Challenge Description

Zero-width characters (U+200B for 0, U+200C for 1) embedded in text used to encode binary ASCII data.

## Steps to Find the Flag

1. Analisis teks yang diberikan dan periksa keberadaan karakter-karakter tak kasat mata (zero-width characters).
2. Petakan karakter U+200B sebagai representasi bit `0` dan U+200C sebagai bit `1`.
3. Ekstrak deretan bit tersebut dan konversikan menjadi teks ASCII untuk membaca flag.

## Conclusion

Data biner flag disembunyikan menggunakan manipulasi steganografi karakter *zero-width* di dalam teks biasa.

**Flag:** `KAITO{tonights_target_is_the_moonlight_sonata}`
