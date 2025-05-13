
package connectDB;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class Database {
	public static Connection con = null;
	private static Database instance = new Database();

	public static Database getInstance() {
		return instance;
	}

	public void connect() {
		String url, user, pass;
		url = "jdbc:sqlserver://localhost:1433;databasename=QL";
		user = "sa";
		pass = "sapassword";
		try {
			con = DriverManager.getConnection(url, user, pass);
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}

	public static Connection getConnection() {
		return con;
	}

	public void disconnect() {
		if (con != null)
			try {
				con.close();
			} catch (Exception e) {
				e.printStackTrace();
			}
	}
}
