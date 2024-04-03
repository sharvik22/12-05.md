# Домашнее задание к занятию «Индексы» Шарапат Виктор

### Задание 1

Напишите запрос к учебной базе данных, который вернёт процентное отношение общего размера всех индексов к общему размеру всех таблиц.

### Решение 1
![image](https://github.com/sharvik22/12-05.md/blob/main/images/1.png)

---

### Задание 2

Выполните explain analyze следующего запроса:
```sql
select distinct concat(c.last_name, ' ', c.first_name), sum(p.amount) over (partition by c.customer_id, f.title)
from payment p, rental r, customer c, inventory i, film f
where date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date and r.customer_id = c.customer_id and i.inventory_id = r.inventory_id
```
- перечислите узкие места;
- оптимизируйте запрос: внесите корректировки по использованию операторов, при необходимости добавьте индексы.

### Решение 2

## До оптимизации 
![image](https://github.com/sharvik22/12-05.md/blob/main/images/2.png)
![image](https://github.com/sharvik22/12-05.md/blob/main/images/2-1.png)

## После оптимизации 

![image](https://github.com/sharvik22/12-05.md/blob/main/images/2-2.png)
![image](https://github.com/sharvik22/12-05.md/blob/main/images/2-3.png)

---

### ДОРАБОТКА

![image](https://github.com/sharvik22/12-05.md/assets/136818757/3e296d8e-f892-4f5f-af3b-13f4104d9472)

![image](https://github.com/sharvik22/12-05.md/assets/136818757/6b6f22e5-96c8-4085-990d-bcac427a9d69)

![image](https://github.com/sharvik22/12-05.md/assets/136818757/73414d54-0da0-4517-9b44-d01f6a6c1196)

![image](https://github.com/sharvik22/12-05.md/assets/136818757/ba296e3f-e90c-418f-a3d0-d684689cbb40)

---

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*

Самостоятельно изучите, какие типы индексов используются в PostgreSQL. Перечислите те индексы, которые используются в PostgreSQL, а в MySQL — нет.

*Приведите ответ в свободной форме.*

### Решение 3

# В PostgreSQL используются следующие индексы:
* B-tree индекс
* Hash индекс
* GiST (Generalized Search Tree) индекс
* SP-GiST (Space-Partitioning GiST) индекс
* GIN (Generalized Inverted Index) индекс
* BRIN (Block Range Index) индекс

# В MySQL используются следующие типы индексов:
* B-tree индекс (применяется по умолчанию для большинства индексов)
* Full-Text индекс (используется для поиска по текстовым данным)
* Spatial индекс (используется для работы с пространственными данными)
* Memory-Optimized индекс (используется для таблиц типа MEMORY)

# В MySQL не используется Hash индекс.
Основными типами индексов в MySQL являются B-tree индексы, которые используются для большинства типов индексации.
