# Grid RecyclerView

Pada praktikum kali ini, akan diperkenalkan bagaimana caranya membuat
RecyclerView dalam tampilan Grid. Secara teori, yang diperlukan adalah merubah
jenis LayoutManager yang akan digunakan, yaitu `GridLayoutManager`.

## Langkah-langkah

- Bukalah class `GridAdapter`, definisikan class tersebut merupakan turunan dari
 `RecyclerView.Adapter` serta ViewHolder seperti pada praktikum sebelumnya.

- Perbedaan dengan Adapter sebelumnya hanya terletak pada layout item yang
 digunakan yaitu: `item_grid.xml`.

- Bukalah class `GridActivity`, perbedaan dengan praktikum sebelumnya kali ini
 digunakan `GridAdapter` dan LayoutManager dengan jenis `GridLayoutManager`.
 Sehingga kodenya menjadi:

  ```java
  RecyclerView teamsView = findViewById(R.id.rv_teams);

  List<TeamLogo> teams = new ArrayList<>();
  teams.add(new TeamLogo("https://upload.wikimedia.org/wikipedia/en/thumb/0/0c/Liverpool_FC.svg/360px-Liverpool_FC.svg.png", "Liverpool"));
  teams.add(new TeamLogo("https://upload.wikimedia.org/wikipedia/en/thumb/e/eb/Manchester_City_FC_badge.svg/360px-Manchester_City_FC_badge.svg.png", "Man. City"));

  GridAdapter adapter = new GridAdapter(this, teams);
  teamsView.setAdapter(adapter);

  RecyclerView.LayoutManager layoutManager = new GridLayoutManager(this, 2);
  teamsView.setLayoutManager(layoutManager);
  ```

- Lengkapi menu kemudian jalankan aplikasi. Perhatikan perbedaan tampilan yang
 terjadi.
