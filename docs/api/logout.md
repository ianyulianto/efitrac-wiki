# Overview
Efitrac memberikan kuasa kepada developer yang ingin menambahkan *handler*
pada proses *post-logout*, di mana proses menghilangkan session dan komponen-
komponen yang diperlukan sudah berjalan dengan sukses.

## Handle it!
Ketika masuk ke tahap post-logout, maka sistem akan mencari apakah ada 
controller yang meng-handle untuk path `/logout` (e.g. 
https://www.efitrac.com/logout). Jika ada, maka sistem akan mengarahkan ke path
tersebut, dan di dalam controller tersebut dapat disisipi process yang 
diperlukan ketika user sudah selesai logout.

Sistem akan mengantarkan user ke path `/v2` (e.g. https://www.efitrac.com/v2) 
ketika di dalam sistem tidak menemukan controller yang meng-handle path
`/logout`.

```java
package com.efitrac.web.controller;

import org.springframework.http.MediaType;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class LogoutController {

    @RequestMapping(
            value = "/logout",
            method = RequestMethod.GET,
            produces = MediaType.TEXT_PLAIN_VALUE
    )
    @ResponseBody
    public String logout() {
        return "Hello world!";
    }

}

}
```

Bacaan selanjutnya:

- [Controller]

[Controller]: controller.md