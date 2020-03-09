# Hapus Data

Untuk proses hapus data digunakan interaksi swipe (kiri atau kanan) dikarenakan
hanya dibutuhkan satu buah operasi (sebagai alternatif anda dapat juga
menggunakan interaksi dialog menu jika diperlukan).

Silahkan ikuti langkah-langkah berikut untuk mengimplementasikan fitur
penghapusan data:

- Untuk membuat interaksi swipe dibutuhkan class `ItemTouchHelper.SimpleCallback`. Tambahkan
 definisi tersebut pada baris terakhir pada method `onCreate()`

  ```java
  ItemTouchHelper.SimpleCallback simpleItemTouchCallback = new ItemTouchHelper.SimpleCallback() {
  };
  ```

  > **Catatan**: `ItemTouchHelper.SimpleCallback` adalah abstract class, sehingga
  > ketika diinstansiasi akan digenerate method yang wajib diimplementasikan. Kode
  > di atas jangan di copy paste.

- Setelah proses generate method telah selesai, tambahkan argumen pada
  constructor `ItemTouchHelper.SimpleCallback()` yang berisi informasi drag
  direction dan swipe direction.

  ```java
  new ItemTouchHelper.SimpleCallback(0, ItemTouchHelper.LEFT | ItemTouchHelper.RIGHT)
  ```

  > **Catatan**: Karena pada fitur ini tidak dibutuhkan interaksi drag, maka nilai
  > drag direction diset dengan nilai 0. Tanda `|` maksudnya operasi hapus dapat
  > dilakukan swipe kiri atau kanan.

- Untuk melakukan operasi hapus, silahkan tambahkan logika berikut pada method
 `onSwiped()`.

  ```java
  int index = viewHolder.getAdapterPosition();
  account.removeTransaction(index);
  adapter.notifyDataSetChanged();
  welcomeText.setText(String.valueOf(account.getBalance()));
  ```

- Ujilah fitur penghapusan data, dan jangan lupa untuk melakukan commit.
