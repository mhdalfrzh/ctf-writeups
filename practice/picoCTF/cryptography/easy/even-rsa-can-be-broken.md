![](images/2026-01-10-12-44-52.png)

Pada challenge ini, kita diberikan koneksi netcat yang menampilkan parameter RSA: modulus $N$, public exponent $e$, dan ciphertext $c$. Tugas kita adalah mendekripsi ciphertext untuk mendapatkan flag.

![](images/2026-01-10-12-45-49.png)

Sesuai judul challenge (*"EVEN RSA CAN BE BROKEN???"*), petunjuk utama terletak pada nilai modulus $N$. Jika dilihat digit terakhirnya (`...711714`), nilai $N$ adalah **bilangan genap** ($N \pmod 2 = 0$).

Pada implementasi RSA yang semestinya:
- Modulus merupakan hasil kali dua bilangan prima ganjil besar: $N = p \times q$.
- Namun karena satu-satunya bilangan prima genap adalah $2$, maka salah satu faktor prima dari $N$ sudah pasti:
  $$p = 2$$
  $$q = \frac{N}{2}$$

Dengan begitu, proses faktorisasi menjadi instan. Kita cukup menghitung nilai totient $\phi(N) = (p - 1)(q - 1)$, mencari private exponent $d \equiv e^{-1} \pmod{\phi(N)}$, dan mendekripsi ciphertext $m = c^d \pmod N$.

Berikut script solver Python untuk merekonstruksi flag:

```python
from Crypto.Util.number import long_to_bytes

n = 19494735855686003875357543310216049619497024127382667840751336507805582069306595528335605454322622686173077869565460327655312290112858745857501305609711714
e = 65537
c = 16453036468118374693440620944168593478730012086505023648238175347012306908746816394611890399773719266411441837650329991951012039297223375799011484794711075

# Faktorisasi trivial karena N adalah bilangan genap
p = 2
q = n // 2

# Menghitung private key d
phi = (p - 1) * (q - 1)
d = pow(e, -1, phi)

# Dekripsi ciphertext
m = pow(c, d, n)
print(long_to_bytes(m).decode())
```

**Flag:** `picoCTF{tw0_1$_pr!m3de643ad5}`