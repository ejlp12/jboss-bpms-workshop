## Instalasi Patch JBoss BPM Suite 6.1.1

Asumsi anda menginstall JBoss BPM Suite versi 6.1.0 di direktori `/Servers/BPMS-6.1/`, berikut langkah-langkah untuk menginstal patch **6.1.1**

1. Download patch file dari http://access.redhat.com
2. Ekstrak `jboss-bpmsuite-6.1.1-patch.zip`, misalnya di `/Installer/BPMS_6.1/jboss-bpmsuite-6.1.1-patch`
3. Stop JBoss BPMS jika sedang jalan
4. Lalu jalankan perintah berikut:

```
cd /Installer/BPMS_6.1/jboss-bpmsuite-6.1.1-patch
./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/business-central.war eap6.x-bc
./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/dashbuilder.war eap6.x-dashbuilder
./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/kie-server.war generic-kie-server
./apply-updates.sh /Servers/BPMS-6.1 eap6.x

```

5. Jalankan kembali JBoss EAP
   Jika tidak ada keluaran error berarti proses patching sudah berhasil.


Berikut contoh output hasil perintah tersebut:

```
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:~
| => cd /Installer/BPMS_6.1/jboss-bpmsuite-6.1.1-patch
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:~/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.1-patch
| => ls -l
total 24
-rw-rw-r--@  1 ejlp12  staff  1174 May 28 20:39 README.txt
-rw-rw-r--@  1 ejlp12  staff  1439 May 28 20:39 apply-updates.bat
-rw-r--r--   1 ejlp12  staff  3107 Jul  6 12:04 apply-updates.log
-rwxr-xr-x@  1 ejlp12  staff  1335 May 28 20:39 apply-updates.sh
drwxr-xr-x   6 ejlp12  staff   204 Jul  6 12:04 backup
-rw-r--r--@  1 ejlp12  staff  4357 May 28 20:32 blacklist.txt
drwxr-xr-x@  3 ejlp12  staff   102 May 28 20:39 conf
drwxr-xr-x@  9 ejlp12  staff   306 May 28 20:39 libs
drwxr-xr-x@ 10 ejlp12  staff   340 May 28 20:39 updates
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:/Installer/BPMS_6.1/jboss-bpmsuite-6.1.1-patch
| => ./apply-updates.sh
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
11:34:16.211 [main] ERROR - Incorrect arguments specified! The program expects two mandatory parameters: <path-to-distribution> and <type-of-distribution>!

Usage: apply-updates.[sh|bat] <path-to-distribution-root> <type-of-distribution>
Description: JBoss BRMS/BPM Suite client patching tool used to apply updates to existing installations.

IMPORTANT: Do not apply the updates to running applications. Shutdown the server first.

Supported distribution types:
	 - eap6.x
	 - eap6.x-bc
	 - eap6.x-dashbuilder
	 - eap6.x-kie-server
	 - generic
	 - generic-bc
	 - generic-dashbuilder
	 - generic-kie-server
	 - was8
	 - was8-bc
	 - was8-dashbuilder
	 - was8-kie-server
	 - wls12c
	 - wls12c-bc
	 - wls12c-dashbuilder
	 - wls12c-kie-server
	 - bpmsuite-engine
	 - planner-engine
	 - supplementary-tools
	 - integration-pack

Examples:
	Patch EAP 6.x Business Central WAR:
		./apply-updates.[sh|bat] <some-path>/jboss-eap-6.4/standalone/deployments/business-central.war eap6.x-bc

	Patch Generic KIE Server WAR:
		./apply-updates.[sh|bat] <some-path-to-tomcat-home>/webapps/kie-server.war generic-kie-server

	Patch whole WebLogic 12c bundle:
		./apply-updates.[sh|bat] <path-to-unzipped-wls12c-bundle> wls12c

	Patch Planner engine bundle:
		./apply-updates.[sh|bat] <path-to-unzipped-planner-bundle> planner-engine

Notes:
  - Working dir needs to be the directory of this script!
  - Java is recommended to be JDK and version 6 or later
  - The environment variable JAVA_HOME should be set to the JDK installation directory
      For example (linux): export JAVA_HOME=/usr/lib/jvm/java-6-sun
      For example (mac): export JAVA_HOME=/Library/Java/Home
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:/Installer/BPMS_6.1/jboss-bpmsuite-6.1.1-patch
| => ./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/business-central.war eap6.x-bc
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
11:36:20.404 [main] INFO  - File blacklist.txt found at /Users/ejlp12/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.1-patch/blacklist.txt.
11:36:20.417 [main] INFO  - Backing-up (copying) contents of directory /Servers/BPMS-6.1/standalone/deployments/business-central.war to ./backup/2015-07-06-11-36-20/eap6.x-bc.
11:36:25.506 [main] INFO  - Removing old files from distribution root /Servers/BPMS-6.1/standalone/deployments/business-central.war
11:36:27.758 [main] INFO  - Applying updates to distribution root /Servers/BPMS-6.1/standalone/deployments/business-central.war
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:/Installer/BPMS_6.1/jboss-bpmsuite-6.1.1-patch
| => ./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/dashbuilder.war eap6.x-dashbuilder
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
12:02:10.870 [main] INFO  - File blacklist.txt found at /Users/ejlp12/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.1-patch/blacklist.txt.
12:02:10.880 [main] INFO  - Backing-up (copying) contents of directory /Servers/BPMS-6.1/standalone/deployments/dashbuilder.war to ./backup/2015-07-06-12-02-10/eap6.x-dashbuilder.
12:02:12.169 [main] INFO  - Removing old files from distribution root /Servers/BPMS-6.1/standalone/deployments/dashbuilder.war
12:02:13.342 [main] INFO  - Applying updates to distribution root /Servers/BPMS-6.1/standalone/deployments/dashbuilder.war
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:/Installer/BPMS_6.1/jboss-bpmsuite-6.1.1-patch
| => ./apply-updates.sh /Servers/BPMS-6.1/standalone/deployments/kie-server.war generic-kie-server
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
12:03:54.624 [main] INFO  - File blacklist.txt found at /Users/ejlp12/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.1-patch/blacklist.txt.
12:03:54.633 [main] INFO  - Backing-up (copying) contents of directory /Servers/BPMS-6.1/standalone/deployments/kie-server.war to ./backup/2015-07-06-12-03-54/generic-kie-server.
12:03:54.902 [main] INFO  - Removing old files from distribution root /Servers/BPMS-6.1/standalone/deployments/kie-server.war
12:03:55.144 [main] INFO  - Applying updates to distribution root /Servers/BPMS-6.1/standalone/deployments/kie-server.war
________________________________________________________________________________
| ejlp12 @ ejlp-macbook:/Installer/BPMS_6.1/jboss-bpmsuite-6.1.1-patch
| => ./apply-updates.sh /Servers/BPMS-6.1 eap6.x
Using Java binary found at /Library/Java/JavaVirtualMachines/jdk1.8.0_40.jdk/Contents/Home/bin/java
12:04:26.408 [main] INFO  - File blacklist.txt found at /Users/ejlp12/Documents/03_RH_JBOSS_INSTALLER/BPMS_6.1/jboss-bpmsuite-6.1.1-patch/blacklist.txt.
12:04:26.420 [main] INFO  - Directory /Servers/BPMS-6.1 is valid distribution root.
12:04:26.420 [main] INFO  - Backing-up (copying) contents of directory /Servers/BPMS-6.1 to ./backup/2015-07-06-12-04-26/eap6.x.
12:04:40.845 [main] INFO  - Removing old files from distribution root /Servers/BPMS-6.1
12:04:50.269 [main] INFO  - Applying updates to distribution root /Servers/BPMS-6.1
```
