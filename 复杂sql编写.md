**Oracle中 如何用一个表的数据更新另一个表中的数据**


merge into table1
using  (select t.idd ,max(t.val) m from table2 t group by t.idd)table2
on (table1.idd = table2.idd)
when matched then
update set table1.val = table2.m