![](images/2025-02-12-18-36-04.png)

Pada soal diberikan sebuah script encode string.
```python
flag = "lactf{REDACTED}"
extended_flag = ""

for c in flag:
    # Buat ngubah string ke biner. contoh A -> 01000001
    o = bin(ord(c))[2:].zfill(8)

    # Mengubah biner 0 pertama menjadi 1
    for i in range(8):
        if o[i] == "0":
            o = o[:i] + "1" + o[i + 1 :]
            break
    # Balikin hasil biner tadi ke string ASCII
    extended_flag += chr(int(o, 2))

print(extended_flag)

with open("chall.txt", "wb") as f:
    f.write(extended_flag.encode("iso8859-1"))
```

Lalu diberikan juga sebuah string hasil encode
==ìáãôæûÆõîîéìùßÅîïõçèßÔèéóßÌïïëóßÄéææåòåîôßÏîßÍáãßÁîäß×éîäï÷óý==

Berdasarkan script encode, sepertinya saya hanya perlu mengubah biner 1 pertama kembali menjadi 0 dan balikin hasilnya ke string ASCII. Berikut scriptnya.
```python
extended_flag = "ìáãôæûÆõîîéìùßÅîïõçèßÔèéóßÌïïëóßÄéææåòåîôßÏîßÍáãßÁîäß×éîäï÷óý"
original_flag = ""

for c in extended_flag:
    o = bin(ord(c))[2:].zfill(8)  # Konversi ke binary (8-bit)
    
    # Ganti 1 pertama jadi 0 untuk mendapatkan binary asli
    for i in range(8):
        if o[i] == "1":
            o = o[:i] + "0" + o[i + 1:]
            break

    original_flag += chr(int(o, 2))  # Konversi balik ke karakter

print(original_flag)
```

**Flag : lactf{Funnily_Enough_This_Looks_Different_On_Mac_And_Windows}**