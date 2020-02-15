# Intent

Membuat aplikasi mobile khususnya Android, mungkin membutuhkan lebih dari satu
activity. Pengolahan data atau menjalankan tugas tidak memungkinkan dilakukan
pada UI main thread, karena jika tugas ini membutuhkan waktu yang lama aplikasi
akan mengalami force close. Aplikasi Android juga menjalankan tugas berdasarkan
event yang diterima. Hal-hal ini dapat dilakukan menggunakan konsep Intent.

## Pengertian Intent

Intent merupakan sebuah mekanisme yang digunakan untuk melakukan sebuah aksi
dari komponen aplikasi. Untuk dapat melakukan sebuah aksi pada sebuah intent,
ada 3 cara yang dapat dilakukan:

- Menjalankan sebuah activity lain baik dengan data ataupun tanpa data
- Membuat sebuah service untuk menjalankan pekerjaan tertentu pada sebuah
 background/non main thread.
- Mengirimkan sebuah broadcast. Pesan yang dikirimkan dalam keadaan tertentu,
 misalkan ketika booting atau sedang melakukan pengisian data baru mengirimkan
 data.

Terdapat 2 model Intent dalam pemrograman Android yaitu:

## Explicit Intent

Dikatakan intent explicit karena intent tersebut biasanya dibuat oleh seorang
programmer berdasarkan kebutuhan yang ada. Untuk memanggil intent tersebut
biasanya digunakan nama kelas, misalkan `id.ac.polinema.WelcomeActivity`

## Implicit Intent

Model intent ini sebaliknya dari intent explicit, kita tidak perlu menggunakan
nama kelas untuk memanggilnya. Intent model ini sudah disediakan oleh system
android, sebagai contoh kita akan melakukan pemanggilan telp maka seorang
programmer tanpa harus membuat intent untuk melakukan pemanggilan telp.

> **Catatan**: Silahkan clone [Starter Code Mobile
> 04](https://github.com/polinema-mobile/2019-mobile04) terlebih dahulu, sebelum
> memulai praktikum.
