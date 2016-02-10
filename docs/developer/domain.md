# Overview
Domain adalah mekanisme dari efitrac untuk melakukan filterisasi data, query ke Database langsung di buat dari domain ini. terdapat 2 tipe domain pada efitrac yaitu domain yang dijabarkan dengan menggunakan String dan dijabarkan dengan menggunakan Java Object. Domain dapat di jabarkan saat melakukkan coding pada Java atau pada saat mendefinisikan Xml tampilan.

---
## Cara Pembuatan Domain
Cara pembuatan domain dengan String atau dengan Object agak berbeda, untuk Domain yang dijabarkan dengan menggunakan String di buat dengan menggunakan bantuan class Domain, untuk tipe Object sendiri cukup dengan menggunakan class List dan turunnannya. 

### Pembuatan Domain Dengan Menggunakan String


Struktur pembuatan domain dengan String :

```java
Domain domain = Domain.Builder("<representasi domain yang di buat>").build();
```



### Pembuatan Domain Dengan Menggunakan Object 

Struktur pembuatan domain dengan Object :

```java
List<Object> domain = new ArrayList<>();
domain.add(new Object[]{"<Field Yang Akan Di Bandingkan>", "<Operator Pembanding>", <Nilai Yang Akan Di Bandingkan>);
domain.add("<kondisi or atau and>");//kondisi "and" atau "or" kalau di perlukan
```

### Tata cara dalam pembuatan domain
Terdapat tata cara yang perlu di perhatikan dalam mendefinisikan domain, dan terdapat sedikit perbedaan dalam pendefinisian dengan String ataupun dengan Object. Berikut adalah cara-cara pendefinisian domain :

| Pendefinisian | String | Object |
|--|--|--|
| Penjabaran value String| harus menggunakan ' ' | cuma menggunakan Object String biasa tanpa menggunakan ' '|
|  | "('name', '=', 'budi')" | new Object[]{"name", "=", "budi"}|
| Penjabaran value Integer| tanpa menggunakan '' | menggunakan value Integer|
|  | "('number', '=', 1)" | new Object[]{"number", "=", 1}|
| Value untuk ID | value untuk ID sama dengan penjabaran value integer | value untuk ID sama dengan penjabaran value integer |
||||
| Penjabaran value untuk "in" atau "not in"|||
|  |"('ids', 'in', [1,2,3])"|List&lt;Integer&gt; paramIds = new ArrayList<>();<br>paramIds.add(1);<br>paramIds.add(2);<br>paramIds.add(3);<br>new Object[]{"ids", "in", paramIds};|
| Penjabaran value untuk between | unknown (TBD) | |
|  |-| List&lt;Object&gt; list = new ArrayList<>();<br>list.add(&lt;start value&gt;);<br>list.add(&lt;end value&gt;);<br>new Object[]{"date","between", list};| 
| Penjabaran fungsi | di mulai dengan '=' | di mulai dengan '=' |
|  | "('user_id', '=', "=current_user_id()")" | new Object[]{"user_id","=", "=current_user_id()"};| 

### Operator yang ada pada domain

| Nama Operator | Simbol Dari Operator |
|--|--|
| equals | = |
| not equals | != |  
| less equals than | <= |
| less than | < |
| more equals than | >= |
| more than | > |
| like | like |
| not like | not like |
| not in | not in |
| in | in |
| between | between |

### Operator kondisi yang ada pada domain

| Nama Kondisi | Simbol Dari Kondisi |
|--|--|
| and | & |
| or | &#124; |
| negate/not* | ! |

\* *negate belum support Operator between, dan cuma di support untuk pencarian dengan AbstractModel.searchN*

TBD : <br>
- Link ke dokumentasi AbstractModel.searchN

### Fungsi-fungsi yang di sediakan pada domain

Fungsi-fungsi bawaan di sediakan untuk membantu dan memperkuat kemampuan dari domain. berikut adalah fungsi-fungsi yang di support oleh domain :


* current_user_id

>Untuk mendapatkan user id yang sedang login saat ini.
<br>Contoh :

>```java
"[('id','=','=current_user_id()')]"
```

* str_to_date

>Untuk mengubah inputan dari string menjadi date.
<br>Contoh :

>```java
"[('tanggal','=','=str_to_date()')]"
```

* date_create(instance tanggal, tipe modifier, nilai modifier)

>Membuat tanggal dan mengubah tanggal agar sessuai dengan kebutuhan.
<br>Contoh :

>```java
"[('tanggal','=','=date_create('now','sec',1)')]"
```

>List value parameter 1 

>| value | keterangan |
|--|--|
| now | tanggal saat ini |

>List value parameter 2 

>| value | keterangan |
|--|--|
| sec | ditambahkan dengan detik |
| day | ditambahkan dengan hari |
| month | ditambahkan dengan bulan |
| year | ditambahkan dengan tahun |
| time | ditambahkan dengan jam,menit,detik dengan format jam:menit:detik |


* today

>Untuk mendapatkan tanggal saat ini.
<br>Contoh :

>```java
"[('tanggal','=','=today()')]"
```

* ref(...)

>Untuk mendapatkan id dari data yang di definisikan di xml
<br>Contoh :

>```java
"[('id','=','=ref('module.record_name')')]"
```

TBD : 
<br>- Kata-katanya rasanya masih kurang tepat

* exec(jenis, nama model, nama fungsi)

>Untuk mengeksekusi method yang ada pada sebuah model.
<br>Contoh :

>Pendefinisian domain 

>```xml
"[('id','=','=exec('func','module.Model','getMyCustomFunc($parent_id)')')]"
```

>Pendefinisian fungsi

>```java
public Integer getMyCustomFunc(Integer parentId) {

        Integer id;

	//Do something here


        return id;
    }
```

* eval

>???

TBD : 
<br>- cari info lebih lanjut soal eval

### Konversi dari penjabaran String ke List&lt;Object&gt;

Untuk menjembatani antara domain dengan representasi String atau Domain dapat menggunakan perintah "NExpression.toObjectList(String domain)" apabila ingin mengubah langsung dari String ke penjabaran tipe Object, apabila sudah dalam bentuk object Domain dapat menggunakan "Domain.toObjectList()" secara langsung.

### Fitur khusus saat menggunakan domain dengan String pada XML untuk view

#### Parameter

Fungsi parameter digunakan untuk mengirimkan nilai dari form yang di buat ke domain, parameter di mulai dengan tanda "$" di ikuti dengan nama field yang ada pada model.

Contoh : 
<br>contoh sederhana

```xml
domain="[('id','=','$parent_id')]"
```

contoh dengan menggunakan fungsi

```xml
domain="[('id','=','=exec('func','module.Model','getMyCustomFunc($parent_id)')')]"
```

Parameter khusus selain field yang ada pada model :

| Nama | Kegunaan |
|--|--|
| parent_id | untuk mendapatkan id dari model parent dari form |




