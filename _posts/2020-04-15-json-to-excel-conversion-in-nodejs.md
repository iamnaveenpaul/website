---
title: JSON to Excel conversion in Nodejs
image: "/assets/exceltojson.jpg"
---

# How to download JSON data into excel file

This is second part in our series dealing with Excel file formats using NodeJS. Lets start by installing **json2xls** node module in our app

<img class="width-100" alt="How to convert excel to json" src="/assets/exceltojson.jpg"/>

```
npm i json2xls
```


Lets build a temporary array with the required columns and then convert it into xls for immediate downloadable file.

```
var json2xls = require('json2xls');

var jsonArr = [{
    foo: 'bar',
    qux: 'moo',
    poo: 123,
    stux: new Date()
},
{
    foo: 'bar',
    qux: 'moo',
    poo: 345,
    stux: new Date()
}];

app.use(json2xls.middleware);

app.get('/',function(req, res) {
    res.xls('data.xlsx', jsonArr);
});
```

Now what if we want to create excel files offline? Using the same module lets do it!


# How to write a Nodejs script to convert JSON data into an excel file and save it to a local file system?
```

var json2xls = require('json2xls');

var json = {
    foo: 'bar',
    qux: 'moo',
    poo: 123,
    stux: new Date()
}

var xls = json2xls(json);

fs.writeFileSync('data.xlsx', xls, 'binary');
```

After doing this, you can see that the data.xlsx file will be created in the same directory.

We have made a tutorial to convert excel to json also. Check this link

[Convert excel to json with nodejs](https://griva.in/node.js/2019/12/05/how-to-convert-excel-to-json-with-nodejs)