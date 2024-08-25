public class Game {

	public static void main(String[] args)throws Exception {
		int score=0;
		List<Integer> sgn=new ArrayList<>();
		List<Integer> uen=new ArrayList<>();
		
		Scanner os=new Scanner(System.in);
		System.out.println("enter id :");
		int id=os.nextInt();
		System.out.println("enter name :");
		String name=os.next();
		Timestamp startedat=new Timestamp(System.currentTimeMillis());
		for(int i=0;i<3;i++) {
			Random r=new Random();
			int num=r.nextInt(10);
			System.out.println("guess the number");
			int un=os.nextInt();
			
			if(num==un) {
				score+=10;
			}
			sgn.add(num);
			uen.add(un);
		}
		SaveGameInfo.saveDate(id, name, ""+sgn, ""+uen, score, startedat);
	}

}
public class SaveGameInfo {
	public static void saveDate(int id,String name,String sgn,String uen,int score,java.sql.Timestamp startedat) throws Exception {
		Class.forName("com.mysql.cj.jdbc.Driver");
		Connection con=DriverManager.getConnection("jdbc:mysql://localhost:3306/jdbc_001","root","tiger");
		PreparedStatement ps=con.prepareStatement("insert into game(id,name,sgn,uen,score,startedat)values(?,?,?,?,?,?)");
		ps.setInt(1, id);
		ps.setString(2, name);
		ps.setString(3, sgn);
		ps.setString(4, uen);
		ps.setInt(5, score);
		ps.setTimestamp(6, startedat);
		
		ps.execute();
		System.out.println("your score : "+score);
	}
}
