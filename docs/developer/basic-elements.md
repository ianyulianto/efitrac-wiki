# Overview

Basic Element merupakan element-element dasar yang dapat digunakan ketika membuat tampilan sebuah model menggunakan xml.

---

## Jenis Basic Element

Untuk membuat tampilan xml, ada beberapa jenis element.

### Element Component

### Element Layout


## Attribute

Untuk membantu dalam rendering sebuah element, terdapat beberapa attribute yang dapat digunakan.
Attribute tersebut bisa dipakai ataupun tidak.

1. Common Attribute
2. Component Attribute
3. Layout Attribute


## Common Attribute
	
Attribute ini dimiliki baik element layout maupun element component. Macam-macam common attribute:

### `id`
    ```xml
    <button id="submit"/>
    ```
	
    Attribute ini digunakan untuk memberikan *unique* id pada element. ID
    tersebut nantinya dapat digunakan untuk mengakses element bersangkutan.

### `icon`
    ```xml
    <button icon="SEARCH"/>
    ```
    Attribute ini digunakan untuk memberikan icon pada element yang sudah
    disediakan. Icon yang disediakan menggunakan icon `Font Awesome`_.

    .. _`Font Awesome`: http://fortawesome.github.io/Font-Awesome/icons/

### `icon-url`
    ```xml
    <button icon-url="http://url_icon_here"/>
    ```
	
    Attribute ini digunakan untuk memberikan icon pada element sesuai dengan
    url_icon_here yang diinputkan.

### `string`
    ```xml
    <button string="Cari Sekarang"/>
    ```
	
    Attribute ini digunakan untuk memberikan caption pada element.
	
	
### `no_caption`
    ```xml
    <field no_caption="true"/>
    ```
	
    Bernilai ``True`` atau ``False``. Attribute ini mengatur apakah caption dari sebuah element dimunculkan apa tidak.

### `invisible`
    ```xml
    <button invisible="true"/>
    ```
    Bernilai ``True`` atau ``False``. Attribute ini mengatur visibility element.

### `width`
    ```xml
    <button width="100%"/>
    ```
    Bernilai ``%`` , ``px`` , atau ``undefined``. Attribute ini mengatur width dari sebuah element.

### `height`
    ```xml
    <button height="100px"/>
    ```
    Bernilai ``%`` , ``px`` , atau ``undefined``. Attribute ini mengatur height dari sebuah element.

### `sizefull`
    ```xml
    <button sizefull="true"/>
    ```
    Bernilai ``True`` atau ``False``. Attribute ini mengatur lebar dan tinggi
    sebuah komponen sesuai dengan containernya.

### `align`
    ```xml
    <button align="middle-center"/>
    ```
    Attribute ini mengatur alignment element. Nilai dari attribute ini yaitu:
    top-left, top-center, top-right, middle-left, middle-center, middle-right,
    bottom-left, bottom-center, bottom-right.
	
### `style``
    ```xml
    <button style="pull-right"/>
    ```
    Attribute ini digunakan untuk menambah class css. Class css tersebut dapat
    dilihat pada . . . . . berikut.

### `border`
    ```xml
    <button border="true"/>
    ```
    Bernilai ``True`` atau ``False``. Attribute ini mengatur visibility dari
    border sebuah element.

### `margin`
    ```xml
    <verticalLayout margin="true"/>
    ```
    Bernilai ``true`` atau ``false``. Attribute ini mengatur margin sebuah komponen.
    Jika dipilih ``true`` secara default bagian atas, kanan, bawah dan kiri element akan diberi margin.
    Untuk mengcustomisasi margin bisa menggunakan cara "true, false, true, false" (from top, right, bottom, left).
    Hasilnya yang akan diberi margin atas dan bawah saja.
	
### `padding`
    ```xml
    <verticalLayout padding="true"/>
    ```
    Bernilai ``True`` atau ``False``. Attribute ini mengatur padding
    sebuah komponen.
	
### `state`
    ```xml
    <button state="draft,submit"/>
    ```
    Attribute ini mengatur visibilty dari sebuah element berdasarkan value dari definisi state pada xml dengan value dari field state yang berasal dari database.

### `groups`
    ```xml
    <button groups="base.sales,base.sales_manager"/>
    ```
    Attribute ini mengatur visibilty dari sebuah element berdasarkan res.group user yang sedang login. Jika sesuai maka element akan ditampilkan.
	
### `attrs``
    ```xml
    <button attrs="{'readonly': [('state', 'not in', ['draft'])]}"/>
    ```
    Attribute ini mengatur visibilty dari sebuah element berdasarkan value dari hasil parse dari sebuah domain.


## Component Attribute
	
Attribute ini merupakan attribute tambahan yang dimiliki oleh element component. Macam-macam common attribute:

### `readonly`
    ```xml
    <field readonly="true"/>
    ```
    Bernilai ``True`` atau ``False``. Attribute ini menunjukan bahwa element ``field``
    tidak bisa diedit datanya.
	
### `required`
    ```xml
    <field name="staff_id" required="true"/>
    ```
    Bernilai ``True`` atau ``False``. Attribute ini menunjukan bahwa nilai dari field tersebut tidak boleh null.

### `name`
    ```xml
    <field name="staff_id"/>
    ```
	Attribute ini sebagai represtatif dari sebuah column pada database atau field pada sebuah model.

### `domain`
    ```xml
		<field name="staff_id" domain="[('department_id', '=', '$parent.department_id')]"/>
    ```
    Digunakan untuk melakukan filter menggunakan domain. attribute domain biasanya dipakai untuk relate field, seperti many2one, one2many, dan many2many.

### `context`
    ```xml
		<field name="staff_id" context="{'department_id' : '1'}"/>
    ```
    Digunakan untuk melakukan mendifinisikan isi context.


## Layout Attribute
	
Attribute ini merupakan attribute tambahan yang dimiliki oleh element layout. Macam-macam common attribute:


### `spacing`
    ```xml
		<horizontallayout spacing="true" >
		...
		</horizontallayout>
    ```
    Bernilai ``True`` atau ``False``. Attribute ini mengatur spacing
    antar komponen yang berada di dalam layout.