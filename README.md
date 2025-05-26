# Bonus Section (Answer Any 5 Questions on readme.md in Bangla) → 10 Marks

## 1. What is PostgreSQL?

PostgreSQL, যেটাকে সংক্ষেপে postgres বলা হয়, এটা একটি শক্তিশালী open-source object-relational database system যেটার ৩৫ বছরের বেশি active development history আছে। এটা প্রথমে ১৯৮০-এর দশকে University of California, Berkeley-তে develop করা হয়েছিল।

PostgreSQL এখনকার দিনে সবচেয়ে advanced database system গুলোর একটি। এটা SQL এবং JSON উভয় ধরনের querying সাপোর্ট করে।

অনেক web application এবং mobile analysis application-এ এটি primary database হিসেবে ব্যবহৃত হয়।

PostgreSQL শেখা সহজ এবং এটি একদম ফ্রি, যেখানে অন্য অনেক database ব্যবহারে হাজার হাজার ডলার লাগে, সেখানে postgreSQL একদম ১০০% ফ্রি — যে কেউ এটা ডাউনলোড করে নিজের প্রোজেক্টে ব্যবহার করতে পারে।

---

## 2. What is the purpose of a database schema in PostgreSQL?

PostgreSQL-এ schema হলো একটা logical structure যেটা table, view, function, constraint, index, data type ইত্যাদি জিনিসগুলোকে গ্রুপ করে manage করতে সাহায্য করে।

একটি database-এর মধ্যে একাধিক schema থাকতে পারে, কিন্তু প্রতিটা schema শুধুমাত্র একটি database-এর অন্তর্ভুক্ত হয়।

Schema-এর কিছু প্রধান উদ্দেশ্য:

* **Organization and structure**: related objects গুলোকে logically group করে।
* **Security and Access Control**: schema level-এ permission set করা যায়।
* **Avoiding Name Conflicts**: এক schema-এ `table1`, আরেকটাতে একই নামে `table1` থাকলেও conflict হবে না।
* **Easier Maintenance**: বড় database সহজে manage ও maintain করা যায়।

---

## 3. Explain the Primary Key and Foreign Key concepts in PostgreSQL.

**Primary Key** হলো table-এর প্রতিটি row বা record-এর জন্য একটা unique identifier — একরকম ID card এর মতো।

* এটা প্রতিটি record কে uniquely identify করে।
* এটা unique হতে হবে।
* এটা null (খালি) হতে পারে না।

```
CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);
```

এখানে `user_id` হচ্ছে primary key।

</br>**Foreign Key** হচ্ছে অন্য একটা table-এর primary key যেটা current table-এ reference হিসেবে ব্যবহৃত হয়।

```
CREATE TABLE orders (
  order_id SERIAL PRIMARY KEY,
  user_id INT REFERENCES users(user_id),
  order_date DATE
);
```

এই example-এ:

* `order_id` হচ্ছে `orders` টেবিলের primary key।
* `user_id` হচ্ছে foreign key, যেটা `users` টেবিলের primary key (`user_id`) কে reference করে।

এইভাবে দুইটা table-এর মাঝে একটা relationship তৈরি হয়।

---

## 4. What is the difference between the VARCHAR and CHAR data types?

`CHAR` আর `VARCHAR` এর মূল পার্থক্য হলো — `CHAR` fixed size character রাখে, আর `VARCHAR` variable size character রাখে।

**CHAR**:

* Fixed length string রাখে।
* প্রতিটা value same length নেয় (padding করে নেয় যদি কম হয়)।
* Memory allocation static হয়।
* যখন সব value একই size-এর হবে ধরে নেওয়া যায়, তখন `CHAR` ব্যবহার করা ভালো।

**VARCHAR**:

* Variable length string রাখে।
* Data যতটুকু প্রয়োজন ততটুকু space নেয়।
* Memory allocation dynamic হয়।
* যখন data entry size বিভিন্ন রকম হয়, তখন `VARCHAR` বেশি উপযুক্ত।

---

## 5. Explain the purpose of the WHERE clause in a SELECT statement.

`SELECT` statement-এ `WHERE` clause ব্যবহার করা হয় একটা নির্দিষ্ট condition অনুযায়ী table থেকে row filter করতে।

মানে — শুধু যেসব row condition match করে, সেগুলোই return হবে।

উদাহরণস্বরূপ:

```
  <!-- students -->
+----+--------+-----+
| id | name   | age |
+----+--------+-----+
| 1  | Naruto | 16  |
| 2  | Ichigo | 19  |
| 3  | Luffy  | 14  |
| 4  | Goku   | 28  |
| 5  | Eren   | 18  |
+----+--------+-----+
```

এখন যদি আমরা এমন students-এর data দেখতে চাই যাদের বয়স ১৮ বা তার বেশি, তাহলে query হবে:

```
SELECT * FROM students WHERE age >= 18;
```

**Output:**

```
  <!-- students -->
+----+--------+-----+
| id | name   | age |
+----+--------+-----+
| 2  | Ichigo | 19  |
| 4  | Goku   | 28  |
| 5  | Eren   | 18  |
+----+--------+-----+
```

এখানে `WHERE age >= 18` condition ব্যবহার করে Naruto এবং Luffy কে exclude করা হয়েছে কারণ তারা ১৮ বছরের কম।