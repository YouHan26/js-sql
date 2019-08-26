# js-sql


### refs
[https://www.w3school.com.cn/sql/sql_insert.asp](https://www.w3school.com.cn/sql/sql_insert.asp)

### Feature
* lazy execute


### Grammar

#### init
```javascript
import {Table} from 'js-sql'

const data = [{
	name: '1',
	age: 11,
	location: 'beijing'
},{
	name: '2',
	age: 22,
	location: 'wuhan'
}]
Table(data)

// just handle col name and col age
Table(data, 'name', 'age')
```

#### select
```javascript
data.select();                 // select * from table
data.select('name', 'age');    // select name,age from table

// with distinct
import {SELECT} from 'js-sql'
data.select('name', 'age', SELECT.DISTINCT);   // select DISTINCT name, age from table

```

#### WHERE

`where('colName', 'value' [,OPERATOR.operator [,OPERATOR.not]])`
`where(WHERE.AND|OR('colName', 'value' [,OPERATOR.operator [,OPERATOR.not]]))`
`where('age>10')`
```javascript

import {OPERATOR} from 'js-sql'


/**
* equal sql:
* select name, age from table
* where name LIKE 'john' AND age>10
*/
data
.select('name', 'age')
.where('name LIKE /lon/', 'age > 10')


/**
* equal sql:
* select name, age from table
* where name LIKE 'john' AND OR > 10
*/
import {WHERE} from 'js-sql';

data
.select('name', 'age')
.where('name LIKE /lon$/',  WHERE.OR('age>10'))


/**
* equal sql:
* select name, age from table
* where name NOT LIKE 'john' AND OR > 10
*/
import {WHERE} from 'js-sql';

data
.select('name', 'age')
.where('name NOT LIKE /lon$/',  WHERE.OR('age>10'))


/**
* custom where condition
*/
data
.select('name', 'age')
.where(function(row){return row.age> 10})


/**
* multiple where
* equal sql:
* select name, age from table
* where (name LIKE 'john' AND age>10)
*/
data
.select('name', 'age')
.where('name LIKE /lon$/')
.where('age>10')

```

##### operator can be:
* =
* !=
* \>
* <
* \>=
* <=
* BETWEEN
* LIKE
* NOT

like will use javascript regex grammar



#### order by
```javascript
/**
* equal sql:
* select name, age from table
* where (name LIKE 'john' AND age>10)
* order by name DESC, age ASC
*/
data
.select('name', 'age')
.where('name LIKE john', 'age>10')
.orderBy('name desc', 'age asc')


/**
* equal sql:
* select name, age from table
* where (name LIKE 'john' AND age>10)
* order by name DESC, age ASC
*/
import {ORDERBY} from 'js-sql';

data
.select('name', 'age')
.where('name LIKE john', 'age>10')
.orderBy('name', ORDERBY.DESC, 'age', ORDERBY.ASC)

```


#### insert
```javascript
/**
* equal sql:
* insert into table (name, age) values ('tony', 10)
*/
import {Table} from 'js-sql'
const data = Table(datasource, 'name', 'age')

data
.insert('tony', '10')

```


#### update
```javascript
/**
* equal sql:
* UPDATE Person SET name = 'Zhongshan 23', age = 'Nanjing'
  WHERE name = 'Wilson'
*/
data
.update(['name', 'tony'], ['age', 10])
.where('name=tony')


//or
import {Table} from 'js-sql'
const data = Table(dataSet, 'name', 'age')

data.update('tony', 10)
.where('name=tony')

```



#### delete
```javascript

/**
* equal sql:
  delete * from table
*/
data
.delete()


data
.delete()
.where('name=tony')
```


#### top
```javascript

/**
* equal sql:
* select * from table
* limit 50
*/
data
.select()
.limit(50)

```
