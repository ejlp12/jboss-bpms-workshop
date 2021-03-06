## Membuat Form User Interface 

1.  Kembali ke perspective Business Process modeling view, buka proses `simple_proc.bpmn2`.
    Lalu klik icon FORM seperti gambar berikut, dan pilih menu item "Generate all Forms"

    ![image](https://cloud.githubusercontent.com/assets/3068071/8499884/467738ea-21c1-11e5-8325-e5cd3683de9e.png)
    
    Form UI akan di-_generate_ secara otomatis. Form yang akan dibuat adalah satu form  untuk proses bisnis, dan form untuk setiap task yang bertipe "User Task". Karena pada proses `simple_proc` hanya ada satu User task maka form yang akan di-generate adalah 2 form.
    
2.  File form yang terbentuk akan dapat dilihat di Project Explorer, pada group "Form Definitions". Selain itu juga akan terbentuk file `ftl` yang merupakan file form (html + js)

    ![image](https://cloud.githubusercontent.com/assets/3068071/8498773/0c19c0b6-21b5-11e5-9d0a-5ed606f3910b.png)
    
3.  Edit form proses yang akan ditampilkan saat proses di-start yaitu dengan mengklik `basicproject.simple_proc-taskform`

    Format nama form untuk proses selalu <package>.<process name>-taskform
   
    ![image](https://cloud.githubusercontent.com/assets/3068071/8499315/da3a61e8-21bb-11e5-9bc4-8293caa73a52.png)

    Arahkan mouse pointer ke field "approve", akan muncul icon2 untuk mengedit field tersebut seperti berikut:
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8499326/f603911a-21bb-11e5-9dfb-2c146df774f6.png)
    
    Klik icon yang paling kanan yaitu untuk menghapus field "approve" karena field ini tidak diperlukan untuk diisi user saat proses baru saja dijalankan.
    
4.  Pindahkan urutan field dengan cara seperti berikut

    ![image](https://cloud.githubusercontent.com/assets/3068071/8499594/c5669e28-21be-11e5-95cc-31ae7d544192.png)
    
5.  Ubah label dari masing-masing field dengan cara seperti berikut:

    ![image](https://cloud.githubusercontent.com/assets/3068071/8499745/0c4d06c8-21c0-11e5-8ef8-48330b2acbe2.png)
    
6.  Save form 

    ![image](https://cloud.githubusercontent.com/assets/3068071/8499795/6c03aa36-21c0-11e5-96b2-b9689fb2cfa7.png)
    
    Isi atau abaikan comment, klik tombol [Save]
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8499959/0d1d08e4-21c2-11e5-9e9d-0494ceaa7638.png)
    
    
7.  Buka form `approve-data-taskform` dan edit sehingga form berbentuk seperti dibawah ini.

    Pastikan juga field "Name" bersifat __Read Only_
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8499946/ec0dc148-21c1-11e5-8c56-6d709967efd2.png)
    
8.  Save form tersebut.

9.  Klik tombol [Open Project Editor] di Project Explorer view, lalu pada Project Editor ubah field Version menjadi "1.1", lalu klik tombol [Save]

    ![image](https://cloud.githubusercontent.com/assets/3068071/8500103/48dc1752-21c3-11e5-87c7-3fb6be717d8b.png)

10. Build & Deploy project tersebut dan jalankan Process Definition sehingga anda mendapatkan form input seperti berikut:

    ![image](https://cloud.githubusercontent.com/assets/3068071/8500207/13b9cb36-21c4-11e5-8abe-e473cffd93ee.png)
    
    dan form berikut saat mengerjakan task "Approve Data"
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8500225/4b479e8e-21c4-11e5-9c00-676807880a36.png)



   
    
    
