## Cloning Repository

Untuk melakukan sharing project yang anda buat ke developer lain atau sebaliknya secara offline, bisa dilakukan export/import repository dengan cara cloning repository GIT yang digunakan untuk menyimpan project.

### Ekspor repository

Untuk mengekspor project yang ada di repository ikuti langkah berikut:

1.  Install GIT di mesin yang anda gunakan

2.  Login ke Busines Central dan akses menu Authoring -> Administration.

    Lalu klik perspective menu Repository -> List seperti gambar berikut
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8506577/f1b8bf52-2244-11e5-9f7c-6528dc2cc064.png)
    
    Bisa dilihat dihalaman RepositoryEditor diatas, ada dua repository yang di JBoss BPMS. Tiap-tiap repository bisa kita clone ke komputer anda dengan menggunakan protokol **git** atau **ssh**
    
    Protokol git digunakan jika kita ingin meng-clone repository tapi mode read-only, artinya kita tidak bisa melakukan update atau commit ke repository. Sedakan dengan protokol ssh hal tersebut memungkinkan. 
    
3.  Kita akan coba clone `repository2` dimana project yang sudah dibuat di LAB sebelumnya yaitu project `simpleproject` berada.

    Klik tulisan `git` yang ada disamping tulisan "Available protocol(s)" pada repository2.
   
    Blok tulisan URL yang tertera disamping, yaitu "git://localhost:9418/repository2"
    Kemudian copy text tersebut.
   
4.  Pada mesin anda yang sudah terinstal GIT, buka terminal atau command prompt, lalu jalankan perintah berikut:

    ```
    git clone git://localhost:9418/repository2
    ```
    
    berikut hasil perintah `git clone` tersebut
    
    ```
    $ git clone git://localhost:9418/repository2
    Cloning into 'repository2'...
    remote: Counting objects: 65, done
    remote: Finding sources: 100% (382/382)
    remote: Getting sizes: 100% (138/138)
    remote: Compressing objects:  64% (2307/3578)
    remote: Total 382 (delta 200), reused 362 (delta 200)
    Receiving objects: 100% (382/382), 62.19 KiB | 0 bytes/s, done.
    Resolving deltas: 100% (211/211), done.
    Checking connectivity... done.
    ```
    
    Kita bisa  lihat direktori hasil clone. Terlihat direktori tersebut adalah GIT repository, ditunjukan dengan ada direktori `.git`
    ```
    $ ls -al repository2/
    total 4
    drwxr-xr-x   5 ejlp12  staff  170 Jul  4 12:19 .
    drwxr-xr-x   3 ejlp12  staff  102 Jul  4 12:17 ..
    drwxr-xr-x  12 ejlp12  staff  408 Jul  4 12:17 .git
    drwxr-xr-x   7 ejlp12  staff  238 Jul  4 12:17 basicproject
    -rw-r--r--   1 ejlp12  staff   79 Jul  4 12:17 readme.md
    ```
    
    Kita lihat isi dari direktori hasil clone:
    
    
    ```
    $ tree repository2/
    repository2/
    ├── basicproject
    │   ├── global
    │   │   ├── backboneformsinclude.fw
    │   │   ├── backbonejsinclude.fw
    │   │   ├── cancelbutton.fw
    │   │   ├── checkbox.fw
    │   │   ├── customeditors.json
    │   │   ├── defaultemailicon.gif
    │   │   ├── defaultlogicon.gif
    │   │   ├── defaultservicenodeicon.png
    │   │   ├── div.fw
    │   │   ├── dropdownmenu.fw
    │   │   ├── fieldset.fw
    │   │   ├── form.fw
    │   │   ├── handlebarsinclude.fw
    │   │   ├── htmlbasepage.fw
    │   │   ├── image.fw
    │   │   ├── jqueryinclude.fw
    │   │   ├── jquerymobileinclude.fw
    │   │   ├── link.fw
    │   │   ├── mobilebasepage.fw
    │   │   ├── orderedlist.fw
    │   │   ├── passwordfield.fw
    │   │   ├── radiobutton.fw
    │   │   ├── script.fw
    │   │   ├── submitbutton.fw
    │   │   ├── table.fw
    │   │   ├── textarea.fw
    │   │   ├── textfield.fw
    │   │   ├── themes.json
    │   │   └── unorderedlist.fw
    │   ├── package-names-white-list
    │   ├── pom.xml
    │   ├── project.imports
    │   └── src
    │       ├── main
    │       │   ├── java
    │       │   │   └── example
    │       │   │       └── basicproject
    │       │   └── resources
    │       │       ├── META-INF
    │       │       │   ├── kie-deployment-descriptor.xml
    │       │       │   └── kmodule.xml
    │       │       └── example
    │       │           └── basicproject
    │       │               ├── WorkDefinitions.wid
    │       │               ├── approve-data-taskform.form
    │       │               ├── approve-data-taskform.ftl
    │       │               ├── basicproject.simple_proc-taskform.form
    │       │               ├── basicproject.simple_proc-taskform.ftl
    │       │               ├── simple_proc.bpmn2
    │       │               └── simple_proc_2.bpmn2
    │       └── test
    │           ├── java
    │           │   └── example
    │           │       └── basicproject
    │           └── resources
    │               └── example
    │                   └── basicproject
    └── readme.md

    18 directories, 42 files
    ```
    
   
5.  Selesai, anda bisa zip (compress) direktori tersebut dan share secara offline ke rekan anda dan rekan anda bisa mengimpor repository tersebut ke JBoss BPMS miliknya.

## Import Repository

Jika anda ingin meng-import repository dari GIT repository lain baik secara lokal maupun remote di JBoss BPMS anda, maka yang perlu dilakukan adalah meng-clone external repository tersebut lewat Business Central.

1.  Akses perspective menu Repository -> Clone  

    ![image](https://cloud.githubusercontent.com/assets/3068071/8506973/3dd38b42-2259-11e5-8e4c-bce618eedbb7.png)
    
2.  Buka browser lalu akses URL berikut `https://github.com/ejlp12/jbossbpms-sample1`
    
    Copy URL untuk clone dengan mengklik tanda copy disebelah kanan URL. Lihat gambar...
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8507044/a814f3e4-225c-11e5-80e2-ea1496a651b0.png)
    

3.  Pada window clone repository masukan nama repository `lahitan-clone`, pilih organization unit `example`, lalu paste github repository URL yang tadi sudah di-copy yaitu `https://github.com/ejlp12/jbossbpms-sample1.git`.

    Klik tombol [Clone]

    ![image](https://cloud.githubusercontent.com/assets/3068071/8507023/9ef241fa-225b-11e5-9170-fdcbd24c0938.png)

4.
