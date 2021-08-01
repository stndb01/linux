## Mendeploy CTFd dengan menggunakan Docker-Compose

### Service yang digunakan 
- CTFd 
- MariaDB
- NGINX

#### CTFd
CTFd adalah framework yang digunakan untuk membuat platform kegiatan Capture the Flag bidang security. Dengan menggunakan framework ini deployment platform CTF dapat dilakukan dengan mudah, dimana tersedia beberapa opsi seperti menggunakan docker, vagrant, ataupun dengan docker-compose.

#### MariaDB
MariaDB adalah salah satu jenis database yang merupakan alternatif dari MySQL dan MariaDB bersifat open source.  

#### NGINX
NGINX adalah salah satu jenis web server yang cepat dan mampu menangani koneksi banyak.

### Fitur CTFd
- Membuat challange, hint, kategori, manajemen tim ataupun hal lain dari interface admin dengan mudah
- Kompetisi CTF dapat diadakan untuk tim ataupun perorangan 
- Menampilkan scoreboard dan menampilkan 10 tim yang memiliki poin tertinggi
- Waktu mulai dan berhenti kompetisi CTF dapat diatur secara otomatis
- dan fitur lainya

### Cara mendeploy CTFd

untuk melakukan deployment CTFd dengan docker-compose dapat dilakukan dengan mudah, tentunya harus memiliki docker dan docker-compose terlebih dahulu pada sistem operasi yang dapat diinstalasi secara manual. Kemudian untuk framework CTFd dapat diunduh dengan kode berikut

```
git clone https://github.com/CTFd/CTFd.git
```

Kemudian kita cukup memodifikasi konfigurasi file docker-compose.yml sesuai dengan kebutuhan. Dalam hal ini tidak banyak yang saya rubah. Salah satu bagian yang saya rubah adalah port yang digunakan. Secara default dalam file docker-compose.yml, port yang digunakan adalah port 8000 (atau port lain). Apabila port yang akan dipakai telah digunakan maka kita dapat memodifikasi PORT pada file compose dengan port lain seperti contoh dibawah.

```
 ports:
      - "8008:8008"
```
atau kita dapat juga menghentikan service yang menggunakan port 8000 dengan perintah berikut

```
sudo fuser 8000/tcp
```
Setelah file docker-compose.yml selesai dikonfigurasi maka dapat menjalankan perintah berikut untuk melakukan proses deployment

```
docker-compose up
```
Untuk pembuatan platform CTF untuk pertama kalinya akan memakan waktu lumayan lama, setelah proses selesai maka kita dapat langsung membuka http://localhost:8000 mengecek hasilnya. Pada halaman awal akan menampilkan halaman admin dan kita dapat memulai untuk mengkonfigurasikan kompetisi CTF yang akan diadakan.