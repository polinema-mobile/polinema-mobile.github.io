# Latihan 2

## Persiapan

Bukalah project **Aplikasiku** pada starter code yang sudah disediakan, dalam
project ini sudah disediakan screen layout desain serta asset yang akan
digunakan untuk membuat aplikasi.

## Screen Layout Desain

Screen layout desain sudah disediakan di dalam starter code layout ini. Layout
dapat Anda lihat pada folder `design`. Untuk melihat isi folder design, ganti
view pada Android Studio menjadi `project`

![folder design](images/03folderdesign2.png)

## Cara Import Drawable

Untuk mengubah desain layout menjadi layout android xml, diperlukan asset berupa
potongan gambar yang sudah disesuaikan ukurannya. Resolusi asset pada Android
mulai dari `hdpi`, `mdpi`, `xdpi`, `xxhdpi`, dan `xxxhdpi`. Untuk semua layout
pada folder design sudah dipotongkan dan disiapkan gambarnya di dalam starter
code.

Jika anda ingin mengetahui proses import drawable, sebagai informasi tambahan
proses untuk memasukkan aset gambar ke folder `res` pada Android Studio
dilakukan dengan cara berikut,

1. Buka tab Resource Manager
   ![resource manager](images/03resourcemanager.png)
2. Klik tombol `+`
   ![resource manager plus](images/03resourcemanagerplus.png)
3. Pilih menu import drawables
   ![import drawable](images/03imagedrawable.png)
4. Select semua folder kemudian klik open
   ![import](images/03importhdpo.png)
5. Pilih gambar yang akan di import kemudian klik import
   ![import again](images/03importhem.png)

## Cara Import Custom Font

Pada starter code juga sudah disediakan dua varian custom font yang dapat
digunakan pada layout android. Untuk mengimport custom font dilakukan dengan
langkah langkah berikut,

1. Klik kanan pada folder `res` kemudian pilih **New -> Android Resource Directory**

![import font](images/03resourcedirectory.png)

2. Pada Resource type, pilih `font`
   ![font](images/03fontfolder.png)

3. Copy dan paste custom font yang Anda miliki ke dalam folder font yang Anda
   buat sebelumnya.

   > **Catatan**: Font yang Anda copy kedalam folder harus menggunakan huruf
   > kecil dan disambungkan dengan menggunakan underscore jika lebih dari satu
   > suku kata.

# Splashscreen

**Splash screen** merupakan tampilan awal yang pertama kali dibuka ketika
aplikasi dijalankan. Ada banyak aplikasi yang menggunakan splash screen, namun
ada juga yang tidak menggunakannya.

## Buka Main Activity

Bukalah file `MainActivity.java`, file ini akan kita jadikan sebagai splash
screen. Pada file `MainActivity.java`, Anda akan menemukan bahwa pada fungsi
onCreate, layout yang dipanggil atau di tampilkan adalah `activity_main.xml`.
Oleh karena itu, untuk mengubah tampilannya kita harus mengubah isi dari file
`activity_main.xml`

## Edit file activity_main.xml

Lakukan langkah langkah berikut untuk membuat splash screen. Desain yang
diinginkan untuk splash screen dapat Anda lihat pada folder `design`.

![splash](images/0304splash.png)

### Tambahkan Logo

1. Hapuslah `TextView` Hello World dari halaman activity_main.xml
2. Buatlah sebuah `ImageView` dan atur posisinya di tengah layar dengan menggunakan constraint layout

```xml
  <ImageView
      android:id="@+id/imageView"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:layout_marginStart="8dp"
      android:layout_marginTop="8dp"
      android:layout_marginEnd="8dp"
      android:layout_marginBottom="8dp"
      android:src="@drawable/ic_logo"
      app:layout_constraintBottom_toBottomOf="parent"
      app:layout_constraintEnd_toEndOf="parent"
      app:layout_constraintStart_toStartOf="parent"
      app:layout_constraintTop_toTopOf="parent" />
```

### Tambahkan Text

1. Buatlah sebuah `TextView` dengan font **montsterrat semi bold** dan ganti
   teks sesuai dengan nama aplikasi yang ingin anda buat.

   > Jangan menggunakan teks **DTS Kominfo** sebagai teks splash screen.

2. Letakkan `TextView` tersebut dibawah logo dengan jarak 8dp.

```xml
  <TextView
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:layout_marginStart="8dp"
      android:layout_marginTop="8dp"
      android:layout_marginEnd="8dp"
      android:fontFamily="@font/montserrat_semi_bold"
      android:textSize="20sp"
      android:text="@string/logo_text"
      app:layout_constraintEnd_toEndOf="parent"
      app:layout_constraintStart_toStartOf="parent"
      app:layout_constraintTop_toBottomOf="@+id/imageView" />
```

> Commit semua perubahan yang telah anda lakukan, kemudian push ke akun GitHub
> anda!

# Welcome Activity

Welcome activity adalah activity yang di jalankan setelah splash screen. Pada activity welcome ini, akan ditampilkan secara singkat fitur-fitur aplikasi. Berikut ini screenshoot tampilan aplikasi yang diharapkan.

![welcome](images/welcomeactivity.png)

## Edit File activity_welcome_slide.xml

Langkah selanjutnya adalah mengubah isi file `activity_welcome_slide.xml`. Jenis
layout yang digunakan adalah constraint layout. Pastikan layout xml dimulai
dengan tag berikut ini. Tambahkan background warna putih.

```xml
<androidx.constraintlayout.widget.ConstraintLayout
  xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#FFFFFF"
    tools:context=".WelcomeSlide">

</androidx.constraintlayout.widget.ConstraintLayout>
```

Pada desain layout terdapat beberapa komponen, yaitu:

1. Gambar Character dengan Calender
2. Text Welcome
3. Sub Text Welcome
4. Text Login
5. Background Footer Merah

### Tambahkan Gambar

Tambahkan gambar dengan nama `ic_eventlist` dari folder drawable ke layout

```xml
<ImageView
  android:id="@+id/calendar"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
  android:src="@drawable/ic_eventlist"
  app:layout_constraintTop_toTopOf="parent"
  app:layout_constraintLeft_toLeftOf="parent"
  app:layout_constraintRight_toRightOf="parent"
  android:layout_marginTop="30dp"
  />
```

Perhatikan penamaan **id** dan **constraint** dari image

![image](images/0305layout2.png)

## Tambahkan Text

Tambahkan sebuah `TextView` dengan id `welcome_text`. Ganti isi teks dengan
sesuai keinginan anda, sebagai contoh: **Welcome To DTS VSGA**

```xml
<TextView
  android:id="@+id/welcome_text"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
  android:textSize="24sp"
  android:textColor="#313131"
  android:text="Welcome To DTS VSGA"
  app:layout_constraintTop_toBottomOf="@id/calendar"
  app:layout_constraintLeft_toLeftOf="parent"
  app:layout_constraintRight_toRightOf="parent"
  android:fontFamily="@font/montserrat_semi_bold"
  />
```

Perhatikan bagaimana `TextView` disusun dan bagaimana cara mengganti font serta warna dari `TextView`.

![welcometext](images/0305welcometext.png)

## Tambahkan Sub Text

Tambahkan sebuah sub text baru di bawah `welcome_text` dengan id `sub_welcome`

```xml
<TextView
  android:id="@+id/sub_welcome"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
  android:textColor="#313131"
  android:text="What is going to happen tomorrow ?"
  app:layout_constraintTop_toBottomOf="@+id/welcome_text"
  app:layout_constraintLeft_toLeftOf="parent"
  app:layout_constraintRight_toRightOf="parent"
  android:fontFamily="@font/montserrat_light"
  />
```

![subtext](images/0305subtext.png)

## Tambahkan Gambar Footer

Tambahkan gambar footer dengan membuat sebuah `ImageView` dengan id
`background_satu`. Perhatikan bahwa footer memiliki constraint ke parent bottom
dan menggunakan `scaleType` dengan value `fitXY`.

```xml
<ImageView
    android:id="@+id/background_satu"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:scaleType="fitXY"
    android:src="@drawable/bg_red"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent" />
```

![footer](images/0305footer.png)

## Tambahkan Text Login

Buatlah sebuah `TextView` dengan id `login_text`. Ganti font dengan `montserrat_light`, `textSize` sebesar `18sp` dan `textColor` dengan warna `#FFFFFF`

```xml
<TextView
    android:id="@+id/login_text"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintLeft_toLeftOf="parent"
    app:layout_constraintRight_toRightOf="parent"
    android:layout_marginBottom="72dp"
    android:textColor="#FFFFFF"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Login"
    android:textSize="18sp"
    android:fontFamily="@font/montserrat_light"
    />
```

![login](images/0305login.png)

> Commit semua perubahan yang telah anda lakukan, kemudian push ke akun GitHub
> anda!

# Form

Pada praktikum kali ini akan dibuat beberapa activity, yaitu:

1. LoginActivity
2. ResetPasswordActivity
3. ForgotPasswordActivity
4. SuccessLoginActivity
5. SuccessResetPasswordActivity

## Membuat LoginActivity

Langkah selanjutnya adalah melakukan desain layout pada file
`activity_welcome_back.xml`. Berikut ini merupakan screenshot tampilan aplikasi
yang diharapkan.

![Sign In](images/Sign%20In.png)

### Edit activity_login.xml

Untuk membuat form login seperti gambar diatas, Anda perlu mengubah isi dari
file `activity_login.xml`. Constraint layout digunakan pada layout
`activity_login.xml`. Pastikan layout xml dimulai dengan tag berikut ini.
Tambahkan background warna putih.

```xml
<androidx.constraintlayout.widget.ConstraintLayout
  xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:app="http://schemas.android.com/apk/res-auto"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:background="#FFFFFF"
  tools:context=".LoginActivity">

</androidx.constraintlayout.widget.ConstraintLayout>
```

Pada desain layout terdapat beberapa komponen yaitu:

1. Judul
2. Sub Judul
3. Username
4. Edit Text Username
5. Password
6. Edit Text Password
7. Text Forgot Password
8. Button Login

#### Tambahkan Judul

Tambahkan sebuah `TextView` untuk menulis judul.

```xml
<TextView
  android:id="@+id/welcome_back"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
  android:layout_marginLeft="24dp"
  android:fontFamily="@font/montserrat_semi_bold"
  android:text="Welcome Back"
  android:textColor="#313131"
  android:textSize="32sp"
  app:layout_constraintLeft_toLeftOf="parent"
  app:layout_constraintTop_toTopOf="parent"
  android:layout_marginTop="90dp"
  />
```

#### Tambahkan Sub Judul

Tambahkan sebuah sub text baru di bawah judul dengan id `sign_in` dengan menggunakan `TextView`

```xml
<TextView
    android:id="@+id/sign_in"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginLeft="24dp"
    android:layout_marginTop="8dp"
    android:fontFamily="@font/montserrat_light"
    android:text="@string/sign_in_to_continue"
    android:textColor="#9b9b9b"
    android:textSize="16sp"
    app:layout_constraintLeft_toLeftOf="parent"
    app:layout_constraintTop_toBottomOf="@id/welcome_back" />
```

#### Tambahkan Username

Tambahkan `TextView` sebagai label Username

```xml
<TextView
        android:id="@+id/reset_code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="20dp"
        android:layout_marginTop="48dp"
        android:text="Username"
        android:textColor="#313131"
        android:textSize="20sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/sign_in" />
```

#### Tambahkan EditText Username

Tambahkan `EditText` untuk pengisian Username

[//]: # "TODO : fix id edt_reset_code"

```xml
<EditText
        android:id="@+id/edt_reset_code"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:layout_marginRight="24dp"
        android:hint="Enter Your Email"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/reset_code"
        />
```

#### Tambahkan Password

Tambahkan label Password menggunakan `TextView`

[//]: # "TODO : fix id edt_reset_code"

```xml
<TextView
        android:id="@+id/new_password"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="20dp"
        android:layout_marginTop="8dp"
        android:text="Password"
        android:textColor="#313131"
        android:textSize="20sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/edt_reset_code" />
```

#### Tambahkan EditText Password

Tambahkan `EditText` untuk pengisian password.

```xml
<EditText
        android:id="@+id/edt_new_password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:layout_marginRight="24dp"
        android:hint="@string/enter_your_password"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/new_password" />
```

#### Tambahkan Text Forgot Password

Tambahkan teks **Forgot Password** yang dapat di-klik sebagai button bagi pengguna yang lupa password.

```xml
<TextView
        android:id="@+id/forgot_password"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="8dp"
        android:layout_marginRight="24dp"
        android:text="@string/forgot_password"
        android:textColor="#313131"
        android:textSize="18sp"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/edt_new_password"
        />
```

#### Buat Drawable button_red.xml

Tambahkan sebuah file pada package **res->drawable** dengan nama `button_red.xml`. Ganti isi file `button_red.xml` dengan kode berikut,

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape="rectangle">
    <solid android:color="#F96060" />
    <corners android:radius="5dp" />
</shape>
```

#### Tambahkan Button Login

Buat button untuk fungsi Log In. Pada button tersebut, ganti teks button menjadi **LOG IN**. Beri warna putih pada teks **LOG IN**.

```xml
<Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="24dp"
        android:layout_marginEnd="24dp"
        android:textSize="18sp"
        android:layout_marginBottom="200dp"
        android:background="@drawable/button_red"
        android:text="LOG IN"
        android:textColor="#FFFFFF"
        app:layout_constraintTop_toBottomOf="@id/forgot_password"
        android:layout_marginTop="80dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        />
```

## Membuat Activity Reset Password

### Edit activity_reset_password.xml

Untuk membuat form reset password seperti gambar diatas yaitu dengan mengubah isi file dari `activity_reset_password.xml`, pada layout ini akan digunakan constraint layout pastikan layout xml dimulai dengan tag berikut ini.

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
  xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:app="http://schemas.android.com/apk/res-auto"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  tools:context=".ResetPasswordActivity">
</androidx.constraintlayout.widget.ConstraintLayout>
```

Pada desain layout terdapat beberapa komponen yaitu:

1. Judul
2. Sub Judul
3. Reset Code
4. Edit Reset Code
5. New Password
6. Edit Text New Password
7. Confirm Password
8. Edit Confirm Password
9. Button Change Password

#### Tambahkan Judul

Tambahkan sebuah TextView untuk menulis judul

```xml
<TextView
        android:id="@+id/welcome_back"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:fontFamily="@font/montserrat_semi_bold"
        android:text="Reset Password"
        android:textColor="#313131"
        android:textSize="32sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:layout_marginTop="90dp"
        />
```

#### Sub Judul

Tambahkan sebuah sub judul baru di bawah judul untuk memberikan keterangan judul

```xml
<TextView
        android:id="@+id/sign_in"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:fontFamily="@font/montserrat_light"
        android:text="Reset code was sent to your email. Please enter the code and create new password."
        android:textColor="#9b9b9b"
        android:textSize="16sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@id/welcome_back" />
```

#### Tambahkan Reset Code

Tambahkan Text View untuk label reset code.

```xml
<TextView
        android:id="@+id/reset_code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="20dp"
        android:layout_marginTop="48dp"
        android:text="@string/reset_code"
        android:textColor="#313131"
        android:textSize="20sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/sign_in" />
```

#### Tambahkan Edit Text Reset Code

Tambahkan Edit Text untuk pengisian Reset Code

```xml
 <EditText
        android:id="@+id/edt_reset_code"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:layout_marginRight="24dp"
        android:hint="@string/enter_your_reset_code"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/reset_code"
        />
```

#### Tambahkan New Password

Tambahkan label New Password menggunakan TextView

```xml
<TextView
        android:id="@+id/new_password"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="20dp"
        android:layout_marginTop="8dp"
        android:text="@string/new_password"
        android:textColor="#313131"
        android:textSize="20sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/edt_reset_code" />
```

#### Tambahkan Edit Text New Password

Tambahkan EditText untuk pengisian password baru.

```xml
<EditText
    <EditText
        android:id="@+id/edt_new_password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:layout_marginRight="24dp"
        android:hint="@string/enter_your_password"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/new_password" />
```

#### Tambahkan Text Confirm Password

Tambahkan text label Confirm Password.

```xml
<TextView
        android:id="@+id/confirm_password"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="20dp"
        android:layout_marginTop="8dp"
        android:text="@string/confirm_password"
        android:textColor="#313131"
        android:textSize="20sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@id/edt_new_password"
        />
```

#### Tambahkan Edit Text Confirm Password

Tambahkan edit text Confirm Password untuk mengkonfirmasi password baru.

```xml
<EditText
        android:id="@+id/edt_confirm_password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:layout_marginRight="24dp"
        android:hint="@string/enter_your_password"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/confirm_password"
        android:layout_marginBottom="62dp"
        />
```

#### Tambahkan Button Change Password

Buat Button Change Password, beri text `CHANGE PASSWORD`.

```xml
<Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="24dp"
        android:layout_marginEnd="24dp"
        android:textSize="18sp"
        android:layout_marginTop="64dp"
        android:background="@drawable/button_red"
        android:text="@string/change_password"
        android:textColor="#FFFFFF"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/edt_confirm_password"
        android:onClick="postChangePassword"
        />
```

## Membuat ForgotPasswordActivity

![forgot](images/ForgotPassword.png)

### Edit activity_forgot_password.xml

Untuk membuat form lupa password seperti gambar diatas yaitu dengan mengubah isi file dari `activity_forgot_password.xml`, pada layout ini akan digunakan constraint layout pastikan layout xml dimulai dengan tag berikut ini.

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
  xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:app="http://schemas.android.com/apk/res-auto"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  tools:context=".ForgotPasswordActivity">
```

Pada desain layout terdapat beberapa komponen yaitu:

1. Judul
2. Sub Judul
3. Reset Code
4. Edit Text Reset Code
5. Button Send Request

#### Tambahkan Judul

Tambahkan sebuah TextView untuk menulis judul

```xml
<TextView
        android:id="@+id/welcome_back"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:fontFamily="@font/montserrat_semi_bold"
        android:text="@string/forgot_password"
        android:textColor="#313131"
        android:textSize="32sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:layout_marginTop="90dp"
        />
```

#### Tambahkan Sub Judul

Tambahkan sebuah sub text baru di bawah judul, berilah id `sign_in`

```xml
<TextView
        android:id="@+id/sign_in"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:fontFamily="@font/montserrat_light"
        android:text="Please enter your email below to recieve your password reset instruction"
        android:textColor="#9b9b9b"
        android:textSize="16sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@id/welcome_back" />
```

#### Tambahkan Reset Code

Tambahkan Text View untuk label Reset Code.

```xml
<TextView
        android:id="@+id/reset_code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="20dp"
        android:layout_marginTop="48dp"
        android:text="@string/username"
        android:textColor="#313131"
        android:textSize="20sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/sign_in" />
```

#### Tambahkan Edit Reset Code

Tambahkan Edit Text untuk pengisian reset code

```xml
 <EditText
        android:id="@+id/edt_reset_code"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="8dp"
        android:layout_marginRight="24dp"
        android:hint="Enter Your Email"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/reset_code"
        />
```

#### Tambahkan Button Send Request

Buat Button Send Request, beri text `SEND REQUEST` dengan warna text putih.

```xml
 <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="24dp"
        android:layout_marginEnd="24dp"
        android:textSize="18sp"
        android:background="@drawable/button_red"
        android:text="@string/send_request"
        android:textColor="#FFFFFF"
        app:layout_constraintTop_toBottomOf="@id/edt_reset_code"
        android:layout_marginTop="32dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        />
```

## Membuat SuccessResetPasswordActivity

### Edit activity_success_reset_password.xml

Untuk membuat activity success seperti gambar diatas yaitu dengan mengubah isi
file dari `activity_success_reset_password.xml`, pada layout ini akan digunakan constraint
layout pastikan layout xml dimulai dengan tag berikut ini.

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
  xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:app="http://schemas.android.com/apk/res-auto"
  xmlns:tools="http://schemas.android.com/tools"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:background="#FFFFFF"
  tools:context=".SuccessResetPasswordActivity">
```

Pada desain layout terdapat beberapa komponen yaitu:

1. Image
2. Judul
3. Sub Judul

### Menambahkan Constraint Guideline

Tambahkan constraint guideline untuk mengatur layout constraint kemudian atur orientation=horizontal dan layout_constraintGuide_percent="0.5" serta berilah id=guideline

```xml
<androidx.constraintlayout.Guideline
        android:id="@+id/guideline"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        app:layout_constraintGuide_percent="0.5" />
```

#### Tambahkan Image

Tambahkan sebuah Image untuk menulis judul berilah id=succes_image serta tambahkan ic_succesfull_logo dari drawable

```xml
  <ImageView
        android:id="@+id/success_image"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="8dp"
        android:src="@drawable/ic_succesfull_logo"
        app:layout_constraintBottom_toTopOf="@+id/txt_success"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent" />
```

#### Tambahkan Judul

Tambahkan sebuah TextView untuk menulis judul berilah id=txt_success dan atur layout constraint yaitu `app:layout_constraintTop_toTopOf="@+id/guideline"`

```xml
<TextView
        android:id="@+id/txt_success"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="@font/montserrat_semi_bold"
        android:text="Successful!!"
        android:textSize="32sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="@+id/guideline" />
```

#### Tambahkan Sub Judul

Tambahkan sebuah sub text baru di bawah judul, berilah id `sub_txt_success`

```xml
<TextView
        android:id="@+id/sub_txt_success"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="24dp"
        android:layout_marginTop="16dp"
        android:layout_marginRight="24dp"
        android:text="You have successfully changed password. Please use your new passwords when logging in"
        android:textAlignment="center"
        android:textSize="16sp"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toBottomOf="@id/txt_success" />
```

## Membuat SuccessLoginActivity

Ulangi langkah yang sama pada tahap pembuatan SuccessResetPasswordActivity, dan
gantilah pesan yang menyatakan anda telah berhasil untuk login.

> Commit semua perubahan yang telah anda lakukan, kemudian push ke akun GitHub
> anda!
