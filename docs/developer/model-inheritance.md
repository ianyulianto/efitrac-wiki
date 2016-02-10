# Overview
Model Inheritance di gunakan untuk ...

## Inheritance Pada Efitrac
Model Inheritance pada efitrac ada 3 macam, dan ketiganya dapat di gunakan dalam pengembangan module-module efitrac, berikut adalah jenis-jenis dari model inheritance yang ada :
### Standard Model Inheritance
Standard Model Inheritance adalah
### Reference Model Inheritance
Reference Model Inheritance adalah
### Partial Model Inheritance
Partial Model Inheritance di gunakan untuk meng-extend fungsional suatu model, Partial Model yang di buat biasanya ditaruh pada module yang berbeda sehingga penambahan dari partial class ini hanya akan berjalan bila module tersebut di install. Partial Model dapat digunakan untuk meng-extend model yang ada pada core walaupun developer tidak memiliki akses terhadap source code di core.

Contoh kasus penggunaan dari Partial Model Inheritance(TBD)

#### Persiapan agar model aware terhadap partial class
Secara default efitrac akan memanggil method dengan urutan paling bawah ke paling atas. tetapi untuk custom code maka developer harus menggunakan AbstractModel.invoke agar custom code yang ada nantinya dapat memanggil method yang di override secara Partial Model.
<br>Contoh penggunaan invoke :

```java
    public void my_method(long userId, int someId, Map context) {    
        //do something here   
        this.invoke("maybe_overrided_method", null, userId, someId, m, context);
        //do something more here
    }
```

dan agar method yang di override tahu harus memanggil parentnya, maka harus memanggil perintah `<AbstracModel>.getParent()` untuk mendapatkan refrensi model parent dari model ini, lalu memanggil `invokeSelf(...)` untuk memanggil method yang ada pada parent model tersebut.

```java
    public void my_method(long userId, int someId, Map context) {    
        //do something here   

        //call parent method of my_method
        this.getParent().invokeSelf("my_method", null, userId, someId, m, context);

        //do something more here
    }
```

##Summary
Setiap Inheritance memiliki kelebihannya masing-masing, pemilihan sesuai kebutuhan akan mempersingkat waktu development, berikut perbandingan singkat kegunaan dari masing-masing jenis :

| Standard Model | Reference Model | Partial Model |
|--|--|--|
| Digunakan untuk membuat model baru dan ingin mengikuti daftar field dan method yang ada pada model lain |Digunakan untuk membuat model baru dan ingin mengikuti list field yang ada di model yang di tuju | Di gunakan jika ingin menambahkan fasilitas dari model yang ada tanpa mengubah model yang sudah ada  | 