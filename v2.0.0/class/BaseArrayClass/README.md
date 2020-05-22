:warning: **This document is aim for older versions (from 2.0.0 to 2.2.9).
Document for new version is https://github.com/mapsplugin/cordova-plugin-googlemaps-doc/blob/master/v2.6.0/README.md**

---------------
# BaseArrayClass

The Base Array class is designed for MVC(Model-View-Controller).

Although the class name contains **"Array"**, but this is **not Javascript Array** class.
If you need to modify an element, use `insertAt()`, `setAt()` and `removeAt()` methods.

The benefit of this class is you are able to catch the events that occurs when you change the value.

The below examples are how to use this class.

## Basic example

```js
var mvcArray = new plugin.google.maps.BaseArrayClass();

// Catch the insert_at event when you insert new value to the mvcArray each time.
mvcArray.on("insert_at", function(index) {
  console.log("---> [insert_at] position : " + index + ", value : " + this.getAt(index));
});

// Catch the set_at event when you change an element with new value.
mvcArray.on("set_at", function(index, oldValue) {
  console.log("---> [set_at] position : " + index + ", value : " + this.getAt(index));
});

// Catch the remove_at event when you delete an element from the mvcArray each time.
mvcArray.on("remove_at", function(index, oldValue) {
  console.log("---> [remove_at] position : " + index + ", value : " + oldValue);
});

mvcArray.push("A");       // ---> [insert_at] position : 0, value : "A"
mvcArray.push("B");       // ---> [insert_at] position : 1, value : "B"
mvcArray.push("C");       // ---> [insert_at] position : 2, value : "C"

mvcArray.pop()            // ---> [remove_at] position : 2, value : "C"

mvcArray.setAt(2, "D");   // ---> [set_at] position : 1, value : "B"

console.log(mvcArray.getArray());  // "A", "D"
```

---

This class extends [BaseClass](../BaseClass/README.md).

## Constructor

<table>
    <tr>
    <th><a href="./constructor/README.md">BaseArrayClass(array?:Array)</a></th>
        <td>A mutable MVC Array.</td>
    </tr>
</table>

## Methods

<table>
    <tr>
        <th><a href="empty/README.md">empty()</a></th>
        <td>Removes all elements from the array.</td>
    </tr>
    <tr>
        <th><a href="forEach/README.md">forEach()</a></th>
        <td>Iterate over each element, calling the provided callback.<br>
        This method provides two ways:<br>
        <ul>
        <li>forEach(fn)</li>
        <li>forEach(fn, callback)</li>
        </ul></td>
    </tr>
    <tr>
        <th><a href="map/README.md">map()</a></th>
        <td>Iterate over each element, calling the provided callback.<br>
        Then you can get the results of each callback.<br>
        This method provides two ways:<br>
        <ul>
        <li>map(fn)</li>
        <li>map(fn, callback)</li>
        </ul></td>
    </tr>
    <tr>
        <th><a href="getArray/README.md">getArray()</a></th>
        <td>Returns a reference to the underlying Array.</td>
    </tr>
    <tr>
        <th><a href="getAt/README.md">getAt(i:number)</a></th>
        <td>Returns the element at the specified index.</td>
    </tr>
    <tr>
        <th>getLength()</th>
        <td>Returns the number of elements.</td>
    </tr>
    <tr>
        <th><a href="insertAt/README.md">insertAt(i:number, elem:*)</a></th>
        <td>Inserts an element at the specified index.</td>
    </tr>
    <tr>
        <th><a href="pop/README.md">pop()</a></th>
        <td>Removes the last element of the array and returns that element.</td>
    </tr>
    <tr>
        <th><a href="push/README.md">push(elem:*)</a></th>
        <td>Adds one element to the end of the array and returns the new length of the array.</td>
    </tr>
    <tr>
        <th><a href="removeAt/README.md">removeAt(i:number)</a></th>
        <td>Removes an element from the specified index.</td>
    </tr>
    <tr>
        <th><a href="setAt/README.md">setAt(i:number, elem:*)</a></th>
        <td>Sets an element at the specified index.</td>
    </tr>
    <tr>
        <th><a href="forEach/README.md">forEach(fn)</a></th>
        <td>Iterate `fn` in synchro.</td>
    </tr>
    <tr>
        <th><a href="forEachAsync/README.md">forEachAsync(fn, callback)</a></th>
        <td>Iterate `fn` in asynchro.</td>
    </tr>
    <tr>
        <th><a href="filter/README.md">filter(fn)</a></th>
        <td>Filter values in synchro.</td>
    </tr>
    <tr>
        <th><a href="filterAsync/README.md">filterAsync(fn, callback)</a></th>
        <td>Filter values in asynchro.</td>
    </tr>
    <tr>
        <th><a href="map/README.md">map(fn)</a></th>
        <td>Map values in synchro.</td>
    </tr>
    <tr>
        <th><a href="mapAsync/README.md">mapAsync(fn, callback)</a></th>
        <td>Map values in asynchro.</td>
    </tr>
    <tr>
        <th><a href="mapSeries/README.md">mapSeries(fn, callback)</a></th>
        <td>Map values in asynchro, but keep the iterate order.</td>
    </tr>
</table>


## Events

<table>
    <tr>
        <th>insert_at</th>
        <td><b>Arguments:  number</b><br>
        This event is fired when  <a href="insertAt/README.md">insertAt()</a> is called. The event passes the index that was passed to  <a href="insertAt/README.md">insertAt()</a>.</td>
    </tr>
    <tr>
        <th>remove_at</th>
        <td><b>Arguments:  number, *</b><br>
        This event is fired when  <a href="removeAt/README.md">removeAt()</a> is called. The event passes the index that was passed to <a href="removeAt/README.md">removeAt()</a> and the element that was removed from the array.</td>
    </tr>
    <tr>
        <th>set_at</th>
        <td><b>Arguments:  number, *</b><br>
        This event is fired when <a href="setAt/README.md">setAt()</a> is called. The event passes the index that was passed to <a href="setAt/README.md">setAt()</a> and the element that was previously in the array at that index.</td>
    </tr>
</table>
