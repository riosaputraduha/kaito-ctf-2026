# Kaito CTF - That Creepy Episode

- Write-Up Author: Ben Ten
- Category: Osint
- Flag: `Kaito{Dogged_6}`

## Challenge Description

![Creepy Episode GIF](./That%20Creepy%20Episode/ezgif.com-video-to-gif-converter.gif)

I remember catching this weirdly unsettling scene on TV as a kid and it stuck with me.........for years. Can you track down the episode title and the minute mark where this clip appears?

Flag format: Kaito{EpisodeName_M} (e.g., Kaito{Beginnings_4})

## Steps to Find the Flag

1. Ekstrak frame dari file GIF `ezgif.com-video-to-gif-converter.gif`.
2. Lakukan Reverse Image Search (menggunakan Google Lens, Yandex, atau alat OSINT lainnya) pada frame tersebut.
3. Temukan acara TV beserta judul episodenya dari hasil pencarian (Episode "Dogged").
4. Cari referensi adegan atau tonton episode tersebut untuk menentukan stempel waktu (menit ke-6).
5. Gabungkan menjadi format flag yang diminta.

## Conclusion

Tantangan ini diselesaikan menggunakan teknik Reverse Image Search pada frame GIF. Pencocokan visual ke basis data mesin pencari memungkinkan identifikasi sumber media asli.

**Flag:** `Kaito{Dogged_6}`
