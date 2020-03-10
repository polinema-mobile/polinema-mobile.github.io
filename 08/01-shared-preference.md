# SharedPreferences

Jika anda membutuhkan sekumpulan data dengan tipe key-value yang ingin anda
simpan dalam aplikasi mobile, anda dapat menggunakan `SharedPreferences` API.
Data dalam `SharedPreferences` akan disimpan dalam sebuah file yang mengandung
key-value secara berpasangan. Setiap file ini dikelola oleh Android framework
yang aksesnya dapat diatur secara private atau dibagikan.

Selain digunakan untuk penyimpanan data sederhana, pemanfaatan
`SharedPreferences` digunakan juga untuk menyimpan pengaturan aplikasi. Dengan
ini pengguna dapat mengatur aplikasi sesuai dengan keinginan.

## Instansiasi SharedPreferences

Ada berbagai cara untuk mendapatkan akses SharedPreferences, antara lain:

- `getSharedPreferences()` Jika anda membutuhkan lebih dari satu file yang
 diidentifikasi berdasarkan nama, dimana diatur pada parameter pertama.

   ```java
   Context context = getActivity();
   SharedPreferences pref = context.getSharedPreferences("nama pref", Context.MODE_PRIVATE);
   ```

   > **Catatan**: `Context.MODE_PRIVATE` menandakan bahwa pengaturan ini tidak
   > dibagikan ke aplikasi lain.

- `getPreferences()` Anda dapat menggunakan cara ini, jika anda membutuhkan
   sebuah pengaturan file dalam activity. Cara ini tidak membutuhkan penamaan,
   dikarenakan akan mengambil secara default yang berkaitan dengan activity.

  ```java
  SharedPreferences pref = getActivity().getPreferences(Context.MODE_PRIVATE);
  ```

- `PreferenceManager` dapat digunakan sebagai cara alternatif lainnya.

## Menyimpan Data

Untuk menyimpan data ke dalam SharedPreferences dibutuhkan class `Editor` yang
bisa didapatkan dari method `edit()` dari instansiasi variable
SharedPreferences.

```java
SharedPreferences preference = PreferenceManager.getDefaultSharedPreferences(context);
Editor editor = preference.edit();

editor.putBoolean("key_name", true);
editor.putString("key_name", "string value");
editor.putInt("key_name", 1);
editor.putFloat("key_name", 1.2f);
editor.putLong("key_name", 1);

editor.apply();

// alternatif chaining

preference.edit().putString("key_name", "string value").apply();
```

**Catatan**: Jangan lupa untuk memanggil fungsi `apply()` untuk menyimpan ke
SharedPreferences.

## Mengambil Data

Data dapat diambil menggunakan method get tipe data seperti berikut:

```java
// get value with default value
preference.getString("key_name", null);
preference.getInt("key_name", -1);
preference.getFloat("key_name", -1f);
preference.getLong("key_name", -1);
preference.getBoolean("key_name", false);
```

## Menghapus Data

Data dihapus dengan menggunakan perintah `remove` dengan parameter key sedangkan
untuk menghapus semua dapat menggunakan `clear()`.

```java
editor.remove("name");
editor.remove("email");
editor.apply();

// atau
editor.remove("name").apply();
```

```java
editor.clear();
editor.apply();

// atau
editor.clear().apply();
```
