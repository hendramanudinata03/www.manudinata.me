---
title: "Nyobain NAT VPS Whplus, VPS Murah Menggunakan Shared IPv4"
---

Beberapa minggu lalu saya sempat mencari layanan penyedia _Virtual Private Server_ (VPS) untuk kebutuhan pribadi, seperti _private VPN & proxy_, _deploy_ program, dan lain sebagainya.

Setelah _Googling_ kesana-kemari, akhirnya saya menemukan layanan **NAT VPS** oleh [Whplus](https://www.whplus.com). _NAT VPS?_ Saya baru pertama kali mendengarnya. Namun, harga yang ditawarkan sangat murah. Untuk spesifikasi minimum (1 vCore 128MB RAM) dipatok dengan harga Rp. 7,500 per bulan. Wow!

Sebelum menelusuri lebih lanjut, saya terlebih dahulu mencari definisi dari NAT VPS. Tidak terlalu banyak artikel yang saya dapatkan, namun informasi yang didapat sudah cukup untuk dijadikan sebagai garis besar.

# Apa itu NAT VPS?

NAT VPS adalah layanan VPS yang menggunakan _shared IPv4_ sebagai akses ke VPS melalui metode NAT _Network Address Translation_. _Maksudnya?_ Satu IPv4 publik digunakan oleh beberapa VPS dalam satu jaringan.

Misalnya saya membeli VPS A dan teman saya membeli VPS B dalam satu wilayah _Datacenter_ yang sama. Saya dan teman saya akan diberi **IP publik yang sama** untuk mengakses VPS. Begitu juga dengan orang lain dalam satu wilayah _Datacenter_.

Menggunakan cara ini sangat ampuh dalam menekan biaya, karena harga satu IPv4 sendiri tergolong _lumayan_.

# Bermain Port

_Wah, kalau saya dan teman saya menggunakan IP yang sama, berarti saya bisa mengakses VPS teman saya, dong?_ Tidak juga. Inilah keunikan dari NAT VPS.

Setiap VPS diberikan 20 port terbuka + 1 port untuk akses SSH (Secure SHell) yang berbeda-beda pada tiap VPS, tergantung dari layanan yang digunakan. Namun biasanya, **port diambil dari angka terakhir IP _private_ VPS**.

Contohnya begini. VPS saya memiliki IP _private_ `192.168.1.100`, dan VPS teman saya memiliki IP _private_ `192.168.1.200`. Berarti, VPS saya memiliki 20 + 1 port yang terbuka, yaitu `10000`, `10001`, `10002` sampai `10019`, ditambah `10020` untuk akses SSH. Mirip dengan VPS teman saya, yaitu `20000`, `20001`, `20002`, sampai `20019`, ditambah `20020` untuk akses SSH.

Dengan pembatasan port ini, menggunakan NAT VPS menjadi semakin menantang. Layanan-layanan yang kita deploy harus mengarah ke port-port yang terbuka. Jika tidak, layanan tersebut tidak akan dapat diakses oleh dunia luar.

# Mengenai Layanan NAT VPS oleh Whplus

Terdapat beberapa penyedia layanan NAT VPS di Indonesia, salah satunya adalah Whplus.

[![Whplus]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/1.png" | relative_url }})](https://www.whplus.com/nat-vps)

Seperti yang saya telah tulis di atas, harga yang ditawarkan sangat murah. Untuk spesifikasi minimum (1 vCPU, 128MB RAM, 3GB storage) dipatok dengan harga Rp. 7,500. Whplus menggunakan rentang pembayaran 3 bulan, 6 bulan, dan 1 tahun. Berarti, dengan spesifikasi tersebut dapat dibeli dengan harga **Rp. 25,000** untuk 3 bulan. Keren!

![Harga NAT VPS Whplus]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/2.png" | relative_url }})

Untuk lokasi _Datacenter_, terdapat 3 lokasi, yaitu Indonesia (Jakarta), Singapura, dan Amerika Serikat.

Setelah melihat lebih lanjut spesifikasi yang diberikan, saya memutuskan untuk membeli **NAT256**, yang mempunyai spesifikasi 1 vCPU, 256MB RAM, dan 5GB storage dengan harga **Rp. 30,000** selama 3 bulan. _Sekalian_ menambah referensi untuk NAT VPS.

![NAT256 Whplus]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/3.png" | relative_url }})

Saya memilih lokasi _Datacenter_ di Indonesia, lalu melakukan _checkout_ pesanan. Terdapat beberapa kolom informasi VPS yang harus saya isi, seperti _hostname_ VPS, _nameserver_ (saya tidak tahu mengapa kolom _nameserver_ harus di-isi, karena ini bukan pembelian hosting/domain), _root password_ VPS, dan _template_ OS yang ingin digunakan.

![Form Checkout Whplus]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/4.png" | relative_url }})

Saya memilih Ubuntu 20.04 (Focal Fossa) sebagai OS. Pada form checkout juga terdapat persetujuan jika layanan yang dipilih merupakan _unmanaged service_ atau layanan tanpa dukungan teknis.

Lanjut ke tahap pembayaran. Metode pembayaran yang Whplus terima hanya melalui transfer bank (BCA dan Mandiri) dan PayPal. Sangat disayangkan Whplus belum menerima pembayaran melalui E-wallet atau QRIS, karena remaja seperti saya tentunya belum memiliki rekening bank sendiri, hanya akun E-wallet. Itupun belum bisa melakukan transfer karena akun belum bisa di-verifikasi. Saya pun mengakalinya dengan menggunakan aplikasi BukaKios, yaitu dengan men-depositkan sejumlah saldo lalu melakukan transfer bank di BukaKios.

Pembayaran berhasil, walaupun ada beberapa kendala sebelum transaksi. Setelah pembayaran, saya melakukan [konfirmasi pembayaran](https://www.whplus.com/konfirmasi-pembayaran.php) agar tidak terjadi hal yang tidak diinginkan.

![Status Lunas]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/5.png" | relative_url }})

Segera setelah pembayaran terkonfirmasi, VPS saya langsung aktif. Mantap!

![Informasi VPS Pada _Client Area_]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/6.png" | relative_url }})

Saya juga mendapatkan satu Email dari Whplus yang berisi informasi mengenai VPS, seperti IP private dan IP publik VPS, perhitungan port yang terbuka, TOS (_Terms Of Service_) dan lain sebagainya.

Oh iya, Whplus juga menggunakan panel Virtualizor sebagai panel kontrol VPS.

![Panel Virtualizor]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/9.png" | relative_url }})

# Mengenai VPS

Berikut adalah tangkapan layar dari informasi VPS melalui `neofetch`:

![Informasi VPS]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/7.png" | relative_url }})

Hasil tes kecepatan internet menggunakan utilitas `speedtest` oleh Ookla:

![Hasil Speedtest]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/8.png" | relative_url }})

Secara spesifikasi tidak terlalu berbeda dengan VPS normal lainnya, hanya saja penggunaan IP dan port yang berbeda. Dan juga, spesifikasi NAT VPS yang ditawarkan oleh Whplus cukup low-end, bahkan di paket termahalnya.

## Nyobain Host Web Dengan Apache

Karena masih penasaran dengan _port_, saya mencoba men- _deploy_ _web server_ Apache di dalam VPS yang mengarah ke salah satu port yang terbuka untuk saya, apakah bisa diakses atau tidak. Harusnya bisa sih, asal mengarah ke port yang sesuai.

Oh iya, VPS ini sudah terpasang Apache secara bawaan, jadi tidak perlu untuk memasangnya lagi (dan sebaiknya jangan, agar tidak terjadi konflik).

Cek terlebih dahulu apakah Apache sudah aktif:

```bash
root@coolnat:~# systemctl status apache2
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2022-03-29 19:06:22 WIB; 1 day 23h ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 11346 ExecReload=/usr/sbin/apachectl graceful (code=exited, status=0/SUCCESS)
   Main PID: 326 (apache2)
      Tasks: 28 (limit: 4466)
     Memory: 1.9M
     CGroup: /system.slice/apache2.service
             ├─  326 /usr/sbin/apache2 -k start
             └─11355 /usr/sbin/apache2 -k start

Mar 29 19:06:22 coolnat.manudinata.me systemd[1]: Starting The Apache HTTP Server...
Mar 29 19:06:22 coolnat.manudinata.me systemd[1]: Started The Apache HTTP Server.
Mar 29 07:00:03 coolnat.manudinata.me systemd[1]: Starting The Apache HTTP Server...
Mar 29 07:00:05 coolnat.manudinata.me systemd[1]: Started The Apache HTTP Server.
Mar 31 07:26:22 coolnat.manudinata.me systemd[1]: Reloading The Apache HTTP Server.
Mar 31 07:26:23 coolnat.manudinata.me systemd[1]: Reloaded The Apache HTTP Server.
```

_Service_ Apache sudah aktif. Jika belum, silahkan aktifkan terlebih dahulu:

```bash
root@coolnat:~# systemctl start apache2
root@coolnat:~# systemctl enable apache2
```

Sekarang, lanjut ke proses penggantian port agar mengarah ke port yang terbuka. Jika tidak, _website_ hanya akan bisa diakses di dalam VPS, tidak oleh dunia luar.

Buka file `/etc/apache2/sites-available/000-default.conf`, lalu pada baris pertama:

```
<VirtualHost *:80>
```

Ganti `80` dengan salah satu port yang terbuka. Silahkan pilih yang mana saja, asal masih belum dipakai. Contohnya:

```
<VirtualHost *:12001>
```

Simpan dan tutup file tersebut.

Selanjutnya, kita perlu mendaftarkan port tersebut ke Apache. Buka file `/etc/apache2/ports.conf`. Pada baris ke-5:

```
Listen 80
```

Dibawahnya, tambahkan:

```
Listen <PortTerbuka>
```

Contohnya:

```
Listen 12001
```

Simpan dan tutup file tersebut, lalu jalankan perintah berikut:

```bash
root@coolnat:~# systemctl restart apache2
```

untuk me- _restart_ _service_ Apache.

Sampai sini _website_ harusnya sudah dapat diakses oleh dunia luar melalui port yang dipilih tadi. Silahkan buka `IP-Publik-VPS:Port` pada _web browser_. Contoh: `202.145.2.100:12001`.

![Tampilan _website_ default Apache]({{ "assets/img/posts-img/2022-03-20-nyobain-nat-vps/10.png" | relative_url }})

Selamat, _website_ dapat diakses dari luar!

# Penutup

Itulah postingan blog saya mengenai NAT VPS. Layanan yang cukup bagus, terutama untuk menghemat pengeluaran, apalagi jika program yang ingin kita _deploy_ tidak terlalu membutuhkan _resource_ yang banyak, menggunakan NAT VPS mungkin sudah cukup.

Terima kasih sudah membaca sampai habis! :D
