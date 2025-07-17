# Inserta data a una tabla con java

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;

public class Main {
  public static void main(String[] args) {
    try {
        Class.forName("com.mysql.jdbc.Driver");
        // Para mas nuevo: Class.forName("com.mysql.cj.jdbc.Driver");

        String url = "";
        String user = "";
        String pass = "";
        Connection con = DriverManager.getConnection(url, user, pass);

        String query = "INSERT INTO user (username, password, email) VALUES (?, ?, ?)";

        PreparedStatement pstmt = con.prepareStatement(query);
        pstmt.setString(1, "juan123");
        pstmt.setString(2, "claveSeguraHasheada");
        pstmt.setString(3, "juan@example.com");
        pstmt.executeUpdate();

        con.close();
    } catch(Exception e) {
      e.printStackTrace();
    }
  }
}
```

✅  1. Statement
Se usa para ejecutar SQL estático, sin parámetros o cuando construyes tú mismo el SQL concatenando valores.

✅ 2. PreparedStatement
Se usa para ejecutar SQL parametrizado. El SQL se precompila y luego se le pasan los valores.
