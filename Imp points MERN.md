- use morgan for logger middleware 
- mongodb powerful query opeartors

| **Operator**           | **Meaning**                   | **Example**                                              |
| ---------------------- | ----------------------------- | -------------------------------------------------------- |
| **`$gt`** / **`$gte`** | Greater than / or equal       | `{ price: { $gt: 100 } }`                                |
| **`$lt`** / **`$lte`** | Less than / or equal          | `{ age: { $lt: 18 } }`                                   |
| **`$in`**              | Matches any value in an array | `{ name: { $in: ['Soham', 'Aarav'] } }`                  |
| **`$or`**              | Matches any of the conditions | `{ $or: [{ name: 'Soham' }, { email: 'test@me.com' }] }` |
| **`$regex`**           | Pattern matching (Search)     | `{ email: { $regex: /gmail/i } }`                        |
https://github.com/kashish281/Real-Time-Collaborative-Whiteboard-
