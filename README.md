## Creating and Insert the Recipes Database in SQL

``` SQL
CREATE TABLE recipes (
  recipe_id INT NOT NULL,
  recipe_name VARCHAR(30) NOT NULL,
  PRIMARY KEY (recipe_id),
  UNIQUE (recipe_name)
);

INSERT INTO recipes 
    (recipe_id, recipe_name) 
VALUES 
    (1,"Tacos"),
    (2,"Tomato Soup"),
    (3,"Grilled Cheese");
```

## Create the Ingredients table:

``` SQL
CREATE TABLE ingredients (
  ingredient_id INT NOT NULL, 
  ingredient_name VARCHAR(30) NOT NULL,
  ingredient_price INT NOT NULL,
  PRIMARY KEY (ingredient_id),  
  UNIQUE (ingredient_name)
);
INSERT INTO ingredients
    (ingredient_id, ingredient_name, ingredient_price)
VALUES 
    (1, "Beef", 5),
    (2, "Lettuce", 1),
    (3, "Tomatoes", 2),
    (4, "Taco Shell", 2),
    (5, "Cheese", 3),
    (6, "Milk", 1),
    (7, "Bread", 2);
```


## Create the recipe-ingredient-mapping table
``` SQL
CREATE TABLE recipe_ingredients (
  recipe_id int NOT NULL, 
  ingredient_id INT NOT NULL, 
  amount INT NOT NULL,
  PRIMARY KEY (recipe_id,ingredient_id)
);

INSERT INTO recipe_ingredients 
    (recipe_id, ingredient_id, amount)
VALUES
    (1,1,1),
    (1,2,2),
    (1,3,2),
    (1,4,3),
    (1,5,1),
    (2,3,2),
    (2,6,1),
    (3,5,1),
    (3,7,2);
```

``` SQL

SELECT * FROM ingredients
    WHERE ingredient_price > 1
    GROUP BY ingredient_name
    HAVING MIN (ingredient_price) > 2
    order by (ingredient_id) ASC

```
The HAVING clause was added to SQL because the WHERE keyword cannot be used with aggregate functions. <br />

The SQL ORDER BY clause is used to sort the data in ascending or descending order, based on one or more columns. Some databases sort the query results in an ascending order by default. <br />

The SQL GROUP BY clause is used in collaboration with the SELECT statement to arrange identical data into groups. This GROUP BY clause follows the WHERE clause in a SELECT statement and precedes the ORDER BY clause. <br />

## Sub-Query

``` SQL
CREATE TABLE t1 (s1 INT, s2 CHAR(5), s3 FLOAT);
INSERT INTO t1 VALUES (1,'1',1.0);
INSERT INTO t1 VALUES (2,'2',2.0);
SELECT sb1,sb2,sb3
  FROM (SELECT s1 AS sb1, s2 AS sb2, s3*2 AS sb3 FROM t1) AS sb
  WHERE sb1 > 1;
```
