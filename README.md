# Jarkom-Modul-1-E24-2023
## Anggota Kelompok
1. Daffa Zimraan Hasan (5025221223)
2. Wardatul Amalia Safitri (5025211006)
   
## Soal 1
### Pertanyaan
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file. </br >
a) Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? </br >
b) Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? </br>
c) Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut? </br>
d) Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

### Penyelesaian
Pada soal pertama, kami diminta untuk mengidentifikasi sequence number (raw) dan acknowledge number (raw) pada packet yang menunjukkan aktivitas mengunggah file dan packet response dari aktivitas tersebut. Karena jenis protokol yang diminta adalah protokol FTP, maka kami melakukan display filter dengan command `ftp`. Lalu, kami mencari jenis aktivitas yang menggunakan command `STOR` sebagai penanda aktivitas mengunggah file. Dari proses ini, ditemukan packet bernomor 147 sebagai packet aktivitas mengunggah file.</br>
![1-request](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/1-request.png)</br>
Selain dengan cara mencari satu per satu command `STOR` dalam wireshark, `ftp.request.command == STOR` juga bisa diterapkan dalam display filter sehingga hanya memunculkan paket dengan command STOR pada protokol ftp.</br>
</br>
Dari sini, kami menemukan informasi terkait sequence number (raw) dan acknowledge number (raw) pada packet yang diminta. Sequence number (raw)-nya adalah **258040667** dan acknowledge number (raw)-nya adalah **1044861039**</br>
Kemudian untuk menjawab pertanyaan poin c dan d, kami mengecek sequence number (raw) dan acknowledge number (raw) pada paket 149. Paket 149 adalah paket response dari aktivitas mengunggah file. </br>
![1-response](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/1-response.png)</br> 
Sehingga didapatkan Sequence number (raw)-nya adalah **1044861039** dan acknowledge number (raw)-nya adalah **258040696**</br>
</br>
Dengan demikian, kami dapat memperoleh flag sebagai berikut
![1-flag](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/1-flag.png)</br>
Untuk soal ini, kami merasa tidak mengalami kendala yang berarti

## Soal 2
### Pertanyaan
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

### Penyelesaian
Pada soal nomor 2, kami diminta menjawab jenis web server yang digunakan pada platform praktikum jaringan komputer. Untuk mengetahui hal ini menggunakan wireshark, pertama-tama kami menerapkan filter `ip.dst == 10.21.78.111` untuk mendapatkan paket yang menuju ip platform praktikum. Sebagaimana yang kita ketahui, platform praktikum jaringan komputer memiliki ip address 10.27.78.111. </br>
![2-filter](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/2-filter.png)</br>
Setelah itu, pilih salah satu paket dan lakukan analisa **Follow TCP Stream** untuk mendapatkan data sebagai berikut </br>
![2-gunicorn](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/2-gunicorn.png)</br>
Dari sini, didapatkan informasi terkait web server yang digunakan dalam platform praktikum jarkom, yaitu **gunicorn**</br>
</br>
Berikut flag yang kami dapatkan dari soal nomor 2 ini
![2-flag](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/2-flag.png)</br>

### Kendala yang dialami
Pada awalnya, saya tidak terpikir bisa melakukan identifikasi web server melalui follow TCP Stream. Jadi, di awal pengerjaan saya melakukan inspect pada platform praktikum dan mengecek bagian network untuk mendapatkan informasi web server yang digunakan oleh platform. Kemudian, ketika mengerjakan nomor soal lainnya saya baru terpikir untuk menggunakan Follow TCP Stream sebagai cara mengecek web server melalui wireshark.

## Soal 3
### Pertanyaan
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut: </br>
a) Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702? </br>
b) Protokol layer transport apa yang digunakan?

### Penyelesaian
### Kendala yang dialami
## Soal 4
### Pertanyaan
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

### Penyelesaian
Pada soal ini kami diminta memasukkan nilai checksum dari paket nomor 130 untuk mendapatkan flag. Cara untuk mendapatkan nilai checksum relatif mudah, karena hanya perlu membuka deskripsi user datagram protocol seperti berikut </br>
![4](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/4.png)</br>
<br>
Kemudian, nilai ini dimasukkan ke netcat untuk mendapatkan flag sebagai berikut
![4-flag](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/4-flag.png)</br>

### Kendala yang dialami
Untuk soal ini, penemuan checksumnya relatif mudah namun saya sempat mengira bahwa nilainya harus diubah ke bentuk desimal.

## Soal 5
### Pertanyaan
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut. </br>
a) Berapa banyak packet yang berhasil di capture dari file pcap tersebut?</br>
b) Port berapakah pada server yang digunakan untuk service SMTP?</br>
c) Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

### Penyelesaian
### Kendala yang dialami
## Soal 6
### Pertanyaan
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

### Penyelesaian
### Kendala yang dialami
## Soal 7
### Pertanyaan
Berapa jumlah packet yang menuju IP 184.87.193.88?

### Penyelesaian
Untuk mendapatkan packet yang menuju IP 184.87.193.88, kami menggunakan display filter `ip.dst == 184.87.193.88`. Sehingga, packet yang ditampilkan hanya packet yang menuju ip tersebut.</br>
![7](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/7.png)</br>
</br>
Dari sini dapat dilihat bahwa jumlah packet yang menuju IP 184.87.193.88 ada 6, sehingga didapatkan flagnya. Untuk persoalan ini, kami tidak mengalami kendala berarti saat mengerjakannya.
## Soal 8
### Pertanyaan
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

### Penyelesaian
Pada soal nomor 8, kami hanya diminta memberikan kueri filter untuk mendapatkan paket yang menuju port 80. Ada 2 protokol yang menggunakan port 80, yaitu tcp dan udp. Jadi, untuk mendapatkan semua protokol yang menuju port 80, kueri yang digunakan adalah `tcp.dstport == 80 || udp.dstport == 80`. Sehingga, didapatkan flag sebagai berikut </br>
![8](https://github.com/wamalias/Jarkom-Modul-1-E24-2023/raw/main/image/8-flag.png)</br>
### Kendala yang dialami
Pada awalnya saya mengira ada space (spasi) antara dst dan port, sehingga beberapa kali jawaban saya salah.
## Soal 9
### Pertanyaan
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

### Penyelesaian
### Kendala yang dialami
## Soal 10
### Pertanyaan
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

### Penyelesaian
### Kendala yang dialami
