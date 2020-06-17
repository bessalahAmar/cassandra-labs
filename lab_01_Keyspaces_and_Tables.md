CQL playground : https://www.katacoda.com/joechu/scenarios/cql-quickstart

1.0) create keyspace named "test_keyspace" with simpleStrategy replication , RF=1 and make write durability to true.
CREATE KEYSPACE test_keyspace WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '1'} AND durable_writes = 'true';

1.1) what is the default value of write durability
true

1.2) what are consequence of using durable write ? 
writes going to be fast but there is high risk of data loss.

2.0) display all the keyspaces
DESC KEYSPACES

2.1) start using keyspace test_keyspace
USE test_keyspace

3.0) create table  employee_by_id with 
    id  int as primary key
    name as string
    position as string

CREATE TABLE employee_by_id ( id int PRIMARY KEY , name text , position text );

3.1) list all the tables this keyspace
DESC TABLES

3.2) get information about the table "employee_by_id"
DESC TABLE employee_by_id

4.0) create table  employee_by_maker with 
    id  int as clustering key
    age as string clustering key
    car_maker string as partition key
    car_model as string
CREATE TABLE employee_by_car_maker (id int , car_maker text , car_model text ,age text, PRIMARY KEY(car_maker,id,age));

4.1) create table  employee_by_maker_and_model with 
    id  int as clustering key
    age as string clustering key
    car_maker string as partition key
    car_model as string as partition key

CREATE TABLE employee_by_car_maker (id int , car_maker text , car_model text ,age text, PRIMARY KEY((car_maker,car_model),id,age));
    
    
    
