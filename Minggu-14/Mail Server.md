# MAIL SERVER
- Dimas Fahrul Putra Arismanto
- Muhammad Ilham Adi Pratama
- Awan Abdillah Akbar Dhiya'ulhaq
- Khozinatul Asror

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
telnet kampus-03.takehome.com smtp
```
[![Cuplikan-layar-2023-05-25-140354.png](https://i.postimg.cc/3RkKZXv1/Cuplikan-layar-2023-05-25-140354.png)](https://postimg.cc/fthnz05S)
cek email
[![Cuplikan-layar-2023-05-25-141401.png](https://i.postimg.cc/wMh3hXCP/Cuplikan-layar-2023-05-25-141401.png)](https://postimg.cc/q6vkr3MX)