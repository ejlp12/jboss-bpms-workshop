## Instalasi JBoss BPM Suite 6.1

Instalasi JBos BPMS versi 6.1 sedikit berbeda dengan versi sebelumnya yaitu 6.0.3. Pada versi 6.1, JBoss EAP harus diinstal dahulu, terpisah dari proses instalasi JBoss BPMS. 

1. Instal JDK 1.8

2.  Download & instal JBoss EAP 6.4 

    Download file installer dari website ini, anda perlu login atau daftar dulu untuk mengunduhnya.
   
    http://www.jboss.org/products/eap/download/
   
    ![image](https://cloud.githubusercontent.com/assets/3068071/8325570/e0ec012e-1a84-11e5-8c8c-53f109ad0903.png)

    Instal dengan mode non-gui menggunakan perintah berikut:
    
    ```
    java -jar jboss-eap-6.4.0-installer.jar -console
    ```

3.  Download & instal JBoss BPM Suite 6.1
   
    Download file installer dari website ini, anda perlu login atau daftar dulu untuk mengunduhnya.
   
    https://www.jboss.org/products/bpmsuite/download/

    ![image](https://cloud.githubusercontent.com/assets/3068071/8325490/4c48c7f0-1a84-11e5-999e-ff032a1db1d4.png)

    Jika anda sudah memiliki **subscription**, anda bisa mendownload dari http://access.redhat.com
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8325307/933e59d8-1a82-11e5-9e2c-ae99fbe6cca8.png)

    ```
    java -jar jboss-bpmsuite-6.1.0.GA-installer.jar -console
    ```
    
    Ikuti langkah demi langkah:
    
    1. Setujui License Agreement
    2. Buat administrative user atau tidak, jika tidak maka administrative user akan menggunakan user admin yang sudah disetup saat instalasi JBoss EAP
    3. Membuat Business Process Management Suite Admin User, user ini adalah user admin untuk BPM. Defaultnya akan bernama `bpmsAdmin`.
    4. Set password untuk user `bpmsAdmin`
    5. Penambahan additional roles that will be used for task management.  
       These roles are custom named and used again when building your processes with human tasks.  Add your custom named roles in a comma separated list below.
    6. Mengkonfigurasi Java Security Manager, pilih tidak untuk mempermudah 
    7. Mengkonfigurasi IPv6 jika server hanya menggunakan IPv6, pilih tidak jika anda menggunakan IPv4
    8. Pilih konfigurasi default atau advance, untuk mempermudah pilih saja "default"
    
    

4.  Jalankan JBoss BPMS

   ```
   cd /Servers/BPMS-6.4
   ./standalone.sh -c standalone-full.xml
   ```

> Abaikan kika saat menjalankan JBoss BPMS, di console muncul log seperti ini:
> ```
> 16:49:45,638 ERROR [stderr] (MSC service thread 1-3) ScriptEngineManager providers.next(): javax.script.ScriptEngineFactory: Provider apple.applescript.AppleScriptEngineFactory not found
> 16:49:45,639 ERROR [stderr] (MSC service thread 1-3) ScriptEngineManager providers.next(): javax.script.ScriptEngineFactory: Provider com.sun.script.javascript.RhinoScriptEngineFactory not found
> ```
> Error tersebut muncul jika kita menggunakan JDK/JRE 1.8
