# Jarkom-Modul-1-B03-2022

## Anggota Kelompok:
|Nama     |NRP    |
|----------|-------|
|Maheswara Danendra Satriananda| 5025201060 |
|James Silaban    | 5025201169 |
|Anak Agung Yatestha Parwata | 5025201234 |

## 1. Sebutkan web server yang digunakan pada "monta.if.its.ac.id"! 

Pertama kita menggunakan display filter `http.host contains monta.if.its.ac.id` kemudian `Follow > TCP Stream` agar bisa mendapatkan response dari request di path login.php

![image](https://user-images.githubusercontent.com/78299006/192095794-69fd7ff0-ae6d-4d4f-95c9-f56b24d3c739.png)

![image](https://user-images.githubusercontent.com/78299006/192095821-a1b529f6-c665-4a87-a24e-5e01726a8dd0.png)

Dari hasil Follow TCP Stream diatas, dalam respons header terdapat header dengan value nginx/1.10.3(Windows)


## 2. Ishaq sedang bingung mencari topik ta untuk semester ini , lalu ia datang ke website monta dan menemukan detail topik pada website “monta.if.its.ac.id” , judul TA apa yang dibuka oleh ishaq ?
Bisa diindentifikasikan bahwa yang kita cari adalah “detail topik”, maka dari itu bisa di highlight yang menandakan sebagai detail topik.

![image](https://user-images.githubusercontent.com/78299006/192095877-b3d96ff1-274d-4175-b1f5-0faf794781c0.png)

Lalu langkah selanjutnya adalah untuk meng-export dari html detail topik.

![image](https://user-images.githubusercontent.com/78299006/192095918-247421f2-8e12-494a-a466-d01fd8e3d0aa.png)

Memilih 194, save dan tambahkan ekstensi .html

![image](https://user-images.githubusercontent.com/78299006/192095932-4071ed44-df4f-479f-90bc-3a9cedbf8e11.png)

Setelah itu maka dapat dibuka file html dari 194(detail topik).

![image](https://user-images.githubusercontent.com/78299006/192095941-bcbbc883-f808-4fbf-a58b-674043df8998.png)



## 3. Filter sehingga wireshark hanya menampilkan paket yang menuju port 80! 
Menggunakan syntax `tcp.dstport == 80 || udp.dstport == 80`,
karena yang akan ditampilkan paket yang menuju port 80, kita perlu menambahkan dst

![image](https://user-images.githubusercontent.com/78299006/192095964-b50797bf-b818-4428-8105-8da0233b5372.png)



## 4. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 21!

Gunakan display filter `tcp.srcport == 21 || udp.srcport == 21,`
kita menambahkan src untuk mengambil paket yang hanya berasal dari port 21

![image](https://user-images.githubusercontent.com/78299006/192094223-f0bd4b90-f3d4-4081-93b4-ac621b74085e.png)


## 5. Filter sehingga wireshark hanya mengambil paket yang berasal dari port 443!
Gunakan display filter `tcp.srcport == 443 || udp.srcport == 443`

![image](https://user-images.githubusercontent.com/78299006/192094310-d7cff90d-1227-4252-b906-08953419587a.png)


## 6. Filter wireshark hanya menampilkan paket yang menuju ke lipi.go.id
Display filter yang dapat digunakan adalah `http.host contains “lipi.go.id”`

![image](https://user-images.githubusercontent.com/78299006/192094580-aecde413-1121-402d-aab5-e4ed7b0aa98e.png)


## 7. Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
Mengambil paket berarti capture filter, berasal berarti src, ip sendiri dapat diambil dari ipconfig (yang digunakan sekarang adalah 192.168.1.2) sehingga filter yang digunakan adalah `ip src  192.168.1.2`

![image](https://user-images.githubusercontent.com/78299006/192094751-7c3e7e13-ebe9-4501-9218-1fed70d52a7a.png)
![image](https://user-images.githubusercontent.com/78299006/192094806-5a0845d5-4bac-4b9b-9dc0-51d5bc07b5d0.png)
![image](https://user-images.githubusercontent.com/78299006/192094849-a86328d2-36c9-481e-90f6-a03b0a595e97.png)


## 8. Telusuri aliran paket dalam file .pcap yang diberikan, cari informasi berguna berupa percakapan antara dua mahasiswa terkait tindakan kecurangan pada kegiatan praktikum. Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.
Berdasarkan petunjuk soal yakni “Percakapan tersebut dilaporkan menggunakan protokol jaringan dengan tingkat keandalan yang tinggi dalam pertukaran datanya sehingga kalian perlu menerapkan filter dengan protokol yang tersebut.”, kami berasumsi bahwa protokol yang digunakan adalah TCP. Setelah kami filter TCP, kami menemukan hal berikut

![image](https://user-images.githubusercontent.com/78299006/192094937-67ae3156-d27c-4e99-abfe-163ed0dbe3c1.png)

Lalu, disalah satu paket kami follow > tcp-stream, kami menemukan percakapan berikut:

![image](https://user-images.githubusercontent.com/78299006/192094972-215f2f0b-153d-431f-8528-fac3f13a751d.png)


## 9. Terdapat laporan adanya pertukaran file yang dilakukan oleh kedua mahasiswa dalam percakapan yang diperoleh, carilah file yang dimaksud! Untuk memudahkan laporan kepada atasan, beri nama file yang ditemukan dengan format [nama_kelompok].des3 dan simpan output file dengan nama “flag.txt”.

Berdasarkan percakapan tersebut, kami menyadari bahwa file akan dikirimkan melalui port 9002, sehingga kami melakukan display filter menggunakan `tcp.port == 9002` hasilnya sebagai berikut:

![image](https://user-images.githubusercontent.com/78299006/192095022-982c659e-521d-4d9e-860c-df0dfe304275.png)

Lalu kami follow -> tcp-stream dan mendapatkan hasil sebagai berikut:

![image](https://user-images.githubusercontent.com/78299006/192095057-b5539f6a-9d13-45f1-b3fd-15cb3c263383.png)

karena ini merupakan salt, kita harus melihat datanya sebagai raw, datanya sebagai berikut:

![image](https://user-images.githubusercontent.com/78299006/192095076-3d7f9d67-64fa-4f5b-ac1e-f33f7717dc54.png)

Lalu kami save as sebagai B03.des3 sesuai dengan arahan soal. Berdasarkan percakapan pun kami mengetahui bahwa passwordnya merupakan “nama karakter anime kembar lima” yakni nakano dengan semua huruf kecil, lalu berdasarkan percakapan juga kami menemukan kita dapat melakukan decrypt menggunakan openssl dengan metode des3, dan di save ke flag.txt.

![image](https://user-images.githubusercontent.com/78299006/192095484-d046b80d-dac4-4209-8274-3366170a1f3e.png)


## 10. Temukan password rahasia (flag) dari organisasi bawah tanah yang disebutkan di atas!

Adapun isi dari flag.txt yakni :

![image](https://user-images.githubusercontent.com/78299006/192095509-b815e7c2-6bc7-4e19-9e13-ca140d16d6ec.png)

### Tambahan
Adapun praktikum kali ini, semua peserta berkontribusi. Dimana, untuk nomor 1-3 dikerjakan oleh Maheswara, 4-6 dikerjakan oleh James, dan 7-10 dikerjakan oleh Yatestha. Juga, terdapat diskusi kelompok dalam pengerjaan praktikum kali ini.
