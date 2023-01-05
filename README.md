# Praktikum 9
 ## Exception Handling
 - *Exception* (eksepsi) merupakan suatu kesalahan *(error)* yang terjadi saat proses eksekusi program sedang berjalan,
 - Kesalahan ini akan menyebabkan program berakhir dengan tidak normal.
## Handling
- Penanganan file adalah bagian penting dari aplikasi apa pun.
## Assertion
*Assertion*(pernyataan) adalah kewajaran program yang kamu bisa aktif/nonaktifkan ketika kamu selesai menjalankan program.
### The Assert Statement
- Saat menemukan pernyataan, Python mengevaluasi ekspresi yang menyertainya, yang mana semoga benar. Jika ekspresi salah, Python memunculkan pengecualian AssertionError.
##### Sintaks untuk pernyataan yaitu :
```
assert Expression[, Arguments]
```
Jika pernyataan gagal, Python menggunakan ArgumentExpression ArgumentExpression sebagai argumen argumen untuk AssertionError AssertionError.
Pengecualian AssertionError Pengecualian AssertionError dapat ditangkap dan ditangani ditangani seperti pengecualian lainnya menggunakan try-
kecuali pernyataan, tetapi jika dibiarkan, mereka akan menghentikan program dan menghasilkan backtrace.
#### Contoh
- Berikut adalah fungsi fungsi yang mengubah suhu dari derajat Kelvin menjadi derajat Fahrenheit.Karena nol derajat Kelvin dingin, fungsi fungsi menyimpannya jika melihat negatif negatif suhu.
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:
```
def KelvinToFahrenheit(Temperature):
    assert (Temperature >= 0),"Colder than absolute zero!"
    return ((Temperature-273)*1.8)+32
print (KelvinToFahrenheit(273))
print (int(KelvinToFahrenheit(505.78)))
print (KelvinToFahrenheit(-5))
```

![gambar](prak9_1.png)

### Menangani Pengecualian
Jika Anda memiliki beberapa kode mencurigakan yang mungkin mengeluarkan pengecualian, Anda dapat mempertahankan program Anda letakkan kode yang mencurigakan di **try: blok**. Setelah coba: blok, sertakan pernyataan sertakan **except:** statemen, diikuti oleh blok kode yang menangani masalah seanggun mungkin.
#### Contoh
- Contoh-contoh ini membuka file, menulis konten file, dan keluar dengan aman karena ada tidak masalah
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:
```
try:
    fh = open("testfile", "w")
    fh.write("This is my test ile for exception handling!!")
except IOError:
    print("Error : cant\'t find file or read data")
else:
    print("Written content in the file successfully")
    fh.close()
```

![gambar](prak9_2.png)

- Contoh ini mencoba membuka file yang Anda tidak memiliki izin menulis, sehingga membuat file pengecualian
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:
```
try:
    fh = open("testfile", "r")
    fh.write("This is my test ile for exception handling!!")
except IOError:
    print("Error : cant\'t find file or read data")
else:
    print("Written content in the file successfully")
    fh.close()
```

![gambar](prak9_3.png)

### Fasal kecuali tanpa Pengecualian
- Anda juga dapat menggunakan pernyataan exception tanpa exception yang didefinisikan sebagai berikut:
```
try:
You do your operations here;
......................
except:
If there is any exception, then execute this block.
......................
else:
If there is no exception then execute this block.
```
Pernyataan coba-kecuali jenis ini menangkap semua pengecualian pengecualian yang terjadi. Menggunakan percobaan seperti try-expect pernyataan tidak dianggap sebagai praktik pemrograman yang baik, karena mereka menangkap semuanya pengecualian tetapi tidak membuat programmer mengidentifikasi kemungkinan penyebab masalah terjadi
### Klausa kecuali dengan Berbagai Pengecualian
- Anda juga dapat menggunakan pernyataan exception yang sama untuk menangani beberapa exception sebagai berikut:
```
try:
You do your operations here;
......................
except(Exception1[, Exception2[,...ExceptionN]]]):
If there is any exception from the given exception list,
then execute this block.
......................
else:
If there is no exception then execute this block.
```
### Klausa coba-akhirnya
#### Contoh
- Jika Anda tidak memiliki izin untuk membuka file dalam mode tulis yang dapat ditulis, maka ini akan menghasilkan hasil berikut:
```
try:
    fh = open("testfile", "w")
    fh.write("This is my test ile for exception handling!!")
finally:
    print("Error : can\'t find file or read data")
```

![gambar](gambar/ok4.png)

- Contoh yang sama dapat ditulis lebih bersih sebagai berikut:
```
try:
    fh = open("testfile", "r")
    try:
    fh.write("This is my test ile for exception handling!!")
    finally:
        print("going to close the file")
        fh.close()
except IOError:
    print("Error : can\'t find file or read data")
```

![gambar](pr9/9.4.png)

Ketika exception dilempar ke dalam blok try, eksekusi segera dilanjutkan ke akhir memblok. Setelah semua pernyataan di blok akhirnya dieksekusi, pengecualian dimunculkan lagi dan ditangani dalam pernyataan kecuali jika ada di lapisan berikutnya yang lebih tinggi dari percobaan-kecuali penyataan.
### Argumen Pengecualian
#### Contoh
- Berikut adalah contoh untuk satu pengecualian
- Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:

![gambar](pr9/9.5.png)

### Melempar Pengecualian
#### Contoh
- Pengecualian dapat berupa string, kelas, atau objek. Sebagian besar pengecualian adalah pengecualian dari inti Python menimbulkan adalah kelas, dengan argumen=argumen yang merupakan turunan dari kelas. Mendefinisikan pengecualian baru cukup mudah dan dapat dilakukan sebagai berikut:
#### > Ketika kode di bawah dijalankan, menghasilkan hasil sebagai berikut:
```
# Drfine a function here.

def temp_convert(var):
    try:
        return int(var)
    except ValueError(Argument):
        print("The argument does not contain numbers\n", Argument)

# Call above function here.

temp_convert("xyz")
```

![gambar](pr9/9.6.png)

### Pengecualian yang Ditetapkan Pengguna
- Python juga memungkinkan Anda membuat pengecualian sendiri dengan menurunkan kelas-kelas dari yang standar pengecualian bawaan.
- Berikut adalah contoh-contoh yang terkait dengan RuntimeError. Di sini, kelas dibuat yang merupakan subkelas dari subkelas RuntimeError. Ini berguna saat Anda perlumenampilkan tampilan informasi yang lebih spesifik saat e pengecualian tertangkap.
- Di blok coba, pengecualian yang ditentukan pengguna dimunculkan dan ditangkap di blok kecuali. Itu variabel e digunakan untuk membuat instance dari kelas Networkerror.
```
class Networkerror(RuntimeError):
    def __init__(self, arg):
        self.arg = arg
try:
    raise Networkerror("Bad hostname")
except Networkerror(e):
    print(e.args)
```
![gambar](pr9/9.7.png)
