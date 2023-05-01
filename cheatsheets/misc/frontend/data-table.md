## Data Table

## Installation

While downloading datatables from a cdn, if you want to use custom features such as export to csv, excel buttons .. etc. you need to include them in your cdn and you can use this cdn builder from their site 

https://datatables.net/download/

## Re-poulating data tables with loops

While working with data tables if you want to populate the table from an ajax call, you have to first destroy and then re-draw the table:
```javascript
$('#table1').DataTable().destroy();
$('#table1').find('tbody').append("<tr><td><value1></td><td><value1></td></tr>");
$('#table1').DataTable().draw();
```

## Styling 

Adding margin between the filter and the table
```css
.dataTables_filter {margin-bottom: 10px;}
```

Making the page load 100 instead of 10
```js
$('#progress_report_table').DataTable({
      "pageLength": 100
});
```