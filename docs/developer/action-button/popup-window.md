# Overview
Action Button dapat melakukan popup window untuk menampilkan sebuah view.

---

## How to make Action Button Popup Window?

Ada 2 langkah untuk membuatnya:

### Define XML Action Button

Seperti pada umumnya, cara mendefine di xml adalah sebagai berikut

```xml
	<form string="My Form">
		<header>
			<actionbutton>
				<button name="my_action_button" string="My Action Button" />
			</actionbutton>
		</header>		
		..		
	</form>
```

### Make function in Java Class Model

Agar button bisa berjalan, perlu dibuatkan function pada java class model tersebut.
Nama function tersebut harus sesuai dengan attribute *name* yang didefinisikan di file xml.

Pada definisi sebelumnya attribute *name* berisi *my_action_button*, jadi pada java class model perlu dibuat function *my_action_button*.

Isi dari function tersebut adalah sebagai berikut:

```java
	public Action fo_folio_transaction_transfer_item(long uid, List ids, Map context) {
		...
		ActionWindow action = new ActionWindow();
		//action.viewId berisi record id dari view yang akan ditampilkan
		action.viewId = "pop_up_my_action_button_form_view"; 
		//action.resModel adalah model dari view yang akan ditampilkan
		action.resModel = "foo.dummy";
		//action.context digunakan untuk mendefiniskan context yang akan digunakan untuk view yang akan ditampilkan
		action.context = new HashMap<>();
		action.context.put("default_param_1","test1");
		action.context.put("default_param_2","test2");
		...
		return action;
	}
```








Pada field `view_mode` terdapat definisi dari jenis-jenis view yang ada pada model tersebut. 
Untuk mendifiniskan secara spesifik view mana yang akan ditampilkan perlu ditambahkan perubahan sebagai berikut:

```xml
<field name="view_XXX" ref="YYY"/>
```

*XXX*  menunjukan tipe view sesuai yang didefinisikan di view_mode. 
*YYY* adalah record id dari view yang didefnisikan untuk tipe view tersebut.

Contoh hasil perubahannya adalah sebagai berikut:

```xml
	<record id="action_demo" model="ir.actions.act_window">
		<field name="name">Demo View</field>
		<field name="type">ir.actions.act_window</field>
		<field name="res_model">foo.dummy</field>
		<field name="view_mode">tree,form,calendar,graph</field>
		<field name="view_tree" ref="view_dummy_tree"/>
		<field name="view_form" ref="view_dummy_form"/>
		<field name="view_calendar" ref="view_dummy_calendar"/>
		<field name="view_graph" ref="view_dummy_graph"/>
		<field name="view_type">tree</field>
	</record>
```
