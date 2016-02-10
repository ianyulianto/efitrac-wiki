#Overview
API ini mempunyai kegunaan dalam hal mendapatkan informasi dari storage yang
digunakan oleh sistem efitrac.

## Calculate Storage
```
GET: /api/storage/size
```
Controller ini akan memberikan informasi tentang ukuran storage. Storage yang
dimaksud di sini dibagi menjadi 2, yaitu storage sebagai database yang diberi
key `database` dan storage yang menyimpan file-file hasil proses upload di mana
kami memberi key `storage`. Berikut adalah nilai contoh nilai kembaliannya:
```json
{
  "success": true,
  "time": 1454989840831,
  "result": {
    "size_in": "kb",
    "database": {
      "name": "efitrac",
      "host": "localhost",
      "size": 4576
    },
    "storage": {
      "online": false,
      "name": "/tmp/efitrac",
      "size": 0
    }
  }
}
```

|       Key            |                                    Deskripsi                                                                  |
|----------------------|---------------------------------------------------------------------------------------------------------------|
| size_in              | Satuan dari key `size`.                                                                                       |
| database             | Berisikan informasi database.                                                                                 |
| database/ **name**   | Nama database.                                                                                                |
| database/ **host**   | Host database.                                                                                                |
| database/ **size**   | Jumlah data yang disimpan pada database dengan satuan `size_in`.                                              |
| storage              | Berisikan informasi tempat penyimpanan file.                                                                  |
| storage/ **online**  | Apakah storage yang digunakan online atau local.                                                              |
| storage/ **name**    | Tempat penyimpanan file yang di-upload.                                                                       |
| storage/ **size**    | Jumlah semua file yang sudah di-upload. Jika `online` berisi **FALSE**, maka nilai ini akan selalu **0**.     | 
