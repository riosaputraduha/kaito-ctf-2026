# Freewill

- Write-Up Author: Ben Ten
- Category: Misc
- Flag: `KAITO{you_chose_nothing_i_chose_everything}`

## Challenge Description

Kaito Kuroba built a story about choice — the same way a magician builds an illusion of free will in the audience.

You will stand at crossroads. Each decision will feel like yours.

But the phantom thief wrote the ending before you arrived.

## Steps to Find the Flag

1. Analisis cipher yang digunakan yaitu Repeating-key XOR yang panjangnya sama dengan plaintext.
2. Gunakan kunci berupa hash SHA256 berukuran 32-byte dari string `kaito:branch:omega`.
3. Dekripsi ciphertext dengan melakukan operasi XOR antara ciphertext dan kunci hash tersebut.

## Conclusion

Flag didapatkan dengan mendekripsi XOR cipher menggunakan *derived key* dari SHA256.

**Flag:** `KAITO{you_chose_nothing_i_chose_everything}`
