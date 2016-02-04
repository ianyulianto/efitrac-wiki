# Overview
Pada Efitrac di sertakan fitur versionning untuk mempermudah melakukan upgrade pada module yang di buat. 


---
## Cara Pemakaian Fitur Versioning
Berikut adalah langkah-langkah cara pemakain fitur Versioning :

1. file version_info.xml yang di letakkan pada base directory dari module yang ada.
2. membuat isi xml dari version_info.xml dengan format.

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

3. Membuat method/fungsi pada class di diskripsikan di xml.

```java
public class Version {
    public String update10000000To10000001() {
        return "Success";
    }
}
```

4. Mengubah version di descriptor.xml sessuai dengan version name yang terakhir di buat di version_info.xml, contoh :

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

1. Pendefinisian upgrade yang ada di file version_info.xml
kalau versi dari module sekarang tidak ada di version_info.xml maka di anggap versi module tersebut tidak di support upgradenya.
2. version_info.xml ada di setiap module, berfungsi untuk penanganan upgrade .
3. version yang di cek adalah version yang ada di ir.module.module di bandingkan dengan version_info.xml.
4. proses logic untuk upgrade ada di method yang di definisikan di tag
"update-proc" akan di execute.

---
## Standarisasi Format Versioning
 Standard penulisan angka pada Versioning :

   RRMMMmmmm

 * R = Release
 * M = major
 * m = minor

