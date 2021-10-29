# Jarkom-Modul-2-E08-2021

## Nomor 8


Setelah melakukan konfigurasi server, maka dilakukan konfigurasi Webserver. Pertama dengan webserver www.franky.yyy.com. Pertama, luffy membutuhkan webserver dengan DocumentRoot pada /var/www/franky.yyy.com.

Untuk melakukan konfigurasi server, pertama-tama pastikan bahwa Record A dan PTR sudah mengarah ke IP Skypie : 


![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/4edcaedaeeea936dc53d329cd4799fe168df5ff7/pictures/Nomor%208a.JPG)

![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/1a54f8081458c29ea6e765eea78b027370354824/pictures/Nomor%208b.JPG)


Selanjutnya pindah ke Skypie dan lakukan instalasi php dan apache dengan command : 

```
apt-get install apache2 -y
apt-get install php -y
apt-get install libapache2-mod-php7.0 -y
```

Jangan lupa start apache dengan command :

`service apache2 start`

Setelah itu pindah directory ke `/etc/apache2/sites-available` untuk membuat config website franky dan gunakan command : 

`cp 000-default.conf franky.E08.com.conf`

Command tersebut untuk menyalin template yang ada di file `000-default.conf` ke file baru `franky.E08.com.conf`. Setelah itu buka file `franky.E08.com.conf`.
Ubah Document Root menjadi :

`DocumentRoot /var/www/franky.E08.com`

dan tambahkan :

```
ServerName franky.E08.com
ServerAlias www.franky.E08.com
```


Isi file sebagai berikut :


![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/ddf3d1d12ecb47bc75968b17ce2b739ebe4ebff5/pictures/Nomor%208c.JPG)


Setelah itu enable website dengan command :

`a2ensite franky.E08.com` dan restart apache dengan `service apache2 restart`.


Setelah itu kembali ke directory root dan download file `franky.zip` yang ada di link : [File Jarkom](https://github.com/FeinardSlim/Praktikum-Modul-2-Jarkom)


Setelah mendownload file digunakan command `wget <link hasil download>` untuk menaruh file `franky.zip` ke dalam Skypie. Sebelum meng-copy file yang ada di dalam `franky.zip` buatlah directory `franky.E08.com` di `/var/www` dengan command : 

`mkdir /var/www/franky.E08.com`

Setelah itu unzip file `franky.zip` dan copy file yang ada di dalam folder `franky` setelah di unzip ke directory `/var/www/franky.E08.com` dengan command :

```
cp /root/franky/home.html /var/www/franky.E08.com
cp /root/franky/index.php /var/www/franky.E08.com
```

Untuk checking apakah file tersebut berhasil di copy gunakan command `ls` di directory `/var/www/franky.E08.com` :

![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/242cd230ec2956953425147a8acef46592477217/pictures/Nomor%208d.JPG)

Konfigurasi website sudah selesai, untuk melakukan checking apakah web server tersebut berhasil kita pindah ke node Loguetown/Alabasta dan install Lynx dengan command :\

```
apt-get update
apt-get install lynx
```

Dan Cek website tersebut dengan command : 

`lynx franky.E08.com` dan `lynx www.franky.E08.com`

**Hasil** : 

![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/57243330c699a9f9c36c5c19949db6b0fba26c0f/pictures/Nomor%208e.JPG)
