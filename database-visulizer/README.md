# Assignment Specification: Database Visualizer

## General Requirements:
1. **Technology Stack**:
   - **ORM:** Prisma
   - **Backend Languages:** Python or Node.js
   - **Database:** PostgreSQL

## API Endpoints:

### SQL Query Endpoints:
Here's a more detailed list of SQL operations with corresponding endpoints:

#### 1. Basic CRUD Operations
- **Create (Insert)**: `/api/query/insert` - Insert new records into a specified table.
- **Read (Select)**: `/api/query/select` - Retrieve records from a table based on specified conditions.
- **Update**: `/api/query/update` - Update existing records in a table based on conditions.
- **Delete**: `/api/query/delete` - Delete records from a table based on conditions.

#### 2. Advanced Querying
- **Aggregate Functions**: `/api/query/aggregate` - Execute queries involving aggregate functions like COUNT, AVG, MIN, MAX, SUM.
- **Group By**: `/api/query/groupby` - Group records based on specified fields and perform aggregate calculations.
- **Order By**: `/api/query/orderby` - Retrieve records sorted by one or more columns.
- **Join Operations**: `/api/query/join` - Perform JOIN operations between tables based on specified conditions.
- **Subqueries**: `/api/query/subquery` - Execute subqueries within another SQL query.

#### 3. Transaction Management
- **Begin Transaction**: `/api/transaction/begin` - Start a new database transaction.
- **Commit Transaction**: `/api/transaction/commit` - Commit the current transaction.
- **Rollback Transaction**: `/api/transaction/rollback` - Rollback the current transaction in case of an error.

#### 4. Database Schema Manipulation
- **Create Index**: `/api/schema/create-index` - Create an index on a table to improve the performance of queries.
- **Add Column**: `/api/schema/add-column` - Add a new column to an existing table.
- **Modify Column**: `/api/schema/modify-column` - Modify the data type or characteristics of an existing column.
- **Drop Column**: `/api/schema/drop-column` - Remove a column from a table.

### Table Creation and Relationship Management Endpoints
#### 1. Table Creation
- `/api/tables/create`: Endpoint to create new tables with specifications including primary keys, foreign keys, and indexes.

#### 2. Table Relationship Management
- **Create Relationship**: `/api/relationships/create` - Define new foreign key relationships between tables.
- **Modify Relationship**: `/api/relationships/modify` - Modify existing relationship constraints.
- **Remove Relationship**: `/api/relationships/remove` - Remove an existing relationship between tables.

### Sample API Endpoint for Advanced Query (Join)
```json
{
  "endpoint": "/api/query/join",
  "method": "POST",
  "description": "Performs a JOIN operation between two tables.",
  "payload": {
    "mainTable": "Orders",
    "joinTable": "Customers",
    "joinCondition": "Orders.customerId = Customers.id",
    "selectFields": ["Orders.id", "Customers.name"],
    "whereCondition": "Customers.region = 'North America'"
  }
}
```

### Table Creation Endpoints
- Endpoints to create tables with specifications for primary keys, foreign keys, and other constraints:

| Endpoint                 | Method | Description                                      |
|--------------------------|--------|--------------------------------------------------|
| `/api/tables/create`     | POST   | Create a new table. Payload should include table schema details such as column names, types, primary key, and foreign keys. |

#### Sample Payload for Table Creation
```json
{
  "tableName": "Users",
  "fields": {
    "id": "int",
    "username": "string",
    "email": "string"
  },
  "primaryKey": "id",
  "foreignKeys": [
    {
      "field": "companyId",
      "referenceTable": "Companies",
      "referenceField": "id"
    }
  ]
}
```

### Table Relationship Endpoints
- Endpoints to explicitly create relationships between existing tables.

| Endpoint                       | Method | Description                                                  |
|--------------------------------|--------|--------------------------------------------------------------|
| `/api/relationships/create`    | POST   | Create a relationship between tables. Payload includes details of the foreign key and reference constraints. |

#### Sample Payload for Creating Relationships
```json
{
  "tableName": "Employees",
  "foreignKey": {
      "field": "departmentId",
      "referenceTable": "Departments",
      "referenceField": "id"
  }
}
```

## Additional Specifications:
5. **Use Prisma Schema**: Define the schema using Prisma's schema language, which will then be used to generate migrations and manage the database schema efficiently.
6. **Prisma Client**: Use Prisma

 Client to interact with the PostgreSQL database, ensuring all queries, inserts, updates, and deletes are handled through Prisma, leveraging its powerful features for database manipulation and query performance.


