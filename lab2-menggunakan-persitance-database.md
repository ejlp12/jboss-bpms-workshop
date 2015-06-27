## Lab2: Mengubah default setting database JBoss BPM Suite
Pada Lab ini kita akan coba mengubah default setting dari database yang digunakan oleh JBoss BPM Suite. Kenapa perlu diubah? 

JBoss BPM Suite yang sudah kita instal menggunakan database engine bernama H2. [Database H2](http://www.h2database.com/) merupakan database open source yang kencang, cukup kecil, dan dibuat menggunakan Java. Database H2 dapat menyimpan data di memory maupun di disk. **Default setting database storage yang digunakan JBoss BPM Suite adalah di memory**, oleh karena itu jika kita menjalankan sebuah bisnis proses di business-central, maka data terkait instance process bisnis tersebut akan hilang jika JBoss BPM Suite kita restart.

Kondisi ini jelas tidak diinginakan terjadi di production environment, bahkan kita juga mungkin tidak mau terjadi di development/test environment. Oleh karena itu kita perlu ubah default data store yang digunakan H2 database menjadi **persistence** yaitu di disk sehingga **data tidak hilang meskipun JBoss BPM Suite kita restrart**.

Jika anda ingin menggunakan database lain, saya akan jelaskan dan bahas di posting terpisah. Saya akan beri contoh bagaimana mengubah konfigurasi JBoss BPM Suite agar dapat menggunakan database PostgreSQL.

Untuk saat ini mari kita ubah konfigurasi agar tetap menggunakan database H2 dengan data store di disk.

1.  Untuk menjalankan H2 database dengan data store di disk, kita perlu menjalankannya secara manual dengan perintah berikut:

    Windows:
    ```
    java -cp "<JBOSS_HOME>/jboss-eap-6.1/modules/system/layers/base/com/h2database/h2/main/h2-1.3.168-redhat-2.jar;%CLASSPATH%" org.h2.tools.Server -tcp -tcpPort 9091 -baseDir C:/jbpms-db/ -web -webPort 8083
    ```
    Linux/Unix/Mac OS-X:
    ```
    java -cp "<JBOSS_HOME>/jboss-eap-6.1/modules/system/layers/base/com/h2database/h2/main/h2-1.3.168-redhat-2.jar:$CLASSPATH" org.h2.tools.Server -tcp -tcpPort 9091 -baseDir /home/jboss/jbpms-db/ -web -webPort 8083 &
    ```
    
    Ganti `<JBOSS_HOME>` dengan path dimana anda menginstal JBoss BPM Suite.
    
    > Untuk mempermudah menjalankan lagi H2 database dilain waktu, buatlah file `h2start.bat` (jika menggunakan Windows) atau `h2start.sh` (jika menggunakan Linux/Unix/Mac OS X) di direktori `<JBOSS_HOME>/jboss-eap-6.1/` dan isi dengan text seperti diatas.
    
    > Perintah diatas akan menjalankan program database H2 yang dapat diakses oleh client pada port 9091 dan akan meyimpan data di `C:/jbpms-db/` atau di  `/home/jboss/jbpms-db/`
    
2.  Test koneksi dengan menggunakan H2 web console. Buka browser dan akses ke URL [http://localhost:8083](http://localhost:8083)
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8391260/b44bc03c-1ce6-11e5-834a-41949bec81f9.png)
    
    Masukan JDBC URL seperti ini:

    Windows:
    ```
    jdbc:h2:tcp://localhost:9091/C/jbpms-db
    ```
    
    Linux/Unix/Mac OS-X:
    ```
    jdbc:h2:tcp://localhost:9091/home/jboss/jbpms-db
    ```
    
    Lalu klik tombol [Test Connection] jika pesan sukses muncul, berarti koneksi ke H2 database berhasil dan kita bisa lanjutkan dengan mengklik tombol [Connect]

3.  Sekarang kita akan ubah konfigurasi JBoss EAP yang digunakan BPM Suite agar menggunakan database H2 yang sudah kita jalankan.
    Menggunakan aplikasi direktori eksplorer, masuklah ke direktori `<JBOSS_BHOME>/jboss-eap-6.1/standalone/configuration/`. Buka file `standalone.xml` dengan menggunakan text editor. Lalu edit bagian `connection-url` di elemen datasource. Sebelumnya value dari elemen tersebut adalah `jdbc:h2:mem:test;DB_CLOSE_DELAY=-1`. Kita perlu ganti value-nya menjadi seperti berikut:
    
    ```xml
    <subsystem xmlns="urn:jboss:domain:datasources:1.1">
      <datasources>
        <datasource jndi-name="java:jboss/datasources/ExampleDS" pool-name="ExampleDS" enabled="true" use-java-context="true">
          <connection-url>jdbc:h2:tcp://localhost:9091/C/jbpms-db</connection-url>
          <driver>h2</driver>
          <security>
            <user-name>sa</user-name>
            <password>sa</password>
          </security>
        </datasource>
        <drivers>
          <driver name="h2" module="com.h2database.h2">
            <xa-datasource-class>org.h2.jdbcx.JdbcDataSource</xa-datasource-class>
          </driver>
        </drivers>
      </datasources>
    </subsystem>
    ```
    
4.  Restart JBoss BPM Suite, lalu coba akses business-central lagi.
    
    Untuk melakukan restart, anda bisa menstop dengan menekan tombol CONTROL+C pada terminal atau command prompt dimana anda sebelumnya menjalankan perintah `standalone.bat` atau standalone.sh

    Lalu start lagi dengan menjalankan perintah `standalone.bat` atau `standalone.sh`. Pastikan output dari perintah tersebut tidak menampakkan pesan error.
    
5.  Jika JBoss BPM Suite telah menggunakan database H2 yang kita jalankan tadi, kita bisa lihat di H2 web console beberapa tabel telah dibuat secara otomatis oleh JBoss BPM Suite seperti gambar berikut:

![image](https://cloud.githubusercontent.com/assets/3068071/8391256/8c297b8a-1ce6-11e5-8ffb-5ff65efcb720.png)

