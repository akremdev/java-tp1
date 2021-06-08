# java-tp1


```java
package jdbcdema;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import javax.sql.rowset.JdbcRowSet;
import com.mysql.cj.jdbc.result.ResultSetMetaData; import
com.sun.rowset.JdbcRowSetImpl;
public class test {
private static Connection myconn=null;
private static Statement st = null;
private static ResultSet rs = null;
static {
try {
Class.forName("com.mysql.jdbc.Driver”);
System.out.println("DRIVER CHARGER OK !");
myconn =DriverManager.getConnection
("jdbc:mysql://localhost/demo", "root" , "");
System.out.println("connection effectuée avec succée !");
}catch (SQLException ex)
{ System.out.println("Erreur connexion \n " +ex.getMessage());
}catch(ClassNotFoundException ex){
System.out.println("Impossible de charger le driver"
+ex.getMessage());
}
}
public static void main(String[] args) throws Exception
{
st= myconn.createStatement();
String req ="select * from employees where numero=1";
rs=(ResultSet) st.executeQuery(req);
java.sql.ResultSetMetaData rsmd;
rsmd= rs.getMetaData();
int ndc =rsmd.getColumnCount();
System.out.println("nbr colonnes " +ndc);
for(int i=1;i<=ndc;i++) {
System.out.println(rsmd.getColumnLabel(i)+ "|");
}
}
}

```
