# Update Data

Untuk proses update data, tidaklah jauh berbeda dengan proses penambahan data.
Yang membedakan adalah diperlukan proses untuk mengambil data dari RecyclerView.
Data bisa didapatkan melalui interface listener yang telah didefinisikan.
Silahkan ikuti langkah-langkah berikut untuk mengimplementasikan fitur perubahan
data.

- Bukalah class `MainActivity`, dan tambahkan kode berikut pada method
 `onTransactionClicked()`.

  ```java
  Intent intent = new Intent(this, SaveActivity.class);
  intent.putExtra(TRANSACTION_KEY, item);
  intent.putExtra(INDEX_KEY, 0);
  startActivityForResult(intent, UPDATE_REQUEST);
  ```

- Pada kode di atas, dilakukan proses definisi intent dan pengiriman data
 transaction serta posisi index data tersebut. Untuk membedakan dengan proses
 penambahan data, digunakan request code yang berbeda yaitu, `UPDATE_REQUEST`.

- Seperti halnya proses tambah data, proses update data akan diproses pada
 `onActivityResult()`. Pada blok kondisi pengecekan request code tambahkan
 kondisi tambahan `else if` untuk proses update data.

  ```java
  else if (requestCode == UPDATE_REQUEST) {
      int index = data.getIntExtra(INDEX_KEY, 0);
      account.updateTransaction(index, transaction);
  }
  ```

- Silahkan uji fitur-fitur yang telah anda terapkan!
- Lakukan commit pada pengerjaan proyek aplikasi anda!
