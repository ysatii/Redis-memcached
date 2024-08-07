# Домашнее задание к занятию «Кеширование Redis/memcached» - Мельник Юрий Александрович




## Задание 1. Кеширование
 

1. `Приведите примеры проблем, которые может решить кеширование.`

### Приведите ответ в свободной форме.

## Решение 1.
 <blockquote>
  <p> 1. **Повышение производительности** - достигается за счет складывания в кэш данных, к которым чаще всего происходит  обращение; </p>
  <p> 2. **Увеличение скорости ответа;** -  достигается за счет складывания в кэш данных, к которым чаще всего происходит  обращение; </p>
  <p> 3. **Экономия ресурсов;** базы данных, например, применяя кэширование тяжелых запросов; </p>
  <p> 4. **Сглаживание бустов трафика**. - резкое увеличение нагрузки на сервере, напрмер веб - увеличилось колличество покупателей магазина </p>  
  Кеш может быть файловым или использовать оперативную память сервера
 </blockquote>


## Задание 2. Memcached
 
1. `Установите и запустите memcached.`
### Приведите ответ в свободной форме.



## Решение 2
1. Установим memcached  
```
sudo apt install memcached
```

2. Проверим статус memcached  
```
systemctl status memcached
```

![alt text](https://github.com/ysatii/Redis-memcached/blob/main/img/image1.jpg)   

3. подлючимся к порту 11211  с помощью telnet и выполним команду **stats**  
![alt text](https://github.com/ysatii/Redis-memcached/blob/main/img/image1_1.jpg)  


## Задание 3. Удаление по TTL в Memcached

1. Запишите в memcached несколько ключей с любыми именами и значениями, для которых выставлен TTL 5.

### Приведите ответ в свободной форме.

## Решение 3
подлючаемся к серверу
```
telnet localhost 11211
```

задаем ключ **name** ttl 5 секунд, длина 4
```
set name 0 5 4
1234
```

ответ  
 <blockquote>
  
  <p>1234</p>
  <p>STORED</p>
 </blockquote>


получаем ключ name, Мы не успели по времени, значение уничтожено  
```
get name
```
ответ  
 <blockquote>
  <p>END</p>
 </blockquote>

задаем ключ **name** ttl 15 секунд, длина 4  
```
set name 0 15 4           
1234
```

ответ  
 <blockquote>
  <p>STORED</p>
 </blockquote>



получаем ключ name  
```
get name
```
ответ  
 <blockquote>
  <p>VALUE name 0 4</p>
  <p>1234</p>
  <p>END</p>
 </blockquote>

устанавливаем first ttl 5, длина 4 байта  
```
set first 0 5 4
qwer
```
ответ  
 <blockquote>
  <p>STORED</p>
 </blockquote>

получаем ключ first, Мы не успели по времени, значение уничтожено  
```
get first
```
ответ  
 <blockquote>
  <p>END</p>
 </blockquote>

устанавливаем ftp ttl 30, длина 6 байта
```
set ftp 0 30 6
valera
```
ответ  
 <blockquote>
  <p>STORED</p>
 </blockquote>

получаем ключ first
```
get ftp
```

ответ  

 <blockquote>
  <p>VALUE ftp 0 6</p>
  <p>valera</p>
  <p>END</p>
  
 </blockquote>

получаем ключ ftp Мы не успели по времени, значение уничтожено  
```
get ftp  
```
ответ  
 <blockquote>
  <p>END</p>
 </blockquote>

![alt text](https://github.com/ysatii/Redis-memcached/blob/main/img/image3.jpg)   

## Задание 4. Запись данных в Redis

1. Через redis-cli достаньте все записанные ключи и значения из базы, приведите скриншот этой операции.

### Приведите ответ в свободной форме.

## Решение 4

1. Устанавливаем redis
```
sudo apt install redis
```
![alt text](https://github.com/ysatii/Redis-memcached/blob/main/img/image4.jpg)  


2. Проверяем статус БД redis
```
systemctl status redis
```
![alt text](https://github.com/ysatii/Redis-memcached/blob/main/img/image4_1.jpg)  

3. Проверяем версию redis
```
redis-cli
info
```
![alt text](https://github.com/ysatii/Redis-memcached/blob/main/img/image4_2.jpg)  

4. установим ключ  key1 = valera  
127.0.0.1:6379> set key1 valera  
OK  

5. проверим ttl key1  
127.0.0.1:6379> ttl key1  
(integer) -1  

6. получим значение key1  
127.0.0.1:6379> get key1  
"valera"  

7. зададим срок жизни  key1 = 10 сек.  
127.0.0.1:6379> expire key1 10  
(integer) 1  

8.  ttl key1 уменьщился до 6 секунд   
127.0.0.1:6379> ttl key1  
(integer) 6  

9.  ttl key1 уменьщился истек, ключ уничтожен 
127.0.0.1:6379> ttl key1  
(integer) -2  

10. значение ключа nil ключ уничтожен
127.0.0.1:6379> get key1  
(nil)  

11. установим ключ  my1 = 12345678 
127.0.0.1:6379> set my1 12345678  
OK  

12. получим значение my1  
127.0.0.1:6379> get my1  
"12345678"  

13. проверим ttl my1  
127.0.0.1:6379> ttl my1  
(integer) -1  
ключ не имеет конкретного времени жизни

14. создадим сколлекцию с содержимым a b c   
127.0.0.1:6379> lpush my_list a b c   
(integer) 3  

15. Добавим новый элемент test   
127.0.0.1:6379> lpush my_list test   
(integer) 4  

16. получим элементы коллекции my_list
127.0.0.1:6379> lrange my_list 0 -1  
1) "test"  
2) "c"  
3) "b"  
4) "a"  
в коллекции данного типа элементы можно ставлять только слева  

127.0.0.1:6379>   


![alt text](https://github.com/ysatii/Redis-memcached/blob/main/img/image4_3.jpg)  



## Задание 5*. Работа с числами

1. Запишите в Redis ключ key5 со значением типа "int" равным числу 5. Увеличьте его на 5, чтобы в итоге в значении лежало число 10.

### Приведите скриншот, где будут проделаны все операции и будет видно, что значение key5 стало равно 10.

## Решение 5
1. установим ключ  key = 5  
127.0.0.1:6379> set key 5  
OK  

2. получим значение key  
127.0.0.1:6379> get key  
"5"  

3. Увеличим на 5  
127.0.0.1:6379> incrby key 5  
(integer) 10  

2. получим значение key  
127.0.0.1:6379> get key  
"10"  

![alt text](https://github.com/ysatii/Redis-memcached/blob/main/img/image5.jpg)  
