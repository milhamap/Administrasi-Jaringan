
# Kelompok – 3
3121600005 – Dimas Fahrul
3121600014 – M Ilham Adu P
3121600016 – Awan Abdillah Akbar
3121600026 - Muh Kozinatul Asror

# Instalasi php 
1. gunakan ~sudo apt -y install php php-cgi php-mysqli php-pear php-mbstring libapache2-mod-php php-common php-phpseclib php-mysql
2. ketik ~php -v untuk memastikan php sudah terinstall
[![1.jpg](https://i.postimg.cc/15SJtjFD/1.jpg)](https://postimg.cc/bd6QVL3v)
# Instalasi Composer
1. Install curl sebelum menginstall composer dengan cara ~sudo apt install curl
[![4.jpg](https://i.postimg.cc/fLTMDKKs/4.jpg)](https://postimg.cc/94S6ByKg)
2. setelah curl terinstall, install composer dengan ~curl -sS https://getcomposer.org/installer | php
3. Pastikan Composer dapat digunakan dan dijalankan secara global. Tambahkan perintah di bawah ini.
- sudo mv composer.phar /usr/local/bin/composer
- sudo chmod +x /usr/local/bin/composer
4. cek komposer dengan ~composer --version
5. buat project larvel ~sudo composer create-project laravel/laravel project-name
[![5.jpg](https://i.postimg.cc/MTTJhG6K/5.jpg)](https://postimg.cc/qt9FK469)
[![6.jpg](https://i.postimg.cc/SQnJ9S6h/6.jpg)](https://postimg.cc/qgdJVdDb)
6. Setelah Laravel terinstall ketikkan php artisan serve untuk mengaktifkan server Laravel, dan 
# Deployment Laravel
1. pindah ke folder var/www/html/
2. Lalu atur permission untuk memastikan proyek dapat berjalan tanpa masalah:
gunakan ~sudo -R 775 /var/www/html/kelompok3-dns/storage
3. Buat virtual host baru untuk proyek ini dengan menjalankan perintah
~sudo nano /etc/apache2/sites-available/laravel.conf
[![7.jpg](https://i.postimg.cc/909mnfbw/7.jpg)](https://postimg.cc/XBV6Z4Tn)
4.ganti ServerName dan ServerAdmin sesuai domain
[![8.jpg](https://i.postimg.cc/fLtDVb6q/8.jpg)](https://postimg.cc/62XDSB6C)
5.Aktifkan Apache rewrite module, lalu restart layanan Apache:
~sudo a2enmod rewrite
~sudo systemctl restart apache2
[![9.jpg](https://i.postimg.cc/PrhnjKrR/9.jpg)](https://postimg.cc/CdvQCG8G)
6. Buka kembali donain kampus-03 maka default pagenya adalah laravel