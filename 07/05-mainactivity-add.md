# Tambah Data

Silahkan mengikuti langkah-langkah berikut untuk mengimplementasikan proses
penambahan data.

- Untuk proses penambahan data menggunakan tampilan `FloatingActionButton`,
 secara garis besar tidak ada perbedaan logika dengan `Button` pada umumnya.
 Tetapi pada praktikum kali ini digunakan kode dengan listener (anda dapat juga
 menggunakan atribut `android:onClick`).

 ```java
 Intent intent = new Intent(MainActivity.this, SaveActivity.class);
 intent.putExtra(TRANSACTION_KEY, new Transaction());
 startActivityForResult(intent, INSERT_REQUEST);
 ```
