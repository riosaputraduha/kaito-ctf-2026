# Berglas

- Write-Up Author: Ben Ten
- Category: Reverse
- Flag: `KAITO{any_card_any_number_no_method_known}`

## Challenge Description

Any card. Any number.

Kaito Kuroba studied this effect for years — the legendary Berglas routine where any spectator choice still ends in miracle.

Kaito performed it five times at a private magic gathering. Five witnesses. Five different choices. Every performance succeeded.

No published method. No explanation. Only the sealed deck from that night.

## Steps to Find the Flag

1. Lakukan *reverse engineering* untuk menemukan bahwa dekripsi menggunakan algoritma AES-256-GCM dengan kunci SHA256(`berglas:acaan:effect`).
2. Namun, data masih tertutup *masking constant* dengan pola `v ^ seed ^ ((i*a+b)&0xFF)`.
3. Lakukan *bruteforce* terhadap parameter seed, a, dan b (diketahui jawabannya: seed=190, a=7, b=11) dan selesaikan dekripsinya.

## Conclusion

Dengan mem-bruteforce variabel *masking* LCG kecil dan mendeskripsi AES-256-GCM, flag berhasil didapatkan.

**Flag:** `KAITO{any_card_any_number_no_method_known}`
