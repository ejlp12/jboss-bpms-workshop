## LAB3: Membuat Project Baru lewat Business Central

1.  Login ke business central [http://localhost:8080/business-central/](http://localhost:8080/business-central/) dengan user `bpmsAdmin`
    
2.  Klik menu Authoring > Administration
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392298/219b77c6-1d10-11e5-9e8b-850e91852931.png)
    
    Klik di submenu Organizational Unit > Manage Organizational Unit,
    Klik tombol Add di sebelah kanan dibawah list Organizational Units,
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392370/1485b1fc-1d13-11e5-89a4-fbb9e04759ab.png)
    
    
    Masukan informasi mengenai Organizational Unit seperti contoh gambar dibawah ini, kemudian klik tombol [OK]
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392323/48cda9f8-1d11-11e5-936d-5004ccaa6686.png)
    
    Nama organizational unit yang baru akan masuk di list dengan nama "acme : jboss" dan kalau anda klik item tersebut, terlihat disebelah kanan windows list tidak ada repository yang dimiliki "acme : jboss"

3.  Sekarang kita buat repository pada organizational unit "acme" yang barusan kita buat.
    Klik di submenu Repository > New Repository
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392193/c5d7e2ca-1d0b-11e5-88e1-584121ba1037.png)
    
    kemudian isikan Repository name dan pilih Organizational unit
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392393/beb501b4-1d13-11e5-902f-e84187214cbc.png)
    
    Lalu klik tombol [Create]. Kita akan lihat di window File Explorer sudah ada entry repository baru. Coba klik repository tersebut untuk melihat detail informasi
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392408/441e6e08-1d14-11e5-8ed4-326d2cc4e84b.png)

  > Catatan:JBoss BPM Suite menggunakan GIT sebagai tempat untuk menyimpan semua artifak (file-file) yang terkait dengan project Business Process maupun Business Rule yang akan kita buat. Default GIT directory yang digunakan JBoss BPM Suite letaknya ada di `<JBOSS_BPMS_INSTALL_DIR>/jboss-eap-6.1/.niogit`

    Berikut isi dari direktori tersebut setelah saya membuat repository baru:
    
    ```
    drwxr-xr-x  9 ejlp12  staff   306B Dec  9 12:43 insurancepolicy.git/
    drwxr-xr-x  9 ejlp12  staff   306B Nov 24 11:02 repository1.git/
    drwxr-xr-x  9 ejlp12  staff   306B Nov 24 11:02 system.git/
    ```
    
4.  Sekarang kita mulai membuat Project di JBoss BPM Suite.
    
    Klik menu Authoring > Project Authoring. Akan muncul Project Explorer view.
    Pastikan ada berada di organizational unit dan repository yang telah anda buat sebelumnya yaitu "acme / insurance"
    
    Klik tombol "New Project" 
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392419/d4839d2e-1d14-11e5-9fa9-7a76c3aff539.png)

    atau pada klik submenu New Item > Project
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392477/59d6c0b8-1d16-11e5-82c5-d4c3d0dc3710.png)
    
    Beri nama new project: `policyquote`, lalu klik tombol [OK].
    
    Isi detail Project General Setting. Isi Project Description: `Insurance process` atau dikosongkan, Group ID: `org.acme.insurance`
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392209/8b1cb8ee-1d0c-11e5-83d2-e2df3648bbaa.png)
    
    Klik tombol [Finish]
    
5.  Sebuah project sudah selesai kita buat!
    Sekarang kita bisa membuat entry/artifact lainnya di project yang sudah kita buat. Kita bisa bikin Business Process, Decision Table, DRL file, dan lain-lain seperti yang terlihat di submenu "New Item" dibawah ini.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8392212/afc86152-1d0c-11e5-8e38-17df2dc5b5a2.png)
    
    Pada Lab selanjutnya, kita akan membuat New Business Process. Yeaaa..
    
    
  
