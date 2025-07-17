# Conexion JDBC

1. Cargar driver
   
```java
Class.forName("com.mysql.jdbc.Driver");
```

2. Crear una conexion
   
```java
Connection con = DriverManager.getConnection(
    "jdbc:mysql://127.0.0.1:3306/dbname?serverTimezone=UTC", 
    "root", 
    "pass"
);
```

3. Crear query

```java
String q = "select * from students";

Statement stmt = con.createStatement();

ResultSet result = stmt.executeQuery(q);
```

# Procesar data

```java
while (result.next()) {
  int id = result.getInt("studentId");
  String name = result.getString("studentName");
}
```

# Cerrar conexion
```java
con.close();
```
