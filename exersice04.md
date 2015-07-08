## Membuat User Task memiliki Group atau Actor secara dimanis

Suatu Task node dapat didelegasikan ke suatu group atau user. Sehingga group atau user tersebut dapat melihat task tersebut untuk kemudian diklaim  dan dikerjakan. 

Task didelegasikan dengan menset properties "Group" atau "Actor"

![image](https://cloud.githubusercontent.com/assets/3068071/8566743/6858acba-258a-11e5-9cfa-157c166db3c8.png)

Property tersebut dapat kita isi dengan beberapa nama user atau beberapa nama group dengan karakter huruf pemisah koma, misalnya: `group1,group2,admin` atau `user01,user02,user03`

Ada kalanya kita ingin membuat agar User Task didelegasikan ke group atau user secara dinamis. Misalnya saya ingin sebuah User Task bernama "Periksa Data" akan didelegasikan ke group PEMERIKSA1 jika proses memiliki data `umur` antara 0  sampe dengan < 12 tahun ,tapi jika data `umur` nilainya antara 12 sampai 20 tahun maka task tersebut didelegasikan ke group PEMERIKSA2, dan jika data `umur` nilainya diatas 20 tahum maka didelegasikan ke group PEMERIKSA3.

Hal tersebut dapat dilakukan dengan membuat sebuah logic penentuan group atau actor sebelum task "Periksa Data". Task "Periksa Data"-nya sendiri perlu kita set agar property "Groups" memiliki nilai sebuah variabel bukan konstanta. Nilai variable tersebut ditulis dengan tanda #{NAMA_VARIABLE} yang **nilainya akan diambil dari Variable Definitions (Process Variables) yang memiliki nama NAMA_VARIABLE.

Kita coba latihan dengan proses sederhana:

Buatlah proces diagram seperti ini.

![image](https://cloud.githubusercontent.com/assets/3068071/8564201/61a3ab5c-2573-11e5-8e98-dce2acef0181.png)

User task pertama yaitu "My Group Task" akan dapat dikerjakan oleh group `taskadmin`. User yang termasuk dalam group `taskadmin` dapat menginput pada task form, nama orang yang dapat mengerjakan User task kedua yaitu "My Auto Assign Task"

User task kedua yaitu "My Auto Assign Task" akan otomatis didelegasikan ke seseorang yang ditentukan oleh orang yang mengerjakan task pertama.

### Petunjuk

1. Gunakan nilai #{myactor} sebagai nilai Actor pada property task kedua.
2. Assign input dari form task pertama ke Variable Definitions dengan nama `myactor`


### Tambahan
Bagaimana jika aktor task kedua ingin dibuat selalu sama dengan actor (user) yang mengerjakan task pertama. Misalnya yang mengerjakan task pertama adalah `ejlp12` yang termasuk dalam group `taskadmin` maka task kedua otomatis didelegasikan ke `ejlp12` juga.

Mau tau caranya?

Masukan script ini di "On Exit Action" pada task pertama.

```java
kcontext.setVariable("myactor", ((org.jbpm.workflow.instance.node.HumanTaskNodeInstance)(kcontext.getNodeInstance())).getWorkItem().getResult("ActorId")); 
```
