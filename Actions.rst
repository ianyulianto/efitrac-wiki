==========
Pengenalan
==========

Action adalah sebuah data yang akan dijadikan tindakan. Terdapat tiga jenis
Action, yaitu sebagai berikut:

``window``
----------

```xml
<action id="action_id_1" type="window">
    <properties>
        <property name="model">mock.currency</property>
        <property name="view_type">
            <view id="view_id_1" />
        </property>
        <property name="view_mode">
            <views>
                <view type="form" />
                <view type="tree" />
            </views>
        </property>
        <property name="domain">
            <where>
                <eq key="symbol" value="Rp" />
            </where>
        </property>
        <property name="limit">100</property>
        <property name="target">new</property>
    </properties>
</action>
```
Action ``window`` akan menampilkan ``view`` dari ``model`` yang sudah didaftarkan.
Dalam action ``window``, terdapat beberapa property yang harus ditentukan
nilainya. Property-property tersebut adalah sebagai berikut,

- ``model``
    ```xml
    <property name="model">mock.currency</property>
    ```
    Property yang menentukan ``model`` mana yang menjadi acuan.

- ``view_type``
    ```xml
    <property name="view_type">
        <view id="view_id_1" />
    </property>
    ```
    Property ``view_type`` menjelaskan bahwa jika sebuah item dipilih, maka
    tampilan (``view``) yang telah ditentukan akan disajikan.

- ``view_mode``
    ```xml
    <property name="view_mode">
        <views>
            <view type="form" />
            <view type="tree" />
        </views>
    </property>
    ```
    Property ini digunakan untuk memberikan pilihan terhadap ``view`` yang dapat
    dipakai untuk melihat data-data yang dipunyai oleh ``model``.

- ``target``
    ```xml
    <property name="target">current</property>
    ```
    Seperti namanya, property ``target`` mempunyai fungsi di mana ``view`` akan
    ditampilkan, apakah di ``tab`` browser sekarang, atau di ``tab`` baru. Nilai
    dari property ini adalah ``current`` dan ``new``. Nilai awal dari property
    ini adalah ``current``.

- ``limit``
    ```xml
    <property name="limit">80</property>
    ```
    Membatasi data yang akan tampil adalah fungsi dari property ``limit``. Nilai
    awal dari property ini adalah **80**.

- ``domain``
    ```xml
    <property name="domain">
        <where>
            <eq key="symbol" value="Rp" />
        </where>
    </property>
    ```
    Property ``domain`` ini dapat dikatakan seperti *where clause* pada SQL.
    Diawali dengan tag ``<where>`` bagian query pun dimulai. Operator yang dapat
    digunakan adalah sebagai berikut,

    - ``eq``
        ```xml
        <eq key="premise" value="comparison" />
        ```
        Operator Equals (=)

    - ``ge``
        ```xml
        <ge key="premise" value="comparison" />
        ```
        Operator Greater Equals (>=)

    - ``gt``
        ```xml
        <gt key="premise" value="comparison" />
        ```
        Operator Greater Than (>)

    - ``le``
        ```xml
        <le key="premise" value="comparison" />
        ```
        Operator Less Equals (<=)

    - ``lt``
        ```xml
        <lt key="premise" value="comparison" />
        ```
        Operator Less Than (<)

``url``
-------

```xml
<action id="action_id_2" type="url">
    <properties>
        <property name="url">http://google.com</property>
        <property name="target">current</property>
    </properties>
</action>
```
Action ini akan mengarahkan tampilan ke tautan url yang ditentukan. Ada dua
property yang ada di Action ini, yaitu:

- ``url``
    ```xml
    <property name="url">http://google.com</property>
    ```
    Link url tautan.


- ``target``
    ```xml
    <property name="target">current</property>
    ```
    Di mana tautan tersebut akan ditampilkan. Bernilai ``current`` atau ``new``
    dan bernilai awal ``current``.