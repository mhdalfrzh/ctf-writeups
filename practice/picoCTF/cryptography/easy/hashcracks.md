Pada challenge ini, diberikan empat buah nilai hash (MD5, SHA1, SHA224, dan SHA512) dan diminta untuk menemukan plaintext asli dari masing-masing hash tersebut. Karena tantangan ini termasuk kategori *easy*, kemungkinan besar hash yang diberikan rentan atau menggunakan password umum sehingga mudah dicrack.

![](images/2026-01-10-12-01-27.png)

Dengan asumsi hash tersebut berasal dari kata sandi umum atau frasa pendek, kita dapat menggunakan layanan cracking online seperti **CrackStation** untuk mendapatkan plaintext-nya.

Prosesnya:
1. Kunjungi situs CrackStation ([https://crackstation.net/](https://crackstation.net/)).
2. Masukkan setiap nilai hash ke dalam kolom input.
3. Klik tombol *"Decrypt"* atau *"Crack"*.

Berikut adalah hasil crack untuk keempat hash tersebut:

| Hash Type | Hash | Plaintext |
|-----------|------|-----------|
| MD5 | `0fc63a4a97506f7f3989b10231db550d` | `alpha` |
| SHA1 | `ef62b60a229d9d03da8128d713701d59c9f4376e` | `beta` |
| SHA224 | `98e65968c016a46d53141a876e1f7dd9b1187f81d081de3b02d306b2` | `gamma` |
| SHA512 | `dbf2f986f6f21436a00f70336b3f3d6b6c8d2d80139f857a079110e88a736a96157dfeb05d4b7226f9b64a0e099c8db5e9a0336612f6847a3e4e467483586646` | `delta` |

Setelah keempat plaintext berhasil diperoleh, kita menyusunnya sesuai urutan yang diminta untuk membentuk flag akhir.

![](images/2026-01-10-12-04-52.png)

**Flag:** `picoCTF{UseStr0nG_h@shEs_&PaSswDs!_ccc21957}`