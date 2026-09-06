![](images/2025-07-26-09-36-06.png)

Pada challenge ini, diberikan sebuah website beserta source code backend-nya. Dari analisis source code backend, terlihat bahwa flag dapat diperoleh melalui endpoint `POST /admin/flag` dengan menyertakan `API_SECRET_KEY` pada header `X-API-Key`.

![](images/2025-07-26-09-38-03.png)

Karena key tersebut tidak didefinisikan di backend, kita beralih memeriksa sisi frontend sesuai petunjuk deskripsi soal (*"...or right at the front!"*). Saat memeriksa file JavaScript (`main.min.js`) melalui Developer Tools, ditemukan komentar yang menarik di baris terakhir:

![](images/2025-07-26-09-38-46.png)

Komentar tersebut membocorkan file source map yang belum dihapus di environment production. File tersebut dapat diakses langsung melalui URL:
> https://web-mini-me-ab6d19a7ea6e.2025.ductf.net/static/js/test-main.min.js.map

Melalui file source map ini, kita dapat merekonstruksi source code asli (`main.js`) sebelum proses *minify*. Di dalamnya, terdapat sebuah fungsi tersembunyi yang belum pernah dipanggil:

```javascript
function qyrbkc() {
  const dhgyvu = [85, 87, 77, 67, 40, 82, 82, 70, 78, 39, 95, 89,
                  67, 73, 34, 68, 68, 92, 84, 57, 70, 87, 95, 77, 75];
  const key = dhgyvu.map((val, i) =>
    String.fromCharCode(Number(val) ^ (i + 1))
  ).join('');
  console.log("Note: Key is now secured with heavy obfuscation, should be safe to use in prod :)");
}
```

Fungsi di atas melakukan operasi XOR antara array angka dengan index (`i + 1`) untuk menghasilkan karakter string. String hasil dekode ini merupakan secret key yang dicari. Kita dapat langsung mengeksekusi logika tersebut melalui console browser:

![](images/2025-07-26-10-16-09.png)

Hasil eksekusi menghasilkan string `TUNG-TUNG-TUNG-TUNG-SAHUR`. Terakhir, kirim request `POST` ke endpoint `/admin/flag` dengan header `X-API-Key` menggunakan `curl`:

![](images/2025-07-26-10-23-39.png)

**Flag:** `DUCTF{Cl13nt-S1d3-H4ck1nG-1s-FuN}`