Given bronze tables as below:
```sql
CREATE TABLE bronze_design
  (id INTEGER, name VARCHAR, type VARCHAR, designer VARCHAR);
INSERT INTO bronze_design VALUES 
  (0,  'part0',   'part', 'Allen'), 
  (1,  'part1',   'part', 'Bobby'), 
  (2,  'part2',   'part', 'Cindy'), 
  (3,  'part00',  'part', 'David'), 
  (4,  'part001', 'part', 'Eddie'), 
  (5,  'part002', 'part', 'Frank'), 
  (6,  'part10',  'part', 'George'), 
  (7,  'part100', 'part', 'Harry'), 
  (8,  'part101', 'part', 'Ivan'), 
  (9,  'part11',  'part', 'Jack'), 
  (10, 'part110', 'part', 'Kevin'), 
  (11, 'part111', 'part', 'Larry'); 

-- company info, import by a CSV
CREATE TABLE bronze_design_office
  (design VARCHAR, office VARCHAR);
INSERT INTO bronze_design_office VALUES 
  ('part001', 'SmartView' ), 
  ('part10', 'FutureIdea');
```

With Data Requirement as below:
- In the new system, each design we call it has a project, and need a unique ID as uuid().
- Design could be a parent of another design by their naming convention, for example, part1 will be the parent of part11.
- Design which has the same ascendant becomes a design group, with the root design name as the group name.
- Design in the same group, their designer will have same design office.

Could you suggest me a silver table schema and the SQL to transform the bronze table to the silver table? DB is duckdb
