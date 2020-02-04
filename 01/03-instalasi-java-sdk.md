# Instalasi JAVA SDK

Lewati modul ini jika anda sudah memiliki Java SDK di komputer anda, untuk
mengecek installasi Java pada komputer silahkan buka terminal (command prompt)
dan ketikkan command `java` dan `javac` jika kedua perintah tersebut menampilkan
hasil yang benar maka lewati bagian ini. Contoh hasil terminal jika JDK belum
terinstall dengan benar.

![java](./images/01-java-error.png)

![javac](./images/02-javac-error.png)

Jika kedua perintah tersebut gagal dilakukan berarti anda belum menginstall JRE dan JDK dengan benar.

## Langkah-langkah installasi

### Klik Installer dan ikuti langkah langkahnya

![install](./images/03-install-jdk.png)

![install](./images/04-install-jdk.png)

![install](./images/05-install-jdk.png)

![install](./images/06-install-jdk.png)

### Setting System Environment

Bukalah system environment variables pada komputer anda kemudian klik tombol Environment Variables

![install](./images/09-environment-variable.png)

Buatlah entry baru pada input System Variables, beri nama sesuai gambar `Variable Name : JAVA_HOME` dan `Variable Value : path install jdk pada komputer anda`

![install](./images/10-environment-variable-create-java-home.png)

![install](./images/11-lokasi-install-java.png)

![install](./images/12-set-java-home.png)

Edit System Variable dengan nama `Path` dan tambahkan `%JAVA_HOME%\bin`

![install](./images/13-edit-path-java.png)

![install](./images/14-java-home-bin.png)

3. Restart Command Prompt
4. Ketikkan Perintah `java` dan `javac` untuk menguji hasil installasi

   ![install](./images/07-install-java-oke.png)

   ![install](./images/08-install-javac-ok.png)
