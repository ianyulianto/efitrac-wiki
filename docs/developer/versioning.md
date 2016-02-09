# Overview
Pada Efitrac di sertakan fitur versionning untuk mempermudah melakukan upgrade pada module yang di buat. 


---
## Cara Pemakaian Fitur Versioning
Berikut adalah langkah-langkah cara pemakain fitur Versioning :

* File version_info.xml yang di letakkan pada base directory dari module yang ada.
* Membuat isi xml dari version_info.xml dengan format.

```xml
<efitrac>
    <versions>
        <version><!-- Version awal yang di support untuk di upgrade -->
            <name>1.0</name>
            <number>10000000</number><!-- versi dari module secara angka -->
        </version><!-- tanpa update proc karena cuma sebagai penanda -->
        <version>
            <name>1.0001</name>
            <number>10000001</number>
            <update-proc>com.efitrac.module.mfm.Version.update10000000To10000001</update-proc>
        </version>
    </versions>
</efitrac>
```

* Membuat method/fungsi pada class di diskripsikan di xml.

```java
public class Version {
    public String update10000000To10000001() {
        return "Success";
    }
}
```

* Mengubah version di descriptor.xml sessuai dengan version name yang terakhir di buat di version_info.xml, contoh :

```xml
<module name="My First Module"
            version="1.0001"
            category="My Module"
            author="Efitrac"
            installable="1"
            auto_install="1"
    >
```



---
## Cara Kerja Fitur Versioning
Versioning ini dapat di aktifkan dengan melakukan beberapa step :

1. Pendefinisian upgrade yang ada pada file version_info.xml
2. Kalau versi dari module sekarang tidak ada di version_info.xml maka di anggap versi module tersebut tidak di support upgradenya, dan proses upgrade module tersebut akan berhenti.
3. Version_info.xml ada di setiap module, berfungsi untuk penanganan upgrade pertiap module yang ada.
4. Version yang di cek adalah version yang ada di ir.module.module di bandingkan dengan version_info.xml.
6. Proses logic untuk melakukan upgrade ada di method yang di definisikan di tag
"update-proc" akan di execute.

---
## Standarisasi Format Versioning
 Standard penulisan angka pada Versioning :

   RRMMMmmmm

 * R = Release
 * M = major
 * m = minor

## Snippet/Example
Berikut adalah kumpulan dari code snippet atau class/method yang sering di pakai untuk melakukkan update.

### Add or Update Model Field Snippet
```java
String msg; 
ModelService modelService=ServiceBeanResolver.getModelService();
try {
    String modelName="my.new.model";
    modelService.initModel(modelName);
    System.out.println("patch MyNewModel success");
} catch (ModelValidationException e) {
    e.printStackTrace();
    msg = e.getMessage();
}
return msg;
```
TBD :
- explanation dari code

### Update XML View Snippet(TBD)