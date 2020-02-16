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

### Explicit Intent

Dikatakan intent explicit karena intent tersebut biasanya dibuat oleh seorang
programmer berdasarkan kebutuhan yang ada. Untuk memanggil intent tersebut
biasanya digunakan nama kelas, misalkan `id.ac.polinema.WelcomeActivity`

### Implicit Intent

Model intent ini sebaliknya dari intent explicit, kita tidak perlu menggunakan
nama kelas untuk memanggilnya. Intent model ini sudah disediakan oleh system
android, sebagai contoh kita akan melakukan pemanggilan telp maka seorang
programmer tanpa harus membuat intent untuk melakukan pemanggilan telp.

## Activity dan Layout

Pengaturan Layout pada Activity diatur dengan menggunakan method
`setContentView()` yang menerima parameter berupa resource layout. Dikarenakan
ada pemisahan logika dan tampilan, untuk menghubungkan digunakan
`findViewById()`. Method tersebut membutuhkan parameter id variabel Component
yang didefinisikan dengan property `android:id`. Contoh penulisan id layout:

```xml
<EditText
    android:id="@+id/input_username"
    android:hint="@string/username_hint"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    />
```

Sedangkan untuk menghubungkan pada Activity dilakukan pada method `onCreate()`
dan disimpan pada variabel sesuai tipe Component. Jika pada layout `<EditText
/>` maka harus disimpan juga dengan tipe `EditText` atau parent yang sama. Pada
versi Android sekarang **TIDAK DIBUTUHKAN** proses casting tipe data lagi.
Contoh:

```java
public class MainActivity extends AppCompat {
  private EditText usernameInput;

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
    usernameInput = findViewById(R.id.input_username);
  }
}
```

> **Catatan**: Silahkan clone [Starter Code Mobile
> 04](https://github.com/polinema-mobile/2019-mobile04) terlebih dahulu, sebelum
> memulai praktikum.
