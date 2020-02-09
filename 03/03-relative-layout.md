# Membuat aplikasi dengan relative layout

## Praktikum

- Bukalah project **RelativeLayout** kemudian ubah default layout pada
  `activity_main.xml` menggunakan layout `RelativeLayout`. Sehingga kode program
  dan tampilan berubah seperti gambar di bawah ini.

!['relativelayout'](images/02-relative-layout.png)

> **RelativeLayout** adalah layout yang menempatkan suatu item relative terhadap parent atau item lain pada UI.

- Untuk mencobanya, tambahkan dua buah button pada layout. Anda dapat menambahkan button dengan menggunakan **pallet** yang ada di sebelah kiri tampilan design. Kemudian jangan lupa menghapus `TextView` "hello world".

!['relativelayout'](images/02-relative-layout-button.png)
!['relativelayout'](images/02-relative-layout-button-drag.png)

- Ubahlah teks dan lebar dari button sehingga menjadi seperti gambar di bawah ini.

!['relativelayout'](images/02-relative-layout-button-width.png)

> Untuk mengubah teks dan lebar button, Anda dapat menggunakan **text mode** atau pada **design mode** dengan mengklik button dan mengganti properties di bagian kanan editor.

- Selanjutnya, ubahlah tampilan dengan mengubah kode program melalui text mode sehingga menjadi seperti gambar di bawah ini.

!['relativelayout'](images/02-relative-layout-buttonpos.png)

Perhatikan pada kode program tersebut. Sebuah item di posisikan pada layout dengan memberikan detail posisinya yang relative terhadap parent.

Pada _button_ pertama ini mempunyai _properties_

- `android:layout_alignParentStart="true"`
- `android:layout_alignParentLeft="true"`
- `android:layout_alignParentTop="true"`

Dengan konfigurasi properties seperti di atas, sebuah item akan diposisikan di sebelah kiri atas.

- untuk lebih memahami relative layout buatlah layout baru seperti pada gambar dibawah ini.

!['relativelayout'](images/02-relative-layout-button-baru.png)

- Berdasarkan percobaan di atas cobalah membuat layout yang sebelumnya menggunakan _linear layout_ dengan _relative layout_.

- Commit semua perubahan yang telah anda lakukan, kemudian push ke akun GitHub
  anda!
