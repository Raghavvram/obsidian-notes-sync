#### 1. **NOT NULL Constraint**

- **Purpose**: Ensures a column cannot have a `NULL` value.
- **Example**: In a `students` table, the `roll_number` field should never be null.

#### 2. **UNIQUE Constraint**

- **Purpose**: Ensures all values in a column are distinct.
- **Note**: Unlike PRIMARY KEY, you can have multiple UNIQUE constraints in a table.
- **Example**: Email addresses in a user table should be unique.

#### 3. **PRIMARY KEY Constraint**

- **Purpose**: Uniquely identifies each record in a table.
- **Rules**: Combines NOT NULL and UNIQUE constraints.
- **Example**: `user_id` in the `users` table as a primary key.

#### 4. **FOREIGN KEY Constraint**

- **Purpose**: Maintains referential integrity by linking one table to another.
- **Behavior**: Ensures that a value in the foreign key column matches a value in the referenced primary key column.
- **Example**: `department_id` in `employees` references `id` in `departments`.

#### 5. **CHECK Constraint**

- **Purpose**: Validates that a value in a column meets a specific condition.
- **Example**: Age must be greater than or equal to 18.

#### 6. **DEFAULT Constraint**

- **Purpose**: Sets a default value for a column when no value is provided.
- **Example**: Set `status = 'active'` if none is provided during insert.

#### 7. **INDEX Constraint** _(not strictly a constraint, but often listed alongside)_

- **Purpose**: Speeds up query performance by indexing key columns.
- **Note**: Doesn’t enforce data rules, just improves efficiency.

---

### 🔗 Summary Table

|Constraint|Enforces|Allows NULL|Uniqueness|Example Use Case|
|---|---|---|---|---|
|NOT NULL|Mandatory field|❌|❌|Name or ID fields|
|UNIQUE|No duplicates|✅|✅|Email addresses|
|PRIMARY KEY|Unique + mandatory|❌|✅|Record identifier|
|FOREIGN KEY|Relationship link|✅|✅|Joining tables|
|CHECK|Custom condition|✅|✅|Age > 18|
|DEFAULT|Default value|✅|✅|Set default status|
|INDEX|Query optimization|✅|✅|Search performance|
