Practice Data: https://github.com/Apollo-Level2-Web-Dev/mongodb-practice



Get ready to unlock the secrets of Mongoose, your key to mastering MongoDB in the Node.js world. This course will turn you into a data boss, teaching you how to add, search for, and change your information with ease.



Let's delve into the exciting journey that will make you a Mongoose master! Here's what you'll explore,



1) Install MongoDB compass & No SQL Booster ( windows, Mac & Linux): Before we dive in, we'll show you how to install the tools you need: MongoDB Compass & NoSQL Booster (think of them as fancy flashlights for your data). We'll have instructions for Windows, Mac, and Linux users.



2) insert, insertOne, find, findOne, field filtering, project: Dive into the fundamentals of inserting data into your MongoDB collections using insert and insertOne methods Master retrieving data. Explore the find method for retrieving multiple documents and findOne for fetching a single document. Learn how to filter specific fields from your retrieved documents using field filtering and projection techniques.



3) $eq, $neq, $gt, $lt, $gte, $lte: Unleash the power of comparison operators like $eq (equal to), $neq (not equal to), $gt (greater than), and more to pinpoint the exact data you need.



4) $in, $nin, implicit and condition: $in (included in) and $nin (not included in) operators for precise data selection. We'll also delve into implicit and conditional logic for crafting complex queries.



5) $and, $or, implicit vs explicit: learn how to combine multiple conditions using $and and $or operators to fine-tune your data retrieval. We'll cover both implicit and explicit ways to combine conditions for maximum flexibility.



6) $exists, $type,$size: Discover operators like $exists, $type, and $size for detailed data inspection.



7) $all , $elemMatch: Master array manipulation with operators like $all, $elemMatch. 



8) $set, $addToSet, $push: Explore operators like $set for updating existing field values, $addToSet for adding unique elements to an array, and $push for adding elements to an array regardless of uniqueness.



9) $unset, $pop, $pull, $pullAll: Learn how to remove specific fields using $unset, remove the last element from an array with $pop, and target specific elements for removal using $pull and $pullAll. 



10) More about $set: We'll also delve deeper into the nuances of $set for advanced usage scenarios.



11) Delete documents, drop collection and how to explore by yourself: Discover how to delete specific documents based on criteria. Learn how to completely remove a collection from your database. We'll equip you with strategies for effectively navigating the official Mongoose documentation to explore advanced features and functionalities on your own.



By diligently following this path and practicing the techniques you learn, you'll be well on your way to becoming a Mongoose Master and confidently managing your MongoDB data!

## 15-1-A Install MongoDB compass & No SQL Booster ( windows)
![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)
copy the path name
![alt text](image-3.png)
double click in path name and click and past the evn
![alt text](image-4.png)

##  15-2 Insert,insertOne, find, findOne, field filtering, project
![alt text](image-5.png)
![alt text](image-6.png)
- 1 when you add one item use insertOne
- 2 when you add Many items use insertMany
- 3 when you find One  items use FindOne
- 4 when you find Many  items use Find
###### Fill Filtering
![alt text](image-7.png)
- 2nd Method use project()
![alt text](image-8.png)

## 15-3 $eq, $neq, $gt, $lt, $gte, $lte
#####  equal =
![alt text](image-9.png)
![alt text](image-10.png)
##### not equal
![alt text](image-11.png)
##### greater than
![alt text](image-12.png)
##### greater than equal = then i am sorting
![alt text](image-13.png)
![alt text](image-14.png)
## 15-4 $in, $nin, implicit and condition
```sql
db.test.find({gender:"Female",age:{$lte:30,$gte:18}},{age:1,gender:1}).sort({ age:1 })
```
  // implicit adn condition
  ![alt text](image-15.png)
  - use $in
  ![alt text](image-16.png)
  - use not $in
  ![alt text](image-17.png)
  ![alt text](image-18.png)
  - use $in
  ```sql
  interests: {$in:["Travelling","Writing"]},
  ```
  ![alt text](image-19.png)
## 15-5 $and, $or, implicit vs explicit
- all data show but now show who is age 16
```sql
db.test.find({
    $and: [
        { age: { $ne: 16 } },
        { age: { $lte: 30 } }
    ]
}).project({age:1,gender:1}).sort({age:-1 })
  // implicit adn condition
  ```
  ![alt text](image-20.png)


```sql
db.test.find({
    $or: [
     { interests:"Cooking"},
     { interests:"Gaming"},
    ]
}).project({interests:1}).sort({age:1 })
```
  ![alt text](image-21.png)

  ```sql
  db.test.find({
    age:{$not:{$gte:50},},
  
}).project({interests:1,age:1})
```
![alt text](image-22.png)

```sql
db.test.find({"skills.name":{$in:["JAVASCRIPT","PYTHON"]}
}).project({interests:1,skills:1}).sort({age:1 })
// use or operatot
// db.test.find({
//     $or: [
//       {"skills.name":"JAVASCRIPT"}
//     ]
// }).project({interests:1,skills:1}).sort({age:1 })
  // implicit adn condition
  ```

  ## 15-6 $exists, $type,$size
  - $exists
  ![alt text](image-23.png)
  - $type
  ![alt text](image-24.png)

 - $size 
  ![alt text](image-25.png)

  ## 15-7 $all , $elemMatch
  - if anyone want  cooking array of he find out index type and field must be string

  db.test.find({"interests.1":"Cooking"},{interests:1})
  ![alt text](image-26.png)


  - all operators he is find same array of objects not need same to same match
```sql
  db.test.find({
 interests:{$all:[ "Gaming", "Cooking", "Writing" ]}
  
}).project({interests:1})
```
![alt text](image-27.png)

- output not showing because he is also want adject match
![alt text](image-28.png)
same to same but if you want just match 2 values then show result use $eleMatch
![alt text](image-29.png)

- $eleMatch
![alt text](image-31.png)
## 15-8 $set, $addToSet, $push
- updateOne
![alt text](image-32.png)
- non primitive type data  array,objects etc you dont use $set for update
- before update interest 
![alt text](image-33.png)
![alt text](image-34.png)
- after update
![alt text](image-35.png)
- $addToSet
![alt text](image-36.png)
- if you want one or more data added use $each
- same value add just  one time 
![alt text](image-37.png)
- same value many time adding use push
![alt text](image-38.png)

## 15-9 $unset, $pop, $pull, $pullAll
- birthday is deleted
![alt text](image-39.png)
- pop last element deleted 
- -1 use first element deleted
![alt text](image-40.png)
- pull tene ber kora
![alt text](image-41.png)
- pull all
![alt text](image-42.png)
![alt text](image-43.png)

## 15-10 More about $set, how to explore documentation
- objects update use set
![alt text](image-44.png)
- positional operator
![alt text](image-45.png)
- increment
![alt text](image-46.png)
## 15-11 delete documents, drop collection and how to explore by yourself
![alt text](image-47.png)
![alt text](image-49.png)
![alt text](image-48.png)
![alt text](image-50.png)

Practice Data: https://github.com/Apollo-Level2-Web-Dev/mongodb-practice/blob/main/practice-data.json



Task Link: https://drive.google.com/file/d/1Be22y-R8C8SIMg_FOfYm8toz0swpocTT/view?usp=sharing