# Webmin


Cara Install Webmin di Debian 10

Menginstal Webmin di Debian Linux adalah proses yang relatif mudah dan hanya akan memakan waktu beberapa menit. Paket webmin tersedia dari repositori Webmin resmi.

    Pertama, perbarui indeks paket dan instal dependensi:

    sudo apt update
    sudo apt install software-properties-common apt-transport-https wget

    Import Webmin GPG key menggunakan perintah wget dan aktifkan Webmin repository:

    wget -q http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -

    sudo add-apt-repository "deb [arch=amd64] http://download.webmin.com/download/repository sarge contrib"

    Setelah repositori diaktifkan, instal paket Webmin dengan menjalankan:

    sudo apt update && sudo apt install webmin

    Jika instalasi berhasil, output berikut akan muncul :

    Webmin install complete. You can now login to https://your_server_ip_or_hostname:10000/
    as root with your root password, or as any user who can use sudo
    to run commands as root.

    Pada Poin ini, Layanan Webmin akan mulai secara otomatis.

Webmin telah diinstal di server Debian Linux Anda.
Webmin dan Firewall di Debian 10

Secara default, Webmin mendengarkan koneksi pada port 10000 di semua interface jaringan. Jika server Anda menjalankan firewall, Anda harus membuka port Webmin.

Pengguna UFW dapat membuka port 10000 dengan mengetik:

sudo ufw allow 10000/tcp

Jika Anda menggunakan nftables untuk memfilter koneksi ke sistem Anda, buka port yang diperlukan dengan menggunakan perintah berikut:

nft add rule inet filter input tcp dport 10000 ct state new,established counter accept

Akses Webmin Melalui Web Interface

Setelah Webmin diinstal pada server Debian Anda, buka browser favorit Anda dan ketikkan hostname server atau alamat IP publik diikuti dengan port Webmin 10000:

https://server_ip_atau_hostname:10000/

Browser akan complain mengenai sertifikat yang tidak valid, karena secara default, Webmin menggunakan sertifikat SSL yang ditandatangani sendiri (self-signed) yang notabene tidak dipercaya oleh browser.

Masuk ke interface web Webmin menggunakan kredensial user root atau user sudo Anda:

webmin login form

Setelah masuk, Anda akan diarahkan ke dasbor Webmin, yang menyediakan informasi dasar tentang sistem Anda.

Dari sini, Anda dapat mulai mengonfigurasi dan mengelola server Debian sesuai kebutuhan Anda.
