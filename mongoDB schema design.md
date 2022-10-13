#mongoDb 

[中文參考文章](https://blog.toright.com/posts/4483/mongodb-schema-%E8%A8%AD%E8%A8%88%E6%8C%87%E5%8D%97.html)
[英文參考文章](https://www.digitalocean.com/community/tutorials/how-to-design-a-document-schema-in-mongodb)


# introduction
> mongoDB 是 NoSQL，但不代表是 No Schema，為了讓資料更好維護，是需要設計好的 schema 的。
- 把會一起 query 的整合到同一個document，加以利用 document-oriented 的優勢
	- 稱作 denormalize，相對於關聯資料庫的 normalize(不重複資料)
	- 減少不同資料間的溝通
## one to one
> 直接在document 下新增一個欄位，放大 NoSQL 的優點

EX:
```json
{
    "_id": ObjectId("612d1e835ebee16872a109a4"),
    "first_name": "Sammy",
    "last_name": "Shark",
    "id_card": {
        "number": "123-1234-123",
        "issued_on": ISODate("2020-01-23"),
        "expires_on": ISODate("2020-01-23")
    }
}
```
## one to many
遇到 one to many 時，會有許多不同情境。child 的部分需要考慮以下原則，去思考如何 model：
- cardinality(基數) 
- independent access → 是否會需要獨立被檢索到
- 確認 one to many 或是 many to many → 如果是 many to many 較不適合使用 Embedded document
### one to few with Embedded Document
> 如果是一對多，但基數不高時、且不太有機會被獨立檢索時，可考慮直接寫在 document 底下 (documents embedded)。 

EX:
```json
{
    "_id": ObjectId("612d1e835ebee16872a109a4"),
    "first_name": "Sammy",
    "last_name": "Shark",
    "emails": [
        {
            "email": "sammy@digitalocean.com",
            "type": "work"
        },
        {
            "email": "sammy@example.com",
            "type": "home"
        }
    ]
}
```
### one to many, many to many with Child Reference。
> 如果是一對多，考慮基數較高、或可能 child 會需要獨立被檢索時，考慮使用Child References。

EX:
```json
// courses
{
    "_id": ObjectId("61741c9cbc9ec583c836170a"),
    "name": "Physics 101",
    "department": "Department of Physics",
    "points": 7
},
{
    "_id": ObjectId("61741c9cbc9ec583c836170b"),
    "name": "Introduction to Cloud Computing",
    "department": "Department of Computer Science",
    "points": 4
}
// students
{
    "_id": ObjectId("612d1e835ebee16872a109a4"),
    "first_name": "Sammy",
    "last_name": "Shark",
    "emails": [
        {
            "email": "sammy@digitalocean.com",
            "type": "work"
        },
        {
            "email": "sammy@example.com",
            "type": "home"
        }
    ],
    "courses": [
        ObjectId("61741c9cbc9ec583c836170a"),
        ObjectId("61741c9cbc9ec583c836170b")
    ]
}
```

### one to squillions with Parent Reference
> 如果可能成長到不可估量的 child，一個 document 很可能超過限制(16 mb)。

EX:
```json
// messages
{
    "_id": ObjectId("61741c9cbc9ec583c836174c"),
    "subject": "Books on kinematics and dynamics",
    "message": "Hello! Could you recommend a good introductory books covering the topics of kinematics and dynamics? Thanks!",
    "posted_on": ISODate("2021-07-23T16:03:21Z"),
    "posted_by": ObjectId("612d1e835ebee16872a109a4")
}
// students
{
    "_id": ObjectId("612d1e835ebee16872a109a4"),
    "first_name": "Sammy",
    "last_name": "Shark",
    "emails": [
        {
            "email": "sammy@digitalocean.com",
            "type": "work"
        },
        {
            "email": "sammy@example.com",
            "type": "home"
        }
    ],
    "courses": [
        ObjectId("61741c9cbc9ec583c836170a"),
        ObjectId("61741c9cbc9ec583c836170b")
    ]
}
```
→ 不管 messages 有無可能被獨立檢索， embedding 都不是一個好的選擇。
### one to many with Two-Way Reference
> parent 與 child 都有對方的 object id
```json
// owner
{
    _id: ObjectID("AAF1"),
    name: "Kate Monster",
    tasks [
        ObjectID("ADF9"),
        ObjectID("AE02"),
        ObjectID("AE73")
    ]
}

// task
{
    _id: ObjectID("ADF9"),
    description: "Write lesson plan",
    due_date:  ISODate("2014-04-01"),
    owner: ObjectID("AAF1")   
}
```
- props
	- 兩邊都可以參照
- cons
	- 要管理兩邊

### one to many denormalizing 
> 如果利用 one to many 的方式，將 child 的 object id 存在 parent 當中，如果想要一些重要資訊，就必須再 query 一次。所以有了以下方法：
```json
{
   name : 'left-handed smoke shifter',
   manufacturer : 'Acme Corp',
   catalog_number: 1234,
   parts : [
       { id : ObjectID('AAAA'), name : '#4 grommet' },
       { id: ObjectID('F17C'), name : 'fan blade assembly' },
       { id: ObjectID('D2AA'), name : 'power switch' },
   ]
}
```
- props 
	- query 更方便
- cons
	- 維護成本提高
→ 讀取頻率高，更改頻率低，該方法才有意義。
→ 如果是 many to many 一次要改的地方會太多，不建議使用。