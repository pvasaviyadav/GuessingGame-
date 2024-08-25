public class Theater {
  private int seats=100;
  private static Theater t=null;
  private Theater(){
  }
  public static Theater getInstance(){
      if (t==null){
          t=new Theater();
          return t;
      }
      else {
          return t;
      }
  }
  public  void book(int n){
      if (n<=seats){
          seats-=n;
          System.out.println("seats are booked");
      }
      else {
          if (n==0)
              System.out.println("so sorry all seats are booked");
          else
              System.out.println("sorry "+seats+" seats are available");

      }
  }
  public int getSeats(){
      return seats;
  }
    }
    class book{
    public static void booktickets(){
        Scanner os=new Scanner(System.in);
        Theater m1=Theater.getInstance();
        System.out.println(m1.getSeats()+" seats are available");
        System.out.println("enter seats");
        int seats=os.nextInt();
        m1.book(seats);
    }
    }
    class bookmyshow{
        public static void main(String[] args) {
            book.booktickets();
            book.booktickets();
        }
    }
