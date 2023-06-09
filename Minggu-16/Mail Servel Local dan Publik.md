# MAIL SERVER LOCAL DAN PUBLIC
- Dimas Fahrul Putra Arismanto
- Muhammad Ilham Adi Pratama (3121600014)
- Awan Abdillah Akbar Dhiya'ulhaq
- Khozinatul Asror

## Mail Server Local
## Instalasi Postfix
gunakan perintah dibawah ini untuk menginstall postfilx
```console
sudo apt install postfix
```
[![Cuplikan-layar-2023-05-25-122644.png](https://i.postimg.cc/Kzb90Rnk/Cuplikan-layar-2023-05-25-122644.png)](https://postimg.cc/FfPgRFCN)
lalu pilih opsi ke 2 **Internet Site** 

[![Cuplikan-layar-2023-05-25-131621.png](https://i.postimg.cc/8zSVrB5M/Cuplikan-layar-2023-05-25-131621.png)](https://postimg.cc/JGPFfXjz)
setelah proses penginstalan selesai gunakan perintah
```console
dpgk-reconfigure
```
perintah diatas akan membuka halaman konfigurasi postflix.
[![Cuplikan-layar-2023-05-25-131708.png](https://i.postimg.cc/hGxnJy8L/Cuplikan-layar-2023-05-25-131708.png)](https://postimg.cc/McWNNYFH)
[![Cuplikan-layar-2023-05-25-131852.png](https://i.postimg.cc/gj7tHdmn/Cuplikan-layar-2023-05-25-131852.png)](https://postimg.cc/Cnj4w3Zg)
[![Cuplikan-layar-2023-05-25-131917.png](https://i.postimg.cc/DzcCY17V/Cuplikan-layar-2023-05-25-131917.png)](https://postimg.cc/nsCYXjsT)
[![Cuplikan-layar-2023-05-25-131943.png](https://i.postimg.cc/9Q5JmLM5/Cuplikan-layar-2023-05-25-131943.png)](https://postimg.cc/D86q5dLB)
[![Cuplikan-layar-2023-05-25-132014.png](https://i.postimg.cc/PfCgNFtP/Cuplikan-layar-2023-05-25-132014.png)](https://postimg.cc/dDKHx6ZY)

restart postfix menggunakan 
```console
systemctl restart postflix  
```

## instalasi dovecot
gunakan perintah
```console
apt-get install -y dovecot-imapd dovecot-pop3d
```
setelah terinstall masuk ke folder dovecot/conf.d
lalu gunakan perintah dibawah ini dan lakukan konfigurasi
```console
nano 10-mail.conf
```
[![Cuplikan-layar-2023-05-25-134408.png](https://i.postimg.cc/d18DPR5B/Cuplikan-layar-2023-05-25-134408.png)](https://postimg.cc/BLnJ2F9L)

restart dovecot menggunakan
```console
systemctl restart dovecot  
```

## Test Mail
buat 2 user baru untuk melakukan pengetesan
gunakan perintah 
```console
telnet kampusmail-03.takehome.com smtp
```
[![Cuplikan-layar-2023-05-25-140354.png](https://i.postimg.cc/3RkKZXv1/Cuplikan-layar-2023-05-25-140354.png)](https://postimg.cc/fthnz05S)
cek email
[![Cuplikan-layar-2023-05-25-141401.png](https://i.postimg.cc/wMh3hXCP/Cuplikan-layar-2023-05-25-141401.png)](https://postimg.cc/q6vkr3MX)

## Mail Server Public
Ini lanjutan dari Mail Server Local
## 1.Membuat User
Untuk membuat User silahkan tuliskan command berikut ini
    
    maildirmake /etc/skel/maildir
    adduser dimas

## 2.Intalasi Squirrelmail
berikut cara ubtuk install Squirrelmail

    apt-get install squirrelmail
setelah file pada forlder /etc/apache2/apache2.conf selesai di edit silahkan tambahkan konfigurasi command berikut ini

    # include the virtual host the configuration:
    include sites-enabled/
    include "/etc/squirrelmail/apache.conf"
Setelah selesai menambahkan command diatas silahkan lakukan restart apache2.
## 3.Konfigurasi Squirrelmail
setelah squirelmail terinstall 
gunakan

    chmod 755 -R /var/www/html/mail

untuk mengakses general option pada apache, lalu konfigurasikan seperti gambar dibawah ini
[![image.png](https://i.postimg.cc/bvXT1nKv/image.png)](https://postimg.cc/w1VLp1xK)

lalu gunakan juga

    perl conf.pl
    
dan konfigurasikan seperti gambar dibawah ini
[![image.png](https://i.postimg.cc/9QNfktWW/image.png)](https://postimg.cc/jDPKwfw9)

terakhir, restart apache dengan

    systemctl restart apache2


## 4.Test SquirrelMail antar Domaind
Silahkan buka domaind mail.kampus-03.takehome.com untuk masuk kehalaman login, selanjutnya masukkan akun yang telah dibuat tadi untuk login ke squirrelmail.

Setelah masuk kedalam halaman dashboard maka check terlebih dahulu apakah domaind kampus kita sudah terhubung dengan domaind kampus lain.
Berikut Command untuk mengecek dommaind sudah tersambung dengan domaind lain

    nslookup -q=mx (domain mail)
[![P6.png](https://i.postimg.cc/tRwFF2N3/P6.png)](https://postimg.cc/23dqDdJy)

Setelah pengecekan domaind silahkan untuk mencoba pengiriman antara domain tersebut.
seperti contoh berikut ini :
[![P5.png](https://i.postimg.cc/rFvCLcnR/P5.png)](https://postimg.cc/PPQ8WGkd)
Gambar diatas merupakan salah satu hasil dari percobaan pengiriman pesan antara domainde dimas@kampus-03.takehome.com ke domain zaki@mail.kampus-02.takehome.com.

[![P2.png](https://i.postimg.cc/wvnqWW2J/P2.png)](https://postimg.cc/Q9kZCJRx)
Berikut gambar dari percobaan domaind zaki@mail.kampus-02.takehome.com sebagai penerima dari domaind dimas@kampus-03.takehome.com.


