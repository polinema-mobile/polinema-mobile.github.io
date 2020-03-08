# RecyclerView Adapter

Untuk menampilkan data pada RecyclerView dibutuhkan adapter. Silahkan buka
project dengan menggunakan Android Studio dan ikuti langkah-langkah berikut
untuk melengkapi kode pada adapter.

- Bukalah class `TransactionAdapter`, class ini merupakan turunan dari class
 `RecyclerViewAdapter<TransactionAdapter.ViewHolder>`. Tambahkan kode berikut
 untuk mendefinisikan hal tersebut.

  ```java
  public class TransactionAdapter extends RecyclerView.Adapter<TransactionAdapter.ViewHolder> {

  }
  ```

- Generate sampai tidak dijumpai tanda-tanda error.

- Pada praktikum kali ini RecyclerView tidak hanya menampilkan data, tetapi
 dapat juga berinteraksi dengan mengguna. Untuk melakukan hal tersebut
 dibutuhkan sebuah `interface`. Bacaan lebih lanjut silahkan buka [tautan
 berikut](https://antonioleiva.com/recyclerview-listener/).

  ```java
  public interface OnItemTransactionListener {
      void onTransactionClicked(int index, Transaction item);
  }
  ```

  **Catatan**: Letakkan definisi interface tersebut di bawah definisi class
  `TransactionAdapter`.

- Tambahkan atribut list data yang akan ditampilkan.

  ```java
  private List<Transaction> items;
  ```

- Tambahkan sebuah listener yang telah didefinisikan sebelumnya.

  ```java
  private OnItemTransactionListener listener;
  ```

- Generate constructor yang membutuhkan dua parameter, list model dan listener.

  ```java
  public TransactionAdapter(List<Transaction> items, OnItemTransactionListener listener) {
      this.items = items;
      this.listener = listener;
  }
  ```

- Pada inner class `ViewHolder` definisikan atribut-atribut berikut.

  ```java
  TextView descriptionText;
  TextView amountText;
  ```

- Lakukan binding pada constructor `ViewHolder` dengan kode berikut.

  ```java
  public ViewHolder(@NonNull View itemView) {
      super(itemView);
      descriptionText = itemView.findViewById(R.id.text_description);
      amountText = itemView.findViewById(R.id.text_amount);
  }
  ```

- Untuk memudahkan proses bind ViewHolder dan data serta penambahan interaksi
 buatlah method seperti pada kode berikut.

  ```java
  public void bind(final int index, final Transaction item) {
      descriptionText.setText(item.getDescription());
      amountText.setText(String.valueOf(item.getAmount()));
      // TODO: Tambahkan interaksi click di sini
  }
  ```

- Pada method bind, lakukan pengaturan click listener.

  ```java
  itemView.setOnClickListener(new View.OnClickListener() {
      @Override
      public void onClick(View v) {
          listener.onTransactionClicked(index, item);
      }
  });
  ```

- Lengkapi ketiga method yang wajib diimplementasikan dalam adapter
 RecyclerView.

  ```java
  @NonNull
  @Override
  public ViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
      View view = LayoutInflater.from(parent.getContext())
              .inflate(R.layout.item_transaction, parent, false);
      return new ViewHolder(view);
  }
  ```

  ```java
  @Override
  public void onBindViewHolder(@NonNull ViewHolder holder, int position) {
      Transaction item = items.get(position);
      holder.bind(position, item);
  }
  ```

  ```java
  @Override
  public int getItemCount() {
      return (items != null) ? items.size() : 0;
  }
  ```

