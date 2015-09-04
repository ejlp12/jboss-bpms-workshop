Silakan lihat dan eksplore kapabilitas dari Form Builder di BPM Suite berikut ini, mudah-mudah membantu.

Referensi dokumentasi:

  - https://access.redhat.com/documentation/en-US/Red_Hat_JBoss_BPM_Suite/6.1/html/User_Guide/sect-Form_Modeler.html
  - http://docs.jboss.org/jbpm/v6.2/userguide/chap-formmodeler.html (Catatan: JBoss BPM Suite 6.1 == jBPM 6.2, karena itu saya referensikan dokumentasi ke jBPM v6.2)


- Mendukung auto generate form dari varibel yang didefinisikan di Human Task pada proses
- Mendukung custom form, yaitu form yang dibuat sendiri (tidak otomatis di-generate) 
- Mendukung perhitungan antar fields dalam sebuah form misalnya field total_amount = amount X unit_price

  ![image](https://cloud.githubusercontent.com/assets/3068071/9673798/546699d6-52d2-11e5-8695-655f4e26f6cc.png)

- Mendukung untuk attach document dari form (https://access.redhat.com/documentation/en-US/Red_Hat_JBoss_BPM_Suite/6.1/html/User_Guide/sect-Form_Modeler.html#Attaching_Documents_to_a_Form)
- Mendukung juga untuk menyimpan dokumen di tempat lain misalnya external Content Management System. Yang diperlukan adalah developer mengimplementasikan custom code untuk menyimpan dokumen.

  > "Ability for you to store your document in a location of your choice. This is defined as Pluggable Variable Persistence and this allows you to store these documents automatically in a centralized content management system (CMS) of choice, behind the scenes"
  > Form yang ada di BPM juga bisa "diambil" untuk diembed di aplikasi external
  > (https://access.redhat.com/documentation/en-US/Red_Hat_JBoss_BPM_Suite/6.1/html/User_Guide/sect-Form_Modeler.html#sect-Rendering_Forms_for_External_Use)

- Mendukung input array pada form, misalnya seperti ini:

  ![image](https://cloud.githubusercontent.com/assets/3068071/9673802/61a3c06a-52d2-11e5-8a73-c9b95a837ddc.png)

- Lookup data bisa diset pada form langsung misalnya untuk dropdown list (combo box) 
- Mendukung Custom Field Type untuk berbagai macam keperluan misalnya lookup data ke database, file upload
- Mendukung customized range (list) untuk field lookup bisa akses ke file, database, dll. Dengan mengimplementasikan class RangeProvider atau SelectValueProvider
  
  Lebih detail bisa dilihat disini: [How to implement data providers in BPMS6 Form Modeler](https://access.redhat.com/solutions/1487113)
  
  Contoh: https://github.com/pefernan/jbpm-form-modeler-examples-src/tree/master/jbpm-form-modeler-dependent-combos
  ```
  @Dependent
  public class CountriesProvider implements RangeProvider {
    Map<String, String> countries = new HashMap<String, String>(  );

    @PostConstruct
    protected void init() {
        countries.put( "es", "Spain" );
        countries.put( "it", "Italy" );
        countries.put( "pt", "Portugal" );
    }

    @Override
    public String getType() {
        return "Countries";
    }

    @Override
    public Map<String, String> getRangesMap( String s ) {
        return countries;
    }
  }
  ```
