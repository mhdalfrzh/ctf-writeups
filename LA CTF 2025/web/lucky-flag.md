![](images/2025-02-12-18-24-56.png)

Pada soal diberikan sebuah website yang menampilkan ribuan box flag. Dari sekian banyak box tersebut, hanya satu box yang berisi flag, dan flag akan muncul ketika box yang benar diklik.

![](images/2025-02-12-18-25-48.png)

Jika mencoba mencarinya secara manual dengan mengklik satu per satu box, tentu akan sangat memakan waktu. Oleh karena itu, langkah selanjutnya adalah melakukan analisis pada source code website. Setelah membuka Developer Tools dan melihat source code halaman, ditemukan sebuah script JavaScript yang digunakan untuk meng-generate flag.

![](images/2025-02-12-18-27-22.png)

Script tersebut berisi logika untuk menentukan posisi box yang sebenarnya berisi flag. Dengan menyalin dan menjalankan script tersebut di Developer Tools → Console, kita dapat langsung mengetahui flag yang dihasilkan.

![](images/2025-02-12-18-27-57.png)

**Flag : lactf{w4s_i7_luck_0r_ski11}**