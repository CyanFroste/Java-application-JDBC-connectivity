## Connecting to mySQL server
### connect.java file to test the connection
```
import java.sql.*; 

public class connect 
{ 
	public static void main(String args[]) 
	{ 
		try
		{ 
			// Establishing Connection using parameters - Connection String, username, password

			Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/Database_name", "root", ""); 

			if (con != null)			 
				System.out.println("Connected");			 
			else			
				System.out.println("Not Connected"); 
			
			con.close(); 
		} 
		catch(Exception e) 
		{ 
			System.out.println(e); 
		} 
	} 
} 
```
local server usually runs on port 3306



### Running it on Command line and checking the connection

- Download the [connector](https://dev.mysql.com/downloads/connector/j/)
- place the connector.jar file in the same directory as your .java and its .class file
- Open the dir containing the connect.java file in command prompt

- To Compile
 ```
 javac -cp mysql-connector-java-8.x.x.jar;. connect.java
 ```
 - To Run
 ```
 java -cp mysql-connector-java-8.x.x.jar;. connect
 ```
 If it shows a time zone error like this :

![](https://github.com/CyanFroste/JAVA-DB/blob/master/Images/time-zone-error.png)

Then Embed this code in the connection string
```
jdbc:mysql://localhost:3306/Database_name?useLegacyDatetimeCode=false&serverTimezone=UTC
```

### When it's done
![](https://github.com/CyanFroste/JAVA-DB/blob/master/Images/connection-success.png)




