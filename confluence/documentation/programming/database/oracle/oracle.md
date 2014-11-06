> **Oracle**  [[home](../../../../home.html)] <br/>
[oficial site](http://www.oracle.com/index.html)<br/>
[oficial documentation](http://www.oracle.com/technetwork/indexes/documentation/index.html)
 

- [Definition](#definition)
- [Tutorials](#tutorials)
- [Details](#details)
- [Tests](#tests)


<a name="definition"></a>
> **Definition:** <br/>

<a name="tutorials"></a>
> **Tutorials:** <br/>

  
<a name="details"></a>
> **Details:**<br/>

 - [Pagination](#pagination)
 - [insert](#insert) 

<a name="pagination"></a>
> **Pagination**

Pagination are of two types: *internal* and *external* <br/>
 
 - In case of internal paging all data is loaded into memory in one shot and display tag handles pagination based upon page size but it only suitable for small data where you can afford those many objects in memory.<br/> 
 - In case of hundreds rows to display than its best to use external pagination by asking database to do pagination. 

**Note:** In pagination, ordering is a very important aspect which can not be missed. It’s virtually impossible to sort large collection in Java using Comparator or Comparable because of limited memory available to Java program, sorting data in database using ORDER BY clause itself is good solution while doing paging in web application.

ROWNUM is a pseudocolumn (not a real column) that is available in a query and it is a value that is inherent to that row of data.
Think of it as being processed in this order:

1. The FROM/WHERE clause goes first. 
2. ROWNUM is assigned and incremented to each output row from the FROM/WHERE clause. 
3. SELECT is applied. 
4. GROUP BY is applied. 
5. HAVING is applied. 
6. ORDER BY is applied.

That is why a query in the following form is almost certainly an error: 

	select * from emp where ROWNUM <= 5 order by sal desc;
	or
    SELECT * from table where rownum between <START> and <END>

 [(Read more)](http://progcookbook.blogspot.ro/2006/02/using-rownum-properly-for-pagination.html)


Oracle database provides a convenient method row_number() which can be used to provide a unique row number to each row in result set. By including row_number() in query you can produce a result set which is numbered and than its just a job to retrieve data from specified indexes or pages. This is similar to using the LIMIT clause, available in some other databases.
[(Read more)](http://javarevisited.blogspot.com/2012/12/oracle-pagination-sql-query-example-for-java.html#ixzz3HuZORKlO)

Other articles to be reviewed:
[[1]](http://www.oracle.com/technetwork/issue-archive/2006/06-sep/o56asktom-086197.html)
[[2]](http://www.oracle.com/technetwork/issue-archive/2007/07-jan/o17asktom-093877.html) 

[***Oracle 12 pagination method***](http://oracle-base.com/articles/12c/row-limiting-clause-for-top-n-queries-12cr1.php)<br/>
[***Pagination methods for different databases***](http://use-the-index-luke.com/sql/partial-results/fetch-next-page)


**Example:**<br/>

    SELECT * FROM (
	    SELECT
	      ord.*,
	      row_number() over (ORDER BY ord.order_id ASC) ROW_NUM
	    FROM Orders ord  
	) WHERE ROW_NUM BETWEEN 0 AND 5  ORDER BY ROW_NUM;

or

    SELECT * FROM ( 
		SELECT *
           FROM sales WHERE sale_date <= ?
            AND NOT (sale_date = ? AND sale_id >= ?)
          ORDER BY sale_date DESC, sale_id DESC
       ) WHERE rownum <= 10;

<a name="insert"></a> 
> **INSERT**


    INSERT ALL
  		INTO rownum_order_test
  		INTO rownum_order_test
		SELECT level
			FROM   dual
		CONNECT BY level <= 10;
	COMMIT;