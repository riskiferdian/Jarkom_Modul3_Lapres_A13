# Laporan Praktikum Modul 3

Anri adalah seorang mahasiswa tingkat akhir yang sedang mengerjakan TA mengenai DHCP dan Proxy. Bu Meguri sebagai dosen pembimbing Anri memberikan tugas pertamanya,
## (1) yaitu untuk membuat topologi jaringan demi kelancaran TA-nya dengan kriteria sebagai berikut: 

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/1.png)

### Penyelesaian

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/2.png)

Anri sudah pernah mempelajari teknik Jaringan Komputer sehingga Anri dapat membuat topologi tersebut dengan mudah. Bu Meguri memerintahkan Anri untuk menjadikan SURABAYA sebagai router, MALANG sebagai DNS Server, TUBAN sebagai DHCP server, serta MOJOKERTO sebagai Proxy server, dan UML lainnya sebagai client. Bu Meguri berpesan pada Anri untuk menyusun topologi secara hati-hati dan memperhatikan gambar topologi yang diberikan Bu Meguri. Karena TUBAN jauh dari client, maka perlu adanya perantara agar bisa saling terhubung.

## (2) SURABAYA ditunjuk sebagai perantara (DHCP Relay) antara DHCP Server dan client. 
### Penyelesaian 
Install dulu “apt-get install isc-dhcp-server”
Tentukan interface mana yang akan diberikan layanan DHCP dengan perintah
nano /etc/default/isc-dhcp-server
kemudian Menentukan interface, maka eth0 dipilih untuk diberikan layanan DHCP

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/3.png)

Kemudian atur dan tambahkan konfigurasi DHCP yang sesuai kemudian restart dengan perintah “ service isc-dhcp-server restart “
Selanjutnya install “ apt-get install isc-dhcp-relay “ di Surabaya dan masukkan IP tuban “10.151.73.116”
Untuk interfacenya kita kosongkan. Kemudian enter.
 
*Lanjutan soal :*
Kriteria lain yang diminta Bu Meguri pada topologi jaringan tersebut adalah: 
Seluruh client TIDAK DIPERBOLEHKAN menggunakan konfigurasi IP Statis.
## (3) Client pada subnet 1 mendapatkan range IP dari 192.168.0.10 sampai 192.168.0.100 dan 192.168.0.110 sampai 192.168.0.200.
### Penyelesaian :
Untuk subnet 1 NID  192.168.0.0
Masukan range yang sesuai dengan soal 
192.168.0.10 – 192.168.100
192.168.110 – 192.168.0.200
 
![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/4.png)

Kemudian konfigurasi client. Lakukan nano “/etc/network/interfaces”
Pada tiap client dan tambahkan 
   *auto eth0*
   *iface eth0 inet dhcp*
   
**Gresik**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/5.png)

**Sidoarjo**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/6.png)

Kemudian restart dan cek ip tiap client apakah sudah masuk dalam range IP DHCP
   **ifconfig**
   
**Gresik**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/7.png)

**Sidoarjo**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/8.png)

## (4) Client pada subnet 3 mendapatkan range IP dari 192.168.1.50 sampai 192.168.1.70.
### Penyelesaian :
Untuk subnet 3 NID  192.168.1.0
Masukan range yang sesuai dengan soal 
192.168.1.50 – 192.168.1.70

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/9.png)

Kemudian konfigurasi client. Lakukan nano “/etc/network/interfaces”
Pada tiap client dan tambahkan 
auto eth0
iface eth0 inet dhcp

**madiun**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/10.png)

**Banyuwangi**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/11.png)

Kemudian restart dan cek ip tiap client apakah sudah masuk dalam range IP DHCP
*ifconfig*

**madiun**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/12.png)

**Banyuwangi**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/13.png)

Untuk selain Client dibuat static dengan konfigurasi yang disesuaikan perintah soal

**Mojokerto**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/14.png)

**Malang**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/15.png)

**tuban**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/16.png)

**Surabaya**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/17.png)

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/18.png)

## (5) Client mendapatkan DNS Malang dan DNS 202.46.129.2 dari DHCP
## (6) Client di subnet 1 mendapatkan peminjaman alamat IP selama 5 menit, sedangkan (6) client pada subnet 3 mendapatkan peminjaman IP selama 10 menit. 
### Penyelesaian :
**(5) Edit configurasi dengan nano /etc/dhcp/dhcpd.conf kemudian Tambahkan DNS yang diminta pada option-domain-name-servers.
(6) ubah default dan max lease time untuk subnet 1 menjadi 300 dan subnet 3 menjadi 600**

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/19.png)

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/20.png)

*Lanjutan soal :*
Bu Meguri adalah dosbing yang suka overthinking. Ia tidak ingin jaringan lokalnya terhubung ke internet secara langsung. Sehingga ia memberi tugas tambahan pada Anri untuk membuatkan Proxy sebagai penghubung jaringan lokal ke internet. Ada beberapa ketentuan yang harus dipenuhi dalam pembuatan Proxy ini. Pertama, akses ke proxy hanya bisa dilakukan oleh Anri sendiri sebagai user TA.
## (7) User autentikasi milik Anri memiliki format: ● User : userta_yyy ● Password : inipassw0rdta_yyy Keterangan : yyy adalah nama kelompok masing-masing. Contoh: userta_c01 Anri sudah menjadwal pengerjaan TA-nya
### Penyelesaian :
Langkah pertama yaitu Install “apt-get install apache2-utils”
Buat user dan password baru, ketikkan htpasswd -c /etc/squid3/passwd userta_a13
New password “inipassw0rdta_a13” kemudian re-type
Kemudian agar akses proxy hanya bisa dilakukan oleh anri sebagai user tambahkan
http_acces deny !USERS (gmbar dibawah)
## (8) setiap hari Selasa-Rabu pukul 13.00-18.00. Bu Meguri membatasi penggunaan internet Anri hanya pada jadwal yang telah ditentukan itu saja. Maka diluar jam tersebut, Anri tidak dapat mengakses jaringan internet dengan proxy tersebut. Jadwal bimbingan dengan Bu Meguri adalah
## (9) setiap hari Selasa-Kamis pukul 21.00 - 09.00 keesokan harinya (sampai Jumat jam 09.00). Agar Anri bisa fokus mengerjakan TA,
## (10) setiap dia mengakses google.com, maka akan di redirect menuju monta.if.its.ac.id agar Anri selalu ingat untuk mengerjakan TA🙂. Untuk menandakan bahwa Proxy Server ini adalah Proxy yang dibuat oleh Anri,
### Penyelesaian :

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/21.png)

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/22.png)

**8.** deklarasi langsung acl no8 time TW 13:00-1800, atur sesuai hari dan jam yang ditentukan.
Agar tidak dapat mengakses internet dengan proxy tersebut diluar jam yang telah ditentukan maka tambahkan
http_access deny !no8 !no9_1 !no9_2
**9.** deklarasi acl no9_1 time TWH 21:00-23.59 dan acl no9_2 acl WHF 00:00-09:00 untuk keesokan harinya
**10.** kemudian tambahkan 
acl no10 dstdomain google.com
deny_info http://monta.if.its.ac.id
## (11) Bu Meguri meminta Anri untuk mengubah error page default squid menjadi seperti berikut:
Note : File error page bisa diunduh dengan cara wget 10.151.36.202/error403.tar.gz Extract : tar -xvf error403.tar.gz
### Penyelesaian :
Pindah direktori ke errors dengan mengetikkan
cd /usr/share/squid/errors
lalu jalankan perintah berikut untuk move
mv /usr/share/squid/errors/en /usr/share/squid/errors/en1
kemudian buat direktori baru
mkdir /usr/share/squid/errors/en
download file
wget 10.151.36.202/ERR_ACCESS_DENIED
kemudian copy
cp -r ERR_ACCESS_DENIED /usr/share/squid/errors/en
## (12) Karena Bu Meguri dan Anri adalah tipe orang pelupa, maka untuk memudahkan mereka, Anri memiliki ide ketika menggunakan proxy cukup dengan mengetikkan domain janganlupa-ta.yyy.pw dan memasukkan port 8080. Keterangan : yyy adalah nama kelompok masing-masing. Contoh: janganlupa-ta.c01.pw
Bantu Anri menyelesaikan TA nya dibawah bimbingan Bu Meguri!
### Penyelesaian :
Buka uml malang kemudian ketikkan perintah berikut
Nano /etc/bind/named.conf.local 

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/23.png)

Selanjutnya ketikkan perintah berikut
Nano /etc/bind/jarkom/janganlupa-ta.a13.pw

![gambar](https://github.com/riskiferdian/Jarkom_Modul3_Lapres_A13/blob/main/images/24.png)

## Selesai..!
