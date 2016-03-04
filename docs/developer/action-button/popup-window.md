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
	public Action my_action_button(long uid, List ids, Map context) {
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
