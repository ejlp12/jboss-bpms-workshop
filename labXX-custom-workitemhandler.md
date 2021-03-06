1. Buat Maven Project di Eclipse (JBDS) dengan `pom.xml` sebagai berikut:

   > Catatan: Saya menggunakan JBoss BPM versi 6.2.1

   ```
   <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>ejlp.sample.workitemhandler</groupId>
        <artifactId>hello-workitemhandler</artifactId>
        <version>1.0</version>
        <name>Hello WorlItemHandler</name>
        <description>The simples WorkItemHandler for jbpm 6</description>

        <dependencies>
            <dependency>
                <groupId>org.jbpm</groupId>
                <artifactId>jbpm-flow</artifactId>
                <version>6.0.3-redhat-9</version>
                <scope>provided</scope>
            </dependency>
        </dependencies>
        
        <repositories>
            <repository>
                <id>jboss-ga-repository</id>
                <name>JBoss GA Tech Preview Maven Repository</name>
                <url>http://maven.repository.redhat.com/techpreview/all</url>
                <layout>default</layout>
                    <releases>
                        <enabled>true</enabled>
                        <updatePolicy>never</updatePolicy>
                    </releases>
                <snapshots>
                    <enabled>false</enabled>
                    <updatePolicy>never</updatePolicy>
                </snapshots>
            </repository>
        </repositories>        
   </project>
   ```

2. Buat sebuah Java class yang akan menjadi Custom Service Task yang kita sebut  Work Item Handler 

   ```
   package ejlp.sample;

   import org.drools.core.process.instance.WorkItemHandler;
   import org.kie.api.runtime.process.WorkItem;
   import org.kie.api.runtime.process.WorkItemManager;

   public class HelloWorkItemHandler implements WorkItemHandler {

        public void abortWorkItem(WorkItem wi, WorkItemManager wim) {
                System.out.println("Oh no, my item aborted.." + wi.getParameter("yourname") );

        }

        public void executeWorkItem(WorkItem wi, WorkItemManager wim) {
                System.out.println("Hello " + wi.getParameter("yourname") );
        }

   }
   ```

3.  Build project `mvn clean install`

    Hasilnya adalah file `hello-workitemhandler-1.0.jar` di direktori `target/`

4.  Login ke Business Central dengan user/role `admin`, lalu akses menu Authoring -> Artifact Repository.

    ![image](https://cloud.githubusercontent.com/assets/3068071/8534429/6e9c2572-2466-11e5-8a73-dd08bdd5eb05.png)
    
    Lalu upload file `hello-workitemhandler-1.0.jar`
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/8534505/2505afb8-2467-11e5-802f-ea8a1aa3f7e0.png)

5. Buat project baru    

6. Tambahakan project depedencies

   Klik tombol [Add from Repositories], pilih file jar yang sudah kita upload.

   Klik tombol [Save]
   
7.  Tambahakan konfigurasi `WorkDefinitions.wid` dengan teks berikut:

   ```
      [
        "name" : "HelloWorld",
        "parameters" : [
          "yourname" : new StringDataType()
      ],        
        "displayName" : "HelloWorld",
        "icon" : "defaultemailicon.gif"
      ] ,
   ```
   Sehingga menjadi seperti ini:
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/12844133/291aba1e-cc30-11e5-861d-e50f7095fccd.png)
  
   Kemudian kilik tombol [Save].
  
8. Buat Process Definitions

   Buat sebuah Process Definition.
   
   Lihat di panel sebelah kiri, anda bisa lihat sebuah Service Task dengan nama "HelloWorld"
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/8551234/85240eec-24ff-11e5-948a-28b51a9c7419.png)

9. Buka project editor dengan mengklik tombol [Open Project Editor] di project explorer

   ![image](https://cloud.githubusercontent.com/assets/3068071/12844410/b37bf5f0-cc31-11e5-9399-83c3c0685a61.png)
   
   kilik tombol [Knowledge Base Settings: Project General Setting] lalu pilih "Knowledge bases and sessions"
   

   Tambahkan Knowledge Base baru dan berinama `EjlpKBase` (sembarang nama), dan klik "Make default"
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/12844495/3b6f9fe8-cc32-11e5-8cda-8c151331ffea.png)

   Tambahakan Knowledge Session, dengan mengkilik tombol [Add], dan berinama `EjlpKSession` (sembarang nama) kemudian pilih sebagai "default", klik Edit
   
   Tambahkan Work Item Handlers, dengan mengkilik tombol [Add], lalu set *Name* `HelloWorld` dan *Type* `ejlp.sample.HelloWorkItemHandler`, klik Ok
   
   ![image](https://cloud.githubusercontent.com/assets/3068071/12844544/83a09baa-cc32-11e5-8c3b-aa5098835cb4.png)

   Klik tombol [Ok]  
  
   Klik tombol [Save] di kanan atas.
   
10. Deploy project.

    Kembali ke "Project General Setting"
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/12845028/a67baf18-cc35-11e5-9c86-874c0f9ff7af.png)
    
    kemudian klik [Build] > [Build and Deploy]
    
   Deploy gagal?
   
11. Deploy (LAGI) 

    ![image](https://cloud.githubusercontent.com/assets/3068071/12845558/4e5e5e3a-cc39-11e5-8ed6-50f4d7f8633d.png)
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/12845090/1544fc38-cc36-11e5-81f2-160e356eedc9.png)

    ![image](https://cloud.githubusercontent.com/assets/3068071/12845080/02f05df2-cc36-11e5-8347-8d5e69b546c0.png)
    
    Hasilnya bisa dilihat dengan seperti dibawah ini. Klik menu Deploy > Process Deployment
    
    ![image](https://cloud.githubusercontent.com/assets/3068071/12845171/c8667ec2-cc36-11e5-80e4-aa97f0cfc30b.png)


Test

![image](https://cloud.githubusercontent.com/assets/3068071/12845439/7385ad54-cc38-11e5-9527-9c921ad6b4e2.png)
