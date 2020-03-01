# RecyclerView Sederhana

Pada praktikum kali ini, kita akan memahami bagaimana untuk membuat RecyclerView
yang sederhana dengan sebuah TextView.

- Silahkan buka starter code yang telah disediakan.
- Buka file `activity_simple.xml`, pada file ini terdapat RecyclerView yang
 digunakan untuk menampilkan data yang berupa list. Tampilan satu buah data
 diatur dalam file `item_simple.xml`.

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="8dp"
    android:orientation="horizontal"
    >

    <TextView
      android:id="@+id/text_name"
      android:layout_width="match_parent"
      android:layout_height="wrap_content"
      android:textSize="24sp"
      tools:text="Club Name"
      />
  </LinearLayout>
  ```

- Untuk menampilkan data ke dalam sebuah RecyclerView dibutuhkan adapter.
 Sebuah Adapter harus diturunkan dari class `RecyclerView.Adapter`. Perhatikan
 class `SimpleAdapter`. Selain itu, sebuah adapter membutuhkan `ViewHolder`.
 ViewHolder bertugas untuk menghubungkan data dengan tampilan layout.

- Pada sebuah Adapter umumnya menyimpan model yang nanti ditampilkan ke dalam
 RecyclerView. Model yang digunakan dalam SimpleAdapter adalah `List<String>`
 dikarenakan hanya dibutuhkan satu informasi text yang ditampilkan pada
 `TextView`.

- Sebuah Adapter harus mengimplementasikan 3 buah methods, yaitu:
    - `onCreateViewHolder`: bertugas untuk menginstansiasi ViewHolder
    - `onBindViewHolder`: menghubungkan data dengan ViewHolder
    - `getItemCount`: mengembalikan jumlah data

- Bukalah file `SimpleActivity.java`, pada class ini terdapat sebuah RecyclerView.
 Supaya RecyclerView dapat digunakan, dibutuhkan LayoutManager. LayoutManager
 yang didukung dalam RecyclerView ada 3, yaitu:
  - LinearLayoutManager
  - GridLayoutManager
  - StaggeredLayoutManager

- Pada class `SimpleActivity`, data yang ditampilkan disimpan dalam variabel
 `teams`. Data tersebut dimasukkan ke dalam adapter yang kemudian ditampilkan
 dengan layout linear.

> **Catatan**: Pahami konsep RecyclerView sebelum melanjutkan ke praktikum
> selanjutnya.
