## Instalasi Patch JBoss BPM Suite 6.1.3

Asumsi anda menginstall JBoss BPM Suite versi 6.1.0 di direktori `/Servers/BPMS-6.1/`, berikut langkah-langkah untuk menginstal patch **6.1.3**

1. Download patch file dari http://access.redhat.com
2. Ekstrak `jboss-bpmsuite-6.1.3-patch.zip`, misalnya di `/Installer/BPMS_6.1/jboss-bpmsuite-6.1.3-patch`
   Ada baiknya anda baca dulu file `README.txt` yang ada di dalam direktori hasil ekstrak tersebut.
   Baca juga [dokumentasi untuk patch](https://access.redhat.com/documentation/en-US/Red_Hat_JBoss_BPM_Suite/6.1/html/Installation_Guide/chap-Patching_and_Upgrading_Red_Hat_JBoss_BPM_Suite.html)
3. Stop JBoss BPMS jika sedang jalan
4. Lalu jalankan perintah berikut:

```
cd /Installer/BPMS_6.1/jboss-bpmsuite-6.1.3-patch
./apply-updates.sh /Servers/BPMS-6.1 eap6.x
./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/business-central.war eap6.x-bc
./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/dashbuilder.war eap6.x-dashbuilder
./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/kie-server.war eap6.x-kie-server
```

Output hasil masing-masing perintah diatas bisa dilihat dibagian paling bawah artikel ini.

5. Jalankan kembali JBoss EAP
   Jika tidak ada keluaran error berarti proses patching sudah berhasil.


Berikut contoh output hasil perintah tersebut:


Detail informasi patch ini bisa dilihat di:

   * Red Hat JBoss BPM Suite 6.1 Update 1 - https://access.redhat.com/jbossnetwork/restricted/softwareDetail.html?softwareId=38283
   * Red Hat JBoss BPM Suite 6.1 Update 2 - https://access.redhat.com/jbossnetwork/restricted/softwareDetail.html?softwareId=38993
   * Red Hat JBoss BPM Suite 6.1 Update 3 - https://access.redhat.com/jbossnetwork/restricted/softwareDetail.html?softwareId=39991



### Output

Berikut output dari hasil 

```
________________________________________________________________________________
$ cd /Installer/BPMS_6.1/jboss-bpmsuite-6.1.3-patch/
________________________________________________________________________________
$ ./apply-updates.sh /Servers/BPMS-6.1-NEW eap6.x
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
22:25:29.131 [main] INFO  - File blacklist.txt found at /Users/ejlp12/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.3-patch/blacklist.txt.
22:25:29.146 [main] INFO  - Directory /Servers/BPMS-6.1-NEW is valid distribution root.
22:25:29.146 [main] INFO  - Backing-up (copying) contents of directory /Servers/BPMS-6.1-NEW to ./backup/2015-09-30-10-25-29/eap6.x.
22:25:46.444 [main] INFO  - Removing old files from distribution root /Servers/BPMS-6.1-NEW
22:25:59.672 [main] INFO  - Applying updates to distribution root /Servers/BPMS-6.1-NEW
22:26:03.052 [main] WARN  - File standalone/deployments/business-central.war/WEB-INF/classes/ErraiApp.properties is on blacklist, creating a new file with suffix .new instead of overwriting. Please investigate the differences and apply them manually.
22:26:03.610 [main] WARN  - File standalone/deployments/business-central.war/WEB-INF/classes/workbench-policy.properties is on blacklist, creating a new file with suffix .new instead of overwriting. Please investigate the differences and apply them manually.
22:26:04.094 [main] WARN  - File standalone/deployments/business-central.war/WEB-INF/web-ui-server.xml is on blacklist, creating a new file with suffix .new instead of overwriting. Please investigate the differences and apply them manually.
22:26:04.097 [main] WARN  - File standalone/deployments/business-central.war/WEB-INF/web.xml is on blacklist, creating a new file with suffix .new instead of overwriting. Please investigate the differences and apply them manually.
________________________________________________________________________________
$  ./apply-updates.sh /Servers/BPMS-6.1-NEW/standalone/deployments/business-central.war eap6.x-bc
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
22:26:32.164 [main] INFO  - File blacklist.txt found at /Users/ejlp12/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.3-patch/blacklist.txt.
22:26:32.174 [main] INFO  - Backing-up (copying) contents of directory /Servers/BPMS-6.1-NEW/standalone/deployments/business-central.war to ./backup/2015-09-30-10-26-32/eap6.x-bc.
22:26:38.034 [main] INFO  - Removing old files from distribution root /Servers/BPMS-6.1-NEW/standalone/deployments/business-central.war
22:26:41.215 [main] INFO  - Applying updates to distribution root /Servers/BPMS-6.1-NEW/standalone/deployments/business-central.war
22:26:43.690 [main] WARN  - File WEB-INF/classes/ErraiApp.properties is on blacklist, creating a new file with suffix .new instead of overwriting. Please investigate the differences and apply them manually.
22:26:44.030 [main] WARN  - File WEB-INF/classes/workbench-policy.properties is on blacklist, creating a new file with suffix .new instead of overwriting. Please investigate the differences and apply them manually.
22:26:44.197 [main] WARN  - File WEB-INF/web-ui-server.xml is on blacklist, creating a new file with suffix .new instead of overwriting. Please investigate the differences and apply them manually.
22:26:44.199 [main] WARN  - File WEB-INF/web.xml is on blacklist, creating a new file with suffix .new instead of overwriting. Please investigate the differences and apply them manually.
________________________________________________________________________________
$  ./apply-updates.sh /Servers/BPMS-6.1-NEW/standalone/deployments/dashbuilder.war eap6.x-dashbuilder
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
22:26:57.959 [main] INFO  - File blacklist.txt found at /Users/ejlp12/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.3-patch/blacklist.txt.
22:26:57.968 [main] INFO  - Backing-up (copying) contents of directory /Servers/BPMS-6.1-NEW/standalone/deployments/dashbuilder.war to ./backup/2015-09-30-10-26-57/eap6.x-dashbuilder.
22:26:59.158 [main] INFO  - Removing old files from distribution root /Servers/BPMS-6.1-NEW/standalone/deployments/dashbuilder.war
22:27:00.631 [main] INFO  - Applying updates to distribution root /Servers/BPMS-6.1-NEW/standalone/deployments/dashbuilder.war
________________________________________________________________________________
$  ./apply-updates.sh /Servers/BPMS-6.1-NEW/standalone/deployments/kie-server.war eap6.x-kie-server
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
22:27:42.773 [main] INFO  - File blacklist.txt found at /Users/ejlp12/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.3-patch/blacklist.txt.
22:27:42.780 [main] INFO  - Backing-up (copying) contents of directory /Servers/BPMS-6.1-NEW/standalone/deployments/kie-server.war to ./backup/2015-09-30-10-27-42/eap6.x-kie-server.
22:27:43.116 [main] INFO  - Removing old files from distribution root /Servers/BPMS-6.1-NEW/standalone/deployments/kie-server.war
22:27:43.323 [main] INFO  - Applying updates to distribution root /Servers/BPMS-6.1-NEW/standalone/deployments/kie-server.war

```

