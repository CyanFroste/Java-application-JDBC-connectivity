## USES
- Get DB Product nam
- Get DB Product Version
- Get JDBC Driver name and version
- Get DB schema
- Get list of Tables and Columns

### Getting Basic Info
```
package jdbctest;
import java.sql.*;

public class Jdbctest {
    private static final String URL = "jdbc:mysql://localhost:3306/test?useLegacyDatetimeCode=false&serverTimezone=UTC"; 
    private static final String USER = "root";
    private static final String PASS = "";
    
    public static void main(String[] args) throws SQLException {
        
        Connection con = null;
	Statement stmt = null;
	ResultSet res = null;
        
        try{
            con = DriverManager.getConnection(URL, USER, PASS);
            
                // Get metadata
		DatabaseMetaData metaData = con.getMetaData();
			
		// Display info about database
		System.out.println("Product name: " + metaData.getDatabaseProductName());
		System.out.println("Product version: " + metaData.getDatabaseProductVersion());
		System.out.println();
			
		// Display info about JDBC Driver
		System.out.println("JDBC Driver name: " + metaData.getDriverName());
		System.out.println("JDBC Driver version: " + metaData.getDriverVersion());
			
	} catch (SQLException e) {
		System.err.println(e);
	} finally {
		close(con);
	}
}

    private static void close(Connection con) throws SQLException {
        if (con != null) {
		con.close();
	}
    }
}
```

### Getting info about Tables and Columns
```
package jdbctest;
import java.sql.*;

public class Jdbctest {
    private static final String URL = "jdbc:mysql://localhost:3306/test?useLegacyDatetimeCode=false&serverTimezone=UTC"; 
    private static final String USER = "root";
    private static final String PASS = "";
    
    public static void main(String[] args) throws SQLException {
        
        Connection con = null;
	Statement stmt = null;
	ResultSet res = null;
        
        String catalog = null;
	String schemaPattern = null;
	String tableNamePattern = null;
	String columnNamePattern = null;
	String[] types = null;
        
        try{
            con = DriverManager.getConnection(URL, USER, PASS);
                
                // Get metadata
		DatabaseMetaData metaData = con.getMetaData();

		// Get list of tables
		System.out.println("List of Tables");
		System.out.println("--------------");

		res = metaData.getTables(catalog, schemaPattern ,tableNamePattern, types);

		while (res.next()) {
			System.out.println(res.getString("TABLE_NAME"));
		}

		// Get list of columns
		System.out.println("\n\nList of Columns");
		System.out.println("--------------");

		res = metaData.getColumns(catalog, schemaPattern, "employees", columnNamePattern);

		while (res.next()) {
			System.out.println(res.getString("COLUMN_NAME"));
		}

        } catch (SQLException e) {
		System.err.println(e);
	} finally {
		close(con, res);
	}
}

    private static void close(Connection con, ResultSet res) throws SQLException {

	if (res != null) {
		res.close();
	}

	if (con != null) {
		con.close();
	}
    }
}
```