# Jarkom-Modul-1-C04-2022

Berikut adalah laporan resmi Praktikum Jaringan Komputer Modul 1 tahun 2022

Anggota Kelompok C04 :
* 5025201077 - Handitanto Herprasetyo
* 5025201057 - Muhammad Fuad Salim
* 5025201257 - Sastiara Maulikh

## 1. Sebutkan web server yang digunakan pada "monta.if.its.ac.id"! 
Display filter dengan syntax "http.host contains monta.if.ac.id". Klik kanan kemudian klik follow dan pilih TCP Stream.
<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192124823-2c68b704-317d-49fa-a1b4-bd98fd8c1b11.png">
 Web server yang digunakan adalah nginx/1.10.3
<img width="640" alt="image" src="https://user-images.githubusercontent.com/94664744/192125193-e02ac6df-aec1-43bc-9a4f-1275380ab8ac.png">

## 2.Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?
Menggunakan filter "http.host contains monta.if.ac.id". Kemudian klik “file” lalu klik “export objects” dan klik http.
<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125257-78679f6f-bb12-4929-a566-e696d7e3b8d3.png">
Kemudian pilih file dengan nama “194” karena file tersebut yang mengandung file detail topik. Save file tersebut dengan format html.
<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125286-896ce937-a8d7-4d1c-8dd5-974210c64f05.png">
Maka didapatkan hasil seperti gambar di bawah
<img width="960" alt="image" src="https://user-images.githubusercontent.com/94664744/192125304-5cdee7cf-f507-405b-a0cb-ee64482cb446.png">

## 3. Ikuti perintah di basic.ichimarumaru.tech! Username dan password bisa didapatkan dari file .pcapng!
- Gunakan syntax filter `http.host contains "basic.ichimarumaru.tech"` pada file `.pcapng` yang telah didownload untuk nomor 1-5.
- Akan terdapat beberapa paket berprotokol `HTTP`.
- Didalam salah satu paket tersebut terdapat basic authorization yang didalamnya terdapat username dan password.
- Gunakan username dan password untuk login ke `basic.ichimarumaru.tech`
- Isi jawaban urutan konfigurasi pengkabelan `T568A`
![Nomor 3](assets/Nomor%203.png)
## 4. Temukan paket mysql yang mengandung perintah query select!
Gunakan filter `mysql.query matches select`
![no4-1](assets/no4-1.png)
![no4-2](assets/no4-2.png)
![no4-3](assets/no4-3.png)

## 5. Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! Username dan password bisa didapat dari query insert pada table users dari file .pcap!
- Gunakan syntax filter `mysql contains username && mysql contains password`
- Akan terdapat satu hasil paket berprotokol `MySQL`
- Buka Paket tersebut akan terdapat query username dan password yang sama dengan yang diminta soal
- Gunakan username dan password untuk login ke `portal.ichimarumaru.tech`
- Isi jawaban urutan konfigurasi pengkabelan `T568B`
![Nomor 5](assets/Nomor%205.png)
## 6. Cari username dan password ketika melakukan login ke FTP Server!
- Gunakan display filter `ftp`
- Cari bagian yang memiliki argumen `Request: USER` diikuti dengan username FTP Server
- Untuk passwordnya, cari bagian yang memiliki argumen `Request: PASS` diikuti dengan password FTP Server
![Nomor 4](https://i.imgur.com/4Nym81b.png)

## 7. Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")
- Gunakan syntax filter `frame contains Real.pdf`
- Akan terdapat paket yang berprotokol `FTP-DATA`
- klik kanan salah satu paket dan kemudian follow TCP Stream
![Nomor 7-1](assets/Nomor%207-1.png)
- Pilih untuk menampilkan data dalam `Raw`
![Nomor 7-2](assets/Nomor%207-2.png)
- Kemudian save as `Real.pdf`
![Nomor 7-3](assets/Nomor%207-3.png)
- Jika berhasil, File tersebut jika dibuka akan terdapat tulisan `YOU FOUND ME`
![Nomor 7-4](assets/Nomor%207-4.png)
## 8. Cari paket yang menunjukan pengambilan file dari FTP tersebut!
- Gunakan display filter `ftp.request.command==RETR`
![Nomor 8](https://i.imgur.com/cseYOBk.png)
Ternyata kosong, karena tidak ada file yang diambil (download)

## 9. Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!
- Gunakan syntax filter `ftp-data.command contains "secret.zip"`
![Nomor 9-1](assets/Nomor%209-1.png)
- Akan terdapat paket yang berprotokol `FTP-DATA`
- klik kanan salah satu paket dan kemudian follow TCP Stream
![Nomor 9-2](assets/Nomor%209-2.png)
- Pilih untuk menampilkan data dalam `Raw`
![Nomor 9-3](assets/Nomor%209-3.png)
- Kemudian save as `secret.zip`
![Nomor 9-4](assets/Nomor%209-4.png)
- Jika berhasil, Didalam zip file tersebut terdapat wanted.pdf yang dikunci
![Nomor 9-5](assets/Nomor%209-5.png)

## 10. Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan password untuk membuka file rahasia yang ada di "secret.zip"!
