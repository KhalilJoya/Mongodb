# Mongodb

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
  admissionDate: 2023-02-01T00:00:00.000Z,
  dob: 2003-09-30T00:00:00.000Z
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
  admissionDate: 2023-02-01T00:00:00.000Z,
  dob: 2002-05-01T00:00:00.000Z
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
  admissionDate: 2023-02-15T00:00:00.000Z,
  dob: 2003-04-08T00:00:00.000Z
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
  admissionDate: 2023-03-01T00:00:00.000Z,
  dob: 2003-09-30T00:00:00.000Z
})
```

```sql
db.student.insertOne({
  name: 'Sohil',
  fatherName: 'Rahim Kha',
  mobileNo: 9079883575,
  email: 'sohil@gmail.com',
  address: 'Sikar',
  admissionDate: 2023-02-15T00:00:00.000Z,
  dob: 2001-05-01T00:00:00.000Z
})
```

```sql
db.student.insertOne({
   name: 'Sonu',
  fatherName: 'Khalil',
  mobileNo: 9079883575,
  email: 'rahim@gmail.com',
  address: 'Jaipur',
  admissionDate: 2023-02-01T00:00:00.000Z,
  dob: 2005-05-01T00:00:00.000Z
})
```

# Mongodb All Question

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

```sql
db.student.find({}).sort({name : 1})
```

### 5. vo sare students ki list return kro jinka admission last 3 months me hua hai

```sql

```

### 6. vo sare students ka only naam btao jinka admission current month me hua hai

```sql

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
