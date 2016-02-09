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
Terdapat aturan-aturan yang

| Pendefinisian | String | Object |
|--|--|--|
| - Penjabaran value String| harus menggunakan ' ' | cuma menggunakan Object String biasa tanpa menggunakan ' '|
| contoh : | "('name', '=', 'budi')" | new Object[]{"name", "=", "budi"}|
| - Penjabaran value Integer| tanpa menggunakan '' | menggunakan value Integer|
| contoh : | "('number', '=', 1)" | new Object[]{"number", "=", 1}|
| - Value untuk ID | value untuk ID sama dengan penjabaran value integer | value untuk ID sama dengan penjabaran value integer |

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
| or | | |
| negate/not* | ! |

\* negate belum support Operator between, dan cuma di support untuk pencarian dengan AbstractModel.searchN

TBD :
- Link ke dokumentasi AbstractModel.searchN

### Fungsi-fungsi yang di sediakan pada domain
fungsi-fungsi bawaan di sediakan untuk membantu dan memperkuat kemampuan dari domain. berikut 


### Konversi dari penjabaran String ke List<Object>
untuk menjembatani antara 

### Tabel Perbandingan Fitur ??? TBD

