# Crypt15

- Write-Up Author: Ben Ten
- Category: Crypto
- Flag: `KAITO{signal_protocol_crypt15_backup_decrypted}`

## Challenge Description

After a Kaito Kid heist, police seized a rooted Android phone tied to Kaito Kuroba.

Forensic analysis recovered an encrypted WhatsApp backup in crypt15 format — end-to-end encrypted, the kind a careful magician would use to hide more than card tricks.

A few artifacts were left behind. Recover the chat contents and find the flag.

`0123456789abcdef0123456789abcdef`

## Steps to Find the Flag

1. Tantangan ini berkaitan dengan dekripsi file `msgstore.db.crypt15`.
2. Terapkan fungsi turunan kunci (KDF) menggunakan iterasi ganda HMAC-SHA256 yang menggabungkan *shard* lokal (16B) dan *shard* remote (16B).
3. Gunakan kunci yang dihasilkan untuk melakukan dekripsi payload dengan AES-256-GCM, lalu lakukan dekompresi menggunakan *zlib inflate*.

## Conclusion

Rekonstruksi KDF untuk mendapatkan kunci AES-256-GCM berhasil mendekripsi database backup Crypt15.

**Flag:** `KAITO{signal_protocol_crypt15_backup_decrypted}`
