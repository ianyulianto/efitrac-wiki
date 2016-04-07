TBD :
<br>- Di rapikan

# Overview
Inherit View adalah mekanisme pada efitrac untuk mengubah view tanpa harus mengubah definisi view utama, ini bertujuan agar aplikasi dapat di custom tanpa mengotori view utama.

---
## Macam-macam cara untuk mencari lokasi node yang akan di beri operasi penyisipan

### Dengan menggunakan nama field secara langsung
Mencari dengan menggunakan nama dari field yang sudah terdaftar terlebih dahulu untuk menentukan lokasi operasi penyisipan

```xml
    <field name="" position="before">
        <field name="new_field">
    </field>
```

### Dengan menggunakan XPath
Mencari dengan menggunakan fasilitas standard pada XML yaitu XPath, cara penggunaan XPath sama dengan metode XPath pada umumnya, jadi pengguna dapat melajari cara penggunaaan XPath dari dokumentasi penggunaan XPath yang tersebar.

```xml
    <xpath expr="//tab-page[@string='Detail']" position="before">
        <tab-page string="Request">
            
        </tab-page>
    </xpath>
```

## Macam-macam cara yang ada untuk menyisipkan sebuah bagian view
### inside(default)
Field tambahan akan di taruh di dalam node yang di inginkan.

```xml
    <xpath expr="//tab-page[@string='Detail']" position="inside">
        <field name="keterangan" width="60%"/>
    </xpath>
```

### replace
    <field name="other1" position="replace">
        <field name="alamat" width="60%"/>
    </field>
### after
Field tambahan akan di taruh setelah node yang di inginkan.

```xml
    <field name="other1" position="after">
        <field name="alamat" width="60%"/>
    </field>
```
### before
Field tambahan akan di taruh sebelum node yang di inginkan.

```xml
    <field name="other1" position="before">
        <field name="alamat" width="60%"/>
    </field>
```
### attributes
```xml
    <field name="other" position="attributes">
        <attribute name="readonly">1</attribute>
    </field>
```

