<img width="1815" height="1029" alt="Screenshot 2025-09-17 033554" src="https://github.com/user-attachments/assets/a5728791-4ad9-47b5-bad3-678b4d38cb02" />


<img width="1898" height="1016" alt="Screenshot 2025-09-17 033747" src="https://github.com/user-attachments/assets/a481c80c-dec2-4230-bf1c-4e911a9b69f5" />




# MKDB
**MKDB** is a lightweight, relational database management system (DBMS) built from scratch in **Rust**. It implements a custom SQL engine, a TCP-based server-client architecture, and persistent on-disk storage.
## Features
- **Custom SQL Engine**: Implements a lexer, parser, analyzer, optimizer, and executor.
- **Client-Server Architecture**: 
  - **Server**: Handles database connections, query processing, and storage management.
  - **Client**: A CLI-based shell with command history and auto-formatting.
- **Supported SQL Statements**:
  - `CREATE DATABASE`, `CREATE TABLE`, `CREATE INDEX`
  - `DROP DATABASE`, `DROP TABLE`
  - `INSERT INTO`
  - `SELECT ... FROM ... WHERE ...`
  - `UPDATE ... SET ... WHERE ...`
- **Data Types**: Supports Integers (i128), Strings, and more.
- **Constraints**: Primary Key, Unique.
## Project Structure
The repository is organized as follows:
- **`src/`**: The core database server implementation.
  - `sql/`: SQL parser and query logic.
  - `storage/`: B-Tree based storage engine and paging.
  - `tcp/`: Networking and protocol handling.
  - `vm/`: Virtual machine / execution engine.
- **`client/`**: The CLI client implementation using `rustyline`.
## Getting Started
### Prerequisites
Ensure you have **Rust** and **Cargo** installed on your machine. You can install them via [rustup.rs](https://rustup.rs/).
### Installation
Clone the repository:
```bash
git clone https://github.com/ningaraddi-raddi/DBMS.git
cd DBMS
```
### Usage
#### 1. Start the Server
Run the server by providing a path for the database file. You can optionally specify a port (default: 8000).
```bash
# Syntax: cargo run <database_file> [port]
cargo run my_database.db
```
*Note: The first time you run this, it will compile the project which may take a few moments.*
#### 2. Start the Client
In a separate terminal window, run the client to connect to the server.
```bash
# Syntax: cargo run -p client <port>
cargo run -p client 8000
```
### Example Session
Once connected via the client, you can execute SQL queries:
```sql
mkdb> CREATE TABLE users (id INT, name STRING);
Query OK, 0 rows affected
mkdb> INSERT INTO users VALUES (1, 'Alice');
Query OK, 1 row affected
mkdb> SELECT * FROM users;
+----+-------+
| id | name  |
+----+-------+
| 1  | Alice |
+----+-------+
1 row
mkdb> UPDATE users SET name = 'Bob' WHERE id = 1;
Query OK, 1 row affected
```
## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
