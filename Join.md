#省、市、区(县)
select xp.id,s.cityName,sp.cityName,xp.cityName from s_provinces s 
inner join s_provinces sp on s.id=sp.parentId 
inner join s_provinces xp on sp.id=xp.parentId
where s.id=440000 
union 
select s.id,s.cityName,sp.cityName,null from s_provinces s 
inner join s_provinces sp on s.id=sp.parentId where s.id=440000 

从查询省市县来看：学习到了union和union all 之间的区别。
union：union用来合并两个或多个select语句的结果集，并消去表中任何重复行。
union 内部的 select 语句必须拥有相同数量的列，列也必须拥有相似的数据类型。
同时，每条 select 语句中的列的顺序必须相同.
union all：union all会显示所有的数据，不会去除重复的行。