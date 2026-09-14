# Neko Haven VIP

- Write-Up Author: Ben Ten
- Category: Beginner
- Flag: `Kaito{n3k0_c4fe_sip_purr_fl4g_991}`

## Challenge Description
Welcome to Neko Haven, the premiere artisan cat cafe in town!

Our celebrity resident, Sir Meowsalot, only meets with guests who hold the secret VIP passcode.

Can you find the secret word and gain entry into the VIP lounge?

`http://31.97.37.38:1341`

## Steps to Find the Flag

1. Periksa *source code* dari aplikasi web (Client-side JavaScript).
2. Cari string yang di-enkode menggunakan base64.
3. Lakukan proses dekode base64 pada string tersebut untuk menemukan teks asli flag.

## Conclusion

Flag ternyata disembunyikan langsung (hardcoded) dalam format base64 di dalam kode JavaScript klien.

**Flag:** `Kaito{n3k0_c4fe_sip_purr_fl4g_991}`
