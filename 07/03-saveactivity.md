# SaveActivity

Untuk operasi tambah dan update dapat ditangani pada tampilan yang sama. Untuk
membedakan operasinya, dapat digunakan *request code* yang berbeda. Silahkan
ikuti langkah-langkah berikut untuk mengimplementasikan `SaveActivity`. Pada
class ini digunakan konsep komunikasi `Intent` dengan menggunakan `Parcelable`.

- Bukalah class `SaveActivity` dan amati dengan seksama.
- Lengkapi proses pengambilan data dari intent pada method `onCreate()`

  ```java
  Bundle extras = getIntent().getExtras();
  if (extras != null) {
      item = extras.getParcelable(MainActivity.TRANSACTION_KEY);
      index = extras.getInt(MainActivity.INDEX_KEY, 0);
      descriptionInput.setText(item.getDescription());
      amountInput.setText(String.valueOf(item.getAmount()));
      if (item.getType() == Transaction.Type.DEBIT) {
          typeRadioGroup.check(R.id.radio_debit);
      } else if (item.getType() == Transaction.Type.CREDIT) {
          typeRadioGroup.check(R.id.radio_credit);
      }
  }
  ```

- Untuk memudahkan proses pengambilan nilai jenis transaksi, buatlah private
 method `getCheckedType()`

  ```java
  private Transaction.Type getCheckedType() {
      if (typeRadioGroup.getCheckedRadioButtonId() == R.id.radio_debit) {
          return Transaction.Type.DEBIT;
      } else if (typeRadioGroup.getCheckedRadioButtonId() == R.id.radio_credit) {
          return Transaction.Type.CREDIT;
      }
      return Transaction.Type.EMPTY;
  }
  ```

- Lengkapi proses submit untuk mengambil nilai dari form dan mengembalikan
 kepada `Activity` yang memanggil `SaveActivity`.

  ```java
  String description = descriptionInput.getText().toString();
  int amount = Integer.parseInt(amountInput.getText().toString());
  Transaction.Type type = getCheckedType();

  item.setDescription(description);
  item.setAmount(amount);
  item.setType(type);

  Intent intent = new Intent();
  intent.putExtra(MainActivity.TRANSACTION_KEY, item);
  intent.putExtra(MainActivity.INDEX_KEY, index);
  setResult(RESULT_OK, intent);
  finish();
  ```
