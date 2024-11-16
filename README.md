# **Snake Game in C with SQL Integration**

## **Overview**
This project is a beginner-friendly implementation of the classic **Snake Game** using **C** for the game logic and **Character User Interface (CUI)** for rendering. It integrates **SQL** to save high scores, allowing players to compete for the best performances.

### **Why This Project?**
- Learn basic **game logic** with C.
- Gain hands-on experience in **database integration** using SQL.
- Understand how to create interactive console applications.

---

## **Features**
### 🎮 **Game Features**:
- Classic Snake Game in the console.
- **Snake Movement**: Use `W`, `A`, `S`, `D` or arrow keys.
- Randomly generated food and real-time score tracking.
- Game ends on collision with walls or the snake itself.

### 🏆 **SQL Integration**:
- Save player scores in a MySQL database.
- Display the **Top 10 High Scores** at the start of the game.

---

## **Getting Started**

### **1. Prerequisites**
To run the project, you need the following installed on your system:
- **C Compiler**: GCC (MinGW or TDM-GCC for Windows).
- **MySQL Server**: To store and manage high scores.
- **MySQL Connector for C**: To enable communication between your C program and MySQL.

---

## **Installation Guide**

### **Step 1: Clone the Repository**
```bash
git clone https://github.com/<your-username>/snake-game-c-sql.git
cd snake-game-c-sql
```

### **Step 2: Install MySQL Connector**
1. Download the **MySQL Connector for C** from [MySQL Connector/C Downloads](https://dev.mysql.com/downloads/connector/c/).
2. Extract the files to a directory, e.g., `C:\mysql-connector-c`.
3. Add the `lib` and `include` folders to your system's **Environment Variables** (`PATH`).

### **Step 3: Set Up the Database**
1. Open your MySQL Command Line Client or Workbench.
2. Create a database and table:
   ```sql
   CREATE DATABASE snake_game;
   USE snake_game;

   CREATE TABLE high_scores (
       id INT AUTO_INCREMENT PRIMARY KEY,
       player_name VARCHAR(50),
       score INT,
       timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
   );
   ```

### **Step 4: Update Database Credentials**
Edit the database connection details in `main.c`:
```c
mysql_real_connect(conn, "localhost", "your-username", "your-password", "snake_game", 3306, NULL, 0);
```
Replace:
- `your-username` with your MySQL username.
- `your-password` with your MySQL password.

### **Step 5: Compile the Code**
Use GCC to compile the program:
```bash
gcc -o snake_game main.c -IC:\mysql-connector-c\include -LC:\mysql-connector-c\lib -lmysql
```

### **Step 6: Run the Game**
Run the executable:
```bash
./snake_game
```

---

## **Gameplay Instructions**
1. **Start the Game**:
   - Run the program, and the Top 10 high scores will be displayed.
2. **Control the Snake**:
   - Use the keyboard:
     - `W`: Up
     - `A`: Left
     - `S`: Down
     - `D`: Right
   - Alternatively, use arrow keys.
3. **Goal**:
   - Eat food (`X`) to grow and increase your score.
   - Avoid colliding with walls (`#`) or the snake itself.
4. **Game Over**:
   - When the game ends, your score is saved in the database.
   - Restart to play again.

---

## **File Structure**
```
snake-game-c-sql/
├── main.c           # Main game logic and database integration
├── README.md        # Project documentation
```

---

<!--## **Screenshots**
Add some screenshots or ASCII art representing the gameplay, such as:  

```
####################
#                  #
#     OOOO         #
#                  #
#         X        #
####################
Score: 10
```
!-->
---

## **Troubleshooting**

### **Common Errors**
1. **`libmysql.dll not found`**:
   - Ensure the `libmysql.dll` file is in the same directory as your executable or in a directory listed in your `PATH`.
2. **Database Connection Issues**:
   - Verify that the MySQL server is running and the credentials in `main.c` are correct.
3. **Compilation Errors**:
   - Ensure the paths to `include` and `lib` folders are correct in your `gcc` command.

### **Test Database Connection**
Run this simple query in `main.c` to test the connection:
```c
if (conn) {
    printf("Connected to MySQL successfully!\n");
} else {
    printf("MySQL connection failed: %s\n", mysql_error(conn));
}
```

---

## **Future Enhancements**
- Add difficulty levels (increase speed as the score increases).
- Introduce obstacles for added challenge.
- Use advanced libraries like **ncurses** to improve graphics.
- Allow players to resume saved games.

---

## **Contributors**
 - [Richa Kumari Jaishwal] (https://github.com/richajaishwal0/)
 - [Shudarsan Regmi](https://github.com/ShudarsanRegmi) 
 - [Swetha Sivakumar]()
 - [Sima Pandit]()
