![](images/2025-07-26-09-36-06.png)

Diberikan sebuah website beserta source code backend-nya. Setelah melakukan analisis pada code backend, terlihat bahwa untuk mendapatkan flag kita perlu mengetahui API_SECRET_KEY. Oleh karena itu, langkah selanjutnya adalah mencari tahu di mana key tersebut disimpan.

![](images/2025-07-26-09-38-03.png)

Berdasarkan deskripsi soal, kemungkinan terdapat hint di sisi frontend. Saat memeriksa tab Network pada browser developer tools, ditemukan sebuah petunjuk yang menarik.

![](images/2025-07-26-09-38-46.png)

Petunjuk tersebut mengarah pada kemungkinan bahwa source map masih tersedia di environment production. Untuk memastikannya, kita mencoba mengakses file source map berikut:
> https://web-mini-me-ab6d19a7ea6e.2025.ductf.net/static/js/test-main.min.js.map

Ternyata file tersebut masih dapat diakses. Dari sini kita mendapatkan source code main.js asli sebelum proses minify. Setelah dianalisis, ditemukan sebuah fungsi tersembunyi yang tidak pernah dipanggil oleh aplikasi:
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
Dari fungsi tersebut terlihat bahwa terdapat sebuah array angka yang di-XOR dengan index (i + 1) untuk menghasilkan karakter ASCII. Hasil akhirnya adalah sebuah string yang kemungkinan besar merupakan API key. Untuk mendapatkan nilainya, kita cukup menjalankan fungsi tersebut di browser console.

![](images/2025-07-26-10-16-09.png)

Setelah dijalankan, kita memperoleh key TUNG-TUNG-TUNG-SAHUR. Selanjutnya kita dapat mengakses endpoint admin berikut dengan menambahkan header:

![](images/2025-07-26-10-23-39.png)

**Flag: DUCTF{Cl13nt-S1d3-H4ck1nG-1s-FuN}**