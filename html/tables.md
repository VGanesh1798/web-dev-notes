# HTML Tables
Tables in HTML are used to display tabular data. **Do not use tables to style the web page**. This is an archaic practice that has been superseded by much better technologies.

## Table Basics
All tables are enclosed in `<table>` tags. Table data is the smallest element of a table and can be inserted using `<td>`. These cells will line up in the same row unless we specify table rows using `<tr>` and put our cells inside these rows. Table headers are special cells that go at the start of a row or column and are defined by `<th>` tags.

Oftentimes we will want to resize cells to format better. By using `rowspan` and `colspan` attributes on table headers and data, we can change how many rows/columns a cell spans. 

Entire columns of data can be styled by using the `<colgroup>` and `<col>` elements. The `<colgroup>` wraps around the column elements (which each correspond to a column of the table), and each column can have its own styling applied to it to affect all of its cells at the same time. We can also use the `span` attribute to apply the same styling to multiple columns without needing to add new column elements in the group.

## Advanced Tables
Tables can have captions, marked with a `<caption>` element. This tag goes right below the opening `<table>` tag.

Like the document as a whole, tables can be structured using `<thead>`, `<tbody>`, and `<tfoot>` to divide up the table easier for styling and formatting purposes. Tables can also be nested inside of one another.

Semantics also exist for tables; table headers are one example. The `scope` attribute can be applied to table headers to tell screen readers what the header is for (like a row or column). The `scope` can also be set to `rowgroup` or `colgroup` for headings that span multiple rows or columns.

An alternative to `scope` is to attach `id` to a table header and attach `headers` to each cell in the header's group to create an association between the cells and header.