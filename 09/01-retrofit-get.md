# Retrofit

Retrofit adalah sebuah library yang digunakan untuk mempermudah proses pertukaran data antara aplikasi android dengan server melalui REST API.
Berikut ini referensi yang dapat digunakan untuk mempelajari retrofit silahkan dipelajari sendiri :

1. [Vogella](https://www.vogella.com/tutorials/Retrofit/article.html)
2. [Codepath](https://github.com/codepath/android_guides/wiki/Consuming-APIs-with-Retrofit)
3. [Meetme](http://engineering.meetme.com/2014/03/best-practices-for-consuming-apis-on-android/)
4. [Jack Wharthon](https://speakerdeck.com/jakewharton/simple-http-with-retrofit-2-droidcon-nyc-2015)
5. [Jack Wharthon on Youtube](https://www.youtube.com/watch?v=t34AQlblSeE)

## Praktikum Get Data dari REST API

Pada praktikum ini akan dipelajari mengai cara melakukan request GET ke suatu endpoint. Endpoint yang digunakan adalah : https://cctv.putraprima.id

> ** Catatan ** : Google menyaratkan semua server yang diakses oleh aplikasi android menggunakan protokol http yang secure (di enkripsi) maka server yang digunakan harus menggunakan https.

### Gradle

Perhatikan build.gradle pada module app :

```gradle
apply plugin: 'com.android.application'

android {
    compileSdkVersion 29
    buildToolsVersion "29.0.2"

    defaultConfig {
        applicationId "id.putraprima.retrofit"
        minSdkVersion 21
        targetSdkVersion 29
        versionCode 1
        versionName "1.0"

        testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }
    compileOptions {
        targetCompatibility = "8"
        sourceCompatibility = "8"
    }
}

dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])

    implementation 'androidx.appcompat:appcompat:1.1.0'
    implementation 'androidx.constraintlayout:constraintlayout:1.1.3'
    testImplementation 'junit:junit:4.12'
    androidTestImplementation 'androidx.test.ext:junit:1.1.1'
    androidTestImplementation 'androidx.test.espresso:espresso-core:3.2.0'

    //retrofit
    implementation 'com.squareup.retrofit2:retrofit:2.7.2'
    implementation 'com.squareup.retrofit2:converter-gson:2.6.2'
    implementation 'com.squareup.okhttp3:logging-interceptor:3.8.0'
    //recyclerview
    implementation 'androidx.recyclerview:recyclerview:1.1.0'
    //material design
    implementation "com.google.android.material:material:1.2.0-alpha05"
}
```

Perhatikan tambahan dependencies dan compileOptions, pada tahap ini ditambahkan dependency retrofit, converter dan logging interceptor, serta pada compileOptions ditambahkan target dan source compatibility.

### Package pada source code

Perhatikan file tree berikut ini

```
├── api
│   ├── helper
│   │   └── ServiceGenerator.java
│   ├── models
│   │   └── AppVersion.java
│   └── services
│       └── ApiInterface.java
└── ui
    ├── MainActivity.java
    └── SplashActivity.java

```

Package pada starter code dibagi sesuai dengan kebutuhan, dibagi menjadi dua package utama yaitu `api` dan`ui`.

Package `api` berisi beberapa package lagi yaitu `helper`, `models` dan `services`.

- `helper` berisi ServiceGenerator.java.
- `models` berisi model yang akan digunakan pada aplikasi.
- `services` berisi interface yang berisi endpoint yang akan diakses.

Package `ui` berisi activity yang digunakan pada aplikasi ini.

### ServiceGenerator

```java
public class ServiceGenerator {

    private static final String BASE_URL = "https://cctv.putraprima.id";

    private static Retrofit.Builder builder =
            new Retrofit.Builder()
                    .baseUrl(BASE_URL)
                    .addConverterFactory(GsonConverterFactory.create());

    private static Retrofit retrofit = builder.build();

    private static HttpLoggingInterceptor logging =
            new HttpLoggingInterceptor()
                    .setLevel(HttpLoggingInterceptor.Level.BODY);

    private static OkHttpClient.Builder httpClient =
            new OkHttpClient.Builder();

    public static <S> S createService(
            Class<S> serviceClass) {
        if (!httpClient.interceptors().contains(logging)) {
            httpClient.addInterceptor(logging);
            builder.client(httpClient.build());
            retrofit = builder.build();
        }

        return retrofit.create(serviceClass);
    }
}
```

Class ini adalah class yang berfungsi melakukan generate terhadap service endpoint retrofit, Detail tutorial mengenai service generator dan kenapa menggunakan service generator dapat anda pelajari lebih lanjut pada [tutorial berikut ini](https://futurestud.io/tutorials/retrofit-2-creating-a-sustainable-android-client).

### AppVersion

Berikut ini kode program AppVersion.java

```java
public class AppVersion {
    String app;
    String version;

    public AppVersion(String app, String version) {
        this.app = app;
        this.version = version;
    }

    public String getApp() {
        return app;
    }

    public void setApp(String app) {
        this.app = app;
    }

    public String getVersion() {
        return version;
    }

    public void setVersion(String version) {
        this.version = version;
    }
}
```

Kode program diatas adalah hasil mapping dari response json yang di request ke endpoint https://cctv.putraprima.id/, berikut ini raw json hasil requestnya :

```json
{
  "app": "Laravel",
  "version": "1.0.0"
}
```

Perhatikan cara mapping dari json ke class model.

### ApiInterface

Daftar endpoint yang diakses dan method yang digunakan serta parameter yang dikirim untuk mengakses endpoit di daftarkan pada file ini, perhatikanlah dengan seksama kode program berikut ini :

```java
public interface ApiInterface{
    @GET("/")
    Call<AppVersion> getAppVersion();
}
```

Pada interface di atas terdapat sebuah annotation @GET("/") ini menunjukkan bahwa method getAppVersion digunakan untuk mengakses endpoint "/" dan menggunakan class AppVersion sebagai class model datanya.

### SplashActivity

Pada splash activity digunakan semua class yang dibuat sebelumnya untuk mengakses endpoint "/", perhatikan fungsi berikut yang ada pada starter code :

```java
    private void checkAppVersion() {
        ApiInterface service = ServiceGenerator.createService(ApiInterface.class);
        Call<AppVersion> call = service.getAppVersion();
        call.enqueue(new Callback<AppVersion>() {
            @Override
            public void onResponse(Call<AppVersion> call, Response<AppVersion> response) {
                Toast.makeText(SplashActivity.this, response.body().getApp(), Toast.LENGTH_SHORT).show();
                //Todo : 2. Implementasikan Proses Simpan Data Yang didapat dari Server ke SharedPreferences
                //Todo : 3. Implementasikan Proses Pindah Ke MainActivity Jika Proses getAppVersion() sukses
                Intent i = new Intent(getApplicationContext(),MainActivity.class);
                startActivity(i);
            }

            @Override
            public void onFailure(Call<AppVersion> call, Throwable t) {
                Toast.makeText(SplashActivity.this, "Gagal Koneksi Ke Server", Toast.LENGTH_SHORT).show();
                //Todo : 4. Implementasikan Cara Notifikasi Ke user jika terjadi kegagalan koneksi ke server silahkan googling cara yang lain selain menggunakan TOAST
            }
        });
    }
```

Kode program diatas di instansiasi kan service generator untuk call retrofit, kemudian pada proses call digunakan callback yang dipanggil secara asynchronous.
