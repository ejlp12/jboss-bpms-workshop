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

    ![image](https://cloud.githubusercontent.com/assets/3068071/8492762/70d016b8-2179-11e5-9f3a-cc48e99efc45.png)
    
3. Isi semua fields form tersebut lalu klik Ok.

4. Lakukan langkah 2 dan 3 sekali lagi dengan masukan nilai yang berbeda untuk semua fields yang ada pada form.

5.  Klik  menu Process Management → Process Instances
    Anda akan lihat dua process instance yang _"hidup"_ (belum completed) di JBoss BPMS.

    Pilih salah satu process instance tersebut dengan mengklik salah satu baris pada daftar Process Instances, dan lihat detil informasi dari process instance tersebut di view sebelah kanan.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8492794/f6de7aec-2179-11e5-81f4-327f8976cce8.png)
    
6.  Perhatikan informasi Current Activities di tab "Instance Detail". Apa maksudnya _"3/Jul/15 11:58:40: 1 - Approve Data (HumanTaskNode)"_?

    ![image](https://cloud.githubusercontent.com/assets/3068071/8492851/0d67bfc0-217b-11e5-889e-3db608b63267.png) 
    
    
    
