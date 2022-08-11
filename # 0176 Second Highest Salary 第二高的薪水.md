### 第二高的薪水
### Second Highest Salary

> `Employee` 表：  
```
+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| salary      | int  |
+-------------+------+
id 是这个表的主键。
表的每一行包含员工的工资信息。
```
> 编写一个 `SQL` 查询，获取并返回 `Employee` 表中第二高的薪水 。如果不存在第二高的薪水，查询应该返回 `null`。  

> Table: Employee
```
+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| salary      | int  |
+-------------+------+
id is the primary key column for this table.
Each row of this table contains information about the salary of an employee.
```
> Write an SQL query to report the second highest salary from the `Employee` table. If there is no second highest salary, the query should report `null`.  

----------

#### I IFNULL + DISTINCT 查询

- 利用 `order by desc` 可以获得工资降序的表  
- 利用 `distinct` 可以实现去重，找到真正第二高的工资  
- 利用 `offset` 可以找到表中第 2 个工资
- 利用 `limit` 可以返回唯一一个值  
- 最后利用 `ifnull` 对只有一条数据的情况进行处理即可  

```MySQL
select ifnull((select distinct salary from Employee order by salary desc limit 1 offset 1), null) as SecondHighestSalary
```
