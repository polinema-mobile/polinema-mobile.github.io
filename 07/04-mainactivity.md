# MainActivity

Pada aplikasi ini dibutuhkan custom `Application`. Hal ini
bertujuan supaya data yang diolah tidak hilang (data in memory). Penggunaan
class `Application` umumnya digunakan untuk singleton atau shared variable.
Pada `AndroidManifest.xml` ditambahkan juga modifikasi yang merujuk ke definisi
class `Application`. Perhatikan pada tag `application` atribut `name` pada kode
berikut.

```xml
<application
    android:name=".Application"
    android:allowBackup="true"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/AppTheme"
    >
    ...
    ...
</application>
```

Langkah-langkah praktikum dapat dijabarkan sebagai berikut

- Bukalah class `Application` dan tambahkan informasi nama pemilik `Account`.
  Perhatikan pada method `onCreate()` dan instansiasi atribut `account` dengan
  nama anda.

  ```java
  @Override
  public void onCreate() {
      super.onCreate();
      account = new Account("Budi");
  }
  ```

- Bukalah class `MainActivity`, pada class ini akan digunakan untuk berinteraksi
  dengan `RecyclerView` sehingga harus mengimplementasikan interface
  `TransactionAdapter.onTransactionItemClicked`. Tambahkan definisi implementasi
  interface pada class `MainActivity`.

  ```java
  public class MainActivity extends AppCompatActivity
    implements TransactionAdapter.OnItemTransactionListener {

  }
  ```

- Generate method `onTransactionClicked()` yang dibutuhkan.

- Tampilkan informasi pada `welcomeText` dan balanceText dengan kode berikut.

  ```java
  welcomeText.setText(String.format("Welcome %s", account.getName()));
  balanceText.setText(String.valueOf(account.getBalance()));
  ```

- Lengkapi inisialisasi `RecyclerView` adapter serta layout manager.

  ```java
  adapter = new TransactionAdapter(account.getTransactions(), this);
  transactionsView.setAdapter(adapter);

  RecyclerView.LayoutManager layoutManager = new LinearLayoutManager(this);
  transactionsView.setLayoutManager(layoutManager);
  ```
