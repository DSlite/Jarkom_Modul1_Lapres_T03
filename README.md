# Lapres Modul 1 Jarkom 2020 - T03

**Oleh:**
  * I Made Dindra Setyadharma (05311840000008)
  * Rindi Kartika Sari (05311840000013)

---

## **Display Filter**

**1.** Sebutkan webserver yang digunakan pada "testing.mekanis.me"!

**Solusi**\
Gunakan filter :

```
http.host contains "testing.mekanis.me"
```

Maka akan muncul paket yang mengandung host `testing.mekanis.me`

![Soal 1-1](https://user-images.githubusercontent.com/17781660/96237151-86d9ce00-0fcf-11eb-8677-ec27fe1f80af.png)

Lalu packet dapat di follow TCP Streamnya.

![Soal 1-2](https://user-images.githubusercontent.com/17781660/96237285-b4bf1280-0fcf-11eb-81ef-14e93ae9f7ff.png)

Jadi webserver yang digunakan adalah **nginx/1.14.0**.
\
\
\
**2.** Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!

**Solusi**\
Pada menu file, Export Objects HTTP

![Soal 2-1](https://user-images.githubusercontent.com/17781660/96237431-e0da9380-0fcf-11eb-9a69-b4923e455089.png)

Lalu akan ditampilkan list object HTTP

![Soal 2-2](https://user-images.githubusercontent.com/17781660/96237485-f2bc3680-0fcf-11eb-8305-262321a43675.png)

Dengan text filter, masukan nama file yang dicari.

![Soal 2-3](https://user-images.githubusercontent.com/17781660/96237558-09628d80-0fd0-11eb-993d-b928e0575629.png)

File tersebut disimpan dengan dengan nama file bebas.

![Soal 2-4](https://user-images.githubusercontent.com/17781660/96237624-1f704e00-0fd0-11eb-9757-c0d4ec1d1050.png)

File dapat dibuka dan dilihat isinya.

![Soal 2-5](https://user-images.githubusercontent.com/17781660/96237680-2f882d80-0fd0-11eb-90ac-f2f0090f5f90.png)
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

![Soal 3-1](https://user-images.githubusercontent.com/17781660/96238029-986fa580-0fd0-11eb-9e00-c4e48a55ed3b.png)

**Username: 10pemuda**\
**Password: guncangdunia**
\
\
\
**4.** Temukan paket dari **web-web** yang menggunakan **basic authentication** method!

**Solusi**\
Gunakan filter:

```
http.authbasic
```

Akan ditampilkan seluruh paket yang menggunakan **basic authentication** method

![Soal 4-1](https://user-images.githubusercontent.com/17781660/96238124-b6d5a100-0fd0-11eb-978f-077aa9bef137.png)

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

![Soal 5-1](https://user-images.githubusercontent.com/17781660/96238226-d4a30600-0fd0-11eb-8d4b-f23a4cf1c6d0.png)

Lalu setelah didekripsi akan didapat username: **kakakgamtenk** dan password: **hartatahtabermuda**. Gunakan username dan password tersebut untuk mengakses aku.pengen.pw dan pertanyaan pada website dijawab.

![Soal 5-2](https://user-images.githubusercontent.com/17781660/96238348-f4d2c500-0fd0-11eb-8cff-11414ee497ba.png)
\
\
\
**6.** Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file "zipkey.txt" (passwordnya adalah isi dari file txt tersebut).

**Solusi**\
Gunakan filter:

```
ftp-data.command == "STOR zipkey.txt" || ftp-data.command == "STOR Answer.zip"
```

Maka akan muncul paket data FTP mengenai "zipkey.txt" dan "Answer.zip"

![Soal 6-1](https://user-images.githubusercontent.com/17781660/96238463-1633b100-0fd1-11eb-9fdb-6b201f57dff5.png)

Pertama, follow TCP stream untuk "zipkey.txt" untuk mendapatkan password.

![Soal 6-2](https://user-images.githubusercontent.com/17781660/96238522-2ea3cb80-0fd1-11eb-8bf1-f18dbffd651e.png)

Terlihat bahwa passwordnya adalah **hey997400323051**. Lalu follow TCP stream untuk "Answer.zip" dan simpan.

![Soal 6-3](https://user-images.githubusercontent.com/17781660/96273256-b5709c80-1001-11eb-9bf0-110557859f3e.png)

Lalu buka file "Open This.pdf" yang terdapat pada "Answer.zip" menggunakan password **hey997400323051**, dan akan muncul pdf yang dimaksud.

![Soal 6-4](https://user-images.githubusercontent.com/17781660/96238737-614dc400-0fd1-11eb-9634-e8ee1602d935.png)
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

![Soal 7-1](https://user-images.githubusercontent.com/17781660/96238789-7165a380-0fd1-11eb-8bf4-138bdd803ef2.png)

Paket tersebut lalu di follow TCP stream.

![Soal 7-2](https://user-images.githubusercontent.com/17781660/96239000-b558a880-0fd1-11eb-84db-4471338008f1.png)

Lalu disimpan dalam bentuk **.zip**. Jika dibuka maka akan muncul file "Yes.pdf".

![Soal 7-3](https://user-images.githubusercontent.com/17781660/96239360-2dbf6980-0fd2-11eb-8588-32baf7cd77c0.png)
\
\
\
**8.** Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!

**Solusi**\
Jika dilihat paket ke **18**, paket tersebut merupakan respon berhasil koneksi terhadap Microsoft FTP Service.

![Soal 8-1](https://user-images.githubusercontent.com/17781660/96239451-4b8cce80-0fd2-11eb-946c-e74dc329f181.png)

Source IP Address tersebut dapat kita gunakan untuk mengetahui apakah Paket RETR yang dicari menggunakan Microsoft FTP Service. Jadi gunakan filter:

```
ftp-data.command contains ""RETR"" && ip.addr == 198.246.117.106
```

![Soal 8-2](https://user-images.githubusercontent.com/17781660/96239494-5cd5db00-0fd2-11eb-8cea-5a0b31ddf9b3.png)

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

![Soal 9-1](https://user-images.githubusercontent.com/17781660/96239549-724b0500-0fd2-11eb-9f5b-5f4d36858a48.png)

Jadi didapatkan Username: **dhana** dan Password: **dhana123**.
\
\
\
**10.** Cari file .pdf di wireshark lalu download dan buka file tersebut!\
clue: "25 50 44 46"

**Solusi**\
Jika diperhatikan pada clue, nilai tersebut merupakan *hex signature* dari file pdf. Maka dari itu kita dapat menggunakan fitur find dengan hex value. Nantinya akan ditunjuk pada paket no **290**

![Soal 10-1](https://user-images.githubusercontent.com/17781660/96239617-83941180-0fd2-11eb-9f91-0c7f7f9c345d.png)

Lalu paket di follow TCP stream

![Soal 10-2](https://user-images.githubusercontent.com/17781660/96239667-94dd1e00-0fd2-11eb-9a5e-292112210ea5.png)

Lalu Disimpan

![Soal 10-3](https://user-images.githubusercontent.com/17781660/96239699-9eff1c80-0fd2-11eb-9bd8-68f2335c278f.png)

Dan terakhir dapat dibuka file .pdf tersebut.

![Soal 10-4](https://user-images.githubusercontent.com/17781660/96239959-e7b6d580-0fd2-11eb-9e9d-6b78c2f4b24d.png)


---

## Capture Filter

**11.** Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

**Solusi**\
Gunakan filter:

```
port 21
```

![Soal 11-1](https://user-images.githubusercontent.com/17781660/96240022-fac9a580-0fd2-11eb-8443-93b42689708c.png)
\
\
\
**12.** Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

**Solusi**\
Gunakan filter:

```
src port 80
```

![Soal 12-1](https://user-images.githubusercontent.com/17781660/96240027-fbfad280-0fd2-11eb-948e-e8cb0df09d68.png)
\
\
\
**13.** Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

**Solusi**\
Gunakan filter:

```
dst port 443
```

![Soal 13-1](https://user-images.githubusercontent.com/17781660/96240031-fc936900-0fd2-11eb-8d64-7d0c734fee66.png)
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

![Soal 14-1](https://user-images.githubusercontent.com/17781660/96240037-fdc49600-0fd2-11eb-88a0-ec8fd8693a83.png)
\
\
\
**15.** Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!

**Solusi**\
Gunakan filter:

```
dst host monta.if.its.ac.id
```

![Soal 15-1](https://user-images.githubusercontent.com/17781660/96240040-fef5c300-0fd2-11eb-933d-e1c4ea36f80e.png)