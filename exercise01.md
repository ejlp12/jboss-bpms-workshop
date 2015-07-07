## Membuat proses dengan gateway

Buatlah proses seperti ini dengan mengedit proses yang sudah anda buat pada LAB03, LAB04, LAB05

![image](https://cloud.githubusercontent.com/assets/3068071/8538267/5bb6bf02-2494-11e5-9313-5e7cedf4ded1.png)

Saat task Approve Data anda "approve", maka hasilnya harusnya seperti ini:

![image](https://cloud.githubusercontent.com/assets/3068071/8538315/f3904604-2494-11e5-8e96-1ea9ecd30e76.png)

Sedangkan saat task Approve Data anda "tidak approve", maka hasilnya harusnya seperti ini:

![image](https://cloud.githubusercontent.com/assets/3068071/8538394/e1bcbe0c-2495-11e5-97e6-2fc5bf19efec.png)

## Petunjuk Pengerjaan

Berikut clue untuk mengerjakan proses tersebut:

1. Delete node atau arrow (tanda panah)

![image](https://cloud.githubusercontent.com/assets/3068071/8538287/82a206ee-2494-11e5-80fb-f6597bdf3837.png)

2. Nilai property "Script" dari Script Task

![image](https://cloud.githubusercontent.com/assets/3068071/8538304/b769b5ca-2494-11e5-8cb2-ec1eaf9847eb.png)

3. Nilai property "Expression" dari tanda panah "approve"

![image](https://cloud.githubusercontent.com/assets/3068071/8538315/f3904604-2494-11e5-8e96-1ea9ecd30e76.png)

4. Nilai property "Expression" dari tanda panah "not approve" hampir sama dengan diatas tapi diset Condition = "is false"

