# Analisis Perbaikan

## Permasalahan 1

### Gejala

Docker Compose gagal dijalankan karena file `docker-compose.yml` tidak dapat diparsing.

### Penyebab

Deklarasi service ditulis tanpa tanda titik dua (`:`).

**Sebelum**

```yaml
services
```

### Solusi

Menambahkan tanda titik dua pada deklarasi service.

**Sesudah**

```yaml
services:
```

---

## Permasalahan 2

### Gejala

Container `web1` tidak dapat terhubung ke database.

### Penyebab

Hostname database menggunakan nama service yang tidak tersedia.

**Sebelum**

```yaml
DB_HOST: mysql
```

### Solusi

Mengubah hostname database sesuai nama service yang ada pada Docker Compose.

**Sesudah**

```yaml
DB_HOST: db
```

---

## Permasalahan 3

### Gejala

Konfigurasi environment database pada web server tidak konsisten.

### Penyebab

Variabel password menggunakan nama `DB_PASS`.

**Sebelum**

```yaml
DB_PASS: student123
```

### Solusi

Mengganti nama variabel menjadi `DB_PASSWORD`.

**Sesudah**

```yaml
DB_PASSWORD: student123
```

Perubahan ini dilakukan pada service `web1`, `web2`, dan `web3`.

---

## Permasalahan 4

### Gejala

Container `web2` gagal melakukan autentikasi ke database.

### Penyebab

Password database tidak sesuai dengan konfigurasi MySQL.

**Sebelum**

```yaml
DB_PASS: wrongpassword
```

### Solusi

Mengganti password menjadi password yang benar.

**Sesudah**

```yaml
DB_PASSWORD: student123
```

---

## Permasalahan 5

### Gejala

Service `web3` gagal dibangun (build).

### Penyebab

Path build mengarah ke folder yang tidak ada.

**Sebelum**

```yaml
context: ./web33
```

### Solusi

Mengubah path build sesuai nama folder yang tersedia.

**Sesudah**

```yaml
context: ./web3
```

---

## Permasalahan 6

### Gejala

Nginx tidak dapat mengakses service `web3`.

### Penyebab

Service `web3` hanya terhubung ke network backend.

**Sebelum**

```yaml
networks:
  - backend
```

### Solusi

Menambahkan network frontend agar dapat diakses oleh Nginx.

**Sesudah**

```yaml
networks:
  - frontend
  - backend
```

---

## Permasalahan 7

### Gejala

Volume database tidak sesuai dengan deklarasi yang digunakan.

### Penyebab

Nama volume yang digunakan berbeda dengan volume yang didefinisikan.

**Sebelum**

```yaml
volumes:
  database-data:
```

### Solusi

Mengubah nama volume agar konsisten.

**Sesudah**

```yaml
volumes:
  db-data:
```

---

## Permasalahan 8

### Gejala

Konfigurasi Nginx tidak valid.

### Penyebab

File `nginx.conf` masih mengandung markdown code block.

**Sebelum**

````nginx
```nginx
````

dan

```nginx
```

````

### Solusi
Menghapus seluruh tag markdown sehingga file hanya berisi konfigurasi Nginx.

---

## Permasalahan 9

### Gejala
Load balancer tidak dapat meneruskan request ke backend pertama.

### Penyebab
Nama host service salah.

**Sebelum**
```nginx
server web11:80;
````

### Solusi

Mengubah nama host sesuai service yang tersedia.

**Sesudah**

```nginx
server web1:80;
```

---

## Permasalahan 10

### Gejala

Load balancer gagal mengakses service `web3`.

### Penyebab

Port backend yang digunakan tidak sesuai.

**Sebelum**

```nginx
server web3:8080;
```

### Solusi

Mengubah port menjadi port layanan Apache yang benar.

**Sesudah**

```nginx
server web3:80;
```

---

## Permasalahan 11

### Gejala

Container `web1` gagal melakukan build.

### Penyebab

Tag image PHP salah penulisan.

**Sebelum**

```dockerfile
FROM php:8.2-apach
```

### Solusi

Memperbaiki nama image.

**Sesudah**

```dockerfile
FROM php:8.2-apache
```

---

## Permasalahan 12

### Gejala

Identitas praktikan pada web1 belum sesuai.

### Penyebab

Masih menggunakan placeholder.

**Sebelum**

```php
$nama = "ganti ke namamu";
$nim  = "ganti ke nimmu";
```

### Solusi

Mengganti dengan identitas praktikan.

**Sesudah**

```php
$nama = "Mohammad Zulfan Ramadhan";
$nim  = "H1H024008";
```

---

## Permasalahan 13

### Gejala

Identitas praktikan pada web2 belum sesuai.

### Penyebab

Masih menggunakan placeholder.

### Solusi

Mengganti placeholder dengan data praktikan.

**Sesudah**

```php
$nama = "Mohammad Zulfan Ramadhan";
$nim  = "H1H024008";
```

---

## Permasalahan 14

### Gejala

Identitas container pada web2 tidak sesuai.

### Penyebab

Label container salah dituliskan.

**Sebelum**

```html
WEB-WEB
```

### Solusi

Mengubah label sesuai nomor container.

**Sesudah**

```html
WEB-2
```

---

## Permasalahan 15

### Gejala

Container `web3` gagal melakukan build.

### Penyebab

Tag image PHP salah penulisan.

**Sebelum**

```dockerfile
FROM php:8.2-apche
```

### Solusi

Memperbaiki nama image.

**Sesudah**

```dockerfile
FROM php:8.2-apache
```

---

## Permasalahan 16

### Gejala

Identitas praktikan pada web3 belum sesuai.

### Penyebab

Masih menggunakan placeholder.

### Solusi

Mengganti placeholder dengan data praktikan.

**Sesudah**

```php
$nama = "Mohammad Zulfan Ramadhan";
$nim  = "H1H024008";
```

---

## Permasalahan 17

### Gejala

Label container web3 tidak sesuai.

### Penyebab

Terdapat kesalahan penulisan nama container.

**Sebelum**

```html
WEB-WOB
```

### Solusi

Mengubah label sesuai nomor container.

**Sesudah**

```html
WEB-3
```

---

## Permasalahan 18

### Gejala

Data identitas mahasiswa pada database belum sesuai.

### Penyebab

Script SQL masih menggunakan placeholder.

**Sebelum**

```sql
'REPLACE_NIM',
'REPLACE_NAME'
```

### Solusi

Mengganti placeholder dengan data mahasiswa yang sebenarnya.

**Sesudah**

```sql
'H1H024008',
'Mohammad Zulfan Ramadhan'
```

###Hasil Akhir
<img width="775" height="337" alt="Screenshot 2026-06-08 143836" src="https://github.com/user-attachments/assets/914f6160-eb14-4ce5-8461-e21c53c4bd3d" />
<img width="756" height="327" alt="Screenshot 2026-06-08 143858" src="https://github.com/user-attachments/assets/2c8b7394-4a1c-4bb6-9409-52e1fdba5d4f" />
<img width="732" height="335" alt="Screenshot 2026-06-08 143849" src="https://github.com/user-attachments/assets/27f1b058-a208-4db7-bd56-bac215f38cb0" />
<img width="1881" height="176" alt="Screenshot 2026-06-08 143659" src="https://github.com/user-attachments/assets/3c4ba530-4d0c-4723-9b94-b01bb1aec337" />
