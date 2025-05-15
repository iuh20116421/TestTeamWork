package connectdb;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
public class connectDB {
	public static Connection con = null;
	public static connectDB instance = new connectDB();
	public static connectDB getInstance() {
		return instance;
	}
	public void connect() {
		String url = "jdbc:sqlserver://localhost:1433; databasename=QL";
		String user = "sa";
		String password = "sapassword";
		try {
			con = DriverManager.getConnection(url, user, password);
		} catch (SQLException e) {
			e.printStackTrace();
			// TODO: handle exception
		}
	}
	public static Connection getConnection() {
		return con;
	}
	public void disconnect() {
		if (con != null) {
			try {
				con.close();
			} catch (SQLException e) {
				e.printStackTrace();
				// TODO: handle exception
			}
		}
	}
	public static void main(String[] args) {
		connectDB db = connectDB.getInstance();
		db.connect();
		if (getConnection() != null) {
			System.out.println("Kết nối thành công cơ sở dữ liệu");
		} else {
			System.out.println("Kết nối thất bại");
		}
		db.disconnect();
	}
}
