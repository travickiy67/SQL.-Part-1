
# Травицкий Сергей
# Домашнее задание к занятию «SQL. Часть 1»

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

---

Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1

Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.  

```
SELECT DISTINCT district FROM address WHERE district LIKE 'K%a' AND district NOT LIKE '% %';
```
<details>
<summary>Скрины</summary>

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/1.png)  

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/1.1.png)  
</details>


### Задание 2

Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года **включительно** и стоимость которых превышает 10.00.

```
SELECT * FROM payment WHERE payment_date BETWEEN '2005-06-15 00:00:00' AND '2005-06-18 23:59:59' AND amount > 10;
```

<details>
<summary>Скрины</summary>

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/2.1.png)   

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/2.2.png)   
</details>


### Задание 3

Получите последние пять аренд фильмов.

```
SELECT * FROM rental ORDER BY rental_id DESC LIMIT 5;
```
<details>
<summary>Скрины</summary>

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/3.1.png)  

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/3.2.png)  
</details>


### Задание 4

Одним запросом получите активных покупателей, имена которых Kelly или Willie. 

Сформируйте вывод в результат таким образом:
- все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
- замените буквы 'll' в именах на 'pp'.

```
SELECT LOWER(REPLACE(first_name, 'LL', 'PP')) AS Имя, LOWER(last_name) AS Фамилия FROM customer WHERE active = 1 AND (first_name LIKE 'Kelly' OR first_name LIKE 'Willie');
```
<details>
<summary>Скрины</summary>

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/4.1.png)  

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/4.2.png)  
</details>


## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 5*

Выведите Email каждого покупателя, разделив значение Email на две отдельных колонки: в первой колонке должно быть значение, указанное до @, во второй — значение, указанное после @.

```
SELECT LEFT(email, POSITION('@' IN email)-1) as 'левая_часть_email',
RIGHT(email, CHAR_LENGTH(email)-POSITION('@' IN email))  as 'правая_часть_email'
FROM sakila.customer;
```

<details>
<summary>Скрины</summary>

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/5.1.png)  

![img](https://github.com/travickiy67/SQL.-Part-1/blob/main/img/5.2.png)  
</details>

### Задание 6*

Доработайте запрос из предыдущего задания, скорректируйте значения в новых колонках: первая буква должна быть заглавной, остальные — строчными.


