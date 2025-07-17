# Crear tabla con java (Statement)

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class Main {
  public static void main(String[] args) {
    try {
        Class.forName("com.mysql.jdbc.Driver");

        String url = "";
        String user = "";
        String pass = "";
        Connection con = DriverManager.getConnection(url, user, pass);

        String query = "CREATE TABLE user ("
            + "id INT PRIMARY KEY AUTO_INCREMENT, "
            + "username VARCHAR(50) NOT NULL UNIQUE, "
            + "password VARCHAR(255) NOT NULL, "
            + "email VARCHAR(100) UNIQUE, "
            + "created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, "
            + "updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP"
            + ");";

        Statement stmt = con.createStatement();
        stmt.executeUpdate(query);

        con.close();
    } catch(Exception e) {
      e.printStackTrace();
    }
  }
}
```
