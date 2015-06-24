## Lab1: Instalasi JBoss BPM Suite 6.0.3

Sebelum melakukukan instalasi, ek kebutuhan instalasi atau sistem yang disupport di halaman berikut:

  [RED HAT JBOSS BPM SUITE 6.0 Supported Configuration](https://access.redhat.com/articles/704703)

Perlu diperhatikan pada halaman tersebut adalah versi JDK yang didukung, jenis dan versi OS yang didukung, jenis dan versi application server yang didukung.

1.  Download file yang diperlukan dari link berikut:
    
    
    https://access.redhat.com/jbossnetwork/restricted/listSoftware.html?downloadType=distributions&product=bpm.suite&productChanged=yes

    Anda harus memiliki akses ke website tersebut terlebih dahulu dengan membeli subscription dari produk JBoss BPM Suite.

    Berikut daftar file yang bisa didownload dari website tersebut:

    ![image](https://cloud.githubusercontent.com/assets/3068071/8324523/a247cc5e-1a7b-11e5-98b2-0eeedaff264d.png)

    Jika anda tidak memiliki akses ke website tersebut, file juga bisa di-download dari link berikut:

    [https://www.jboss.org/products/bpmsuite/download/](https://www.jboss.org/products/bpmsuite/download/)
  
    Klik tombol 'DOWNLOAD' di halaman tersebut, anda perlu daftar dan login dulu, tabpa bayar, untuk bisa download file installer di jboss.org. Anda bisa menggunakan JBoss BPM Suite dengan gratis untuk keperluan development.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8324542/c75c40ce-1a7b-11e5-8fc1-fe877014e472.png)



2.  Baca dokumentasi instalasi Jboss BPM SUite 6.0 [disini](https://access.redhat.com/documentation/en-US/Red_Hat_JBoss_BPM_Suite/6.0/html/Installation_Guide/chap-Installation_options.html#sect-The_Red_Hat_JBoss_BPM_Suite_Installer_installation)

    Pada dasarnya, jika kita akan menginstal JBoss BPM Suite ada beberapa cara yaitu:
    
    * Instalasi dari file jar yang didalamnya sudah termasuk JBoss EAP. Instalasi dari file jar ini pada dasarnya adalah instalasi menggunakan GUI dan sangat mudah. Jika OS kita tidak mendukung grafis, misalnya kita menggunakan console di Linux yang tidak memiliki X server, maka kita juga bisa menginstal menggunakan mode text. Baik dengan mode GUI maupun text, cara instalasinya berupa wizard, jadi tinggal ikuti saja langkah-langkahnya.
    
    * Instalasi dari file zip yang merupakan file yang siap dideploy di JBoss EAP. Untuk instalasi dari file ini, ini harus melakukan instalasi JBoss EAP terlebih dahulu sebagai produk terpisah. Setelah itu file zip ini bisa diekstrak dan ditimpa ke folder dimana JBoss EAP diinstal.
    
    * Instalasi dari file zip yang merupakan file yang siap dideploy di application server lain misalnya Tomcat.


3.  Install JDK 1.6 atau 1.7, misal kita instal JDK di direktori `C:\Java\jdk1.6.0`

    Jika menggunakan Windows set PATH variable pada system agar menggunakan JDK tersebut dengan cara berikut:
    
    `setx JAVA_HOME "C:\Java\jdk1.6.0"setx PATH %JAVA_HOME%\bin;%PATH%`
    
    Test dengan perintah berikut:
    
    `echo %PATH%`

    Pastikan direktori `C:\Java\jdk1.6.0\bin` ada di output hasil perintah diatas. 
    
    Kemudian pastikan juga dengan perintah berikut: `java -version`
    Contoh hasil output 

    ```
    java version "1.6.0_65"Java(TM) SE Runtime Environment (build 1.6.0_65-b14-462-11M4609)Java HotSpot(TM) 64-Bit Server VM (build 20.65-b04-462, mixed mode)
    ```
    
4.  Jalankan installer JBoss BPMS dengan perintah berikut dari command line:

    ```
    java -jar jboss-bpms-installer-6.0.3.GA-redhat-x.jar
    ```

    Ikuti wizard windows.. anda hanya perlu intuisi untuk bisa menyelesaikan proses instalasinya :-) Anda perlu ingat-ingat password untuk user `admin` dan `bpmsAdmin` yang anda masukan waktu instalasi.

    > CATATAN PENTING: Jika instalasi dilakukan di Windows, pada saat proses instal berlangsung, ditengah jalan bisa jadi anda menemukan error seperti ini: 

    ```
    Error occurred during initialization of VM
    Could not reserve enough space for object heap
    Error: Could not create the Java Virtual Machine.
    Error: A fatal exception has occurred. Program will exit.
    ```
    
    Akibat error tersebut proses instalasi BPM tidak selesai sempurna (gagal). Tapi pada dasarnya instalasi EAP sudah selesai dengan baik, hanya saja EAP tidak bisa di-start. Ini problem yang sudah diketahui. Untuk mengatasinya adalah sebagai berikut:
    
    Buka file `<JBOSS_BPMS_INSTALL_DIR>\jboss-eap-6.1\bin\standalone.conf.bat`
    
    Edit baris berikut:
    
    ```
    set "JAVA_OPTS=-Xms1303M -Xmx1303M -XX:MaxPermSize=256M"
    ```
    
    Menjadi:
    
    ```
    set "JAVA_OPTS=-Xms1303M -Xmx1303M"
    ```
    
    Karena instalasi BPM Suite sebelumnya tidak selesai (gagal), jadi kita perlu mengulangi. Untuk mempermudah sebaiknya kita lakukan instalasi lagi dengan metode ekstrak file zip. Yang perlu kita lakukan hanya mengekstrak file `jboss-bpms-6.0.3.GA-redhat-1-deployable-eap6.x.zip` dan biarkan file-file dari zip menimpa file yang sudah ada di `<JBOSS_BPMS_INSTALL_DIR>\jboss-eap-6.1`

5.  Jalankan JBoss BPM Suite dengan perintah berikut:
    Masuk ke direktori bin di direktori dimana JBoss BPM Suite (direktori JBoss EAP) diinstal
    
    ``` 
    cd <JBOSS_BPMS_INSTALL_DIR>\jboss-eap-6.1\bin
    standalone.bat
    ```
    
    Jika JBoss BPMS Suite berhasil dijalankan maka hasil perintah tersebut tidak memperlihatkan pesan error dan diakhiri dengan output seperti ini:

    ```
    18:13:29,168 INFO  [org.jboss.as.server] (ServerService Thread Pool -- 27) JBAS018559: Deployed "dashbuilder.war" (runtime-name : "dashbuilder.war")
    18:13:29,170 INFO  [org.jboss.as.server] (ServerService Thread Pool -- 27) JBAS018559: Deployed "business-central.war" (runtime-name : "business-central.war")
    18:13:29,310 INFO  [org.jboss.as] (Controller Boot Thread) JBAS015961: Http management interface listening on http://127.0.0.1:9990/management
    18:13:29,311 INFO  [org.jboss.as] (Controller Boot Thread) JBAS015951: Admin console listening on http://127.0.0.1:9990
    18:13:29,312 INFO  [org.jboss.as] (Controller Boot Thread) JBAS015874: JBoss BPM Suite 6.0.3.GA (AS 7.2.1.Final-redhat-10) started in 103955ms - Started 669 of 741 services (71 services are passive or on-demand)
    ```
    
    Coba akses dari browser URL berikut [http://localhost:8080/business-central](http://localhost:8080/business-central)

    Seharusnya anda mendapatkan screen login seperti ini:


  ![image](https://cloud.githubusercontent.com/assets/3068071/8324761/d904dd52-1a7d-11e5-931f-b078eba7de2c.png)


    Login dengan username `bpmsAdmin` dan password seperti yang udah anda set pada saat instalasi. Setelah login anda akan mendapatkan tampilan seperti ini. Karena pengguna `bpmsAdmin` memiliki role `admin` yang mempunyai hak akses ke semua menu/aktifitas di aplikasi business-cental maka semua menu ditampilkan dan dapat diakses.


    Sekarang kita akan coba menambahkan user lain dengan role yang berbeda. JBoss BPM Suite, memiliki beberapa jenis role yaitu:

      * Admin role - This role is meant to provide any user given it with full and complete access to all areas of the product.
      * Developer role - This role provides full access, except to the Administration perspective where you manage project and organizational setup.
      * Analyst role - This role provides the same access as the Developer role, except for no access to the asset repository and deployments.
      * User role - This is the role designed for the user of your system who is only allowed to manage processes, tasks that are generated for them, and view the created or provided reporting dashboards.
      * Manger role - This is the most restrictive role where we allow the user to view Business Activity Monitoring data in the form of provided or created reporting dashboards.
      
      (dicopy dari: http://www.schabell.org/2014/05/redhat-jboss-bpmsuite-user-role-access.html)

   Untuk membuat user baru, gunakan script add-user.sh (untuk Windows gunakan add-user.bat) 
    
    ```
    cd <JBOSS_BPMS_INSTALL_DIR>\jboss-eap-6.1\bin
    add-user.bat
    ```
    
    Ikuti perintahnya, seperti berikut:
    
    ```
    What type of user do you wish to add?
     a) Management User (mgmt-users.properties)
     b) Application User (application-users.properties)
    (a): b

    Enter the details of the new user to add.
    Realm (ApplicationRealm) :
    Username : mydev
    Password :
    Re-enter Password :
    What roles do you want this user to belong to? (Please enter a comma separated list, or leave blank for none)[  ]: developer
    About to add user 'mydev' for realm 'ApplicationRealm'
    Is this correct yes/no? yes
    Added user 'mydev' to file '/Users/eariobow/Servers/BPMS_603/jboss-eap-6.1/standalone/configuration/application-users.properties'
    Added user 'mydev' to file '/Users/eariobow/Servers/BPMS_603/jboss-eap-6.1/domain/configuration/application-users.properties'
    Added user 'mydev' with roles developer to file '/Users/eariobow/Servers/BPMS_603/jboss-eap-6.1/standalone/configuration/application-roles.properties'
    Added user 'mydev' with roles developer to file '/Users/eariobow/Servers/BPMS_603/jboss-eap-6.1/domain/configuration/application-roles.properties'
    Is this new user going to be used for one AS process to connect to another AS process?
    e.g. for a slave host controller connecting to the master or for a Remoting connection for server to server EJB calls.
    yes/no? yes
    To represent the user add the following to the server-identities definition <secret value="UGFzc3cwcmQh" />
    ```
    
    Buatlah beberapa user dengan role yang berbeda-beda, kemudian coba untuk login ke business-central.

    Lab1: Instalasi JBoss BPM Suite 6.0.3 telah selesai.
    Selanjutnya kita akan melakukan perubahan database yang digunakan oleh JBoss BPM Suite.
