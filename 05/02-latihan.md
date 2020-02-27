# Latihan

1. Silahkan Fork repositori berikut ini ke repositori anda :[Starter Code Latihan](https://github.com/polinema-mobile/intent-score-challenge)
2. Setelah melakukan fork silahkan clone repositori tersebut ke komputer anda.
3. Silahkan membuka setiap activity pada kode program android tersebut dan perhatikan tag //TODO yang diberikan pada masing masing activity
4. Main Activity :

   1. Validasi Input Home Team
   2. Validasi Input Away Team
   3. Ganti Logo Home Team
   4. Ganti Logo Away Team
   5. Next Button Pindah Ke MatchActivity

5. Match Activity :
   1. Menampilkan detail match sesuai data dari main activity
   2. Tombol add score baik pada home team maupun away team membuka ScorerActivity
   3. Pada Scorer Activity di isikan nama pencetak gol
   4. MatchActivity Menerima kembali intent ini dan menyimpan nama pencetak gol serta menambah score sesuai dengan tim yang dipilih
   5. Tombol Cek Result menghitung pemenang dari kedua tim dan mengirim nama pemenang beserta detail pencetak gol ke ResultActivity, jika seri di kirim text "Draw"
6. Result Activity :
   1. Menampilkan pemenang dari pertandingan, data didapat dari MatchActivity


> **Referensi**: Silahkan baca [referensi
> berikut](https://stackoverflow.com/questions/920306/sending-data-back-to-the-main-activity-in-android)
> untuk mengimplementasikan di atas. Gunakan method `startActivityForResult()`
> untuk memanggil `Activity` dan gunakan method `setResult()` untuk mengirimkan
> hasil kembali ke `Activity`.
