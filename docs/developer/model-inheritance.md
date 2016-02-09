# Overview
Inherit View adalah mekanisme pada efitrac untuk mengubah view tanpa harus mengubah definisi view utama, ini bertujuan agar aplikasi dapat di custom tanpa mengotori view utama.





## Mempersiapkan agar model dapat mensupport &lt;input istilah&gt;
Secara default efitrac akan memanggil method dengan urutan paling bawah ke paling atas. tetapi untuk custom code maka developer harus menggunakan AbstractModel.invoke agar custom code yang ada nantinya dapat memanggil method yang di extend secara &lt;input istilah&gt;.
<br>Contoh penggunaan invoke :

```java
    //input example
```

dan agar method yang di extend tahu harus memanggil parentnya, maka harus memanggil 
