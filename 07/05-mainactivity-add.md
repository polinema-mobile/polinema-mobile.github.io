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

- Proses pengisian data dilakukan dalam `SaveActivity` yang kemudian hasilnya
 dikirimkan ke `MainActivity` melalui Intent. Untuk menerima hasil, silahkan
 override method `onActivityResult()` dan tambahkan kode berikut.

  ```java
  if (resultCode == RESULT_OK) {
      Transaction transaction = data.getParcelableExtra(TRANSACTION_KEY);
      if (requestCode == INSERT_REQUEST) {
          account.addTransaction(transaction);
      }
      adapter.notifyDataSetChanged();
      welcomeText.setText(String.valueOf(account.getBalance()));
  }
  ```

- Perhatikan method `adapter.notifyDataSetChanged()`, method ini memberitahukan
 kepada `RecyclerView` bahwa telah terjadi perubahan data.
