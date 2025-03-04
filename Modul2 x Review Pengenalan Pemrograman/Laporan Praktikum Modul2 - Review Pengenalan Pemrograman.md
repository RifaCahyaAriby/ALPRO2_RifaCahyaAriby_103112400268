<h1 align="center">Laporan Praktikum Modul2 - Review Pengenalan Pemrograman</h1>
<center>Nama : Rifa Cahya Ariby <center>
<center>NIM : 103112400268 <center>



___
 # Dasar Teori

Bahasa Go atau yang biasa di sebut Go lang menawarkan pemrograman yang simpel namun andal, dengan sintaks yang lugas dan efisien. Program Go wajib memiliki package main dan fungsi main() sebagai gerbang awal eksekusi. Pengembangan meliputi penulisan kode dalam berkas .go, kompilasi dengan perintah go build, dan menjalankan program lewat terminal. Go menyediakan beragam tipe daTa seperti integer, float, boolean, dan string, serta mendukung deklarasi variabel yang fleksibel. Kontrol alur program mencakup perulangan for dalam berbagai bentuk, serta percabangan bersyarat dengan if-else dan switch-case untuk pengambilan keputusan.


# SOAL 2A


> 1. Telusuri program berikut dengan cara mengkompilasi dan mengeksekusi program. Silakan masukan data yang sesuai sebanyak yang diminta program. Perhatikan keluaran yang diperoleh. Coba terangkan apa sebenarnya yang dilakukan program tersebut?

```go
package main

import "fmt"

func main() {

var (

satu, dua, tiga string

temp string

)

fmt.Print("Masukan input string: ")

fmt.Scanln(&satu)

fmt.Print("Masukan input string: ")

fmt.Scanln(&dua)

fmt.Print("Masukan input string: ")

fmt.Scanln(&tiga)

fmt.Println("Output awal = " + satu + " " + dua + " " + tiga)

temp = satu

satu = dua

dua = tiga

tiga = temp

fmt.Println("Output akhir = " + satu + " " + dua + " " + tiga)

}
```






> Kode tersebut merupakan program yang meninta input string dari pengguna sebanyak 3 kali, kemudian menampilkan output awal dan akhir dari string tersebut. Output awal adalah gabungan dari ketiga string yang diinputkan, sedangkan output akhir adalah gabungan dari ketiga string yang diinputkan tetapi dengan aturan yang dibalik

## Output
![Output](output/2a%20no1.png)

___

> 2. Tahun kabisat adalah tahun yang habis dibagi 400 atau habis dibagi 4 tetapi tidak habis
> dibagi 100. Buatlah sebuah program yang menerima input sebuah bilangan bulat dan
> memeriksa apakah bilangan tersebut merupakan tahun kabisat (true) atau bukan (false).


```go
package main

import "fmt"

    func main() {

        var tahun int

        fmt.Print("Tahun: ")

        fmt.Scan(&tahun)

        kabisat := (tahun/400*400 == tahun) || (tahun/4*4 == tahun && tahun/100*100 != tahun)

        fmt.Println("Kabisat:", kabisat)
    }
```

## Output
![Output](output/2a%20no2.png)

---

>3. Buat program Bola yang menerima input jari-jari suatu bola (bilangan bulat). Tampilkan
> Volume dan Luas kulit bola. 𝑣𝑜𝑙𝑢𝑚𝑒𝑏𝑜𝑙𝑎 = ! " 𝜋𝑟" dan 𝑙𝑢𝑎𝑠𝑏𝑜𝑙𝑎 = 4𝜋𝑟# (π ≈ 3.1415926535).

```go
package  main
import "fmt"

func main() {

    var jari float64

    var luas , volume float64

    const phi = 3.1415926535

  
    fmt.Print("Jari-jari bola: ")

    fmt.Scan(&jari)

    luas = 4.0 * phi * jari * jari

    volume = (4.0 / 3.0) * phi * jari * jari * jari

    fmt.Printf("Luas bola: %.4f\n", luas)

    fmt.Printf("Volume bola: %.4f\n", volume)

}
```


> Program diatas adalah untuk menghitung luas dan volume sesuai algoritma yang ada pada soal lalu %.4f\n dipakai untuk menghasilkan 4 digit angka sebelum koma 

## Output
![Output](output/2a%20no3.png)
___

> 4. Dibaca nilai temperatur dalam derajat Celsius. Nyatakan temperatur tersebut dalam Fahrenheit
> 𝐶𝑒𝑙𝑠𝑖𝑢𝑠 = (𝐹𝑎ℎ𝑟𝑒𝑛ℎ𝑒𝑖𝑡 − 32) ×5/9
> 𝑅𝑒𝑎𝑚𝑢𝑟 = 𝐶𝑒𝑙𝑐𝑖𝑢𝑠 ×4/5
> 𝐾𝑒𝑙𝑣𝑖𝑛 = (𝐹𝑎ℎ𝑟𝑒𝑛ℎ𝑒𝑖𝑡 + 459.67) ×5 / 9

```go
package main

import "fmt"

func main() {

    var celsius float64

    fmt.Print("Temperatur Celsius: ")

    fmt.Scan(&celsius)

    fahrenheit := (celsius * 9 / 5) + 32

    reamur := celsius * 4 / 5

    kelvin := celsius + 273

  

    fmt.Println("Derajat Reamur:", reamur)

    fmt.Println("Derajat Fahrenheit:", fahrenheit)

    fmt.Println("Derajat Kelvin:", kelvin)

}
```

> Program ini meminta input suhu dalam Celsius dari pengguna, kemudian mengonversinya ke Reamur, Fahrenheit, dan Kelvin, dan akhirnya menampilkan hasil konversi tersebut.

## Output
![Output](output/2a%20no4.png)

>5. Tipe karakter sebenarnya hanya apa yang tampak dalam tampilan. Di dalamnya tersimpan
> dalam bentuk biner 8 bit (byte) atau 32 bit (rune) saja.
> Buat program ASCII yang akan membaca 5 buat data integer dan mencetaknya dalam
> format karakter. Kemudian membaca 3 buah data karakter dan mencetak 3 buah karakter
> setelah karakter tersebut (menurut tabel ASCII)
> Masukan terdiri dari dua baris. Baris pertama berisi 5 buah data integer. Data integer
> mempunyai nilai antara 32 s.d. 127. Baris kedua berisi 3 buah karakter yang berdampingan
> satu dengan yang lain (tanpa dipisahkan spasi).
> Keluaran juga terdiri dari dua baris. Baris pertama berisi 5 buah representasi karakter dari
> data yang diberikan, yang berdampingan satu dengan lain, tanpa dipisahkan spasi. Baris
> kedua berisi 3 buah karakter (juga tidak dipisahkan oleh spasi).

```go
package main

import "fmt"
func main() {
	var a, b, c, d, e int
	var x, y, z byte
	
	fmt.Scan(&a, &b, &c, &d, &e)
	fmt.Printf("%c%c%c%c%c\n", a, b, c, d, e)
	
	fmt.Scanf("%c%c%c", &x, &y, &z)
	fmt.Printf("%c%c%c\n", x+3, y+3, z+3)
}

```

> Program ini menerima lima input bilangan bulat dan menginterpretasikannya sebagai kode ASCII untuk karakter, lalu mencetak kelima karakter tersebut. Selanjutnya, program menerima tiga input karakter, menambahkan 3 ke masing-masing kode ASCII karakter tersebut, dan mencetak tiga karakter baru hasil penambahan. Singkatnya, program ini mengonversi angka menjadi karakter dan melakukan pergeseran karakter berdasarkan kode ASCII.

## Output
![Output](output/2a%20no5.png)

# SOAL 2B

> 1. Siswa kelas IPA di salah satu sekolah menengah atas di Indonesia sedang mengadakan
> praktikum kimia. Di setiap percobaan akan menggunakan 4 tabung reaksi, yang mana
> susunan warna cairan di setiap tabung akan menentukan hasil percobaan. Siswa diminta
> untuk mencatat hasil percobaan tersebut. Percobaan dikatakan berhasil apabila susunan
> warna zat cair pada gelas 1 hingga gelas 4 secara berturutan adalah ‘merah’, ‘kuning’,
> ‘hijau’, dan ‘ungu’ selama 5 kali percobaan berulang.
> Buatlah sebuah program yang menerima input berupa warna dari ke 4 gelas reaksi
> sebanyak 5 kali percobaan. Kemudian program akan menampilkan true apabila urutan
> warna sesuai dengan informasi yang diberikan pada paragraf sebelumnya, dan false untuk
> urutan warna lainnya.
>![Output](output/Pasted%20image%2020250228184331.png)


```go
package main

import "fmt"
func main() {
    var g1, g2, g3, g4 string
    var berhasil bool
    berhasil = true
    for i := 1; i <= 5; i++ {
        fmt.Print("Percobaan", i, ": ")
        fmt.Scan(&g1, &g2, &g3, &g4)
        if g1 != "merah" && g2 != "kuning" && g3 != "hijau" && g4 != "ungu" {
            berhasil = false
        }
    }
    fmt.Print("Berhasil: ", berhasil)
}
```

Program ini mensimulasikan 5 percobaan, di mana pengguna memasukkan 4 kata. Program memeriksa apakah setiap input sesuai dengan urutan "merah kuning hijau ungu". Jika ada satu kesalahan, hasilnya akan false. Namun, logika kondisi sebaiknya menggunakan || agar mendeteksi kesalahan dengan benar, bukan && yang selalu false kecuali semua salah.
## Output
![Output](output/2b%20no1.png)

> 2.  Suatu pita (string) berisi kumpulan nama-nama bunga yang dipisahkan oleh spasi dan ‘–‘,
> contoh pita diilustrasikan seperti berikut ini.
> Pita: mawar – melati – tulip – teratai – kamboja – anggrek
> Buatlah sebuah program yang menerima input sebuah bilangan bulat positif (dan tidak nol)N, kemudian program akan meminta input berupa nama bunga secara berulang sebanyakN kali dan nama tersebut disimpan ke dalam pita.(Petunjuk: gunakan operasi penggabungan string dengan operator “+” ). Tampilkan isi pita setelah proses input selesai.
> ![Output](output/Pasted%20image%2020250228184409.png)


```go
package main
import "fmt"
func main () {
    var n int
    var bunga string
    fmt.Print("N: ")
    fmt.Scan(&n)

    pita := ""
    for i := 1; i <= n; i++ {
        fmt.Printf("Bunga %d : ", i)
        fmt.Scan(&bunga)
        if i == 1 {
            pita += bunga

        } else {

            pita += " – " + bunga
        }
    }
    fmt.Println("Pita: ", pita)
}
```
> Program ini mengambil sejumlah input bunga dari pengguna, kemudian menggabungkannya menjadi sebuah string yang disebut "pita" dengan pemisah " – ".

## Output
![Output](output/2b%20no2.png)

>3. Setiap hari Pak Andi membawa banyak barang belanjaan dari pasar dengan mengendarai
> sepeda motor. Barang belanjaan tersebut dibawa dalam kantong terpal di kiri-kanan motor.
> Sepeda motor tidak akan oleng jika selisih berat barang di kedua kantong sisi tidak lebih
> dari 9 kg.
> Buatlah program Pak Andi yang menerima input dua buah bilangan real positif yang
> menyatakan berat total masing-masing isi kantong terpal. Program akan terus meminta
> input bilangan tersebut hingga salah satu kantong terpal berisi 9 kg atau lebih.
> ![Output](output/Pasted%20image%2020250228184827.png)

```go
package main
import "fmt"
func main() {
    for {
        var berat1, berat2 float64
        fmt.Print("Masukan berat belanjaan di kedua kantong: ")
        fmt.Scanln(&berat1, &berat2)
        if berat1 < 0 || berat2 < 0 || berat1 + berat2 > 150 {
            fmt.Println("Proses selesai")
            break
        }
        selisih := berat1 - berat2
        if selisih < 0 {
            selisih = -selisih
        }
        oleng := selisih >= 9
        fmt.Println("Sepeda motor pak Andi akan oleng:", oleng)
    }
}
```
>Program ini mensimulasikan apakah sepeda motor Pak Andi akan oleng berdasarkan berat belanjaan di kedua kantong. Program akan terus meminta input berat belanjaan sampai total berat melebihi 150 atau salah satu berat bernilai negatif. Jika selisih berat kedua kantong lebih dari atau sama dengan 9, program akan mencetak "Sepeda motor pak Andi akan oleng: true", jika tidak, program akan mencetak "Sepeda motor pak Andi akan oleng: false".

## Output
![Output](output/2b%20no3.png)

4. 
$$
f(k) = \frac{(4k + 2)^2}{(4k + 1)(4k + 3)}
$$
Buatlah sebuah program yang menerima input sebuah bilangan sebagai K, kemudian
menghitung dan menampilkan nilai f(K) sesuai persamaan di atas.
√2 merupakan bilangan irasional. Meskipun demikian, nilai tersebut dapat dihampiri
dengan rumus berikut:
![Output](output/Pasted%20image%2020250228185224.png)
![Output](output/Pasted%20image%2020250228185140.png)
Modifikasi program sebelumnya yang menerima input integer 𝐾 dan menghitung √2
untuk 𝐾 tersebut. Hampiran √2 dituliskan dalam ketelitian 10 angka di belakang koma.

```go
package main
import (
    "fmt"
    "math"
)
func main() {
    var k int
    fmt.Print("Masukan bilangan: ")
    fmt.Scan(&k)
    result := 1.0

    for i := 1; i <= k; i++ {
        numerator := math.Pow(float64(4*k+2),2)
        denumerator := float64((4*k)*(4*k+3))
        result *= numerator/denumerator
    }
    fmt.Printf("Hasil dari operasi fungsi = %.10f\n",result)
}
```
> Program ini menghitung hasil perkalian berulang berdasarkan input bilangan bulat `k`. Perulangan dilakukan sebanyak `k` kali, di mana setiap iterasi mengalikan hasil sebelumnya dengan suatu pecahan yang numerator dan denumeratornya dihitung berdasarkan nilai `k`. Hasil akhir dari perkalian tersebut, dengan format 10 angka desimal di belakang koma, dicetak ke layar. Dapat disimpulkan bahwa program ini mengimplementasikan sebuah fungsi matematika yang hasilnya bergantung pada nilai `k`.
## Output
![Output](output/2b%20no4.png)

# Soal 2C

> 1. PT POS membutuhkan aplikasi perhitungan biaya kirim berdasarkan berat parsel. Maka,
> buatlah program BiayaPos untuk menghitung biaya pengiriman tersebut dengan
> ketentuan sebagai berikut!
> Dari berat parsel (dalam gram), harus dihitung total berat dalam kg dan sisanya (dalam
> gram). Biaya jasa pengiriman adalah Rp. 10.000,- per kg. Jika sisa berat tidak kurang dari
> 500 gram, maka tambahan biaya kirim hanya Rp. 5,- per gram saja. Tetapi jika kurang dari
> 500 gram, maka tambahan biaya akan dibebankan sebesar Rp. 15,- per gram. Sisa berat
> (yang kurang dari 1kg) digratiskan biayanya apabila total berat ternyata lebih dari 10kg.
![Output](output/Pasted%20image%2020250228190238.png)

```go
package main

import "fmt"

func main() {

    var beratgram,sisagram, kg, biayadasar, totalBiaya, biayatambahan int

  

    fmt.Print("Berat parsel (gram): ")

    fmt.Scan(&beratgram)

  

    kg = beratgram / 1000

    sisagram = beratgram % 1000

    biayadasar = kg * 10000

  

    if kg > 10 {

        biayatambahan = 0

    } else if sisagram >= 500 {

        biayatambahan = sisagram * 5

    } else {

        biayatambahan = sisagram * 15

    }

    totalBiaya = biayadasar + biayatambahan

  

    fmt.Printf("Detail berat: %d kg + %d gr\n", kg, sisagram)

    fmt.Printf("Detail biaya: Rp. %d + Rp. %d\n", biayadasar, biayatambahan)

    fmt.Printf("Total biaya: Rp. %d\n", totalBiaya)

  

}
```
> Program ini menghitung total biaya pengiriman parsel berdasarkan beratnya. Berat parsel dalam gram diinput, lalu dihitung biaya dasar berdasarkan kilogram dan biaya tambahan berdasarkan sisa gram. Biaya tambahan berbeda tergantung sisa gram dan total kilogram. Terakhir, program menampilkan detail berat dan biaya, serta total biaya pengiriman.

## Output
![Output](output/2c%20no1.png)

> 2. Diberikan sebuah nilai akhir mata kuliah (NAM) [0..100] dan standar penilaian nilai mata
> kuliah (NMK) sebagai berikut:
> ![Output](Pasted%20image%2020250228190837.png)
> ![Output](Pasted%20image%2020250228190906.png)

``` go
package main

import "fmt"

func main() {
 var nam float64 
 var nmk string
 fmt.Print("Nilai akhir mata kuliah:  ")
 fmt.Scan(&nam)
 if nam > 80 {
 nmk = "A"
 }  else if 72.5 < nam && nam <= 80 {
	nmk = "AB"
	} else if 65 < nam && nam <= 72.5 {
	nmk = "B"
	} else if 57.5 < nam && nam <= 65 {
	nmk = "BC"
	} else if 50 < nam && nam <= 57.5 {
	nmk = "C"
	} else if 40 < nam && nam <= 50 {
	nmk = "D"
	} else if nam <= 40 {
	nmk = "E"
	}
   
	fmt.Println("Nilai mata kuliah:  ", nmk)
}

```
Jawablah pertanyaan-pertanyaan berikut:
a. Jika nam diberikan adalah 80.1, apa keluaran dari program tersebut? Apakah eksekusi
program tersebut sesuai spesifikasi soal?
b. Apa saja kesalahan dari program tersebut? Mengapa demikian? Jelaskan alur program
seharusnya!
c. Perbaiki program tersebut! Ujilah dengan masukan: 93.5; 70.6; dan 49.5. Seharusnya
keluaran yang diperoleh adalah ‘A’, ‘B’, dan ‘D’.
Jawaban :
// 1. jika saya memasukan nam 80.1 maka akan menghasilkan A
// 2. kesalahan dari program yang terdapat pada modul yaitu
// - kurang nya else untuk melakukan percabangan
// - ada kesalahan penulisan tanda >
// - perlu disesuaikan posisi else yang benar
// - ada kesalahan penulisan variabel nam pada variable nmk
// 3. Sudah saya perbaiki dan hasilnya benar


> 3. Sebuah bilangan bulat b memiliki faktor bilangan f > 0 jika f habis membagi b. Contoh: 2
> merupakan faktor dari bilangan 6 karena 6 habis dibagi 2.
> Buatlah program yang menerima input sebuah bilangan bulat b dan b > 1. Program harus
> dapat mencari dan menampilkan semua faktor dari bilangan tersebut!
> Bilangan bulat b > 0 merupakan bilangan prima p jika dan hanya jika memiliki persis duafaktor bilangan saja, yaitu 1 dan dirinya sendiri.Lanjutkan program sebelumnya. Setelah menerima masukan sebuah bilangan bulat b > 0.Program tersebut mencari dan menampilkan semua faktor bilangan tersebut. Kemudian,program menentukan apakah b merupakan bilangan prima.
> [Output](output/Pasted%20image%2020250228191454.png)

``` go
package main

import "fmt"

func main() {
	var b int
	var Prima string
	fmt.Print("Bilangan: ")
	fmt.Scan(&b)

	fmt.Print("Faktor: ")
	Prima = "true"
	for i := 1; i <= b; i++ {
		if b%i == 0 {
			fmt.Print(i, " ")
			if i != 1 && i != b {
				Prima = "false"
			}
		}
	}
	fmt.Println()
	fmt.Print("Prima: ", Prima)
}
```
> Program ini menerima input bilangan bulat : b, kemudian menampilkan faktor-faktor dari bilangan tersebut. Setelah menampilkan faktor, program menentukan apakah bilangan tersebut prima atau bukan. Jika bilangan hanya memiliki dua faktor (1 dan bilangan itu sendiri), maka program akan mencetak "Prima: true". Jika tidak, program akan mencetak "Prima: false". Singkatnya, program ini melakukan faktorisasi bilangan dan menentukan keprimaannya.
## Output
![Output](output/2c%20no3.png)
