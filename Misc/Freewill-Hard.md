# Freewill-Hard

- Write-Up Author: Ben Ten
- Category: Misc
- Flag: `KAITO{authorship_was_never_yours}`

## Challenge Description

Kaito Kid never improvises the finale. The applause changes. The destination does not.

You will walk crossroads and sign your path. The seal will bear your decisions.

But seals are not always signatures of authorship.

Recover what Kaito wrote before the show began.

## Steps to Find the Flag

1. Eksekusi trigger yang berada pada dead code di dalam bagian `_ARCHIVE`.
2. Hal ini akan memicu dekripsi AES-256-GCM pada ledger.
3. Kunci yang digunakan untuk AES-256-GCM ini adalah SHA256(`kaito:branch:omega`).

## Conclusion

Menemukan dan menjalankan trigger pada *dead code* berhasil mengambil kunci untuk mendekripsi AES-256-GCM.

**Flag:** `KAITO{authorship_was_never_yours}`
