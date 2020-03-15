# Retrofit POST

Berikut ini langkah membuat post request ke suatu endpoint :

- Tambahkan class model yang dibutuhkan untuk mengirim data ke endpoint.
- Tambahkan endpoint ke file ApiInterface.
- Tambahkan call di activity yang menggunakan.

## Contoh

Login REST API input :

Endpoint : https://mobile.putraprima.id/api/auth/

```json
{
  "UserId": "1234",
  "Password": "1234"
}
```

Model :

```java
class LoginRequest{
    public String UserId, Password;
    //constructor
    //getter setter
}
```

Login REST API response :

```json
{
  "UserId": "1234",
  "FirstName": "Keshav",
  "LastName": "Gera",
  "ProfilePicture": "312.113.221.1/GEOMVCAPI/Files/1.500534651736E12p.jpg"
}
```

Model :

```java
class LoginResponse{

    public string UserId,FirstName,LastName,ProfilePicture;
    //constructor
    //setter
    //getter
}
```

ApiInterface :

```java
Interface ApiInterface{
    @POST("/api/auth/")
    Call<LoginResponse> login(@Body LoginRequest loginRequest);
}

```

Activity :

```java
    private void login() {
        ApiInterface service = ServiceGenerator.createService(ApiInterface.class);
        Call<LoginResponse> call = service.doLogin(loginRequest);
        call.enqueue(new Callback<LoginResponse>() {
            @Override
            public void onResponse(Call<LoginResponse> call, Response<LoginResponse> response) {
                Toast.makeText(SplashActivity.this, response.body().getFirstName(), Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onFailure(Call<LoginResponse> call, Throwable t) {
                Toast.makeText(SplashActivity.this, "Gagal Koneksi Ke Server", Toast.LENGTH_SHORT).show();
            }
        });
    }
```
