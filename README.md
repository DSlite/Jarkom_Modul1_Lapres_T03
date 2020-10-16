# Lapres Modul 1 Jarkom 2020 - T03

**Oleh:**
  * I Made Dindra Setyadharma (05311840000008)
  * Rindi Kartika Sari (05311840000013)

---

## **Display Filter**

**1.** Sebutkan  webserver yang digunakan pada "testing.mekais.me"!

**Solusi**\
Gunakan filter :

```
http.host contains "testing.mekanis.me"
```

Maka akan muncul paket yang mengandung host `testing.mekanis.me`

![Soal 1-1](#)

Lalu packet dapat di follow TCP Streamnya.

![Soal 1-2](#)

Jadi webserver yang digunakan adalah **nginx/1.14.0**.
\
\
\
**2.** Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!

**Solusi**\
Pada menu file, Export Objects HTTP

![Soal 2-1](#)

Lalu akan ditampilkan list object HTTP

![Soal 2-2](#)

Dengan text filter, masukan nama file yang dicari.

![Soal 2-3](#)

File tersebut disimpan dengan dengan nama file bebas.

![Soal 2-4](#)

File dapat dibuka dan dilihat isinya.

![Soal 2-5](#)
\
\
\
**3.** Cari username dan password ketika login di "ppid.dpr.go.id"!

**Solusi**\
Gunakan filter:

```
http.host contains "ppid.dpr.go.id" && frame contains "login" && http.request.method contains "POST"
```

Maka akan didapatkan sebuah paket. Jika dilihat HTML Form yang dikirim maka akan terlihat username dan password yang dimaksud.

![Soal 3-1](#)

**Username: 10pemuda**\
**Password: guncangdunia**
\
\
\
**4.** Temukan paket dari **web-web** yang menggunakan **basic authentication** method!

**Solusi**\
Gunakan filter:

```
http.basicauth
```

Akan ditampilkan seluruh paket yang menggunakan **basic authentication** method

![Soal 4-1](#)

Setelah dilihat satu-persatu, ada 2 buah web yang menggunakan metode autentikasi tersebut, yaitu **testing.mekanis.me** dan **aku.pengen.pw**.
\
\
\
**5.** Ikuti perintah di aku.pengen.pw! Username dan password bisa didapatkan dari file *.pcapng*!

**Solusi**\
Gunakan filter:

```
http.host contains "aku.pengen.pw"
```

Maka akan ditampilkan paketnya. Lalu akan muncul metode autentikasinya adalah basic.

![Soal 5-1](#)

Lalu setelah didekripsi akan didapat username: **kakakgamtenk** dan password: **hartatahtabermuda**. Gunakan username dan password tersebut untuk mengakses aku.pengen.pw dan pertanyaan pada website dijawab.

![Soal 5-2](#)
\
\
\
**6.** Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file "zipkey.txt" (passwordnya adalah isi dari file txt tersebut).

**Solusi**\
Gunakan filter:

```
ftp-data.command = "STOR zipkey.txt" || ftp-data.command "STOR Answer.zip"
```

Maka akan muncul paket data FTP mengenai "zipkey.txt" dan "Answer.zip"

![Soal 6-1](#)

Pertama, follow TCP stream untuk "zipkey.txt" untuk mendapatkan password.

![Soal 6-2](#)

Terlihat bahwa passwordnya adalah **hey997400323051**. Lalu follow TCP stream untuk "Answer.zip" dan simpan.

![Soal 6-3](#)

Lalu buka file "Open This.pdf" yang terdapat pada "Answer.zip" menggunakan password **hey997400323051**, dan akan muncul pdf yang dimaksud.

![Soal 6-4](#)
\
\
\
**7.** Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut. Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"

**Solusi**\
Gunakan filter:

```
ftp-data contains "Yes.pdf"
```

Maka nanti akan muncul paket yang isinya mengandung "Yes.pdf"

![Soal 7-1](#)

Paket tersebut lalu di follow TCP stream.

![Soal 7-2](#)

Lalu disimpan dalam bentuk **.zip**. Jika dibuka maka akan muncul file "Yes.pdf".

![Soal 7-3](#)
\
\
\
**8.** Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!

**Solusi**\
Jika dilihat paket ke **18**, paket tersebut merupakan respon berhasil koneksi terhadap Microsoft FTP Service.

![Soal 8-1](#)

Source IP Address tersebut dapat kita gunakan untuk mengetahui apakah Paket RETR yang dicari menggunakan Microsoft FTP Service. Jadi gunakan filter:

```
ftp-data.command contains ""RETR"" && ip.addr == 198.246.117.106
```

![Soal 8-2](#)

Jadi objek yang didownload hanya file **Readme**.
\
\
\
**9.** Cari username dan password ketika login FTP pada localhost!

**Solusi**\
Gunakan filter:

```
ftp.request.command contains "USER" || ftp.request.command contains "PASS"
```

![Soal 9-1](#)

Jadi didapatkan Username: **dhana** dan Password: **dhana123**.
\
\
\
**10.** Cari file .pdf di wireshark lalu download dan buka file tersebut!\
clue: "25 50 44 46"

**Solusi**\
Jika diperhatikan pada clue, nilai tersebut merupakan *hex signature* dari file pdf. Maka dari itu kita dapat menggunakan fitur find dengan hex value.

![Soal 10-1](#)

Akan ditunjuk pada paket no **290**

![Soal 10-2](#)

Lalu paket di follow TCP stream

![Soal 10-3](#)

Lalu Disimpan

![Soal 10-4](#)

Dan terakhir dapat dibuka file .pdf tersebut.

![Soal 10-5](#)

---

## Capture Filter

**11.** Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

**Solusi**\
Gunakan filter:

```
port 21
```

![Soal 11-1](#)
\
\
\
**12.** Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

**Solusi**\
Gunakan filter:

```
src port 80
```

![Soal 12-1](#)
\
\
\
**13.** Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

**Solusi**\
Gunakan filter:

```
dst port 443
```

![Soal 13-1](#)
\
\
\
**14.** Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

**Solusi**\
Gunakan filter:

```
src host [ip_sendiri]
```

Untuk `[ip_sendiri]` dapat dilihat menggunakan command `ipconfig` pada terminal

![Soal 14-1](#)
\
\
\
**15.** Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!

**Solusi**\
Gunakan filter:

```
dst host monta.if.its.ac.id
```

![Soal 15-1](#)