## Instalasi JBoss BPM Suite 6.1

Instalasi JBos BPMS versi 6.1 sedikit berbeda dengan versi sebelumnya yaitu 6.0.3. Pada versi 6.1, JBoss EAP harus diinstal dahulu, terpisah dari proses instalasi JBoss BPMS. 

1. Instal JDK 1.8

2. Download & Instal JBoss EAP 6.4 and install it

![image](https://cloud.githubusercontent.com/assets/3068071/8325570/e0ec012e-1a84-11e5-8c8c-53f109ad0903.png)

```
java -jar jboss-eap-6.4.0-installer.jar -console
```

3. Download & Instal JBoss BPM Suite 6.1

![image](https://cloud.githubusercontent.com/assets/3068071/8325307/933e59d8-1a82-11e5-9e2c-ae99fbe6cca8.png)

https://www.jboss.org/products/bpmsuite/download/

![image](https://cloud.githubusercontent.com/assets/3068071/8325490/4c48c7f0-1a84-11e5-999e-ff032a1db1d4.png)

```
java -jar jboss-bpmsuite-6.1.0.GA-installer.jar -console
```

4. Jalankan JBoss BPMS

```
cd /Servers/BPMS-6.4
./standalone.sh -c standalone-full.xml
```

