[1] SQL the complete reference, 3rd

# Chapter 13

- DDL: Data Definition Language
- Core:
  - 3 verbs: CREATE, DROP, ALTER
  - Can be used while the DBMS is running
- CREATE TABLE
  - Basic syntax: Fig. 13-1
  - The creator is the owner by default. But you can also specify the owner in the statement.
  - The order of the columns in the statement is also the left-to-right order of the columns in the created table.
- DROP TABLE
  - Basic syntax: Fig. 13-3
- ALTER TABLE
  - Basic syntax: Fig. 13-4
- CASCADE vs. RESTRICT
  - CASCADE: If the dropped object has objects depending on it, drops them as well.
  - RESTRICT: If the dropped object has objects depending on it, throws error.

# Chapter 11: Data integrity
