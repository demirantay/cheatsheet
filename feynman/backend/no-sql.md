# NoSQL

### What

- So NoSQL is an umbrella term for every other database management system designed other than the traditional (relational) database management systems such as (table, row, colum, ... etc.) 

- Main types of NoSQL databases:
  - Document databases (stores data in documents .ex. json)
  - Key-Value stores (like a dictioanry)
  - Column-oriented databases (stores data in table, row but dynamic columns)
  - Graph Databases (stores data in nodes and edges)

- NoSQL features:
  - Felixable schemes
  - Horizontal scaling
  - Fast queries due to the data model
  - Ease of use for developers

- Document databases are for general purposes

- Key- value based ones are ideal for large volumes of data with simple lookup queries

- Wide-column work well with large amounts of data with predictable query patterns

- Graph databases work well with analyzing and traversing relationships

### Why

- NoSQL databases are used for: cheapness, developent fastness and scaling.

- SQL databases are like automatic transmission and NoSQL databases are like manual transmission. Once you switch to NoSQL, you become responsible for a lot of work that the system takes care of automatically in a relational database system. Similar to what happens when you pick manual over automatic transmission. Secondly, NoSQL allows you to eke more performance out of the system by eliminating a lot of integrity checks done by relational databases from the database tier. Again, this is similar to how you can get more performance out of your car by driving a manual transmission versus an automatic transmission vehicle.

  However the most notable similarity is that just like most of us can’t really take advantage of the benefits of a manual transmission vehicle because the majority of our driving is sitting in traffic on the way to and from work, there is a similar harsh reality in that most sites aren’t at Google or Facebook’s scale and thus have no need for a Bigtable or Cassandra.

### Where

- NoSQL is used for Big data and real-time web apps. For example, companies like Twitter, Facebook and Google collect terabytes of user data every single day.

### When

- The use cases for a graph database and a key-value database are quite different. Using a dynamo-style DB (e.g. Casandra) is different than using a document-db. Like any technology choice, each type of database has it's own advantages and disadvantages. In this case these differences are especially important because 'NoSQL' databases are highly optimized to do one-to-a-few specific things really well at the cost of doing other things poorly. A RDMBS is sort of a jack-of-all-trades and a NoSQL database is a one-trick-pony (by design.) It can make sense to use a NoSQL DB if you are playing to its strengths and its weaknesses are not relevant.
