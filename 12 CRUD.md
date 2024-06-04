# Assignment No 12

### **Aim :** Design and Develop MongoDB Queries using CRUD operations. (Use CRUD operations, SAVE method, logical operators)

## 1. create

1. insertOne()
```
db.student.insertOne({
    student_id: "S001",
    name: "Dipak",
    age: 21,
    major: "Computer Science"
})

```

2. insertMany()
```
db.student.insertMany([
    {
        student_id: "S002",
        name: "Akash",
        age: 22,
        major: "Mathematics"
    },
    {
        student_id: "S003",
        name: "Krushana",
        age: 20,
        major: "Physics"
    }
])

```

## 2. Read

1. find()
```
  db.student.find().pretty()
```

2. findOne()
```
  db.student.findOne({ student_id: "S001" })
```
## 3. Update
1. UpdateOne()
```
  db.student.updateOne(
    { student_id: "S001" }, 
    { $set: { age: 22 } }
)

```
2. UpdateMany()
```
  db.student.updateMany(
    { major: "Mathematics" }, 
    { $set: { major: "Applied Mathematics" } }
)
```
3. ReplaceOe()
```
db.student.replaceOne(
    { student_id: "S003" },
    {
        student_id: "S003",
        name: "Rohan",
        age: 21,
        major: "Astrophysics"
    }
)
```
## 4. Delete
1. deleteOne()
```
db.student.deleteOne({ student_id: "S002" })
```

2. deleteMany()
```
db.student.deleteMany({ age: { $gt: 21 } })
```

```
db.student.find({
    age: { $gt: 20 },
    $or: [
        { name: "John" },
        { name: "Alice" }
    ]
})

```
```
// Save a new student document
db.students.save({
    "_id": ObjectId("609eb6b246de2f102314d21f"),
    "name": "David",
    "age": 23,
    "major": "Physics",
    "GPA": 3.8
})

// Update the existing student document with the same _id
db.students.save({
    "_id": ObjectId("609eb6b246de2f102314d21f"),
    "name": "David",
    "age": 24,
    "major": "Physics",
    "GPA": 3.9
})

```
