# Jarkom-Modul-1-C04-2022

Berikut adalah laporan resmi Praktikum Jaringan Komputer Modul 1 tahun 2022

Anggota Kelompok C04 :
* 5025201077 - Handitanto Herprasetyo
* 5025201057 - Muhammad Fuad Salim
* 5025201257 - Sastiara Maulikh

### 1. Sebutkan web server yang digunakan pada "monta.if.its.ac.id"! 
Display filter dengan syntax `http.host contains monta.if.ac.id`. Klik kanan kemudian klik `follow` dan pilih `TCP Stream`.

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192124823-2c68b704-317d-49fa-a1b4-bd98fd8c1b11.png">

 Web server yang digunakan adalah `nginx/1.10.3`
 
<img width="640" alt="image" src="https://user-images.githubusercontent.com/94664744/192125193-e02ac6df-aec1-43bc-9a4f-1275380ab8ac.png">

### 2.Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?

Menggunakan filter `http.host contains monta.if.ac.id`. Kemudian klik `file` lalu klik `export objects` dan klik http.

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125257-78679f6f-bb12-4929-a566-e696d7e3b8d3.png">

Kemudian pilih file dengan nama `194` karena file tersebut yang mengandung file detail topik. Save file tersebut dengan format `html`.

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125286-896ce937-a8d7-4d1c-8dd5-974210c64f05.png">

Maka didapatkan hasil seperti gambar di bawah.

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125304-5cdee7cf-f507-405b-a0cb-ee64482cb446.png">

### 3. Filter sehingga wireshark hanya menampilkan paket yang menuju port 80! 

Menggunakan `tcp.dstport==80`, sehingga didapatkan hasil

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125541-bdfa22e8-153d-4eec-ac2a-0c77471ad9a6.png">

### 4. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21!

Menggunakan `tcp.srcport==21`, sehingga didapatkan hasil

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125572-c05645b7-71ab-4c21-ba57-cb17673794b0.png">

### 5. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 443!

Menggunakan `tcp.srcport==443`, sehingga didapatkan hasil

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125647-109c26b1-ed38-478d-ade0-c5b15cdb0379.png">

### 6. Filter sehingga wireshark hanya menampilkan paket yang menuju ke lipi.go.id !

Menggunakan `http.host contains “lipi.go.id” `, sehingga didapatkan hasil

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125676-eaff1385-5a31-43b4-b1f6-402f85e30250.png">

### 7. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

Menggunakan `src host IP` `src host 192.168.0.3`, sehingga didapatkan hasil

<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125748-3c8a5c46-e103-405a-bfb7-cd75dfe03cfc.png">

### Untuk soal 8-10, silahkan baca cerita di bawah ini!

```
Di sebuah planet bernama Viltrumite, terdapat Kementerian Komunikasi dan Informatika yang baru saja menetapkan kebijakan baru. Dalam kebijakan baru tersebut, pemerintah dapat mengakses data pribadi masyarakat secara bebas jika memang dibutuhkan, baik dengan maupun tanpa persetujuan pihak yang bersangkutan. Sebagai mahasiswa yang sedang melaksanakan program magang di kementerian tersebut, kalian mendapat tugas berupa penyadapan percakapan mahasiswa yang diduga melakukan tindak kecurangan dalam kegiatan Praktikum Komunikasi Data dan Jaringan Komputer 2022. Selain itu, terdapat sebuah password rahasia (flag) yang diduga merupakan milik sebuah organisasi bawah tanah yang selama ini tidak sejalan dengan pemerintahan Planet Viltrumite. Tunggu apa lagi, segera kerjakan tugas magang tersebut agar kalian bisa mendapatkan pujian serta kenaikan jabatan di kementerian tersebut!
```
### 8. Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.

Setelah dianalisa di wireshark terdapat kejanggalan di port `60236` & `65432`

Maka dari itu kita dapat memfilter paket=paket yang berasal dan akan menuju ke port-port tersebut dengan `“tcp.port == 60236 && tcp.port == 65432”`

![no8](https://user-images.githubusercontent.com/80630201/192173819-ee046e7f-aba1-4774-a901-b892476808a7.png)

Kemudian kita hanya perlu melakukan follow pada hasil filter tersebut dan akan muncul percakapan antara dua mahasiswa tersebut

![no8 1](https://user-images.githubusercontent.com/80630201/192173821-dd52904f-7a9f-4939-b952-4619f7d55e75.png)

### 9. Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.

Dengan informasi percakapan yang ada pada soal sebelumnya diketahui bahwa kedua mahasiswa tersebut akan mengirim file di port `9002`, maka dari itu kita dapat memfilter dengan `“tcp.port == 9002”` lalu kita cari file salt dari hasil filter tersebut, setelah file salt ditemukan selanjutnya kita follow file tersebut dan kemudian save as file tersebut dengan nama sesuai ketentuan soal yaitu `C04.des3`.

![no9 1](https://user-images.githubusercontent.com/80630201/192173744-3dc60f1a-0aa1-42f8-a969-d61019180418.png)

![no9 2](https://user-images.githubusercontent.com/80630201/192173752-7e91f3dd-6bac-43c8-a9fc-3cdcc38245bb.png)

Selanjutnya kita akan decrypt file tersebut dengan `openssl` dengan metode `des3` menggunakan terminal, di sini kami menggunakan terminal linux

### 10. Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!

![no10](https://user-images.githubusercontent.com/80630201/192174131-1bd77d04-402b-48c4-9940-200129b2c998.png)
