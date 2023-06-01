# Mongodb Question and Query

# Test 1

### use WecodeAcademy

```sql
use wecodeacademy;
```

### createCollection

```sql
db.createCollection('Student');
```

### insert data

```sql
db.student.insertOne({
  name: 'Khalil Joya',
  fatherName: 'Murad Kha Joya',
  mobileNo: 9079883575,
  email: 'khalil@gmail.com',
  address: [
    'Jhotwara',
    'Jaipur',
    'Raj',
    302012
  ],
  admissionDate: new Date("2023-02-01"),
  dob: new Date("2003-09-30")
})
```

```sql
db.student.insertOne({
  name: 'Shera',
  fatherName: 'Kalam Kha',
  mobileNo: 9079883575,
  email: 'shermo@gmail.com',
  address: [
    'Karkwal',
    'Merta City',
    'Raj',
    341510
  ],
  admissionDate: new Date("2023-04-20"),
  dob: new Date("2002-05-25")
})
```

```sql
db.student.insertOne({
  name: 'Rafik',
  fatherName: 'Ganni Kha',
  mobileNo: 9116451518,
  address: [
    'Peeh',
    'Ajmer City',
    'Raj',
    302012
  ],
  admissionDate: new Date("2023-04-20"),
  dob: new Date("2004-06-15")
})
```

```sql
db.student.insertOne({
 name: 'Sameer',
  fatherName: 'Murad Kha',
  mobileNo: 9509438964,
  email: 'sameer@gmail.com',
  address: [
    'Karkwal',
    'Merta City',
    'Raj',
    341510
  ],
  admissionDate: new Date("2023-04-20"),
  dob: new Date("2005-06-25")
})
```

```sql
db.student.insertOne({
  name: 'Sohil',
  fatherName: 'Rahim Kha',
  mobileNo: 9079883575,
  email: 'sohil@gmail.com',
  address: 'Sikar',
  admissionDate: new Date("2023-03-01"),
  dob: new Date("2001-03-02")
})
```

```sql
db.student.insertOne({
   name: 'Sonu',
  fatherName: 'Khalil',
  mobileNo: 9079883575,
  email: 'rahim@gmail.com',
  address: 'Jaipur',
  admissionDate: new Date("2023-03-01"),
  dob: new Date("2004-07-18")
})
```

### 1. Vo sare students ki list btao jinka email ni hai

```sql
db.student.find({email: {$exists: false}})

```

### 2. Vo sare students ki list btao jinka mobile number same hai

```sql
db.student.find({mobileNo : {$eq :9079883575}})
```

### 3. Sare students ka only email and mobile return krvao

```sql
db.student.find({},{email:1 ,mobileNo : 1})
```

### 4. students record ki name se sorting krni hai

#### ascending order

```sql
db.student.find({}).sort({name : 1})

```

#### descending order

```sql
db.student.find({}).sort({name : -1})
```

### 5. vo sare students ki list return kro jinka admission last 3 months me hua hai

```sql
var currentDate = new Date();
var last3Month = new Date();
last3Month.setMonth(currentDate.getMonth() - 3)

db.student.find({admissionDate : {$gte : last3Month, $lte : currentDate}})
```

### 6. vo sare students ka only naam btao jinka admission current month me hua hai

```sql
var currentDate = new Date();
var stratMonth = new Date(currentDate.getFullYear(), currentDate.getMonth(), 1);
var endMonth = new Date(currentDate,getFullYear(), currentDate.getMonth() + 1, 0);

db.student.find({admissionDate : {$gte : stratMonth, $lte : endMonth}}, {studentName : 1})
```

### 7. vo sare students ka naam btao jinki dob year same hai

```sql

```

### 8. vo sare students ka naam btao jinka address jaipur, nagaur ya karauli ho

```sql
db.student.find({address: { $in: ["Jaipur", "Nagaur", "Karauli"] }}, { name: 1, _id: 0 })
```

### 9. vo sare students ka naam btao jo Sikar, Jhunjhun se ni hai

```sql
db.student.find({address: { $nin: ["Sikar", "Jhunjhun"] }}, { name: 1, _id: 0 })
```

### 10. vo sare students ka naam btao jinka Address Sikar hai and fathername Rahim hai

```sql
db.student.find({$and: [{ address: "Sikar" },{ fatherName: "Rahim" }]}, { name: 1, _id: 0 })
```

### 11. vo sare students ka naam btao jinka fathername Khalil ho or email id rahim@gmail.com ho

```sql
db.student.find({$or: [{ fatherName: "Khalil" },{ email: "rahim@gmail.com" }]}, { name: 1, _id: 0 })
```

### 12. question 11 ko nor se kro

```sql
db.student.find({$nor: [{ fathername: "Khalil" },{ email: "rahim@gmail.com" }]}, { name: 1, _id: 0 })
```

### 13. Vo sare students ka naam btao jinka father name Ahmed ni hai

```sql
db.student.find({ "fatherName": { $not: { $eq: "Ahmed" } } }, { name: 1,  _id :  0 })
```

### 14. Vo sare students ka naam btao jinka mobile 945345435 ni hai

```sql
db.student.find({mobile: { $ne: "945345435" }}, { name: 1, _id: 0 })
```

# Test 2

### 1. Create database wecodeacademy

```sql
use wecodeAcademy
```

### 2. create collection batches

```sql
db.createCollection('batches')
```

### 3. add 5 documents in this way

```sql
db.batches.insertMany([{
batchName : 'Node.js',
students : ["Khalil","SherMo","Aarif","Rafik","Mazzid"],
duration :5,
fees : 5000,
marks : [30,40,50,60,70,80]
},

{
batchName : 'JavaScript',
students : ["Irfan","Khalil","SherMo.","Taiyab","Aadil"],
duration :10,
fees : 10000,
marks : [50,60,70,80,30,90,99,95,75,45,68,87,59]
},

{
batchName : 'Designing',
students : ["Sohil Khan","Sameer","Tahir Khan","Farman","Aadil"],
duration :7,
fees : 15000,
marks : [60,70,80,90,99,95,75,68,87,59]
},
{
batchName : 'Node.js',
students : ["Afjal","VAkeel"]
duration :15,
fees : 12000,
marks : [80,30,90,99,95]
},

{
batchName : 'Designing',
students : ["Farman","Sohil"],
duration :13,
fees : 18000,
marks : [60,70,80,90,99,95,75,68,87,59]
}
]);

```

### 4. Vo sare batches ke naam btao jinke student ke marks 50% se kam hai.

```sql
db.batches.find({marks: { $lt: 50 }});
```

### 5. marks array me se sirf vhi marks rkhne hain jo 60+= hain. baki sbko remove krdo.

```sql
db.batches.find({marks: { $lt: 60 }});
```

### 6. marks array me starting se 3rd index se 5 new marks add krne hai.

```sql
db.batches.updateMany({}, {$push : {marks : {$each : [70,80,90,100,60], $position: 3}}});
```

### 7. Back/Last se 4th position se 5 new marks add krne hain.

```sql
db.batches.updateMany({}, {$push : {marks : {$each : [30,40,50,60,70], $position: -4}}});
```

### 8. Students array ko ascending and marks Array ko desc order me sort krna hai.

```sql
db.batches.updateMany({}, {$push : {students : {$each : [], $sort : 1}, marks:{$each : [], $sort : -1}}});
```

### 9. Marks array me sirf 10 numbers rkhne hain starting se baki sb remove kr dene hain.

```sql
db.batches.updateMany({}, {$push : {marks : {$each : [], $slice : 10}}});
```

### 10. Agar marks array me max number 99 hai to thik otherwise max number 99 krdo.

```sql
db.batches.updateMany({},{ $max: { "marks.$[]": 99 } });
```

### 11. fees field ko rename krke totalfees krdo.

```sql
db.batches.updateMany({}, {$rename : {"fees": "totalFees"}});
```

### 12. duration ko 2 se multiply krdo.

```sql
db.batches.updateMany({}, {$mul : {duration : 2}});
```

### 13. students array me se Irfan, Adil ka naam hai to remove krdo.

```sql
db.batches.updateMany({}, {$pull : {students : {$in : ["Irfan", "Aadil"]}}});
```

### 14. Agar fees 10000 se jyada hai to duration field ko remove krdo.

```sql
db.batches.updateMany({totalFees : {$gt : 10000}}, {$unset : {duration : ""}});
```

### 15. Vo sare students search kro jinke naam me Khan hai aur batchName Designing hai aur fees 12000 se jyada hai aur students array ki size 10 ho.

```sql
db.batches.find({$and : [{students : {$regex : /khan/i}}, {batchName : "Designing"}, {totalFees : {$gt : 12000}}, {students : {$size : 10}}]});
```

# Test 3

### 1. Create a collection named "books" in MongoDB.

```sql
db.createCollection("Books")
```

### 2. Insert a document into the "books" collection with the following details :

- Title: "The Great Gatsby"
- Author: "F. Scott Fitzgerald"
- Year: 1925

```sql
db.Books.insertOne({Title: "The Great Gatsby",Author: "F. Scott Fitzgerald",Year: 1925})
```

### 3. Insert another document into the "books" collection with the following details :

- Title: "To Kill a Mockingbird"
- Author: "Harper Lee"
- Year: 1960

```sql
db.Books.insertOne({Title: "To Kill a Mockingbird",Author: "Harper Lee",Year: 1960})
```

### 4. Write a query to find all documents in the "books" collection.

```sql
db.Books.find()
```

### 5. Write a query to find documents in the "books" collection where the author is "F. Scott Fitzgerald".

```sql
db.Books.find({Author: "F. Scott Fitzgerald" })
```

### 6. Write a query to find documents in the "books" collection where the year is greater than 1950.

```sql
db.Books.find({ Year: { $gt: 1950 } })
```

### 7. Write an update query to change the author of the document with the title "To Kill a Mockingbird" to "Harper Lee (edited)".

```sql
db.Books.updateOne({ Title: "To Kill a Mockingbird" },{ $set: { Author: "Harper Lee (edited)" } })
```

### 8. Write an update query to add a new field "genre" with the value "Fiction" to all documents in the "books" collection.

```sql
db.Books.updateMany({},{ $set: { genre: "Fiction" } })
```

### 9. Write a query to find documents in the "books" collection where the genre is "Fiction".

```sql
db.Books.find({ genre: "Fiction" })
```

### 10. Write a query to find documents in the "books" collection where the title starts with the letter "T".

```sql
db.Books.find({ Title: /^T/ })
```

### 11. Write an update query to increment the year by 1 for all documents in the "books" collection.

```sql
db.Books.updateMany({},{ $inc: { Year: 1 } })
```

### 12. Write a query to find documents in the "books" collection where the year is between 1950 and 1970.

```sql
db.Books.find({ Year: { $gte: 1950, $lte: 1970 } })
```

### 13. Write a query to find documents in the "books" collection where the author's name contains the letter "a".

```sql
db.Books.find({Author: /a/ })
```

### 14. Write an update query to remove the "genre" field from all documents in the "books" collection.

```sql
db.Books.updateMany({},{ $unset: { genre: "" }})
```

### 15. Write a query to find documents in the "books" collection where the author's name ends with the letter "y".

```sql
db.Books.find({ Author: /y$/ })
```

### 16. Write an update query to change the title of the document with the author "Harper Lee" to "Go Set a Watchman".

```sql
db.Books.updateOne({ Author: "Harper Lee" },{ $set: { Title: "Go Set a Watchman" } })
```

### 17. Write a query to find documents in the "books" collection where the title contains the word "Great".

```sql
db.Books.find({ Title: /Great/ })
```

### 18. Write a query to find documents in the "books" collection where the title is an exact match for "The Great Gatsby".

```sql
db.Books.find({ Title: "The Great Gatsby" })
```

### 19. Write an update query to add an array field named "categories" with the values ["Classic", "Fiction"] to all documents in the "books" collection.

```sql
db.Books.updateMany({},{ $set: { categories: ["Classic", "Fiction"] } })
```

### 20. Write a query to find documents in the "books" collection where the "categories" field contains the value "Fiction".

```sql
db.Books.find({ categories: "Fiction" })
```

### 21. Write a query to find documents in the "books" collection where the title contains the word "The" in a case-insensitive manner.

```sql
db.Books.find({ Title: { $regex: /The/i } })
```

### 22. Write a query to find documents in the "books" collection where the author's name starts with the letter "J".

```sql
db.books.find({ author: /^J/ })
```

### 23. Write an update query to increment the "year" field by 5 for all documents in the "books" collection.

```sql
db.Books.updateMany({},{ $inc: { Year: 5 } })
```

### 24. Write a query to find documents in the "books" collection where the title is not equal to "Moby Dick".

```sql
db.Books.find({ Title: { $ne: "Moby Dick" } })
```

### 25. Write a query to find documents in the "books" collection where the author's name is either "J.K. Rowling" or "George R.R. Martin".

```sql
db.Books.find({ Author: { $in: ["J.K. Rowling", "George R.R. Martin"] } })
```

### 26. Write a query to find documents in the "books" collection where the year is either 2000 or 2010.

```sql
db.Books.find({ Year: { $in: [2000, 2010] } })

```

### 27. Write an update query to multiply the "year" field by 2 for all documents in the "books" collection.

```sql
db.Books.updateMany({},{ $mul: { Year: 2 } })
```

### 28. Write a query to find documents in the "books" collection where the title ends with the letter "s".

```sql
db.Books.find({ Title: /s$/ })
```

### 29. Write a query to find documents in the "books" collection where the author's name is not in ["Stephen King", "Agatha Christie"].

```sql
db.Books.find({ Author: { $nin: ["Stephen King", "Agatha Christie"] } })
```

### 30. Write an update query to set the "year" field to 2022 for the document with the highest year in the "books" collection.

```sql
db.Books.updateOne({}, { $set: { Year: 2022 } }, { sort: { Year: -1 } });


db.Books.aggregate({ $group : { _id: null, max: { $max : "$Year" }}});
```
