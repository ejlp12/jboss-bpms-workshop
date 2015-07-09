## Membuat BPM Client & Menggunakan KIE Remote API

1. Login ke Business Central, akses menu Authoring -> Administration.
   Lalu klik submenu Repositories -> Clone Repositories untuk meng-cloning repository dari `https://github.com/ejlp12/jbossbpms-sample1.git`
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/8581936/10f7b380-25ee-11e5-8289-811bcee223c8.png)
  
   Buka project `basicproject` dari repository tersebut, lalu buka process diagram `simple_proc.bpmn2`
   
   Kemudian build dan deploy project tersebut.
   
2. Jalankan (start) proses definition tersebut.

3. Dengan menggunakan JBoss Developer Studio, buat sebuah project Maven dengan cara mengimport dari SCM (GIT) yaitu dari url berikut:

  `https://github.com/ejlp12/bpm-6.1-rest-standalone-client.git`
  

4. Set Maven central di JBDS dengan cara: buka Preference Window, lalu ketik "maven" di search menu, pilih "JBoss Maven Integration" di menu kiri
   
   Klik tombol [Configure Maven Repositories...]
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/8582220/a2e1fdf4-25ef-11e5-921b-da646802cfda.png)
   
   Akan muncul window Maven Repositories, klik tombol [Add Repository..]
   Pada window Add Maven Repository, klik drop-down menu (combo box) dan pilih `redhat-techpreview-all-repository`
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/8582319/4ac8b0a8-25f0-11e5-9963-3841b8a0f874.png)
   
5. Pada project yang baru saja diimport, lakukan update Maven Project. Klik kanan project `bpm-6.1-rest-standalone-client` pilih menu Maven lalu Update Project
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/8582415/d8b4562e-25f0-11e5-919c-94f8bb96b70b.png)
   
   Lalu klik "Force update of Snapshot/Releases" dan klik tombol [Ok]
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/8582505/705ee340-25f1-11e5-9d6b-3bc8f5ff8054.png)

6. Buka file java `ejlp.sample.Main` dan ubah field-field static berikut DEPLOYMENT_ID, APP_URL, USER, PASSWORD

   Perhatikan dan baris per baris dari file tersebut.
   

7. Jalankan `ejlp.sample.Main` sebagai Java Application dan perhatikan hasilnya.
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/8582625/2eeff696-25f2-11e5-88a7-f58300ca779e.png)

### Latihan Mandiri

Ubah/tambahkan kode Java dari class `ejlp.sample.Main` agar task terakhir yang di-CLAIM dan dikerjakan (COMPLETE) sehingga task tersebut tidak lagi muncul di Task List.

### Pentunjuk

1. Gunakan google.com :-)
2. Lihat User Task status lifecycle berikut:

   ![image](https://docs.jboss.org/jbpm/v6.2/userguide/images/TaskService/WSHT-lifecycle.png)
   
3. Lihat dokumentasi.


4. Code:

      
      ```
      long TASK_ID = 100; // Cobalah sebuah Task ID yang terlihat di Task List di Business Central
      Task task = taskService.getTaskById(TASK_ID);
		  if (task.getTaskData().getStatus() == Status.Ready) {
			
				taskService.claim(TASK_ID, "user01");
				taskService.start(TASK_ID, "user01");
			
				Map<K, V> out_params = new HashMap<>();
				out_params.put("out_approve", new Boolean(true));
			
				taskService.complete(TASK_ID, "user01", out_params);
			
			}
			```

  
