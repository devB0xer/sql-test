# решение тестового задания

1. select bk.name from books as bk where bk.cost < 100000 order by bk.name ASC;

2. select auth.name, count(bk.id) as `count` from authors as auth 
    join books as bk on auth.id = bk.authorid
    join styles as sl on bk.styleid = sl.id
    where (auth.deathday is NULL) and (sl.name = "Детективы")
    group by auth.name order by 2 DESC;

3. select auth.name, sl.name as `style`, max(bk.cost) as `max-cost`
    from authors as auth
    join books as bk on auth.id = bk.authorid
    join styles as sl on bk.styleid = sl.id
    group by auth.name, sl.name;

4. select sl.name as `style`, count(dlv.id) as "delivery-count", count(distinct dlv.bookid) as "uniq-book"
    from styles as sl
    join books as bk on sl.id = bk.styleid
    join delivery as dlv on bk.id = dlv.bookid
    group by sl.name;
    
5. select rck.rackno, rck.section from racks as rck
    left join placement as plc on rck.id = plc.rackid
    where pls.bookid is NULL

6. 3 (3NF).  каждый столбец (не ключевой) зависит от первичного ключа

7. 
    1. вынести секции в отдельную таблицу от стоек.
    2. разделить в таблице авторов (и абонентов) фио на столбцы фамилия, имя, отчество
    3. добавить большк информации к таблице абонентов, например, номер телефона или почта