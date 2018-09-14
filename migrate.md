--lagou_company公司分离
drop table if exists lagou_company;
create table lagou_company as 
select distinct t.company_id	as cid,
								t.company_short_name as short_name,
								t.company_full_name	as full_name,
								t.company_size as size,
								t.financestage
from lagou_position_bk;
数据库分割分为水平分割和垂直分割。
      水平分割：按记录进分分割，不同的记录可以分开保存，每个子表的列数相同。
水平分割通常在下面的情况下使用：
      A 表很大，分割后可以降低在查询时需要读的数据和索引的页数，同时也降低了索引的层数，提高查询速度。
      B 表中的数据本来就有独立性，例如表中分别记录各个地区的数据或不同时期的数据，特别是有些数据常用，而另外一些数据不常用。
      C需要把数据存放到多个介质上。

      垂直分割：按列进行分割，即把一条记录分开多个地方保存，每个子表的行数相同。
       把主码和一些列放到一个表，然后把主码和另外的列放到另一个表中。如果一个表中某些列常用，而另外一些列不常用，则可以采用垂直分割，另外垂直分割可以使得数据行变小，一个数据页就能存放更多的数据，在查询时就会减少I/O 次数。其缺点是需要管理冗余列，查询所有数据需要join操作。
对表进行表格的拆分主要是为了减轻数据库和硬盘的压力。同时避免数据冗余。

