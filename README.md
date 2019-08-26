# js-sql


### refs
[https://www.w3school.com.cn/sql/sql_insert.asp](https://www.w3school.com.cn/sql/sql_insert.asp)
[https://juejin.im/post/5c7e524af265da2d914db18f#heading-10](https://juejin.im/post/5c7e524af265da2d914db18f#heading-10)

### Feature
* lazy execute


### Grammar

#### Table
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

#### Data Operator
* select
* update
* insert
* delete


#### Data filter
* where
  
  `=  >  <  !=  >=  <=`
* where IN | where BETWEEN

  `BETWEEN  IN`
* AND | OR | NOT
* LIKE

  `%  _`
  
#### Data PreHandle
* text

  `LFET RIGHT`
  
  `LOWER UPPER`
  
  `LTRIM RTRIM`
  
  `LENGTH`
  
  `SOUNDEX`
  
* date[TODO]
* math[TODO]
* sum

  `AVG COUNT MAX MIN SUM`
  
  
#### Data sort and Data group
* order by

  `ASC DESC`
* group by
* HAVING




#### 子查询


#### Data join
* join
 
 `NATURAL JOIN`
 
 `INNER JOIN`
 
 `LEFT JOIN`
 
 `RIGHT JOIN`
 
 `OUTER JOIN`
 

