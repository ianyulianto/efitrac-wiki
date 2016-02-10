#Overview
Tidak hanya memberikan dukungan sistem modular *business-object*, Efitrac juga 
memberikan dukungan penuh kepada developer agar dapat mengembangkan sistemnya
dengan lebih fleksibel, yaitu dengan mendukung pembuatan *controller* baru
di dalam sistem.

#How it works?
Efitrac akan memeriksa package `com.efitrac.web.controller` dengan tujuan 
mendaftarkan controller dengan path yang ditentukan ke dalam sistem.

```java
package com.efitrac.web.controller;

import org.springframework.http.MediaType;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller(
        value = "/hello"
)
public class FooController {

    @RequestMapping(
            value = "/foo",
            method = RequestMethod.GET,
            produces = MediaType.TEXT_PLAIN_VALUE
    )
    @ResponseBody
    public String foo() {
        return "Hello world!";
    }

}

```

Contoh di atas menunjukkan bahwa class **FooController** akan meng-handle path
`/hello`. Dapat dilihat function `#foo()` akan meng-handle path `/foo`. 
Dikarenakan pada controller sudah ada definisi path, maka definisi path pada
function akan ditambahkan path dari controller itu terlebih dahulu. Dari contoh,
berarti untuk mengakses function `#foo()` path yang harus diminta adalah
`/hello/foo`.

Format penulisan controller dapat dipelajari dari **Spring MVC**. Format 
tersebut diadopsi oleh Efitrac dikarenakan Efitrac sendiri berbasis framework
Spring MVC, sehingga cara penulisannya pun sama.