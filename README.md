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

![alt text](https://github.com/ysatii/Redis-memcached /blob/main/img/image1.jpg)   

3. подлючимся к порту 11211  с помощью telnet и выполним команду **stats**
![alt text](https://github.com/ysatii/Redis-memcached /blob/main/img/image1_1.jpg)  


## Задание 3. Удаление по TTL в Memcached

1. Запишите в memcached несколько ключей с любыми именами и значениями, для которых выставлен TTL 5.

### Приведите ответ в свободной форме.

## Решение 3
 <blockquote>
  <p> solushen </p>
 </blockquote>


## Задание 4. Запись данных в Redis

1. Через redis-cli достаньте все записанные ключи и значения из базы, приведите скриншот этой операции.

### Приведите ответ в свободной форме.

## Решение 4
 <blockquote>
  <p> solushen </p>
 </blockquote>


## Задание 5. Работа с числами

1. Запишите в Redis ключ key5 со значением типа "int" равным числу 5. Увеличьте его на 5, чтобы в итоге в значении лежало число 10.

### Приведите скриншот, где будут проделаны все операции и будет видно, что значение key5 стало равно 10.

## Решение 5
 <blockquote>
  <p> solushen </p>
 </blockquote>

