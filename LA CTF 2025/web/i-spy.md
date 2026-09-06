![](images/2025-02-12-18-28-59.png)

Pada challenge ini, diberikan sebuah website (`https://i-spy.chall.lac.tf/`).

![](images/2025-02-12-18-30-03.png)

Tujuan challenge adalah mengumpulkan 10 token secara berurutan. Setiap token yang dimasukkan ke form akan memberikan hint mengenai lokasi token berikutnya hingga akhirnya mendapatkan flag.

Berikut petunjuk dan cara menemukan token di setiap stage:

1. **A token in the HTML source code**  
   Buka *View Page Source* (`Ctrl + U`), token disisipkan di dalam komentar/elemen HTML.

2. **A token in the JavaScript console**  
   Buka *Developer Tools → Console*, token dicetak langsung melalui `console.log()`.

3. **A token in the stylesheet**  
   Buka file stylesheet CSS halaman melalui tab *Sources* atau *Network*, token berada di dalam komentar CSS.

4. **A token in javascript code**  
   Periksa file JavaScript yang dimuat halaman, token tersimpan di dalam variabel/kode script.

5. **A token in a header**  
   Buka *Developer Tools → Network*, periksa response headers dari HTTP request halaman.

6. **A token in a cookie**  
   Buka *Developer Tools → Application → Cookies*, token tersimpan sebagai salah satu value cookie.

7. **A token where the robots are forbidden from visiting**  
   Buka file `/robots.txt`. Di dalamnya terdapat path yang di-*disallow* (`/a-magical-token.txt`) yang berisi token.

8. **A token where Google is told what pages to visit and index**  
   Buka file `/sitemap.xml` yang mengatur indeks mesin pencari, token tercantum di dalamnya.

9. **A token received when making a DELETE request to this page**  
   Kirim HTTP request dengan method `DELETE` ke URL website (misalnya via `curl -X DELETE https://i-spy.chall.lac.tf/` atau fungsi `fetch` di console). Token akan muncul pada response.

10. **A token in a TXT record at i-spy.chall.lac.tf**  
    Cek DNS TXT record pada domain `i-spy.chall.lac.tf` menggunakan command `dig TXT i-spy.chall.lac.tf +short` atau melalui tool online seperti [nslookup.io](https://www.nslookup.io/domains/i-spy.chall.lac.tf/dns-records/txt/).

Setelah menginputkan token ke-10, website menampilkan flag akhir:

![](images/2025-02-12-18-34-29.png)

**Flag:** `lactf{1_sp0773d_z_t0k3ns_4v3rywh3r3}`