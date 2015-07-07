1. Buat Maven Project dengan pom.xml sebagai berikut


```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>
        <groupId>org.jugvale.jbpm.workitemhandler</groupId>
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

2. Create Work Item Handler

```
package ejlp.sample;

import org.drools.core.process.instance.WorkItemHandler;
import org.kie.api.runtime.process.WorkItem;
import org.kie.api.runtime.process.WorkItemManager;

public class HelloWorkItemHandler implements WorkItemHandler {

        public void abortWorkItem(WorkItem wi, WorkItemManager wim) {
                System.out.println("Oh no, my item aborted..");

        }

        public void executeWorkItem(WorkItem wi, WorkItemManager wim) {
                System.out.println("Hello World!");
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
   
7. Set Knowledge Base and Sessions
   Tambahkan Knowledge Base baru, dan Make as default
   Tambahakan Knowledge Session, [Add], pilih sebagai default, klik Edit
   Tambahkan Work Item Handlers, [Add], set *Name* dan *Type*, klik Ok
   Klik tombol [Save]
   
8.  Tambahakan konfigurasi `WorkDefinitions.wid`

    ```
      [
        "name" : "TestWorkItemHandler",
        "displayName" : "HelloWorld",
        "icon" : "defaultemailicon.gif"
      ] ,
    ```
    
    ```
    import org.drools.core.process.core.datatype.impl.type.StringDataType;
    import org.drools.core.process.core.datatype.impl.type.ObjectDataType;

    [
      [
        "name" : "TestWorkItemHandler",
        "displayName" : "HelloWorld",
        "icon" : "defaultemailicon.gif"
      ] ,
      [
        "name" : "Email",
        "parameters" : [
          "From" : new StringDataType(),
          "To" : new StringDataType(),
          "Subject" : new StringDataType(),
          "Body" : new StringDataType()
      ],
      "displayName" : "Email",
      "icon" : "defaultemailicon.gif"
    ],
    **DIHAPUS**
  ```
  
  9. Buat Process Definitions
  
  