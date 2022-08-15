# week03_day02_hw_rahafalammar

create database store;


create table countries (
code int primary key,
name varchar(20) unique not null,
continent_name varchar(20) not null
);


create table users (
id int primary key ,
country_code int,
full_name varchar(20) not null ,
email varchar(20) unique not null ,
gender char(1) check ( gender='m' or gender='f' ) not null ,
date_of_birth varchar(15),
created_at timestamp default NOW() not null,
foreign key (country_code) references countries(code)
);


create table orders (
id int primary key ,
user_id int,
status varchar(20) check ( status='start' or status='finish' ) not null,
created_at timestamp default NOW() not null,
foreign key (user_id) references users(id)
);


create table products (
id int primary key ,
name varchar(10) not null,
price int default 0,
status varchar(10) check ( status='valid' or status='expired' ) not null,
created_at timestamp default NOW() not null
);

create table order_products (
order_id int,
products_id int,
quantity int default 0,
foreign key (order_id) references orders(id),
foreign key (products_id) references products(id)
);


# DML - Insert

insert into countries values (20,'Egypt','Northeast Africa');
insert into users values (01,20,'RahafA','Ra@a.com','f','1970-01-01');
insert into orders values (01,01,'start','1970-01-01');
insert into products values (01,'T-shirt',100,'valid','1970-01-01');
insert into products values (02,'Dress',200,'valid','1970-01-01');
insert into order_products values (01,01,2);

# DML - Update

update countries set continent_name='Africa' where code=20;
delete from products where id=02;

