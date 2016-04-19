# Overview
Pada Efitrac di sertakan fitur Reporting untuk menunjang pembuatan aplikasi. fitur reporting pada efitrac menggunakan JasperReport.

---

Langkah-langkah membuat report

1. membuat file xxxx_report.xml, dimana xxxx adalah nama dari module
Contoh xml

```xml
<report
        id="report_name"
        string="Report Title"
        model="sale.customer_order"
        report_type="jasper-pdf"
        file="sale.sale_report"
        name="sale.sale_report"
        menu="false"
/>
```

| Nama | Keterangan |
|------|------------|
| id | id unik pengenal report(di ir.model.data) |
| string | title dari report |
| name | nama unik pengenal report |
| model | model yang memiliki report |
| report_type | sementara "jasper-pdf" |
| file | file repory |
| menu | untuk menandakan apakah di munculkan menu report di menu print <insert image here> |



menu = untuk menandakan apakah di munculkan menu report di menu print <insert image here>

2. menambahkan file xxxx_report.xml di descriptor
3. 