# Overview
Setiap model bisa memiliki view lebih dari satu untuk setiap jenis view yang ada. Multiple view ini digunakan untuk mengatur view mana yang akan ditampilkan jika suatu menu di klik.

---

## How to define multiple view in act_window?

Pada umumnya, untuk mendifinisakan sebuah act_window adalah sebagai berikut:

```xml
	<record id="action_demo" model="ir.actions.act_window">
		<field name="name">Demo View</field>
		<field name="type">ir.actions.act_window</field>
		<field name="res_model">foo.dummy</field>
		<field name="view_mode">tree,form,calendar,graph</field>
		<field name="view_type">tree</field>
	</record>
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
