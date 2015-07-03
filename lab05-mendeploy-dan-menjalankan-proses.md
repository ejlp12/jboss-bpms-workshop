## Mendeploy Project dan Menjalankan Proses Definition

Pada LAB ini kita akan belajar untuk melakukan deployment project dan juga menjalankan  serta melakukan test dari proses definition yang sudah dibuat pada LAB sebelumnya.

### Build & Deploy Project

1.  Buka project editor dengan mengklik tombol [Open Project Editor] di Project Explorer view
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8493319/bb35a994-2182-11e5-8072-4056301652fa.png)

2.  Klik tombol Build  → [Build & Deploy]

    ![image](https://cloud.githubusercontent.com/assets/3068071/8492559/935c92fa-2175-11e5-9d0e-b1761fbd2257.png)
   
    > Jika proses "Build failed" perhatikan message view di bawah Project Editor view seperti berikut.
    > Eror bisa terjadi karena ada kesalahan atau ketidak lengkapan process definition yang dibuat atau karena project sudah dideploy
    >
    > ![image](https://cloud.githubusercontent.com/assets/3068071/8492628/bd3c7c6a-2176-11e5-9993-23d46c4f7ffc.png)
    
3.  Project yang sudah dideploy dan siap dijalankan dapat dilihat dengan mengakses menu Deploy → Process Deployments  

    ![image](https://cloud.githubusercontent.com/assets/3068071/8492660/598631a6-2177-11e5-8c43-fc7de5106baf.png)
   
    ![image](https://cloud.githubusercontent.com/assets/3068071/8492681/a0817ee4-2177-11e5-80c1-7745a299bb5f.png)
    
    Kita bisa lihat di daftar tersebut bahwa project yang kita buat yaitu **example:basicproject:1.0** sudah terdeploy.
    
### Menjalankan proses

Project yang kita buat hanya memiliki satu Process Definition dengan nama **simple_proc**. Proses tersebut akan dapat dilihat dan dijakankan. Ikuti langkah-langkah berikut

1.  Klik pada menu Process Management → Process Definitions

    ![image](https://cloud.githubusercontent.com/assets/3068071/8492716/a2ef5826-2178-11e5-9ceb-f36ac3fcc193.png)

2.  Klik tombol _play_ di kolom Action untuk menjalankan proses tersebut. Akan muncul form 

    ![image](https://cloud.githubusercontent.com/assets/3068071/8494195/e1a9e19e-218c-11e5-99cb-63104d681120.png)
    
3. Isi semua fields form tersebut lalu klik Ok.

4. Lakukan langkah 2 dan 3 sekali lagi dengan masukan nilai yang berbeda untuk semua fields yang ada pada form.

5.  Klik  menu Process Management → Process Instances
    Anda akan lihat dua process instance yang _"hidup"_ (belum completed) di JBoss BPMS.

    Pilih salah satu process instance tersebut dengan mengklik salah satu baris pada daftar Process Instances, dan lihat detil informasi dari process instance tersebut di view sebelah kanan.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8492794/f6de7aec-2179-11e5-81f4-327f8976cce8.png)
    
6.  Perhatikan informasi Current Activities di tab "Instance Detail". 

    Apa maksudnya _"3/Jul/15 11:58:40: 1 - Approve Data (HumanTaskNode)"_?
    Maksudnya adalah saat ini proses sedang berada pada node dengan nama "Approve Data", node tersebut berupa HumanTaskNode atau User Task. Kita akan lebih jelas jika kita lihat proses diagram yang memperlihatkan jalur proses yang sudah dilalui dan menunjukan posisi terakhir dari proses.
    
    Klik tombol [Option] lalu Process Model

    ![image](https://cloud.githubusercontent.com/assets/3068071/8492851/0d67bfc0-217b-11e5-889e-3db608b63267.png) 
    
    Akan muncul dialog window yang menunjukan Process Model, obyek yang berwarna abu-abu berarti node atau jalur yang sudah dilewati (dieksekusi), node dengan **warna merah** berarti posisi proses saat ini.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8494271/77ae783a-218d-11e5-840e-e2d88350ccbf.png)

    Tutup window tersebut
    
7.  Sekarang klik tab "Process Variables". Perhatikan bahwa kita bisa lihat nilai varibel yang dimasukan di form UI saat proses dijalankan.

    ![image](https://cloud.githubusercontent.com/assets/3068071/8494329/24f1892e-218e-11e5-83dc-07bae48fd299.png)
    
    Kita juga dapat mengubah nilai variabel tersebut dan melihat histori perubahan nilai tersebut
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8495364/42389f5a-2197-11e5-9f11-c98613457c37.png)
    
8.  Klik tab "Documents"    

    ![image](https://cloud.githubusercontent.com/assets/3068071/8495982/df6764d8-219b-11e5-9adf-9e478e41740d.png)
    

9.  Explore tabel Process Instances, klik tombol untuk memilih kolom yang bisa ditampilkan seperti terlihat di gambar ini:
    
    Tabel secara default menampilkan process instance yang dalam status "Active", kita dapat melihat instances dengan status lain dengen mengklik tombol disebelah tulisan "Showing"

    ![image](https://cloud.githubusercontent.com/assets/3068071/8496054/781e2d42-219c-11e5-98cb-9ad5f051f06a.png)
    
    

    ![image](https://cloud.githubusercontent.com/assets/3068071/8496054/781e2d42-219c-11e5-98cb-9ad5f051f06a.png)

    
### Melihat Daftar Task dan Mengeksekusi Task

1.  Klik menu Tasks → Task List

    ![image](https://cloud.githubusercontent.com/assets/3068071/8497024/094fa384-21a4-11e5-8585-2071a470891c.png)


2.  Pilih salah satu task dengan mengklik satu task di tabel Task List.

    Detail dari input variabel akan terlihat di bagian kanan window pada tab "Work"

    ![image](https://cloud.githubusercontent.com/assets/3068071/8497069/55e16d04-21a4-11e5-83d5-927d80e08406.png)
    
    > Pada contoh gambar, saya memilih task dengan process instance ID = 9.
    
3.  Klaim salah satu task, dengan mengklik tombol [Claim] atau icon gembok pada tabel Task List
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8497113/af7dd7b2-21a4-11e5-9332-e73bbeca6cc9.png)

    Ketika suatu task diklaim oleh seorang user, maka task tersebut tidak bisa diklaim oleh user lain.

4.  Selesaikan task yang sudah diklaim dengan mengisi field yang ada di box "Output" lalu mengklik tombol [Complete]

    ![image](https://cloud.githubusercontent.com/assets/3068071/8497270/0f37ecbe-21a6-11e5-9969-7188836bca56.png)

    Selain menyelesaikan (Complete) suatu task, task yang di klaim juga dapat di-unclaim (Release) atau di-Save yaitu field atau variabel output disimpan. Proses Save biasanya dilakukan jika kita sudah mengisi field yang diperlukan tapi belum selesai dan ingin menyelesaikannya nanti.
    
5.  Task yang sudah diselesaikan (Completed), dalam contoh Task dengan proses ID = 9,  hilang dari Task List dan proses akan berlanjut mengikuti jalur pada diagram process definition. 
    
    Sekarang kita lihat proses ID = 9 di Process Instance List. Kita tidak akan menemukannya karena proses instance dengan ID = 9 sudah completed. Kita dapat melihat process tersebut di list "Completed".
    
    Klik menu Process Management → Process Instances, lalu klik tombol |Completed|

    ![image](https://cloud.githubusercontent.com/assets/3068071/8497744/e0b6e526-21a9-11e5-867c-03783185c0e4.png)
    
    Pilih instance yang sudah completed, lalu lihat proses modelnya. Sekarang tampilan process model menjadi seperti ini:
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8497744/e0b6e526-21a9-11e5-867c-03783185c0e4.png)
    
10. Kita sudah menyelesaikan eksekusi proses. 

    LAB berikutnya kita akan membuat form UI yang lebih baik dari form yang di-generate secara otomatis.
    
    
    
    
