# RecyclerView FastAdapter

Selain menggunakan cara official untuk mengimplementasikan RecyclerView,
terdapat beberapa alternatif lain. Library tambahan dapat ditambahkan untuk
mempermudah implementasi RecyclerView, yaitu:

- [FastAdapter](https://github.com/mikepenz/FastAdapter)
- [BRVAH BaseRecyclerViewAdapterHelper](http://www.recyclerview.org/) (tidak
 dibahas dalam modul ini.)

## FastAdapter

FastAdapter membantu menyederhanakan proses untuk penggunaan RecyclerView.
Dengan library ini, kompleksitas adapter dapat dikurangi. Sehingga pengembang
dapat fokus pada logika aplikasi. Selain itu library ini bertujuan juga untuk
mengurangi kesalahan yang mungkin akan terjadi. Untuk menggunakan library
FastAdapter, silahkan tambahkan dependency pada file `build.gradle`.

```groovy
implementation 'com.mikepenz:fastadapter:3.3.1'
```

> **Catatan**: Versi terakhir yang mendukung bahasa pemrograman Java adalah `3.3.1`.

## Demo

Fitur-fitur yang didukung, dapat dilihat pada [Google Play](https://play.google.com/store/apps/details?id=com.mikepenz.fastadapter.app).

## Langkah-langkah

- Tambahkan library FastAdapter pada file `build.gradle`

  ```groovy
  implementation 'com.mikepenz:fastadapter-commons:3.3.1'
  ```

- Untuk menggunakan FastAdapter dengan cara membuat sebuah class yang diturunkan
 dari `AbstractItem` yang mempunyai definisi generic pemodelan data dan
 ViewHolder. Silahkan buat sebuah class dengan kode berikut

  ```java
  public class TeamItem extends AbstractItem<TeamItem, TeamItem.ViewHolder> {

  }
  ```

- Generate (`Alt + Enter`) inner class `LogoItem.ViewHolder` sehingga struktur class menjadi
 berikut.

  ```java
  public class TeamItem extends AbstractItem<TeamItem, TeamItem.ViewHolder> {

    public class ViewHolder {

    }
  }
  ```

- Tambahkan definisi class `ViewHolder` sebagai turunan dari `FastAdapter.ViewHolder<TeamItem>`

  ```java
  public class ViewHolder extends FastAdapter.ViewHolder<TeamItem> {

  }
  ```

- Pindahkan cursor pada definisi class `ViewHolder`, generate `Implements methods`
- Pindahkan cursor pada definisi class `ViewHolder`, generate `Create constructor matching super`

- Pindahkan cursor pada definisi class `TeamItem`, generate (`Alt + Enter`)
 abstract method dengan mengimplementasikan method
 pada pada class turunan `AbstractItem`.

- Tambahkan atribut ke dalam class `TeamItem` seperti berikut

  ```java
  private String logo;
  private String name;
  ```

- Generate constructor dengan shortcut `Cmd + N` (mac) atau `Alt + Insert` (windows atau linux)

- Tambahkan atribut berkaitan dengan tampilan layout pada `ViewHolder`. Sisipkan
 kode berikut pada inner class `ViewHolder`.

  ```java
  ImageView logoImage;
  TextView nameText;
  ```
- Binding atribut dengan tampilan pada constructor `ViewHolder` sehingga kode
 menjadi seperti berikut.

  ```java
  public ViewHolder(View itemView) {
      super(itemView);
      logoImage = itemView.findViewById(R.id.image_logo);
      nameText = itemView.findViewById(R.id.text_name);
  }
  ```

- Lakukan bind model ke layout pada method `bindView()`, sehingga kodenya
 menjadi berikut.

  ```java
  @Override
  public void bindView(TeamItem item, List<Object> payloads) {
      Picasso.get().load(item.logo).into(logoImage);
      nameText.setText(item.name);
  }
  ```

- Implementasikan kode berikut pada method `unbindView()`

  ```java
  @Override
  public void unbindView(TeamItem item) {
      logoImage.setImageBitmap(null);
      nameText.setText(null);
  }
  ```

- Implementasikan pada method `getViewHolder()` untuk menginstansiasi
 ViewHolder. Sisipkan kode berikut.

  ```java
  return new ViewHolder(v);
  ```

- Pada method `getType()` implementasikan untuk mendapatkan ID unique. Dapat
 menggunakan id dari recyclerview.

  ```java
  return R.id.rv_teams;
  ```

- Sedangkan pada method `getLayoutRes()` anda cukup mendefinisikan layout item
 yang akan digunakan.

  ```java
  return R.layout.item_logo;
  ```

- Implementasi model item dengan menggunakan `FastAdapter` telah selesai.
 Sebagai langkah berikutnya, tinggal memasukan model tersebut ke dalam
 `FastAdapter`.

- Buatlah Activity baru dan beri nama `FastAdapterActivity`.

- Sisipkan kode berikut pada method `onCreate()` untuk menampilkan RecyclerView dengan FastAdapter.

  ```java
  RecyclerView teamsView = findViewById(R.id.rv_teams);

  ItemAdapter<TeamItem> itemAdapter = new ItemAdapter<>();
  FastAdapter<IItem> fastAdapter = FastAdapter.with(itemAdapter);

  List<TeamItem> teams = new ArrayList<>();
  teams.add(new TeamItem("https://upload.wikimedia.org/wikipedia/en/thumb/0/0c/Liverpool_FC.svg/360px-Liverpool_FC.svg.png", "Liverpool"));
  teams.add(new TeamItem("https://upload.wikimedia.org/wikipedia/en/thumb/e/eb/Manchester_City_FC_badge.svg/360px-Manchester_City_FC_badge.svg.png", "Man. City"));


  itemAdapter.add(teams);
  teamsView.setAdapter(fastAdapter);

  RecyclerView.LayoutManager layoutManager = new LinearLayoutManager(this);
  teamsView.setLayoutManager(layoutManager);
  ```

- Tambahkan menu pada `MainActivity` untuk memanggil `FastAdapterActivity`.
