# Parcelable

## Teori

Untuk memudahkan pengiriman banyak data melalui Bundle, dapat menggunakan
Parcelable. Parcelable dapat memudahkan pengiriman Obyek secara langsung.
Sebagai contoh: data `username`, `name` dan `age`, dapat dikirimkan secara
langsung dengan membuat obyek `User` yang mengimplementasi `Parcelable`.

> **Catatan**: Untuk memudahkan implementasi `Parcelable`, silahkan tambahkan
> plugin **Android parcelable code generator** melalui **Settings** -> **Plugins**

## Praktikum

- Pada praktikum sebelumnya, data yang dikirimkan dapat dimodelkan menjadi data
 `User`. Tambahkan package dengan nama `model` kemudian tambahkan file java
 dengan nama `User.java`

- Pada `User` tambahkan atribut yang dibutuhkan, yaitu `username`, `name` dan
 `age`.

 ```java
 private String username;
 private String name;
 private int age;
 ```

- Dengan memanfaatkan fitur dari Android Studio, generate constructor dengan
 menekan shortcut `Alt + Insert` (Windows) atau `Cmd + N` (Mac). Pilih semua
 atribut, kemudian tekan **OK**.

- Ulangi langkah generate untuk getter dan setter.

- Untuk menggunakan `Parcelable`, sebuah class harus mengimplementasikan
 interface `Parcelable`. Tambahkan pernyataan `implements Parcelable` pada
 deklarasi class.

- Dengan memanfaatkan plugin **Android parcelable code generator**, ulangi
 langkah generate kemudian pilih menu **Parcelable**. Periksa kembali file
 `User.java` sampai tidak ada tanda merah.

- Ulangi langkah-langkah pada praktikum sebelumnya, yang sedikit berbeda pada
 proses pengiriman akan digunakan class `User`.

  ```java
  // deklarasi variabel user
  User user = new User(username, name, age);

  // ...
  // tambahkan user ke dalam intent
  intent.putExtra(USER_KEY, user);
  ```

## Pertanyaan

- Lengkapi project sehingga dapat menampilkan data menggunakan pendekatan
 `Parcelable`
