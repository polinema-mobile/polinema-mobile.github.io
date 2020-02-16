# Explicit Intent

## Teori

Pemanggilan Intent secara explicit dengan menentukan nama Activity tujuan.
Intent membutuhkan dua parameter, yang pertama adalah `Context` (dapat
didapatkan dari `Activity` atau `Application`) dan berikutnya adalah
nama `NamaActivity.class`.

```java
Intent intent = new Intent(this, NextActivity.class);
startActivity(intent);
```

## Praktikum

- Bukalah project `Intent` yang telah anda clone, dengan Android Studio.
- Amati file `MainActivity.java` dan `activity_main.xml`.
- Pada `activity_main.xml`, tambahkan atribut
 `android:onClick="handleExplicitIntent"` pada tombol dengan id
 `@+id/button_explicit`
- Generate handler untuk menangani aksi ketika tombol ditekan dengan shortcut
 `Alt + Enter`
- Pilih menu `Create 'handleExplicitIntent(View)' in 'MainActivity'`
- Pada handler ini, tambahkan logika untuk membuka `ExplicitIntentActivity`
 dengan menggunakan `Intent`.

  ```java
  Intent intent =  new Intent(this, ExplicitIntentActivity.class);
  startActivity(intent);
  ```

  > **Catatan**: Untuk membuka Activity lain, pada Android digunakan Intent yang
  > berisi informasi Activity yang dipanggil. Intent ini tidak akan dijalankan,
  > sebelum dipanggil `startActivity()`.

- Jalankan project, kemudian perhatikan apa yang terjadi!
- Tekan tombol **back** untuk kembali ke Activity sebelumnya.
- Perhatikan kembali, pada file `activity_main.xml` tambahkan atribut
- `android:onClick="handleExit"` pada tombol dengan id `@+id/button_exit`
- Generate handler untuk menangani aksi ketika tombol ditekan dengan shortcut
 `Alt + Enter`
- Pilih menu `Create 'handleExit(View)' in 'MainActivity'`
- Pada handler ini, tambahkan logika untuk menutup/mengakhiri `Activity` dengan
 menggunakan fungsi `finish()`.

 > **Catatan**: Jika anda menginginkan Activity ketika ditekan tombol **back**
 > tidak kembali ke Activity sebelumnya anda bisa menambahkan method `finish()`
 > setelah `startActivity()`.

## Pertanyaan

- Lengkapi `ExplicitIntentActivity` sehingga bisa mengambil nilai pada `EditText` kemudian menampilkannya pada `TextView`.

> **Petunjuk**: buatlah dua buah atribut dengan nama `nameInput` dan `outputText`.

> ```java
> private EditText nameInput;
> private TextView outputText;
> ```

> Dengan menggunakan method `findViewById()` simpan component ke dalam atribut di
> atas.
