==========
Pengenalan
==========

Menu memiliki fungsi sebagai **navigator** halaman. Menu dibagi menjadi tiga
jenis, yaitu ``root``, ``container``, ``sub-menu``. Sebelum menjelaskan tentang
penggunaan dari ketiga jenis menu, penjelasan umum tentang menu akan dijelaskan
sebagai berikut,

```xml
<?xml version="1.0" encoding="UTF-8"?>
<efitrac>
    <menus>
        <menu id="menu_id_1" label="Menu 1">
            <properties>
                <property name="action">open_window_1</property>
                <property name="seqNo">100</property>
            </properties>
        </menu>
        <menu id="menu_id_2" label="Menu 2">
            <properties>
                <property name="parent">menu_id_1</property>
                <property name="seqNo">200</property>
            </properties>
        </menu>
        <menu id="menu_id_3" label="Menu 3">
            <properties>
                <property name="parent">menu_id_1</property>
                <property name="action">open_window_2</property>
                <property name="seqNo">114</property>
            </properties>
        </menu>
    </menus>
</efitrac>
```

Root tag ``<efitrac>`` akan mengawali semua file descriptor yang ada. Berawal dengan
tag ``<menus>``, daftar menu akan didaftarkan. Tag ``<menu>`` mempunyai dua
attribute yang wajib, yaitu ``id`` dan ``label``. Attribute ``id`` akan menjadi
identifier dari sebuah menu yang nantinya dijadikan sebagai referensi tautan.
Attribute ``label`` akan berfungsi sebagai label dari menu.

Seperti yang sudah dijelaskan, ``menu`` mempunyai tiga jenis, yaitu sebagai
berikut,

- ``root``
    Jenis ini akan tampil pada awal mula web dijalankan.

- ``container``
    Menu jenis ``container`` adalah menu yang **tidak** mempunyai ``action`` dan
    mempunyai parent.

- ``sub-menu``
    Menu ini mempunyai sifat seperti menu pada umumnya. Mempunyai action dan
    parent.

========
Property
========

Menu juga mempunyai property yang dapat menunjang performa. Berikut adalah
daftar menu yang ada pada menu,

- ``parent``
    ```xml
    <properties>
        <property name="parent">menu_id_1</property>
    </properties>
    ```
    Bernilai identifier atau ``id`` dari menu yang lain yang dianggap sebagai
    parent.

- ``action``
    ```xml
    <properties>
        <property name="action">action_id_1</property>
    </properties>
    ```
    Berasal dari komponen Action_.

- ``seqNo``
    ```xml
    <properties>
        <property name="seqNo">1000</property>
    </properties>
    ```
    Bernilai sebuah **Integer** yang menentukan urutan dari menu yang diperlihatkan.
    Jika tidak diset, maka nilai awalnya adalah 0.

Jenis menu mempunyai sebuah template property yang dapat dijadikan sebagai
referensi. Template property tersebut adalah sebagai berikut,

- ``root``
    Menu jenis ini tidak mempunyai nilai ``action`` dan ``parent``.

- ``container``
    ```xml
    <properties>
        <property name="parent">menu_id_1</property>
    </properties>
    ```
    Property ``parent`` yang merujuk ke menu lain, menjadikan sebuah menu menjadi
    menu dengan jenis ``container``.

- ``sub-menu``
    ```xml
    <properties>
        <property name="parent">menu_id_1</property>
        <property name="action">open_window_2</property>
    </properties>
    ```
    Property ``parent`` merujuk ke menu lain dan menu ``action`` merujuk ke Action_
    yang sudah didaftarkan.



.. _Action: https://github.com/pararaton/modular/wiki/Action
