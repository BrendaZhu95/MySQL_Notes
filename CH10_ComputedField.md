# 计算字段

## 拼接字段
**拼接 (concatenate)** 将值联结到一起构成单个值
```mysql
SELECT Concat(vend_name, ' (', vend_country, ')') FROM vendors ORDER BY vend_name;
->
+--------------------------------------------+
| concat(vend_name, ' (', vend_country, ')') |
+--------------------------------------------+
| ACME (USA)                                 |
| Anvils R Us (USA)                          |
| Furball Inc. (USA)                         |
| Jet Set (England)                          |
| Jouets Et Ours (France)                    |
| LT Supplies (USA)                          |
+--------------------------------------------+
<-
```

### 去掉空格并使用别名
```mysql
SELECT Concat(RTrim(vend_name), ' (', RTrim(vend_country), ')') AS vend_title FROM vendors ORDER BY vend_name; 
->
+-------------------------+
| vend_title              |
+-------------------------+
| ACME (USA)              |
| Anvils R Us (USA)       |
| Furball Inc. (USA)      |
| Jet Set (England)       |
| Jouets Et Ours (France) |
| LT Supplies (USA)       |
+-------------------------+
<-
```

## 执行算术计算
```mysql
SELECT prod_id, quantity, item_price FROM orderitems WHERE order_num = 20005;
->
+---------+----------+------------+
| prod_id | quantity | item_price |
+---------+----------+------------+
| ANV01   |       10 |       5.99 |
| ANV02   |        3 |       9.99 |
| TNT2    |        5 |      10.00 |
| FB      |        1 |      10.00 |
+---------+----------+------------+
<-

SELECT prod_id, 
       quantity, 
       item_price, 
       quantity*item_price AS expanded_price 
FROM orderitems 
WHERE order_num = 20005;
->
+---------+----------+------------+----------------+
| prod_id | quantity | item_price | expanded_price |
+---------+----------+------------+----------------+
| ANV01   |       10 |       5.99 |          59.90 |
| ANV02   |        3 |       9.99 |          29.97 |
| TNT2    |        5 |      10.00 |          50.00 |
| FB      |        1 |      10.00 |          10.00 |
+---------+----------+------------+----------------+
<-
```






