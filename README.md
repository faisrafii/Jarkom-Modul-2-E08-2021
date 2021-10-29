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


## Nomor 9 


Setelah itu, Luffy juga membutuhkan agar url www.franky.yyy.com/index.php/home dapat menjadi menjadi www.franky.yyy.com/home. 


Pada Skypie pindah ke directory `/etc/apache2/sites-available` dan buka file `nano franky.E08.com.conf`.
Tambahkan di dalam file config tersebut : 

```
<Directory /var/www/franky.E08.com>
    Options +FollowSymLinks -Multiviews
    AllowOverride All
</Directory>
```

Isi file sebagai berikut :

![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/fd02ea04c52ec4cd71de5567724755a45926a95f/pictures/Nomor%209a.JPG)


Setelah itu gunakan command `a2enmod rewrite` untuk mengaktifkan module rewrite dan restart apache dengan command `service apache2 restart`.
Setelah itu pindah ke directory `/var/www/franky.E08.com` dan buat file `.htaccess` dengan command `nano .htaccess`. 
Tambahkan isi file tersebut dengan :

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^home$ $index.php/home
```

Setelah itu cek apakah config untuk rewrite berhasil dengan mengakses website di Loguetown/Alabasta dengan command :

`lynx www.franky.E08.com/home`

**HASIL :**

![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/57243330c699a9f9c36c5c19949db6b0fba26c0f/pictures/Nomor%208e.JPG)


## Nomor 10


Setelah itu, pada subdomain www.super.franky.yyy.com, Luffy membutuhkan penyimpanan aset yang memiliki DocumentRoot pada /var/www/super.franky.yyy.com.


Sama halnya dengan nomor 8, pindah ke directory `/etc/apache2/sites-available` untuk membuat config super.franky dan gunakan command : 

`cp 000-default.conf super.franky.E08.com.conf`


Setelah itu buka file `franky.E08.com.conf` dan ubah Document Root menjadi :

`DocumentRoot /var/www/super.franky.E08.com`


dan tambahkan :

```
ServerName super.franky.E08.com
ServerAlias www.super.franky.E08.com
```


Isi file sebagai berikut :


![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/e940f9d85dff908a294c0651d388d301d3dbf230/pictures/Nomor%2010a.JPG)


Setelah itu enable website dengan command :

`a2ensite super.franky.E08.com` dan restart apache dengan `service apache2 restart`.


Setelah itu kembali ke directory root dan download file `super.franky.zip` yang ada di link : [File Jarkom](https://github.com/FeinardSlim/Praktikum-Modul-2-Jarkom)


Setelah mendownload file digunakan command `wget <link hasil download>` untuk menaruh file `super.franky.zip` ke dalam Skypie. Sebelum meng-copy file yang ada di dalam `super.franky.zip` buatlah directory `super.franky.E08.com` di `/var/www` dengan command : 

`mkdir /var/www/super.franky.E08.com`


Setelah itu unzip file `super.franky.zip` dan copy file yang ada di dalam folder `super.franky` setelah di unzip ke directory `/var/www/super.franky.E08.com` dengan command :

```
cp -r /root/franky/error /var/www/super.franky.E08.com
cp -r /root/franky/public /var/www/super.franky.E08.com
```


Setelah itu cek di Loguetown/Alabasta dengan command:

`lynx super.franky.E08.com` dan `lynx www.super.franky.E08.com`


**HASIL:**


![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/b88bb6d5f33fdabb4e0ad38e033255d60994e5fe/pictures/Nomor%2010b.JPG)


## Nomor 11


Akan tetapi, pada folder /public, Luffy ingin hanya dapat melakukan directory listing saja.


Pindah ke directory `/etc/apache2/sites-available` dan buka file `super.franky.E08.com.conf` dan tambahkan isi file sebagai berikut :


```
<Directory /var/www/super.franky.E08.com/public>
     Options +Indexes
</Directory>
```


Setelah itu restart apache dengan `service apache2 restart`.


Setelah itu cek di Loguetown/Alabasta dengan command:

`lynx super.franky.E08.com/public` dan `lynx www.super.franky.E08.com/public`


**HASIL:**


![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/28f79da154b6d6213068db435fa8e4bdca5d1f11/pictures/Nomor%2011a.JPG)


## Nomor 12


Tidak hanya itu, Luffy juga menyiapkan error file 404.html pada folder /error untuk mengganti error kode pada apache.


Pindah ke directory `/etc/apache2/sites-available` dan buka file `super.franky.E08.com.conf` dan tambahkan isi file sebagai berikut :

`ErrorDocument 404 /error/404.html`


Setelah itu restart apache dengan `service apache2 restart`.


Setelah itu cek di Loguetown/Alabasta dengan command:

`lynx super.franky.E08.com/bebaslur`


**HASIL:**


![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/e684ba2d3b8553425df09eeddce2885d55d9e6bc/pictures/Nomor%2012a.JPG)


## Nomor 13


Luffy juga meminta Nami untuk dibuatkan konfigurasi virtual host. Virtual host ini bertujuan untuk dapat mengakses file asset www.super.franky.yyy.com/public/js menjadi www.super.franky.yyy.com/js.


Pindah ke directory `/etc/apache2/sites-available` dan buka file `super.franky.E08.com.conf` dan tambahkan isi file sebagai berikut :


```
<Directory /var/www/super.franky.E08.com/public/js>
     Options +Indexes
</Directory>
 
Alias "/js" "/var/www/super.franky.E08.com/public/js"
```


Setelah itu cek di Loguetown/Alabasta dengan command:

`lynx super.franky.E08.com/js`


**HASIL:**


![ImgSrc](https://github.com/faisrafii/Jarkom-Modul-2-E08-2021/blob/63e65e37b62a3def435fca61b809bbc2d248b73e/pictures/Nomor%2013a.JPG)
