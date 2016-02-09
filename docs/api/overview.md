# Application Programming Interface (API)
Efitrac mempunyai API yang dapat digunakan untuk mendukung pembuatan sistem
dengan efitrac. API yang dapat diakses dengan melalui request HTTP dengan
pengembalian sebuah JSON Format.

Berikut adalah contoh hasil kembalian dari API,
```json
{
  "success": true,
  "time": 1454581068274,
  "result": {
    "size_in": "kb",
    "mysql": {
      "name": "efitrac",
      "host": "localhost",
      "size": 123
    },
    "s3": {
      "name": "efi",
      "size": 345
    }
  }
}
```

Nilai di dalam key `result` akan beragam, sesuai dengan api yang diminta. 
Sedangkan nilai `time` adalah nilai millisecond ketika response dari server.