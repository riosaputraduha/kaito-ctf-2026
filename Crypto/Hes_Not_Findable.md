# He's Not Findable

- Write-Up Author: Ben Ten
- Category: Crypto
- Flag: `Kaito{c3ntr4l_f1n1t3_curv3_hnp_l4tt1c3_c137}`

## Challenge Description

M-Morty! (burp) Look at me! I locked onto Rick Prime's portal exhaust across the Curve, but the sensor's dropping the middle of his signature. Don't just stand there drooling like a dead mackerel, Morty! Sit your little ass down, we need to fix the math M-Mor*(burp)*..ty!

![He's Not Findable](./assets/images.jpeg)

## Steps to Find the Flag

1. Analisis implementasi Elliptic Curve Cryptography (ECC) yang diberikan.
2. Identifikasi kerentanan berupa penggunaan ulang atau *bias* pada *nonce* (k) dalam penandatanganan.
3. Lakukan eksploitasi serangan *nonce reuse* / HNP (Hidden Number Problem) untuk memulihkan *private key* dan mendapatkan flag.

## Conclusion

Pemulihan *private key* berhasil dilakukan akibat kelemahan matematis pada pembuatan *nonce* ECC.

**Flag:** `Kaito{c3ntr4l_f1n1t3_curv3_hnp_l4tt1c3_c137}`
