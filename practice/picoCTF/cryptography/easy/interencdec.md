![](images/2026-01-10-12-52-57.png)

Pada challenge ini, kita diberikan sebuah file teks terenkripsi. Judul soal *interencdec* mengindikasikan bahwa pesan ini telah melalui beberapa lapisan *encoding* dan enkripsi.

Isi teks awal:
```text
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzJhMnd6TW1zeWZRPT0nCg==
```

Pesan dapat dipecahkan dengan membongkar lapisannya satu per satu:

1. **Decode Base64 Pertama**  
   Teks awal memiliki pola padding khas Base64 (`==`). Hasil decode pertama menghasilkan representasi string byte Python:
   ```text
   b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg2a2wzMmsyfQ=='
   ```

2. **Decode Base64 Kedua**  
   Ambil string di dalam tanda petik (`d3Bqdkp...==`) lalu lakukan decode Base64 sekali lagi:

   ![](images/2026-01-10-12-57-09.png)

   Hasil decode lapisan kedua menghasilkan teks:  
   `wpjvJAM{jhlzhy_k3jy9wa3k_86kl32k2}`

3. **Dekripsi Caesar Cipher**  
   Format teks di atas terlihat menyerupai format flag (`picoCTF{...}`). Dengan mendekripsinya menggunakan **Caesar Cipher** (rotasi/shift 19 atau mundur 7 huruf), kita mendapatkan flag akhir:

   ![](images/2026-01-10-12-58-48.png)

**Flag:** `picoCTF{caesar_d3cr9pt3d_86de32d2}`