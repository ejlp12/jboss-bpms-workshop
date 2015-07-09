GIT Repository pada JBoss BPM Suite 6.1 secara default akan membuka port hanya untuk lookback interface (**127.0.0.1 atau localhost**).

Kalau anda mencoba melakukan **koneksi dari IP address lain akan ditolak**.

Untuk membuat Git Repository bisa diakses dari IP address lain maka perubahan konfigurasi yaitu menambahkan system propoerti di file konfigurasi JBoss EAP yaitu di `standalone.xml` atau 1standalone-[[full]-ha]].xml`

Tambahan pada tag `<system-properties>`

```
<property name="org.uberfire.nio.git.daemon.host" value="ip_address"/>
<property name="org.uberfire.nio.git.ssh.host" value="ip_address"/>
```

Lalu **restart** JBoss BPMS

Konfigurasi lainnya bisa dilihat di [http://docs.jboss.org/jbpm/v6.2/userguide/wb.Workbench.html#wb.systemProperties](http://docs.jboss.org/jbpm/v6.2/userguide/wb.Workbench.html#wb.systemProperties)
