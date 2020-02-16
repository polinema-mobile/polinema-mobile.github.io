# Android Bundle

## Teori

Untuk berkomunikasi antar Activity, Android menggunakan
[Bundle](https://developer.android.com/reference/android/os/Bundle). Bundle
dapat dikirimkan melalui
[Intent](https://developer.android.com/reference/android/content/Intent).
Pengiriman data melalui Bundle, dapat digunakan salah satu cara berikut:

1. Menggunakan Bundle dari Intent

  ```java
  Intent intent = new Intent(this, Example.class);
  Bundle extras = intent.getExtras();
  extras.putString(key, value);
  ```

2. Menginstansiasi Bundle

  ```java
  Intent intent = new Intent(this, Example.class);
  Bundle bundle = new Bundle();
  bundle.extras.putString(key, value);
  intent.putExtras(bundle);
  ```

3. Menggunakan method `putExtra()` pada Intent.

  ```java
  Intent intent = new Intent(this, Example.class);
  intent.putExtra(key, value);
  ```

Pada Activity yang dikirimkan data, diperlukan proses pembacaan data. Untuk
pembacaan data, disesuaikan dengan tipe data yang dikirimkan. Di bawah ini
merupakan contoh pembacaan data dengan tipe data String.

```java
Bundle bundle = getIntent().getExtras();
String value = bundle.getString(key);
```

atau dapat disingkat

```java
String value = getIntent().getExtras().getString(key);
```

## Praktikum

- Pada project **Intent** bukalah file `BundleActivity.java` kemudian tambahkan
 konstanta sebagai berikut.

  ```java
  public static final String USERNAME_KEY = "username";
  public static final String NAME_KEY = "name";
  public static final String AGE_KEY = "age";
  ```

 > **Tips**: anda dapat menggunakan snippet `psfs` untuk mempermudah membuat
 > konstanta.

- Deklarasikan atribut untuk digunakan menghubungkan `EditText` dengan layout.

  ```java
  private EditText usernameInput;
  private EditText nameInput;
  private EditText ageInput;
  ```

- Bind atribut dengan view pada layout, lakukan hal ini pada method `onCreate()`

  ```java
  usernameInput = findViewById(R.id.input_username);
  ```

- Lengkapi langkah bind untuk atribut yang lain berdasarkan informasi berikut.

| Atribut     | Id                |
| ---         | ---               |
| `nameInput` | `R.id.input_name` |
| `ageInput`  | `R.id.input_age`  |

- Bukalah file `activity_bundle.xml` kemudian perhatikan pada bagian tombol
 **Submit**

- Tambahkan atribut `android:onClick="handleSubmit"`, kemudian generate handler
 dengan shortcut `Alt + Enter`
- Tambahkan logika untuk mengirimkan data ke Activity lain dengan menggunakan
 Intent.
- Pada method `handleSubmit(View view)` tangkap nilai dari masing-masing
 EditText.

  ```java
  String username = usernameInput.getText().toString();
  String name = nameInput.getText().toString();
  int age = Integer.parseInt(ageInput.getText().toString());
  ```

  > **Catatan**: Untuk `age` ditambahkan proses konversi dari `String` ke `int`.

- Instansiasi `Intent` dan atur target **Activity** ke `ProfileBundleActivity`

  ```java
  Intent intent = new Intent(this, ProfileBundleActivity.class);
  ```

- Untuk mengirimkan data ke Activity lain, dapat digunakan method `putExtra()`
 pada Intent. Method ini membutuhkan dua parameter, yaitu key dan value. Untuk
 memudahkan pada umumnya untuk key digunakan konstanta. Konstanta yang
 dibutuhkan telah dibuat pada langkah awal. Silahkan lengkapi implementasi
 berdasarkan pada tabel berikut.

| Key            | Value      |
| ---            | ---        |
| `USERNAME_KEY` | `username` |
| `NAME_KEY`     | `name`     |
| `AGE_KEY`      | `age`      |

- Sebagai langkah terakhir, panggil method `startActivity()` berisi data `Intent` yang telah dikonfigurasi.

  ```java
  // Implementasi kode sebelumnya
  // ...

  startActivity(intent);
  ```

- Pada tahapan ini, anda telah berhasil untuk mengirimkan data ke *Activity*
 lain.

- Sebagai langkah selanjutnya, dibutuhkan proses untuk membaca data yang telah
 dikirimkan. Bukalah dan amati file `ProfileBundleActivity.java` serta
 `activity_profile_bundle.xml`.

- Tambahkan atribut yang berkaitan dengan layout.

  ```java
  private TextView usernameText;
  private TextView nameText;
  private TextView ageText;
  ```

- Bind atribut dengan id pada layout sesuai informasi tabel berikut.

| Atribut        | Id                   |
| ---            | ---                  |
| `usernameText` | `R.id.text_username` |
| `nameText`     | `R.id.text_name`     |
| `ageText`      | `R.id.text_age`      |

- Untuk mendapatkan akses data yang telah dikirimkan dapat menggunakan method
 `getIntent().getExtras()`. Tambahkan kode berikut setelah proses bind.

  ```java
  Bundle extras = getIntent().getExtras();
  ```

- Untuk menghindari kemungkinan tidak didapatkan nilai data, lakukan proses
 pengecekan nilai bukan `null`.

  ```java
  if (extras != null) {

    // TODO: tampilkan nilai yang didapatkan ke tampilan

  }
  ```

## Pertanyaan

- Lengkapi `ProfileBundleActivity` sehingga bisa menampilkan informasi data
 profile yang telah diterima.
