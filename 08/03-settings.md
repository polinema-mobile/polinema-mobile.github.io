# Settings

# Settings

Anda dapat mengatur kebutuhan aplikasi sesuai dengan kebutuhan pengguna.
Pengaturan ini akan disimpan dalam `SharedPreferences`. Untuk memudahkan, anda
dapat menggunakan library `androidx.preference`. Silahkan tambahkan library ke
dalam file `build.gradle` (app).

```
implementation 'androidx.preference:preference:1.1.0'
```

## Hirarki dan Widget

Untuk membangun pengaturan pada pengguna. Anda tinggal mendefinisikan sebuah
skema yang dibungkus dalam `PreferenceScreeen`. Untuk mengelompokkan pengaturan
anda dapat menggunakan `PreferenceCategory`. Selain itu dalam pengaturan juga
dikenal bermacam widget yang umum digunakan antara lain:

- `CheckBoxPreference`
- `EditTextPreference`
- `ListPreference`
- `MultiSelectListPreference`
- `SeekbarPreference`
- `SwitchPreference`

Penggunaan widget yang dibutuhkan, disesuaikan dengan jenis data yang akan
disimpan.

## Pembuatan Pengaturan

Untuk menampilkan pengaturan yang diinginkan, buatlah sebuah fragment yang
diturunkan dari class `PreferenceFragmentCompat`. Dalam class tersebut, override
method `onCreatePreferences` dan atur resource file xml yang dibutuhkan dengan
menggunakan method `setPreferencesFromResource(R.xml.nama_pref, rootKey)`.

## Langkah Percobaan

Pada aplikasi sebelumnya akan ditambahkan fitur untuk menyimpan username
berdasarkan preferensi user pada halaman settings.

- Tambahkan library preference yang dibutuhkan.

  ```
  implementation 'androidx.preference:preference:1.1.0'
  ```

- Untuk membuat halaman pengaturan dibutuhkan layout. Tambahkan file
 `preferences.xml` pada folder `res/xml`. Isinya sebagai berikut:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <preferencescreen
      xmlns:app="http://schemas.android.com/apk/res-auto"
      >

      <checkboxpreference
          app:defaultvalue="false"
          app:key="key_keep_username"
          app:title="keep username"
          />
  </preferencescreen>
  ```

- Tambahkan class baru dengan nama `SettingsFragment`. Atur class ini sebagai
 turunan dari `PreferenceFragmentCompat`.

  ```java
  public class SettingsFragment extends PreferenceFragmentCompat {

  }
  ```

  > **Catatan**: Untuk API 29, penggunaan PreferenceActivity sudah *deprecated*.

- Letakkan cursor anda pada definisi class dan tekan shortcut `Alt + Enter`.
 Pilih menu **Implements methods**.

- Pada method `onCreatePreferences()` atur tampilan layout berdasarkan resource
 xml `preferences.xml` yang telah dibuat.

  ```java
  @Override
  public void onCreatePreferences(Bundle savedInstanceState, String rootKey) {
      setPreferencesFromResource(R.xml.preferences, rootKey);
  }
  ```

- Buatlah activity baru, dan beri nama `SettingsActivity`. Activity ini akan
 digunakan untuk menampilkan Fragment yang telah dibuat.

- Bukalah file `activity_settings.xml` kemudian pindah ke mode design.
- Carilah komponen fragment kemudian drag ke dalam desain. Pilih fragment
 `SettingsFragment`.

- Atur fragment sehingga layout memenuhi layar desain.
- Bukalah file `menu_main.xml` dan atur nilainya sehingga hasil akhirnya menjadi
 berikut.

  ```xml
  <menu
      xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:app="http://schemas.android.com/apk/res-auto"
      xmlns:tools="http://schemas.android.com/tools"
      tools:context="com.dhanifudin.cashflow.MainActivity"
      >
      <item
          android:id="@+id/action_settings"
          android:orderInCategory="100"
          android:title="@string/action_settings"
          app:showAsAction="never"
          />
      <item
          android:id="@+id/action_logout"
          android:orderInCategory="101"
          android:title="Logout"
          app:showAsAction="never"
          />
  </menu>
  ```

- Buka activity `MainActivity` kemudian implementasikan logika untuk menampilkan
 `SettingsActivity` pada method `onOptionsItemSelected()`. Letakkan logika pada
 blok `R.id.action_settings`.

  ```java
  Intent intent = new Intent(this, SettingsActivity.class);
  startActivity(intent);
  return true;
  ```

- Tambahkan logika untuk melakukan proses logout.

  ```java
  else if (id == R.id.action_logout) {
      session.logout();
      Intent intent = new Intent(this, LoginActivity.class);
      startActivity(intent);
      finish();
      return true;
  }
  ```
- Buka kembali class `Session`. Dibutuhkan penambahan logika untuk mempermudah
 mengakses nilai preferensi pengguna. Tambahkan konstanta untuk key keep
 username.

  ```java
  private static final String KEEP_USERNAME_KEY = "key_keep_username";
  ```

- Tambahkan getter untuk keep username

  ```java
  public boolean isKeepUsername() {
      return preferences.getBoolean(KEEP_USERNAME_KEY, false);
  }
  ```
- Buka kembali activity `LoginActivity`, tambahkan logika untuk menuliskan
 username ketika login berhasil.

  ```java
  if (success) {
      if (session.isKeepUsername()) {
          session.setUsername(username);
      }

      // logika code yang lain...
      // ...
  }
  ```

- Pada method `onCreate()` activity `LoginActivity` tambahkan logika untuk
 mengatur nilai username jika opsi keep username dicentang.

  ```java
  if (session.isKeepUsername()) {
      usernameInput.setText(session.getUsername());
  }
  ```

- Jalankan aplikasi serta uji apakah fitur sudah sesuai. Jangan lupa untuk
 melakukan commit dan push ke repository masing-masing.

