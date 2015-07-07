## Membuat Task yang dijalankan Paralel

Setelah selesai mengerjakan **Exercise01**, coba ubah agar proses menjadi seperti ini:

* Setelah task "Approve Data",  akan ada dua Task yang harus dijalankan bersamaan (parallel).
  Kedua task tersebut akan dijalankan apapun hasil approval (approve maupun tidak approve maka dua task berikutnya akan dieksekusi) 

* Untuk memudahkan, buatlah kedua Task tersebut sebagai Script Task, dengan masing-masing mengluarkan output di Console Window
  1. Script Task #1 dengan nama "Kirim Email", mengeluarkan ouput "** EMAIL TERKIRIM **"
  2. Script Task #2 dengan nama "Kirim SMS", mengeluarkan output "** SMS TERKIRIM **"
  
* **Jika dan hanya jika** kedua task tersebut selesai maka proses berhenti (selesai).

Jalankan Process Definition yang sudah dibuat hingga proses berhenti (mencapai End Node) dan lihat proses diagram hasil jalannya proses.

Petunjuk:

Pilih mana yang kira-kira sesuai dari proses berikut, dan tentukan jenis Gateway node-nya jika diperlukan:

Gambar #1:

![image](https://cloud.githubusercontent.com/assets/3068071/8539490/96593344-24a6-11e5-8354-3eaf46c23f9e.png)

Gambar #2:

![image](https://cloud.githubusercontent.com/assets/3068071/8539460/4c276188-24a6-11e5-9db4-82da6039eb60.png)

Gambar #3:

![image](https://cloud.githubusercontent.com/assets/3068071/8539434/d81f0db8-24a5-11e5-9470-4406489df957.png)
