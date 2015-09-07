==========
Pengenalan
==========

Fields adalah kumpulan dari komponen ``field``. Komponen ``field`` sendiri dapat
diartikan seperti kolom disebuah table. Komponen ini dapat ditentukan akan
disimpan pada database atau hanya sebagai kolom pembantu yang mana tidak disimpan
pada database. Jenis dari komponen ``field`` dikelompokkan menjadi tiga macam,
yaitu:

- **Common**
    Kelompok umum seperti input box, calendar, dan lain-lain.
- **Relational**
    Field-field yang mempunyai relasi ke Model lain, seperti *Foreign Key* pada
    SQL.
- **Functional**
    Field yang secara umum tidak disimpan pada database, di mana nilainya berasal
    dari kembalian ``function`` baik dari server maupun dari client.

Common
------

- **Text**
    ```xml
    <field id="field_id_1" type="text" label="Ini Field Free Text (Memo)" />
    ```
    Sebuah multiline inputbox yang mempunyai sifat seperti ``<textarea>`` yang
    dipunyai oleh html.

- **Boolean**
    ```xml
    <field id="field_id_2" type="boolean" label="ini Field Boolean" />
    ```
    Field checkbox yang bernilai ``True`` atau ``False``.

- **Selection**
    ```xml
    <field id="field_id_3" type="selection" />
    ```
    Field yang mempunyai sifat seperti combobox yang mempunyai daftar nilai yang
    ditentukan dan memilih sebuah nilai dari daftar tersebut.

- **Char**
    ```xml
    <field id="field_id_4" type="char" label="Ini Field Characters" />
    ```
    Sebuah input box single-line.

- **Integer**
    ```xml
    <field id="field_id_5" type="integer" label="Ini Field Integer" />
    ```
    Hampir sama seperti **Char**, tetapi hanya menerima angka tanpa decimal.

- **Float**
    ```xml
    <field id="field_id_6" type="float" label="Ini Field Float" />
    ```
    Sama seperti **Integer** dengan perbedaan field ini dapat menerima bilangan
    decimal.

- **Date**
    ```xml
    <field id="field_id_7" type="date" label="Ini Field Date(Tanggal Saja)" />
    ```
    Sebuah input kalender yang bernilai tanggal. Waktu dalam field ini diabaikan.

- **Datetime**
    ```xml
    <field id="field_id_8" type="datetime" label="Ini field Datetime (tanggal dan waktu)" />
    ```
    Sama seperti field **Date**, hanya saja waktu dalam field ini dicatat.

- **File**
    ```xml
    <field id="field_id_9" type="file" label="Ini field untuk upload file" />
    ```
    Field yang digunakan untuk upload sebuah atau beberapa file sekaligus.

- **Location**
    ```xml
    <field id="field_id_10" type="location" label="ini Field untuk location" />
    ```
    Field yang menampilkan peta lokasi. Nilai dari field ini adalah geolocation
    Latitude dan Longitude.

- **Canvas**
    ```xml
    <field id="field_id_11" type="canvas" label="Ini field canvas" />
    ```
    Field yang nilai inputnya berasal dari goresan stylus atau tangan pengguna
    (e.g. tanda tangan).

- **Scanner**
    ```xml
    <field id="field_id_12" type="scanner" label="Ini field Scanner" />
    ```
    Seperti namanya, field ini digunakan untuk scan code (e.g. Barcode, QRCode).
    Input berasal dari thrid party.

Relational
----------

- **Many to One**
    ```xml
    <field id="field_id_14" type="many2one" label="Ini field Many to One" />
    ```
    Relasi Many to One ini dapat diartikan seperti sebuah Combobox yang mana
    daftar itemnya berasal dari Model yang berelasi (e.g. Banyak ``product``
    termasuk sebuah ``category``).

- **One to Many**
    ```xml
     <field id="field_id_15" type="one2many" label="Ini field One to Many" />
    ```
    Field ini dapat diartikan seperti Order Detail pada Order. (e.g. Sebuah
    ``order`` mempunyai banyak ``order_detail``).

- **Many to Many**
    ```xml
    <field id="field_id_16" type="many2many" label="Ini field many to many" />
    ```
    Field ini pasti mempunyai sebuah Model *"Moderator"* atau penengah agar
    dapat terjalinnya relasi Many to Many.

.. Functional (*Pending*)
.. ----------------------

.. Dalam kelompok ini, field yang digunakan hanya satu, yaitu field ``functional``.
Field ini dapat mengambil sifat dari field-field lain. Selain itu, field ini juga
dapat ditentukan apakah akan disimpan pada database atau tidak.

========
Property
========

Setiap field mempunyai daftar properti yang dimiliki. Properti Field juga
dikelompokkan menjadi dua macam, yaitu properti *common* dan *unique*.
Properti umum yang dimaksudkan adalah properti yang dipunyai oleh semua field,
sedangkan properti khusus adalah properti yang hanya dipunyai oleh field tertentu.
Property dari field dimulai dengan tag ``<properties>`` sebagai penanda wadah
dari daftar property. Sedangkah property sendiri memiliki tag ``<property>``.

Common
------

Property yang berada pada kelompok *Common* **tidak harus** ditulis atau diset.
Pada awalnya, property-property tersebut telah mempunyai nilai awal. Berikut
adalah property-property yang masuk ke dalam kelompon *Common*,

- ``required``
    ```xml
    <field id="field_id_1" type="text" label="Ini Field Free Text (Memo)">
        <properties>
            <property name="required">True</property>
        </properties>
    </field>
    ```
    Bernilai ``True`` atau ``False``. Seperti namanya, property ini mengharuskan
    sebuah ``field`` harus mempunyai nilai, tidak boleh kosong
    (e.g. empty string), atau ``NULL``.

- ``read_only``
    ```xml
    <field id="field_id_1" type="text" label="Ini Field Free Text (Memo)">
        <properties>
            <property name="read_only">True</property>
        </properties>
    </field>
    ```
    Bernilai ``True`` atau ``False``. Property ini menunjukan bahwa ``field``
    tidak bisa diedit datanya.

- ``help``
    ```xml
    <field id="field_id_1" type="text" label="Ini Field Free Text (Memo)">
        <properties>
            <property name="help">
                Bagian Help~!
            </property>
        </properties>
    </field>
    ```
    Property yang berisi deskripsi tentang ``field`` agar tujuan adanya
    ``field`` tersebut menjadi lebih jelas.

Unique
------

Kebalikan dari property *Common*, property ini hanya dipunyai oleh masing-masing
``field``. Jika ada property yang tidak seharusnya di sebuah ``field``, maka
akan diabaikan. Berikut adalah daftar ``field`` yang mempunyai property *unique*
beserta property *unique* masing-masing,


- **Text**
    ```xml
    <field id="field_id_1" type="text" label="Ini Field Free Text (Memo)">
        <properties>
            <property name="length">250</property>
        </properties>
    </field>
    ```
    Property yang dipunyai field ``Text`` hanyalah property ``length``. Property
    ini dimaksudkan jumlah karakter yang ada tidak boleh melebihi batas yang
    telah ditentukan. Karater yang dimaksud tidak lepas dari ``whitespace``.

    Jika tidak diset property length, maka akan dianggap tak terbatas.

- **Selection**
    ```xml
    <field id="field_id_3" type="selection">
        <properties>
            <property name="entries">
                <entries>
                    <entry id="entry_id_1">Entry 1</entry>
                    <entry id="entry_id_2">Entry 2</entry>
                    <entry id="entry_id_3">Entry 3</entry>
                </entries>
            </property>
        </properties>
    </field>
    ```
    Property dari field ``selection`` adalah property ``entries``. Property
    ini mempunyai anak tag ``<entrues>`` di mana element tersebut berisi daftar
    item yang dipunyai. Setiap item yang didaftarkan ditandai dengan tag
    ``<entry>``, tidak lupa dengan attribute ``id`` yang dipunyai sebagai
    identitas entry tersebut. Value dari tag ``<entry>`` adalah kumpulan
    karakter yang akan ditampilkan.

    Jika tidak diset property-nya, maka akan terlihat kosong.

- **Char**
    ```xml
    <field id="field_id_4" type="char" label="Ini Field Characters">
        <properties>
            <property name="length">20</property>
            <property name="hidden">True</property>
            <property name="format">^[A-Z0-9._%+-]+@[A-Z0-9.-]+\\.[A-Z]{2,6}$</property>
        </properties>
    </field>
    ```
    Field ``char`` mempunyai beberapa macam property *unique* yang dijelaskan
    sebagai berikut,

    - ``length``
        Property yang digunakan untuk membatasi karakter yang diisikan.

    - ``hidden``
        Property yang mengubah nilai yang tampil menjadi tidak terlihat nilai
        aslinya, seperti input password.

    - ``format``
        Property yang mengikat format dari nilai yang diinputkan. Menggunakan
        format *regex* dari **Java**.

- **Integer**
    ```xml
    <field id="field_id_5" type="integer" label="Ini Field Integer">
        <properties>
            <property name="digit">5</property>
        </properties>
    </field>
    ```
    Property yang menentukan batas banyaknya *digit* yang diperbolehkan.

- **Float**
    ```xml
    <field id="field_id_6" type="float" label="Ini Field Float">
        <properties>
            <property name="digit">3,6</property>
        </properties>
    </field>
    ```
    Property yang menentukan batas banyaknya *digit* dan *decimal* yang
    diperbolehkan. Pada contoh di atas dapat diartikan sebagai maksimum digit
    angka **sebelum** *delimiter* adalah 3 dan **setelah** *delimiter*
    adalah 6 (e.g. 999,123456). Symbol dari *delimiter* akan tergantung
    ``locale`` dan jika property tidak diset, maka digit angka *setelah* maupun
    *sebelum* adalah tak terbatas.

- **Date**
    ```xml
    <field id="field_id_7" type="date" label="Ini Field Date(Tanggal Saja)">
        <properites>
            <property name="date_format">dd-MMM-yyyy</property>
        </properties>
    </field>
    ```
    Property ``date_format`` menjelaskan representasi waktu yang ada. Format yang
    digunakan adalah format waktu dari **Java**. Jika ada format **waktu**,
    maka akan bernilai **0**.

- **Datetime**
    ```xml
    <field id="field_id_8" type="datetime" label="Ini field Datetime (tanggal dan waktu)">
        <properties>
            <property name="date_format">dd-MMM-yyyy HH:mm:ss</property>
        </property>
    </field>
    ```
    Property ``date_format`` menjelaskan representasi waktu yang ada. Format yang
    digunakan adalah format waktu dari **Java**.

- **File**
    ```xml
    <field id="field_id_9" type="file" label="Ini field untuk upload file">
        <properties>
            <property name="type">
                <include>
                    image/*
                    application/*
                </include>
                <exclude>
                    image/jpeg
                    image/png
                    application/json
                </exclude>
            </property>
        </property>
    </field>
    ```
    Property pada field ``file`` akan menentukan tipe file apa saja yang boleh
    di-upload. Penamaan tipe file mengikuti aturan dari **MIME**. Seperti yang
    telihat di atas, yang akan dilihat adalah yang diperbolehkan dahulu
    (``include``), setelah itu yang tidak diperbolehkan (``exclude``).

- **Location**
    ```xml
    <field id="field_id_10" type="location" label="ini Field untuk location">
        <properties>
            <property name="anchor">
                <geolocation>
                    <latitude>123</latitude>
                    <longitude>-20</longitude>
                </geolocation>
            </property>
        </properties>
    </field>
    ```
    Property ``anchor`` menandakan di mana peta lokasi akan dibukakan untuk
    pertama kali.

    Jika tidak diset, maka peta akan menunjukan semua benua.

- **Canvas**
    ```xml
    <field id="field_id_11" type="canvas" label="Ini field canvas" />
    ```
    Field yang nilai inputnya berasal dari goresan stylus atau tangan pengguna
    (e.g. tanda tangan).

- **Scanner**
    ```xml
    <field id="field_id_12" type="scanner" label="Ini field Scanner">
        <properties>
            <property name="target">Barcode</property>
        </properties>
    </field>
    ```
    Property ``target`` mempunyai fungsi sebagai penanda jika field ``scanner``
    digunakan untuk membaca/ scan sebuah kode, contohnya adalah Barcode. Nilai
    dari property ini adalah sebagai berikut,

    - ``Barcode``
        ```xml
        <property name="target">Barcode</property>
        ```
        Untuk membaca kode dari Barcode.

    - ``QRCode``
        ```xml
        <property name="target">QRCode</property>
        ```
        Untuk membaca kode dari QRCode.

    Jika tidak diset, maka nilai awal dari properti ini adalah ``Barcode``.

- **Many to One**
    ```xml
    <properties>
        <property name="ref_model">
            <model id="account.company" />
        </property>
    </properties>
    ```

    Pada field bersifat *relational field* ini mempunyai property ``ref_model``
    yang digunakan untuk mencatat referensi identifier (seperti Primary Key) dari
    model yang dituju.

- **One to Many**
    ```xml
    <properties>
        <property name="ref_model">
            <model id="account.company">
                <field id="field_id_1" />
            </model>
        </property>
    </properties>
    ```

    Seperti field ``many2one``, field ini juga mempunyai property ``ref_model``,
    perbedaan ada di bagian nilainya. Tag ``<model>`` mempunyai nilai sebuah tag
    ``<field>``. Field ini **tidak disimpan** pada database, melainkan hanya
    sebagai field pembantu untuk mencari relasinya.

- **Many to Many**
    ```xml
    <properties>
        <property name="ref_model">
            <model id="account.company">
                <field id="field_id_1" />
            </model>
            <this>
                <field id="field_id_1" />
            </this>
            <moderator id="account.company_momod" />
        </property>
    </properties>
    ```

    Untuk field terakhir ini mempunyai property yang cukup banyak di dalam tag
    ``ref_model``. Ada tiga tag yang harus ada, yaitu ``<model>``, ``<this>``,
    ``<moderator>``. Tag ``<model>`` dan tag ``<this>`` adalah informasi yang
    menentukan field mana yang menjadi pacuan. Sedangkan tag ``<moderator>``
    bernilai Model mana yang akan menjadi penengah dari relasi.

=======
Default
=======

Field dapat mempunyai *default value* atau nilai awal. Nilai awal tersebut
didefinisikan pada bagian tag ``<default>``.

```xml
<fields>
... code omitted ...
</fields>
<default>
    <field id="field_id_1">Default Value</field>
</default>
```

Dapat dilihat contoh xml di atas adalah contoh penggunaan tag ``<default>``. Nilai
dari tag tersebut adalah nilai **valid** field yang dituju. Ketentuan *valid*
yang dimaksud adalah nilai awal tersebut harus mengikuti peraturan yang ada pada
field, mulai dari format dan