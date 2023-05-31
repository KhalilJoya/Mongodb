{
$jsonSchema: {
    bsonType: 'object',
    required: [
      'name',
      'fatherName',
      'email',
      'DOB',
      'mobile',
      'batchName'
    ],
    properties: {
      name: {
        bsonType: 'string',
        description: 'hello name'
      },
      fatherName: {
        bsonType: 'string',
        description: 'hello father'
      },
      email: {
        bsonType: 'string',
        pattern: '^[a-zA-Z0-9._]+@+[a-zA-Z]+.+[a-zA-Z]{2,}$',
description: 'hello email'
},
DOB: {
bsonType: 'date',
description: 'hello dob'
},
mobile: {
bsonType: 'string',
pattern: '^(\\+?91|0)?[6789]\\d{9}$',
description: 'hello mobile'
},
batchName: {
bsonType: 'string',
'enum': [
'Node.js',
'Designing',
'JavaScript',
'ComputerBasic'
],
description: 'hello batch'
},
motherName: {
bsonType: 'string',
description: 'hello mother'
},
address: {
bsonType: 'string',
description: 'hello address'
},
fees: {
bsonType: 'number',
minimum: 2000,
maximum: 50000,
description: 'hello fees'
},
marks: {
bsonType: 'array',
description: 'hello marks'
}
}
}
}

db.Student.insertOne({name : "Khalil Joya",fatherName : "Murad Kha", motherName : "Jebun Bano",email :"khalil786@gamil.com",DOB : ISODate("2003-09-30T00:00:00.000Z"),mobile : "+919079883575" ,batchName :"Node.js",address :"Jaipur",fees :20000,marks : [70,80,90]})
