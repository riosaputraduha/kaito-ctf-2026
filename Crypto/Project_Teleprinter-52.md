# Project Teleprinter-52

- Write-Up Author: Ben Ten
- Category: Crypto
- Flag: `Kaito{QAJRCEBTHUZNLKOVYMIWXPDFGS_PBTUXACNHVSKWEMRDGJOQLIFYZ_IOWKZNVDALUFPQYSJTBCMEGRXH_AQ_BH_CX_DZ_ES_FR_GV_IP_JT_KL_MO_NU_WY}`

## Challenge Description

We intercepted communications from an experimental electromechanical teleprinter unit (Model TP-52), You know what to do .

## Steps to Find the Flag

1. Manfaatkan pasangan *known-plaintext* untuk membangun batasan aljabar (algebraic constraints) dari simulator Enigma (berbasis Numpy).
2. Gunakan algoritma *Depth-First Search* (DFS) yang dipadukan dengan batasan tersebut untuk mencari pola *wiring* rotor.
3. Rekonstruksi perutean rotor yang benar untuk membaca keseluruhan flag.

## Conclusion

Serangan *known-plaintext* dikombinasikan dengan DFS berhasil merekonstruksi parameter *wiring* Enigma yang kompleks.

**Flag:** `Kaito{QAJRCEBTHUZNLKOVYMIWXPDFGS_PBTUXACNHVSKWEMRDGJOQLIFYZ_IOWKZNVDALUFPQYSJTBCMEGRXH_AQ_BH_CX_DZ_ES_FR_GV_IP_JT_KL_MO_NU_WY}`
