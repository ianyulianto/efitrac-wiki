# Overview
Custom View adalah sebuah view yang bisa dibuat sesuai keinginan developer menggunakan komponent-komponent vaadin.
View ini dibuat dengan meng-extend class **CustomViewLayout**

---

## CustomViewLayout
Class ini merupakan class induk untuk membuat tampilan custom view. Di dalam class ini terdapat function-function pendukung seperti :

* getModelRef : Digunakan untuk mendapatkan referensi model dari view ini
* getParent : Digunakan untuk mendapatkan parent dari view ini
* getXMLNode : Digunakan untuk mendapatkan node xml dari view ini
* getAttribute : Digunakan untuk mendapatkan attribute dari xml element untuk view ini

## How to build custom view?

Untuk membuat sebuah custom view ada 2 langkah mudah yang harus dilakukan:

### Membuat java class dari custom view

Untuk membuat custom view, view tersebut harus extend dari *CustomViewLayout*.
Dibawah ini contoh cara membuat class CobaCustomView.

```java
public class CobaCustomView extends CustomViewLayout {

    VerticalLayout view=new VerticalLayout();

    public CobaCustomView(ViewPage parent, AbstractModel model,Node node) {
        super(parent, model,node);
    }

	/**
     * digunakan untuk merender view yang akan ditampilan
     * @return
     */
    @Override
    public void render() {
        Map<String, Field> fields = getModelRef().getFields();

        /**
			CODE YOUR VIEW HERE
		**/
    }

	/**
     * digunakan untuk mengembalikan view yang akan ditampilan
     * @return
     */
    @Override
    public Layout getComponent() {
        return view;
    }

}
```
### Menggunakan custom view menggunakan xml

Kemudian, custom view tersebut dapat digunakan dengan cara biasanya, menggunakan xml.
Contoh cara penggunaan custom view tersebut pada xml.

```xml
<field name="arch" type="xml">
	<custom string="Coba Custom" source="com.efitrac.module.xxx.CobaCustomView">
	</custom>
</field>
```

Pada contoh code diatas, kita dapat menggunakan custom view tersebut dengan menggunakan tag `<custom>`
dan diberi attribute `source` untuk menentukan letak dimana file java dari custom view tersebut berada. 
Di dalam tag custom juga bisa diberi tag-tag yang lain sesuai kebutuan dari developer.


