# Disguises

- Write-Up Author: Ben Ten
- Category: Beginner
- Flag: `KAITO{the_disguise_fools_eyes_not_the_timeline}`

## Challenge Description

After Kaito Kid vanishes from the Beika Art Museum, four witnesses swear they saw him.

Three are describing disguises planted to scatter the police. One statement matches the real escape.

Find the truth. Open what Kid left behind.

## Steps to Find the Flag

1. Analisis petunjuk timeline dan lokasi untuk menemukan string kunci (yaitu `north_tower:2103`).
2. Lakukan hashing SHA256 pada petunjuk tersebut untuk menghasilkan passphrase.
3. Gunakan passphrase tersebut untuk mendekripsi file menggunakan algoritma Repeating-Key XOR.

## Conclusion

Memadukan petunjuk OSINT/logika untuk membentuk *passphrase* SHA256 berhasil membuka kunci enkripsi XOR.

**Flag:** `KAITO{the_disguise_fools_eyes_not_the_timeline}`
