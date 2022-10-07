# SectDB
SectDB is an free to use JavaScript library that provides powerful in-memory database capabilities to both browser and server applications such as Node.js

NPM: `npm i sectdb` [(NPM Package)](https://www.npmjs.com/package/sectdb)

Home Page: https://www.sectly.online/sectdb

Full Documentation: https://www.sectly.online/sectdb/docs

## Create a DB (Database)
Just pass in a JSON array:

```js
var products = SectDB([
  { "item"  : 1,
    "name"  : "Smart Phone X",
    "price" : 99.99
  },
  { "item"  : 2,
    "name"  : "HD TV",
    "price" : 1799.99
  }
]);
```

## Example queries

```js
// where item is equal to 1
var item1 = products({item:1});

// where price is less than 100
var lowPricedItems = products({price:{lt:100}});

// where name is like "Smart Phone"
var Smartphones = products({name:{like:"Smart Phone"}});

// get first record
products().first();

// get last record
products().last();
```

## Example record manipulation

```js
// update the price of the Smart Phone X to 89.99
products({item:1}).update({price:89.99});

// loop over the records and call a function
products().each(function (r) {alert(r.name)});

// sort the records by price descending
products.sort("price desc");

// select only the item names into an array
products().select("name"); // returns ["HD TV","Smart Phone X"]

// Inject values from a record into a string template.
// Row value will be set to "<tr><td>HD TV</td><td>17999.99</td></tr>"
var row = products({item:2})
  .supplant("<tr><td>{name}</td><td>{price}</td></tr>");
```

## Use it in Node.JS
SectDB is easy to use in Node.JS. Simply copy type in console/terminal `npm i sectdb` and require the module:

```js
const SectDB = require( 'SectDB' ).SectDB;

const myDatabase = SectDB();

myDatabase.insert({ message: "Hello, World!" })

myDatabase.save("Example")
```
