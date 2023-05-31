# MongoDB Question

### 1. Create a collection named "books" in MongoDB.

```
db.createCollection("Books")
```

### 2. Insert a document into the "books" collection with the following details :

- Title: "The Great Gatsby"
- Author: "F. Scott Fitzgerald"
- Year: 1925

```
db.Books.insertOne({Title: "The Great Gatsby",Author: "F. Scott Fitzgerald",Year: 1925})
```

### 3. Insert another document into the "books" collection with the following details :

- Title: "To Kill a Mockingbird"
- Author: "Harper Lee"
- Year: 1960

```
db.Books.insertOne({Title: "To Kill a Mockingbird",Author: "Harper Lee",Year: 1960})
```

### 4. Write a query to find all documents in the "books" collection.

```
db.Books.find()
```

### 5. Write a query to find documents in the "books" collection where the author is "F. Scott Fitzgerald".

```
db.Books.find({Author: "F. Scott Fitzgerald" })
```

### 6. Write a query to find documents in the "books" collection where the year is greater than 1950.

```
db.Books.find({ Year: { $gt: 1950 } })
```

### 7. Write an update query to change the author of the document with the title "To Kill a Mockingbird" to "Harper Lee (edited)".

```
db.Books.updateOne({ Title: "To Kill a Mockingbird" },{ $set: { Author: "Harper Lee (edited)" } })
```

### 8. Write an update query to add a new field "genre" with the value "Fiction" to all documents in the "books" collection.

```
db.Books.updateMany({},{ $set: { genre: "Fiction" } })
```

### 9. Write a query to find documents in the "books" collection where the genre is "Fiction".

```
db.Books.find({ genre: "Fiction" })
```

### 10. Write a query to find documents in the "books" collection where the title starts with the letter "T".

```
db.Books.find({ Title: /^T/ })
```

### 11. Write an update query to increment the year by 1 for all documents in the "books" collection.

```
db.Books.updateMany({},{ $inc: { Year: 1 } })
```

### 12. Write a query to find documents in the "books" collection where the year is between 1950 and 1970.

```
db.Books.find({ Year: { $gte: 1950, $lte: 1970 } })
```

### 13. Write a query to find documents in the "books" collection where the author's name contains the letter "a".

```
db.Books.find({Author: /a/ })
```

### 14. Write an update query to remove the "genre" field from all documents in the "books" collection.

```
db.Books.updateMany({},{ $unset: { genre: "" }})
```

### 15. Write a query to find documents in the "books" collection where the author's name ends with the letter "y".

```
db.Books.find({ Author: /y$/ })
```

### 16. Write an update query to change the title of the document with the author "Harper Lee" to "Go Set a Watchman".

```
db.Books.updateOne({ Author: "Harper Lee" },{ $set: { Title: "Go Set a Watchman" } })
```

### 17. Write a query to find documents in the "books" collection where the title contains the word "Great".

```
db.Books.find({ Title: /Great/ })
```

### 18. Write a query to find documents in the "books" collection where the title is an exact match for "The Great Gatsby".

```
db.Books.find({ Title: "The Great Gatsby" })
```

### 19. Write an update query to add an array field named "categories" with the values ["Classic", "Fiction"] to all documents in the "books" collection.

```
db.Books.updateMany({},{ $set: { categories: ["Classic", "Fiction"] } })
```

### 20. Write a query to find documents in the "books" collection where the "categories" field contains the value "Fiction".

```
db.Books.find({ categories: "Fiction" })
```

### 21. Write a query to find documents in the "books" collection where the title contains the word "The" in a case-insensitive manner.

```

```

### 22. Write a query to find documents in the "books" collection where the author's name starts with the letter "J".

```
db.books.find({ author: /^J/ })
```

### 23. Write an update query to increment the "year" field by 5 for all documents in the "books" collection.

```
db.Books.updateMany({},{ $inc: { Year: 5 } })
```

### 24. Write a query to find documents in the "books" collection where the title is not equal to "Moby Dick".

```
db.Books.find({ Title: { $ne: "Moby Dick" } })
```

### 25. Write a query to find documents in the "books" collection where the author's name is either "J.K. Rowling" or "George R.R. Martin".

```
db.Books.find({ Author: { $in: ["J.K. Rowling", "George R.R. Martin"] } })
```

### 26. Write a query to find documents in the "books" collection where the year is either 2000 or 2010.

```
db.Books.find({ Year: { $in: [2000, 2010] } })
```

### 27. Write an update query to multiply the "year" field by 2 for all documents in the "books" collection.

```
db.Books.updateMany({},{ $mul: { Year: 2 } })
```

### 28. Write a query to find documents in the "books" collection where the title ends with the letter "s".

```
db.Books.find({ Title: /s$/ })
```

### 29. Write a query to find documents in the "books" collection where the author's name is not in ["Stephen King", "Agatha Christie"].

```
db.Books.find({ Author: { $nin: ["Stephen King", "Agatha Christie"] } })
```

### 30. Write an update query to set the "year" field to 2022 for the document with the highest year in the "books" collection.

```

```

### 1. Create database wecodeacademy

```
use wecodeacademy;
```

### 2. create collection batches

```
db.createCollection("batches");
```

### 3. add 5 documents in this way

```
{"batchName": "Node.js","students": ["Khalil","SherMo","Aarif","Rafik","Mazzid"],"duration": 5,"fees": 5000,"marks": [30,40,50,60,70,80]};

{"batchName": "JavaScript","students": ["Irfan Khan","Khalil","SherMo.","Taiyab","Aadil"],duration": 10,fees": 10000,marks": [50,60,70,80,30,90,99,95,75,45,68,87,59]};


{"batchName": "Designing","students":["Sohil Khan","Sameer","Tahir Khan","Farman","Aadil"],"duration": 7,fees": 15000,"marks": [60,70,80,90,99,95,75,68,87,59]};

{"batchName": "Node.js","students": ["Afjal","VAkeel"],"duration": 15,"fees": 12000,"marks": [80,30,90,99,95]};

{"batchName": "Designing","students": ["Farman","Sohil"],"duration": 13,"fees": 18000,"marks": [60,70,80,90,99,95,75,68,87,59]};
```
