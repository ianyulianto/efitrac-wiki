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

### Aturan-aturan dalam pembuatan domain

### Operator yang ada pada domain

| Nama Operator | Simbol Dari Operator |
|--|--|
| equals | = |


### Fungsi-fungsi yang di sediakan pada domain
fungsi-fungsi bawaan di sediakan untuk membantu dan memperkuat kemampuan dari domain. berikut 

## Tabel Perbandingan Fitur ??? TBD

