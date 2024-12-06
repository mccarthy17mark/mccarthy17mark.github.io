---
title: MySql
layout: tutorial
pageId: mysql
parentId: tech
usemathjax: true

published: false
---

{% include toc.html %}

mysql -u root -p

SELECT `COLUMN_NAME` 
FROM `INFORMATION_SCHEMA`.`COLUMNS` 
WHERE `TABLE_SCHEMA`='yourdatabasename' 
    AND `TABLE_NAME`='yourtablename';
	
CREATE TABLE IF NOT EXISTS table_name (
    column_name TYPE [column_constraint],
    [table_constraint,]
);

CREATE TABLE IF NOT EXISTS supplies (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255),
  description VARCHAR(255),
  manufacturer VARCHAR(255),
  color VARCHAR(255),
  inventory INT CHECK (inventory >= 0)
);
