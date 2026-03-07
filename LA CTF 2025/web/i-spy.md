![](images/2025-02-12-18-28-59.png)

Pada soal diberikan sebuah web berikut.

![](images/2025-02-12-18-30-03.png)

Tujuan dari challenge ini adalah menemukan token tersembunyi di berbagai tempat pada website untuk dapat melanjutkan ke stage berikutnya hingga akhirnya mendapatkan flag.

Setiap stage memberikan sebuah hint mengenai lokasi token berikutnya. Dengan mengikuti petunjuk tersebut dan melakukan inspeksi pada berbagai bagian website (HTML, JavaScript, header, DNS, dll.), kita dapat menemukan semua token.

Berikut daftar hint dan cara menemukannya:
1. **A token in the HTML source code.** Hint pertama menyebutkan bahwa token berada di HTML source code. Dengan membuka View Page Source, kita dapat menemukan token pertama yang tersembunyi di dalam HTML.
2. **A token in the JavaScript console.** Hint berikutnya menyebutkan token ada di JavaScript console. Dengan membuka Developer Tools Console, akan muncul token yang dicetak melalui console.log().
3. **A token in the stylesheet**. Token berikutnya berada di file CSS. Dengan membuka file stylesheet pada tab Sources atau Network, kita dapat menemukan token yang disisipkan di dalam komentar atau isi CSS.
4. **A token in javascript code**. Token selanjutnya berada di dalam kode JavaScript. Dengan membuka file JavaScript yang digunakan oleh halaman, kita dapat menemukan token tersebut.
5. **A token in a header.** Hint berikutnya menyebutkan token berada di header request API. Dengan membuka Developer Tools → Network, lalu melihat request ke API, token dapat ditemukan pada bagian HTTP headers.
6. **A token in a cookie.** Token berikutnya berada di cookie browser. Cookie dapat dilihat melalui Developer Tools → Application → Cookies
7. **A token where the robots are forbidden from visiting.** Hint berikutnya mengarah ke robots.txt. Akses /robots.txt dan di dalamnya terdapat path yang di-disallow /a-magical-token.txt
8. **A token where Google is told what pages to visit and index.** Hint berikutnya menyebutkan token berada di tempat Google diberitahu halaman mana yang harus di-index File tersebut adalah /sitemap.xml.
9. **A token received when making a DELETE request to this page.** Hint berikutnya menyebutkan token didapat dengan melakukan request DELETE ke halaman tersebut.

10. **A token in a TXT record at i-spy.chall.lac.tf.** Hint terakhir menyebutkan token berada pada DNS TXT record dari domain i-spy.chall.lac.tf. TXT record dapat dicek menggunakan web 
https://www.nslookup.io/domains/i-spy.chall.lac.tf/dns-records/txt/

![](images/2025-02-12-18-34-29.png)

**Flag : lactf{1_sp0773d_z_t0k3ns_4v3rywh3r3}**