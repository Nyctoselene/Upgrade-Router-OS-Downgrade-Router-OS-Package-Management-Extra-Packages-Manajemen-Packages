# Upgrade RouterOS, Downgrade RouterOS, Package Management, Extra Packages, RouterBoot

# Upgrade RouterOS\
Untuk upgrade RouterOS dapat dilakukan secara manual dan secara otomatis, sebagai contoh disini saya akan upgrade RouterOS dari versi 6.42 ke 7.19.\
 **A. Secara Manual**
  1.Menggunakan Windows File Explorer
   a. Sebelum mendownload RouterOS yang baru, kita harus mengetahui dulu arsitektur prosesornya. Arsitekturnya bisa di lihat pada tab system > resources bagian Architecture name atau pada title bar winbox di bagian akhir dalam kurung

![Resources](Resources.png)

   b. Buka website mmikrotik.com/download, cari versi yang diinginkan dengan architecture yang sesuai lalu download. Pastikan filenya ber ekstensi ***.npk**

![Download](Download.png)

   c. Jika sudah selesai, hubungkan PC dengan MikroTik lalu buka File Explorer lalu pada bagian Address Bar, ketik ftp://(IP MikroTik)

![FTP](FTP.png)

   d. Setelah itu akan muncul pop up untuk memasukan username dan password. Masukan username dan password dari mikrotik lalu klik Log On

![Pop Up](Pop%20Up.png)

   e. Copy/Drag and Drop file RouterOS yang telah didownload tadi dari Windows ke MikroTik.

![Copy](Copy.png)

  2. Menggunakan FileZila
    
  3. Menggunakan WinBox
   a. Buka tab Files > Upload lalu pilih file RouterOS yang telah didownload

![Upload](Upload.png)

   b. Jika file sudah berhasil diupload, reboot Mikrotik dengan cara buka tab System > Reboot dan tunggu hingga reboot selesai
      
   c. Login dan cek hasilnya pada tab System > resource atau atau pada title bar WinBox

![Hasil](Hasil.png)

 **B. Secara Otomatis**
  1. Buka tab System > Packages > Check for Update

![Package](Package.png)

  2. Setelah itu akan muncul beberapa versi yang dapat dipilih, mulai dari yang stable, long term, development hingga testing. Disarankan untuk memilih versi stable agar tidak ada bug atau error.
    
  3. Klik Download&Install, pastikan router terkoneksi ke internet.

![Update](Update.png)

  4. Tunggu hingga proses download selesai dan router akan reboot secara otomatis.
    
  5. Cek hasilnya pada tab System > resource atau atau pada title bar WinBox.

![Hasil1](Hasil1.png)
     
# Downgrade RouterOS 
  1. Download versi terdahulu dari MikroTik untuk downgrade. Sebagai contoh disini saya mendownload versi 6.49. Donwload pada website mikrotik.com/download
 
  2. Setelah selesai pindahkan file RouterOS ke MikroTik dengan metode yang sama seperti saat akan upgrade.

![UploadD](UploadD.png)

  3. Buka winbox dan buka tab System > Packages lalu klik Downgrade.

![Downgrade](Downgrade.png)

  4. Setelah itu akan muncul pop up konfirmasi, pilih OK, dan router akan reboot dan start otomatis.     

![Pop UpD](Pop%20UpD.png)

  5. Cek hasilnya pada tab System > resource atau atau pada title bar WinBox.

![Hasil2](Hasil2.png)


# Package management
Dalam mengelola package di MikroTik pada tab System > Packages, ada beberapa perintah yang dapat digunakan
  1. Disable
  Menjadwalkan paket supaya dimatikan setelah reboot berikutnya. Setelahnya, fitur yang ada pada paket tersebut tidak dapat diakses. Jika paket berhasil di disable, paket tersebut akan berubah menjadi warna abu-abu.
       
![B Disable](B%20Disable.png)

![A Disable](A%20Disable.png)

  2. Enable
  Kebalikan dari disable, menjadwalkan paket supaya dinyalakan setelah reboot berikutnya. Setelah reboot, fitur yang ada pada paket tersebut dapat diakses kembali. Jika paket berhasil di enable, paket tersebut tidak lagi berwarna abu-abu.

![B Enable](B%20Enable.png)

![A Enable](A%20Enable.png)

  3. Downgrade
  Menurunkan versi RouterOS ke versi paing lama yang ada pada storage MikroTik.

  4. Uninstall
  Menghapus paket yang terpasang supaya terhapus setelah reboot selanjutnya.

  5. Unschedule
  Menghapus jadwal perubahan yang telah dibuat sebelumnya.

![B Unschedule](B%20Unschedule.png)

![A Unschedule](A%20Unschedule.png)

# Extra Package
Extra Package merupakan kumpulan perangkat lunak tambahan atau modul yang diinstal di atas sistem operasi RouterOS untuk menambahkan fungsionalitas khusus atau fitur lanjutan yang tidak termasuk dalam instalasi dasar. Untuk memasang Extra packages prosesnya sama dengan saat Upgrade MikroTik. Berikut adalah extra package untuk Mikrotik

![B Extra](B%20Extra.png)

![A Extra](A%20Extra.png)

Setelah memasang extra packages, terlihat ada beberapa package baru. Diantaranya: 
1.
2.
3.
4.

# RouterBOOT
RouterBOOT adalah firmware bawaan pada perangkat MikroTik yang berfungsi sebagai bootloader.

**RouterBOARD reset button**
RouterBOOT reset button mempunyai tiga fungsi:

 1. Tahan tombo selama proses booting hingga lampu LED mulai berkedip, lalu lepaskan tombol untuk mereset konfigurasi RouterOS (total 5 detik).
 
 2. Tahan tombol selama 5 detik lagi, lampu LED menjadi menyala terus, lalu lepaskan tombol untuk mengaktifkan mode CAPs (total 10 detik).
 
 3. Atau tahan tombol selama 5 detik lagi hingga lampu LED mati, lalu lepaskan tombol untuk membuat RouterBOARD mencari server Netinstall (total 15 detik).

Jika menahan tombol sebelum menyalakan daya, RouterBOOT cadangan akan digunakan selain semua tindakan di atas. Untuk melakukan tindakan di atas tanpa memuat loader cadangan, tekan tombol segera setelah menyalakan daya ke perangkat.

**Configuration**
Untuk perangkat RouterBOARD yang dilengkapi dengan fitur serial console connector, menu konfigurasi dapat diakses melalui loader RouterBOOT. Port serial RouterBOARD dikonfigurasi pada kecepatan 115200 bit/detik, 8 data bits, 1 bit stop, dan no parity. Disarankan untuk menonaktifkan kontrol aliran perangkat keras. 

Contoh tampilan menu yang tersedia di RouterBOOT 7.4beta4
    RouterBOOT booter 7.4beta4

    CRS328-24P-4S+

    built by build at Jun/15/2022 11:34:09 from revision 73B4521C

    CPU frequency: 800 MHz
      Memory size: 512 MiB
        Storage size:  16 MiB

    Press Ctrl+E to enter etherboot mode
    Press any key within 2 seconds to enter setup


    RouterBOOT-7.4beta4
    What do you want to configure?
       d - boot delay
       k - boot key
       s - serial console
       n - silent boot
       o - boot device
       z - extra kernel parameters
       r - reset booter configuration
       e - format storage
       w - repartition nand
       g - upgrade firmware
       i - board info
       p - boot protocol
       b - booter options
       j - boot os
       t - hardware tests
       l - erase license
       x - exit setup
    your choice: 

**Simple Upgrade**

RouterBOOT dapat diperbarui dari RouterOS dengan cara:

Jalankan perintah /system routerboard upgrade
Reboot router untuk menerapkan pembaruan (/system reboot)

    [admin@admin] > system/routerboard/upgrade 
    Do you really want to upgrade firmware? [y/n] 

# Kesimpulan
Upgrade, downgrade, pengelolaan paket, dan paket tambahan di RouterOS dilakukan guna menyesuaikan fungsi router dengan kebutuhan pengguna. Upgrade dilakukan untuk memperoleh pembaruan fitur, sedangkan downgrade dilakukan untuk kembali ke versi sebelumnya jika muncul masalah atau tidak kompatibel, pengelolaan paket memungkinkan pengguna untuk mematikan dan menghidupkan paket sesuai dengan kebutuhan, dan paket tambahan berfungsi untuk meningkatkan kemampuan router melebihi fungsi standar yang ada.
