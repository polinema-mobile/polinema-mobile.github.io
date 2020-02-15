# Implicit Intent

## Teori

Terkadang pada aplikasi Android yang dibangun, membutuhkan activity bawaan yang
telah disediakan oleh Android. Pemanggilan Intent ini dilakukan secara implicit.
Pada umumnya untuk melakukan ini, cukup dengan mendefinisikan aksi tertentu
(dapat menggunakan konstanta pada Intent yang umumnya menggunakan prefiks
`ACTION`).

Aplikasi yang umum digunakan antara lain:

- Call
- Dialpad
- Contact
- Browser
- Call Log
- Gallery
- Camera

Sebagai contoh pemanggilan Gallery yang berisi gambar, dapat dilihat pada kode
berikut.

```java
Intent intent = new Intent(Intent.ACTION_PICK, MediaStore.Images.Media.EXTERNAL_CONTENT_URI);
```

## Praktikum

- Buka dan amati file `MainActivity.java` dan `activity_main.xml` dalam project
 **Intent**.

- Pada tombol **Implicit Intent** tambahkan atribut
 `android:onClick="handleImplicitIntent"`, kemudian generate handler menggunakan
 shortcut `Alt + Enter`.

- Lengkapi dengan logika intent, untuk menuju ke Activity
 `ImplicitIntentActivity`

  ```java
  Intent intent = new Intent(this, ImplicitIntentActivity.class);
  startActivity(intent);
  ```

- Buka `ImplicitIntentActivity.java` dan pelajari layout
 `activity_implicit_intent.xml`. Pada Activity ini terdapat gambar avatar yang
 sumber gambarnya diambil dari gallery.

- Pada `ImplicitIntentActivity.java`, tambahkan konstanta `TAG` yang digunakan
 untuk kebutuhan logging.

  ```java
  private static final String TAG = ImplicitIntentActivity.class.getCanonicalName();
  ```

- Selain `TAG`, dibutuhkan juga konstanta lain yaitu `GALLERY_REQUEST_CODE` yang
 digunakan untuk mendefinisikan request code pemanggilan implicit intent.

  ```java
  private static final int GALLERY_REQUEST_CODE = 1;
  ```

- Pada tombol **Change Avatar** dalam layout `activity_implicit_intent.xml` tambahkan
 atribut `android:onClick="handleChangeAvatar"`, kemudian generate handler menggunakan
 shortcut `Alt + Enter`.

- Pada blok handler tersebut, tambahkan logika untuk mendefinisikan aksi
 pemilihan gambar dari gallery secara implicit.

  ```java
  Intent intent = new Intent(Intent.ACTION_PICK, MediaStore.Images.Media.EXTERNAL_CONTENT_URI);
  startActivityForResult(intent, GALLERY_REQUEST_CODE);
  ```

  > **Catatan**: Jika anda mengamati, pada pemanggilan Activity kali ini digunakan
  > `startActivityForResult()`. Hal ini dilakukan jika pada Activity pemanggil
  > membutuhkan return value dari pemanggilan Activity. Dalam kasus ini yaitu, url
  > path gambar gallery.

- Override method `onActivityResult` dalam `ImplicitIntentActivity`. Url gambar
 pada gallery yang dipilih akan diterima pada method ini. Tambahkan logika
 berikut untuk menangani logika pemrosesan url gambar.

  ```java
  if (resultCode == RESULT_CANCELED) {
      return;
  }

  if (requestCode == GALLERY_REQUEST_CODE) {
    if (data != null) {
      try {
        Uri imageUri = data.getData();
        Bitmap bitmap = MediaStore.Images.Media.getBitmap(this.getContentResolver(), imageUri);
        avatarImage.setImageBitmap(bitmap);
      } catch (IOException e) {
        Toast.makeText(this, "Can't load image", Toast.LENGTH_SHORT).show();
        Log.e(TAG, e.getMessage());
      }
    }
  }
  ```
