## Contoh mengganti domain dengan menggunakan onchange

```java
OnChangeReturnValue result = new OnChangeReturnValue();
Domain domain = new
Domain.Builder("[('deliveryorder_id.salesorder_id','='," + soId + ")" +
               ",('state','in',['submitted'])]").build();
result.addDomain("invoice_gi.gi_id", domain);
```
## Yang di support oleh onchange pada saat mengganti domain

* Mengganti domain untuk field dalam model tersebut
* Mengganti domain untuk field dari parent 
* Parent mengganti domain pada field child(OneToMany)

## behaviour dari domain pada onChange
* me-replace domain yang di set pada xml ataupun pada field
