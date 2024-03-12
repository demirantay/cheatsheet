# MongoDB

MongoDB is an open-source document database and leading NoSQL database. MongoDB is written in C++

Terminology:
|RDBMS|Mongo|
|--|--|
|Database|Database|
|Table|Collection|
|Tuple/Row|Document|
|Column|Field|
|Table Join|Embedded Documents|
|Primary Key|Primary Key (Default key _id provided by MongoDB itself)|

Logic:
```sql
-- server operations
sudo service mongodb start
sudo service mongodb stop
sudo service mongodb restart

-- to get into the client server
mongo
```

### Basics

```python

# Normal Data Model
{
	_id: <ObjectId101>,
	Emp_ID: "10025AE336"
}

{
	_id: <ObjectId102>,
	empDocID: " ObjectId101",
	First_Name: "Radhika",
	Last_Name: "Sharma",
	Date_Of_Birth: "1995-09-26"
}

# Embedded Data Model
{
	_id: ,
	Emp_ID: "10025AE336"
	Personal_details:{
		First_Name: "Radhika",
		Last_Name: "Sharma",
		Date_Of_Birth: "1995-09-26"
	},
	Contact: {
		e-mail: "radhika_sharma.123@gmail.com",
		phone: "9848022338"
	},
}
```

Commands:
```sql
-- showing all of the databases
show dbs

-- show current database
db

-- create or switch database
use dbname

-- drop database
db.dropDatabase()

-- create collection
db.createCollection('posts')

-- show collections
show collections

-- insert row
db.posts.insert({
  title: 'Post One',
  body: 'Body of post one',
  category: 'News',
  tags: ['news', 'events'],
  user: {
    name: 'John Doe',
    status: 'author'
  },
  date: Date()
})

-- Insert multiple rows
db.posts.insertMany([
  {
    title: 'Post Two',
    body: 'Body of post two',
    category: 'Technology',
    date: Date()
  },
  {
    title: 'Post Three',
    body: 'Body of post three',
    category: 'News',
    date: Date()
  },
  {
    title: 'Post Four',
    body: 'Body of post three',
    category: 'Entertainment',
    date: Date()
  }
])

--- Get all rows
db.posts.find()

-- Get all rows formatted
db.posts.find().pretty()

-- Find rows
db.posts.find({ category: 'News' })

-- Sort Rows
# asc
db.posts.find().sort({ title: 1 }).pretty()
# desc 
db.posts.find().sort({ title: -1 }).pretty()

-- Count rows
db.posts.find().count()
db.posts.find({ category: 'news' }).count()

-- Limit rows
db.posts.find().limit(2).pretty()

-- Chaining
db.posts.find().limit(2).sort({ title: 1 }).pretty()

-- For Each
db.posts.find().forEach(function(doc) {
  print("Blog Post: " + doc.title)
})

-- find one row
db.posts.findOne({ category: 'News' })

-- find specific fields
db.posts.find({ title: 'Post One' }, {
  title: 1,
  author: 1
})

-- update row
db.posts.update({ title: 'Post Two' },
{
  title: 'Post Two',
  body: 'New body for post 2',
  date: Date()
},
{
  upsert: true
})

-- update specific field
db.posts.update({ title: 'Post Two' },
{
  $set: {
    body: 'Body for post 2',
    category: 'Technology'
  }
})

-- Increment Field ($inc)
db.posts.update({ title: 'Post Two' },
{
  $inc: {
    likes: 5
  }
})

-- Rename field
db.posts.update({ title: 'Post Two' },
{
  $rename: {
    likes: 'views'
  }
})

-- Delete Row
db.posts.remove({ title: 'Post Four' })

-- Subdocuments
db.posts.update({ title: 'Post One' },
{
  $set: {
    comments: [
      {
        body: 'Comment One',
        user: 'Mary Williams',
        date: Date()
      },
      {
        body: 'Comment Two',
        user: 'Harry White',
        date: Date()
      }
    ]
  }
})

-- Find element in an array
db.posts.find({
  comments: {
     $elemMatch: {
       user: 'Mary Williams'
       }
    }
  }
)

-- Add Index
db.posts.createIndex({ title: 'text' })

-- Text Search
db.posts.find({
  $text: {
    $search: "\"Post O\""
    }
})

-- Greater and Less than
db.posts.find({ views: { $gt: 2 } })
db.posts.find({ views: { $gte: 7 } })
db.posts.find({ views: { $lt: 7 } })
db.posts.find({ views: { $lte: 7 } })

```

## Python with MongoDB

```
pip install PyMongo
```
