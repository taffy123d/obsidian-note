
B+树：
- 数据只存在叶子节点，内部节点只存索引键
- 所有叶子节点通过双向链表连接，支持高效的范围扫描与顺序遍历
MySQL为什么选用B+树：
- 范围查询高效
- 磁盘IO更少 { 内部节点不存数据只存键值 需要的磁盘读写次数更少 }
- 支持排序和分组（叶子节点天然有序）
- 全表扫描友好 （沿着叶子节点链表顺序读取即可顺序完成全表扫描，比随机IO快得多） 



数据类型
```
INT    --整数
DECIMAL(m,n)    -小数点小数 m几位数 n小数点后几位
VARCHAR(n)     --字符串
BLOB         --（图片 影片 档案）
DATE          --'YYYY-MM--DD'日期
TMESTAMP     --'YYYY-MM-DD HH:MM:SS'记录时间
```

建库建表
```
CREATE DATABASE `sql_test`;
SHOW DATABASES;
USE `sql_test`;
```

```
CREATE TABLE student(
	`student` INT PRIMARY KEY AUTO_INCREMENT,
	`name`  VARCHAR(20) NOT NULL ,
	`major` VARCHAR(50) DEFAULT NULL,
	`GPA` DECIMAL(3,2) DEFAULT 0
);
CREATE INDEX idx_student_name ON student(`name`)
```


```
CREATE TABLE student(
	`student_id` INT PRIMARY KEY AUTO_INCREMENT,
	`name` VARCHAR(20) NOT NULL,
	`major` VARCHAR(20) DEFAULT NULL,
	`GPA` DECIMAL(3,2) DEFAULT 0,
	
	INDEX idx_student_name(`name`)
);
```

```
DESCRIBE `student`;
```

增加列
```
ALTER TABLE `student` ADD GPA DECIMAL(3,2);
```

```
ALTER TABLE `student` DROP COLUMN GPA;
```
增
```
INSERT INTO `student` VALUES(1,"张三","数学",3.21);

INSERT INTO `student` (`name`,`major`,`student_id`,`GPA`) VALUES("lihua","数学",4,3.21);
```
改
```
UPDATE `student`
SET `major` = '英语'
WHERE `major` = 'English';
```
删
```
DELETE FROM `student`
WHERE `student_id` = 4;
```
查
```
SELECT * FROM `student`;
SELECT `name`,`major` FROM `student`;

SELECT * FROM `student` ORDER BY `GPA`;
SELECT * FROM `student` ORDER BY `GPA` DESC;
SELECT * FROM `student` ORDER BY `GPA` `student` DESC;

SELECT * FROM `student` ORDER BY `GPA` DESC LIMIT 3;

SELECT * FROM `student`
WHERE `major`= "物理"
ORDER BY `GPA` DESC
LIMIT 2
```

