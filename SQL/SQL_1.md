Date: 2024-12-18  

SQL을 사용해 데이터를 정제한다. 데이터는 Google Coursera data analytics course에서 다운 받은 car_info table을 바탕으로 한다.  

## 데이터 정리
### 공백값 및 NULL 검사하기

MySQL에서는 Null 값과 공백을 구분해 아무리 `IS NULL` 연산을 수행해도 공백 값을 불러오지 못했다.  
데이터에 공백값이 있는 것을 excel로 열어 확인하고, 이후 재진행  
```SQL
select 
    distinct num_of_doors
from 
    gcc_cars.car_info;
```  
+--------------+  
| num_of_doors |  
+--------------+  
| two          |  
| four         |  
|              |  
+--------------+  

위처럼 공백값이 존재하기 때문에 다음처럼 비교문을 사용해 해결했다.  

```SQL
select make, num_of_doors  
from gcc_cars.car_info  
where num_of_doors = " ";  
```  
+-------+--------------+  
| make  | num_of_doors |  
+-------+--------------+  
| dodge |              |  
| mazda |              |  
+-------+--------------+  

### 데이터 수정하기(UPDATE)

```SQL
UPDATE gcc_cars.car_info
SET num_of_doors="four"
WHERE make = "dodge"
    AND fuel_type = "gas"
    AND body_style = "sedan";
```
Query OK, 1 row affected (0.01 sec)
Rows matched: 3  Changed: 1  Warnings: 0  

```SQL
SELECT  
DISTINCT num_of_cylinders  
FROM gcc_cars.car_info  
```  
+------------------+  
| num_of_cylinders |  
+------------------+  
| four             |  
| six              |  
| five             |  
| three            |  
| twelve           |  
| two              |  
| tow              |  
| eight            |  
+------------------+  
8 rows in set (0.00 sec)  

```SQL
UPDATE gcc_cars.car_info
SET num_of_cylinders = "two"
WHERE num_of_cylinders = "tow";
```  
+------------------+  
| num_of_cylinders |  
+------------------+  
| four             |  
| six              |  
| five             |  
| three            |  
| twelve           |  
| two              |  
| eight            |  
+------------------+  
7 rows in set (0.00 sec)  

### MIN, MAX 함수 이용하기  

```SQL
SELECT
MIN(compression_ratio) AS min_compression_ratio,
MAX(compression_ratio) AS max_compression_ratio
FROM gcc_cars.car_info;
```
+-----------------------+-----------------------+  
| min_compression_ratio | max_compression_ratio |  
+-----------------------+-----------------------+  
|                     7 |                    70 |  
+-----------------------+-----------------------+  
최댓값은 23이어야 하나, 70을 반환하고 있다.  
따라서 70값을 가진 행을 제외하고 위의 쿼리를 다시 실행한다.  
그 코드는 아래와 같다.  

```SQL
SELECT
MIN(compression_ratio) AS min_compression_ratio,
MAX(compression_ratio) AS max_compression_ratio
FROM gcc_cars.car_info
WHERE compression_ratio <> 70;
```  
```SQL
SELECT
    -> COUNT(*) AS num_of_rows_to_delete
    -> FROM
    -> gcc_cars.car_info
    -> WHERE compression_ratio = 70;
```  

오류가 있는 행으로 밝혀져 행 전체를 삭제하기로 하고 위의 코드로 70의 값을 가지고 있는 행의 개수를 찾는다.  
1개 있어서 `DELETE` 명령어로 삭제한다.  

```SQL
DELETE
    -> FROM gcc_cars.car_info
    -> WHERE compression_ratio = 70;
```  

## 고급 데이터 정리 함수  
### CAST 함수  
data type 변환을 위해 사용함  

### CONCAT()  
여러 문자열을 합해 새로운 문자열을 만듦
