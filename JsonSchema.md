### JsonSchema

### create Collection Students

```
db.createCollection("Student");
```

### Name (string) , FatherName (string) , MotherName (string) , DOB (date) , Email (string) (emailid validation) , Mobile (string) (indian mobile number regex) , Address (string) , BatchName (enum [Node.js, Designing, JavaScript,Computerbasic]) , Fees (number) (minmum 2000 maximum 50000) , Marks (array) , [emaild, dob, mobile, name, fathername, batchname] mandatory he.

```
{
  $jsonSchema: {
    bsonType: 'object',
    required: ['name','fatherName','email','DOB','mobile','batchName'],
    properties: {
      name: {
        bsonType: 'string',
        description: 'name'
      },
      fatherName: {
        bsonType: 'string',
        description: 'fatherName'
      },
      email: {
        bsonType: 'string',
        pattern: '^[a-zA-Z0-9._]+@+[a-zA-Z]+.+[a-zA-Z]{2,}$',
        description: 'email Address'
      },
      DOB: {
        bsonType: 'date',
        description: 'DOB'
      },
      mobile: {
        bsonType: 'string',
        pattern: '^(\\+?91|0)?[6789]\\d{9}$',
        description: 'mobileNumber'
      },
      batchName: {
        bsonType: 'string',
        'enum': ['Node.js','Designing','JavaScript','ComputerBasic'],
        description: 'batchName'
      },
      motherName: {
        bsonType: 'string',
        description: 'motherName'
      },
      address: {
        bsonType: 'string',
        description: 'address'
      },
      fees: {
        bsonType: 'number',
        minimum: 2000,
        maximum: 50000,
        description: 'fees'
      },
      marks: {
        bsonType: 'array',
        description: 'marks'
      }
    }
  }
}
```

### Insert Data

```
db.Student.insertOne({name : "Khalil Joya",fatherName : "Murad Kha", motherName : "Jebun Bano",email :"khalil786@gamil.com",DOB : ISODate("2003-09-30T00:00:00.000Z"),mobile : "+919079883575" ,batchName :"Node.js",address :"Jaipur",fees :20000,marks : [70,80,90]})
```
