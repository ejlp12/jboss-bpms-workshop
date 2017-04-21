## Mengunakan Signal Event dan Timer

Buatlah proses diagram dengan kasus seperti ini:

1. User A memulai proses dengan memasukan input field "Nama Klien" dan "Deskripsi"

2. Kemudian user B, akan menerima data tersebut, dia bisa melihat data yang diinput dan bisa melakukan persetujuan (approval).

3. Jika user B setuju (approve) maka akan dikirimkan Email notifikasi ke Klien dan proses selesai.
   
   Gunakan Script Task seperti pada contoh/latihan sebelumnya sebagai simulasi pengiriman email.
   
4. Jika user B tidak setuju (not approve) maka akan dikirimkan Email notifikasi ke Klien, selain itu Klien dapat mengajukan keberatan dalam jangka waktu 5 menit. (Jangka waktu dibuat pendek agar mudah saat dites).

  Jika dalam jangka waktu itu tidak ada event keberatan dari Klien maka proses selesai.

5. Keberatan dari Klien harus melalui persetujuan user C.  Keputusan user C dapat mengubah nilai persetujuan yaitu dari "not approve" menjadi "approve"









[Clue]

https://docs.jboss.org/jbpm/v6.0/userguide/jBPMBPMN2.html#d0e3180

![image](https://cloud.githubusercontent.com/assets/3068071/25266623/febb5f90-269b-11e7-883a-42b28a328d1c.png)





