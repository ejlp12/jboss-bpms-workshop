## Membuat New Business Process Definition

Dalam lab ini kita akan membuat sebuah Business Process Diagram (Process Definition) sederhana yang hasil akhirnya seperti ini:

![image](https://cloud.githubusercontent.com/assets/3068071/8491337/ee93c63a-2160-11e5-913c-30e45cbaee95.png)

Process Definition tersebut akan memiliki dua form, form pertama adalah input data (name & description) dan form kedua adalah proses approval dimana pengguna (user) dapat mengubah field description dan menentukan apakah dia akan approve atau reject (tidak approve).

1.  Login ke Business Central
2.  Buka Project Authoring perspective (Authoring → Project Authoring).
3.  Pada Project Explorer (Project Authoring → Project Explorer), pilih project dimana Process definition ingin dibuat.
    Dalam hal ini Anda harus memilih (memastikan) project "example / repository2 / basicproject" yaitu project yang sudah dibuat pada lab sebelumnya.
   
    ![image](https://cloud.githubusercontent.com/assets/3068071/8490833/c7356578-2159-11e5-81e4-2795360f4eb8.png)

4.  Dari menu perspective, pilih New Item → Business Process   
   
    ![image](https://cloud.githubusercontent.com/assets/3068071/8490859/3d40a250-215a-11e5-8370-f65abc7ca182.png)
   
5.  Dari dialog window "Create New Business Process", isi nama business process : `simple_proc`, dan pastikan package yang dipilih adalah `example.basicproject` lalu klik OK
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8490872/6970ab22-215a-11e5-9f3e-4f1feec56dbf.png)
    
6.   Akan muncul sebuah Business Process view, dengan tab "Process Modeling" **canvas** seperti ini
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8490906/2e0bcb7e-215b-11e5-85dd-fd5118ec44a6.png)
    
    Canvas tersebut kita gunakan untuk membuat diagram BPMN.
    Klik tombol bertanda << di bagian kanan atas untuk melihat properties dari BPMN-Diagram, tanda << akan merubah menjadi >>
    
7. Klik start event node, gambar lingkarang dengan warna hijau, kemudian klik tanda kotak kecil pada gambar yang muncul disebelah kanan node tersebut. Lihat ilustrasi berikut
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8490930/abeb08de-215b-11e5-836f-8d521d60ac7b.png)
    
8. Hasilnya adalah seperti gambar berikut. Sekarang klik Task node, gambar kotak yang tersambung dengan start node, kemudian klik tanda lingkaran pada gambar yang muncul disebalah kanan node tersebut.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8490965/644a54fc-215c-11e5-9676-4570c24f8a8e.png)
    
9.  Klik lagi Task Node, lalu klik tanda _kunci pas_ dibagian bawah, akan muncul pop-up menu. Pilih User Task pada menu tersebut. Ini akan membuat task node tersebut menjadi tipe User Task (kadang disebut juga Human Task)
   
    ![image](https://cloud.githubusercontent.com/assets/3068071/8491000/02ce18de-215d-11e5-9b17-2b343d4c59d2.png)
   
10. Klik dua kali User Task untuk memberi nama node tersebut. Berinama node tersebut: `Approve Data`
    Memberi nama suatu task juga dapat dilakukan dengan mengeset properties view disebelah kanan.
    
    Lalu set juga "Task Name" pada properties view, dengan nilai `approve-data` (Jangan gunakan spasi untuk Task Name)
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8491107/74b5f20e-215e-11e5-9ccd-11299f7ed82e.png)
    
### Menset properties dari komponen pada process definition

11. Klik pada bagian kosong di canvas, sehingga anda dapat melihat properties dari Process Definition seperti gambar dibawah ini. Pada tabel properties klik dibagian kanan dari kolom "Varibel Definitions"

    > Variable definitions adalah variabel-variabel dari proses, yang akan disimpan selama proses hidup, mulai dari proses tersebut diinisialisasi (terdapat instance dari process tersebut) sampai proses tersebut berakhir.
    > Variabel-variabel proses tersebut dapat diakses oleh semua task yang ada dalam diagram.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8491173/80bf9df6-215f-11e5-8a35-0277aee8fb0f.png)
    
  Akan muncul editor untuk variable definitions, buatlah ketiga variable berikut dengan mengklik tombol "Add Variable" dibagian atas. Kemudian klik tombol Ok
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8491245/2454db2a-2160-11e5-81e3-e7a4ca42acbb.png)
    
    
### Menset lebih lanjut properties dari User Task    
    
12. Klik lagi node "Approve Data", set properties tabel sebagai berikut 
    Property "Groups" dengan nilai `taskadmin`

    > Property Group berarti task ini nantinya dapat dilihat atau diklaim untuk kemudian dikerjakan oleh user yang memiliki group atau role `taskadmin`. Kita bisa definisikan beberapa group sekaligus dengan memisahkan menggunakan tanda koma, misalnya `taskadmin,hrd,finance`
    > Jika task ini ingin dapat dilihat atau diklaim oleh user tertentu maka anda perlu menset nilai dari properti **Actors**
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8491918/bd1d4bc0-216b-11e5-9223-412c00562557.png)
    
13. Set "DataInputSet" untuk menambahkan variabel input yang dapat diterima oleh task tersebut DARI Process Definition.
    Buat dua varibel input dengan nama `in_name` dan `in_desc` lalu klik tombol Ok
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8491450/ef0df836-2162-11e5-8698-4c2f3d0d96b0.png)
    
    > Lihat desain form yang akan kita buat pada gambar paling atas.
    > Dua variabel input pada User Task ini akan diperoleh dari Variable Definitions yang diset pada saat proses dijalankan yaitu pada form user interface (UI) pertama.
    > Sedangkan variabel `approve` pada proses definition tidak akan diset pada saat awal proses dijalankan, jadi kita tidak perlu mengambil variabel tersebut karena pasti nilai-nya 0. Varibel `approve` akan jadi output dari User Task ini yang nilainya didapat dari user saat menentukan dari form UI kedua.


14. Set "DataOuputSet" untuk menambahkan variabel output yang dapat _diberikan_ oleh task tersebut KE Process Definition.
    Buat dua varibel input dengan nama `out_desc` dan `out_approve` lalu klik tombol Ok
    
    > Pada desain form kedua, kita akan membuat field `name` tidak bisa diubah oleh orang yang melakukan "Approval Data", pengguna hanya bisa mengubah atau mengisi field `description` dan menentukan apakah dia akan approve atau tidak.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8491470/693689de-2163-11e5-8826-f5bd4770d66f.png)
    
15. Set "Assignment", untuk melakukan copy data dari Varibel Definitions ke variabel task (Data Input) atau copy data dari variabel task (Data Ouput) ke Variable Definitions.
    
    Buatlah assignment seperti ini, dengan mengklik tombol [Input Mapping] sebanyak dua kali, dan juga tombol [Output Mapping] sebanyak dua kali.
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8491535/032c82f4-2165-11e5-921c-9fecf4c6389c.png)
    
    > Kita tidak menggunakan [Input Assignment] karena tidak ada varibel yang akan kita _hardcode_ nilainya.
    Input Assignment dapat kita gunakan jika ada Data Input yang ingin kita set nilainya dengan suatu nilai tertentu tanpa meng-copy dari Variable Definitions. Contoh misalnya seperti ini:
    >
    > ![image](https://cloud.githubusercontent.com/assets/3068071/8491600/94939808-2166-11e5-848f-3d1b2ef100cb.png)

16. Save diagram 

    ![image](https://cloud.githubusercontent.com/assets/3068071/8492329/44aa4eca-2172-11e5-9c5c-367541785ec0.png)
    
### Selesai
    
