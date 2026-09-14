# Pizza Syndicate

- Write-Up Author: Ben Ten
- Category: Forensics
- Flag: `Kaito{n4p0l1_s4uc3_m4f14_m3m0ry_c4rv1ng_p1zz4_1924}`

## Challenge Description

Mamma Mia! Disastro nel forno!

At 03:42 AM, the smart wood-fired oven at Restorante Don Peperoni spiked to 500°C, incinerating a 48-hour batch of sacred sourdough crust. Luigi pulled the emergency power cord, but not before dumping the controller's RAM and capturing the kitchen Wi-Fi network traffic.

Those ruthless bastards from The Crust Cartel injected an in-memory implant to steal Don Peperoni's 100-year sacred Napoli sauce formula.

recover Don Peperoni's legendary sauce formula before Uncle Don loses his mind!

## Steps to Find the Flag

1. **Analisis RAM (`oven_core_ram.raw`)**:
   - `0xf0000`: Ditemukan HWID string = `NP-9000-8F3A-44C1-229E`.
   - `0x520000`: ELF stub dengan `.rodata` di `0x522050`. String diobfuscate XOR (`0x5c`). Deobfuscate dapat: `PIZZA_SAUCE_V2` dan `::CrustCartelVendetta1924::`.
   - `0x880000`: Cipher vault ditemukan. Mulai dari `0x880010`. IV 16-byte di `0x880012`, ciphertext 688-byte di `0x880022`.

2. **Turunkan Kunci AES-256-CBC**:
   - Kunci = SHA256 gabungan terbalik `[VLT, BI, HW]`: `peperoni_heritage_1924` + `::CrustCartelVendetta1924::` + `NP-9000-8F3A-44C1-229E`.
   - Kunci heks: `d7df86a807bd5811ed5ab1773c0d4f47afaefe813af70cc5ed16d9e1446aa20b`.

3. **Dekripsi**:
   - Gunakan AES-256-CBC, kunci SHA256, dan IV.
   - Dekripsi payload di `0x880022`.
   - Hasil berisi resep dan flag.

## Conclusion

Serangan pakai implantasi in-memory ELF stub dan enkripsi AES-256-CBC. Analisis string RAM dan memori layout rakit kunci dekripsi.

**Flag:** `Kaito{n4p0l1_s4uc3_m4f14_m3m0ry_c4rv1ng_p1zz4_1924}`