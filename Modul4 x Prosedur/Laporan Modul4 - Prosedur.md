<h1 align="center">Laporan Praktikum Modul4 - Prosedur</h1>

<center>Nama : Rifa Cahya Ariby <center>
<center>NIM : 103112400268 <center>

# Dasar Teori
Prosedur dapat dipahami sebagai kumpulan instruksi dalam suatu program yang dikelompokkan menjadi satu instruksi baru. Tujuan utama dari prosedur adalah untuk menyederhanakan kode dalam program yang kompleks, terutama pada sistem yang besar. Saat dipanggil dalam program utama, prosedur akan memberikan efek langsung terhadap jalannya program.

Suatu subprogram dikategorikan sebagai prosedur jika tidak memiliki deklarasi tipe nilai yang dikembalikan dan tidak menggunakan kata kunci _return_ dalam tubuh subprogramnya. Dalam struktur program, prosedur memiliki kedudukan yang setara dengan instruksi dasar seperti _assignment_ atau perintah yang berasal dari pustaka tertentu, misalnya _fmt.Scan_ dan _fmt.Print_ dalam bahasa pemrograman Go. Oleh karena itu, dalam penamaan prosedur, sebaiknya digunakan kata kerja atau istilah yang mencerminkan suatu proses, seperti _cetak_, _hitungRerata_, _cariNilai_, _belok_, atau _mulai_.

## Soal 1
1. Minggu ini, mahasiswa Fakultas Informatika mendapatkan tugas dari mata kuliah matematika
diskrit untuk mempelajari kombinasi dan permutasi. Jonas salah seorang mahasiswa, iseng
untuk mengimplementasikannya ke dalam suatu program. Oleh karena itu bersediakah kalian
membantu Jonas? (tidak tentunya ya :p)
Masukan terdiri dari empat buah bilangan asli 𝑎, 𝑏, 𝑐, dan 𝑑 yang dipisahkan oleh spasi, dengan
syarat 𝑎 ≥ 𝑐 dan 𝑏 ≥ 𝑑.
Keluaran terdiri dari dua baris. Baris pertama adalah hasil permutasi dan kombinasi 𝒂 terhadap
𝑐, sedangkan baris kedua adalah hasil permutasi dan kombinasi 𝑏 terhadap 𝑑.
Catatan: permutasi (P) dan kombinasi (C) dari 𝑛 terhadap 𝑟 (𝑛 ≥ 𝑟) dapat dihitung dengan
menggunakan persamaan berikut!

![[soal1m4.png]]

code
``` go
package main

import "fmt"

func faktorial(n int, hasil *int) {

    *hasil = 1

    for i := 1; i <= n; i++ {

        *hasil *= i

    }

}

  

func permutasi(n, r int, hasil *int) {

    var fn, fnr int

    faktorial(n, &fn)

    faktorial(n-r, &fnr)

    *hasil = fn / fnr

}

  

func kombinasi(n, r int, hasil *int) {

    var fn, fr, fnr int

    faktorial(n, &fn)

    faktorial(r, &fr)

    faktorial(n-r, &fnr)

    *hasil = fn / (fr * fnr)

}

  

func main() {

    var a, b, c, d int

    fmt.Scan(&a, &b, &c, &d)

    var p1, c1, p2, c2 int

    permutasi(a, c, &p1)

    kombinasi(a, c, &c1)

    permutasi(b, d, &p2)

    kombinasi(b, d, &c2)

    fmt.Println(p1, c1)

    fmt.Println(p2, c2)

}
```

## Output

![[o1m4.png]]

Program ini dibuat untuk menghitung permutasi dan kombinasi dari dua pasang bilangan dengan menggunakan prosedur tanpa return.
Pertama, program membaca empat bilangan sebagai input, yaitu `a, b, c, d`. Kemudian, nilai faktorial dihitung menggunakan prosedur `faktorial`, yang menerima sebuah bilangan `n` dan menyimpan hasil faktorialnya dalam variabel yang dikirim melalui pointer.
Prosedur `permutasi` menggunakan hasil faktorial untuk menghitung nilai permutasi berdasarkan rumus `P(n,r) = n! / (n-r)!`. Demikian pula, prosedur `kombinasi` menggunakan faktorial untuk menghitung kombinasi berdasarkan rumus `C(n,r) = n! / (r!(n-r)!)`.
Setelah hasil permutasi dan kombinasi dihitung untuk dua pasangan bilangan (`a` dengan `c` dan `b` dengan `d`), program mencetak hasilnya ke layar dalam dua baris, di mana setiap baris berisi hasil permutasi dan kombinasi yang dihitung.
Kode ini dibuat dengan pendekatan modular, di mana setiap perhitungan memiliki prosedurnya sendiri, sehingga lebih terstruktur dan mudah dipahami. Penggunaan pointer dalam prosedur memungkinkan hasil dihitung langsung tanpa perlu mengembalikan nilai, sesuai dengan konsep prosedur dalam pemrograman Go.


## Soal 2
2. Kompetisi pemrograman tingkat nasional berlangsung ketat. Setiap peserta diberikan 8 soal
yang harus dapat diselesaikan dalam waktu 5 jam saja. Peserta yang berhasil menyelesaikan
soal paling banyak dalam waktu paling singkat adalah pemenangnya.
Buat program gema yang mencari pemenang dari daftar peserta yang diberikan. Program harus dibuat modular, yaitu dengan membuat prosedur hitungSkor yang mengembalikan total soal
dan total skor yang dikerjakan oleh seorang peserta, melalui parameter formal. Pembacaan
nama peserta dilakukan di program utama, sedangkan waktu pengerjaan dibaca di dalam
prosedur.prosedure hitungSkor(in/out soal, skor : integer)
Setiap baris masukan dimulai dengan satu string nama peserta tersebut diikuti dengan adalah
8 integer yang menyatakan berapa lama (dalam menit) peserta tersebut menyelesaikan soal.
Jika tidak berhasil atau tidak mengirimkan jawaban maka otomatis dianggap menyelesaikan
dalam waktu 5 jam 1 menit (301 menit).
Satu baris keluaran berisi nama pemenang, jumlah soal yang diselesaikan, dan nilai yang
diperoleh. Nilai adalah total waktu yang dibutuhkan untuk menyelesaikan soal yang berhasil
diselesaikan.

![[soal2m4.png]]

Keterangan:
Astuti menyelesaikan 6 soal dalam waktu 287 menit, sedangkan Bertha 7 soal dalam waktu
294 menit. Karena Bertha menyelesaikan lebih banyak, maka Bertha menang. Jika keduanya
menyelesaikan sama banyak, maka pemenang adalah yang menyelesaikan dengan total waktu
paling kecil.

``` go
package main
import "fmt"
func hitungskor(waktu [8]int, soal *int, total *int) {

    for i := 0; i < 8; i++ {

        if waktu[i] < 301 {

            *soal++

            *total += waktu[i]

        }

    }

}

  

func main() {

    var nama, pemenang string

    var waktu [8]int

    maxsoal, minwaktu := 0, 999999

    for {

        fmt.Scan(&nama)

        if nama == "Selesai" {

            break

        }

        for i := 0; i < 8; i++ {

            fmt.Scan(&waktu[i])

        }

        var soal, total int

        hitungskor(waktu, &soal, &total)

        if soal > maxsoal || (soal == maxsoal && total < minwaktu) {

            maxsoal, minwaktu, pemenang = soal, total, nama

        }

    }

    fmt.Println(pemenang, maxsoal, minwaktu)

}
```

## Output
![[o2m4.png]]

Pada program ini dinyatakan bahwa dalam sebuah kompetisi pemrograman, pemenang ditentukan berdasarkan jumlah soal yang berhasil diselesaikan dalam waktu sesingkat mungkin. Jika ada peserta dengan jumlah soal yang sama, maka peserta dengan total waktu penyelesaian yang lebih kecil akan menjadi pemenang. Program ini menggunakan pendekatan modular dengan prosedur `hitungSkor` untuk menghitung jumlah soal dan total waktu, serta `cariPemenang` untuk membaca data dan menentukan pemenang.

## Soal 3
3. Skiena dan Revilla dalam Programming Challenges mendefinisikan sebuah deret bilangan. Deret
dimulai dengan sebuah bilangan bulat n. Jika bilangan n saat itu genap, maka suku berikutnya
adalah ½n, tetapi jika ganjil maka suku berikutnya bernilai 3n+1. Rumus yang sama digunakan
terus menerus untuk mencari suku berikutnya. Deret berakhir ketika suku terakhir bernilai 1.
Sebagai contoh jika dimulai dengan n=22, maka deret bilangan yang diperoleh adalah:
22 11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
Untuk suku awal sampai dengan 1000000, diketahui deret selalu mencapai suku dengan nilai
1.Buat program skiena yang akan mencetak setiap suku dari deret yang dijelaskan di atas untuk
nilai suku awal yang diberikan. Pencetakan deret harus dibuat dalam prosedur cetakDeret yang
mempunyai 1 parameter formal, yaitu nilai dari suku awal.
prosedure cetakDeret(in n : integer )
Masukan berupa satu bilangan integer positif yang lebih kecil dari 1000000.
Keluaran terdiri dari satu baris saja. Setiap suku dari deret tersebut dicetak dalam baris yang
dan dipisahkan oleh sebuah spasi.

![[soal3m4.png]]

``` go
package main
import "fmt"
func cetakderet(n int) {

    for n != 1 {

        fmt.Print(n, " ")

        if n%2 == 0 {

            n /= 2

        } else {

            n = 3*n + 1

        }

    }

    fmt.Println(1)

}

func main() {

    var num int

    fmt.Scan(&num)

    if num > 0 && num < 1000000 {

        cetakderet(num)

    }

}
```
## Output
![[o3m4.png]]

Kesimpulan dari program ini adalah bahwa program mencetak deret bilangan berdasarkan aturan Collatz (3n+1). Program akan terus membagi angka dengan 2 jika genap atau mengalikannya dengan 3 dan menambahkan 1 jika ganjil, hingga mencapai angka 1. Program ini efisien dan hanya memproses bilangan positif kurang dari 1.000.000.
