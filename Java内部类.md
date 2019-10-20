new一个内部类的方法可以是Outer.new Inner()
内部类可以任意获得外部类的成员变量

```
public class InnerTest {
    public static void main(String[] args) {
        Game a= new Game("234234");
        Game b= new Game("bbbbbb");
        //a.new ThreadDriver();
        var pool = Executors.newFixedThreadPool(200);
        pool.execute(a.new Player());
        pool.execute(a.new Player());
        pool.execute(b.new Player());
        pool.shutdown();        
    }   
}
class Game {
    private String s;
    Game(String s){
        this.s = s;
    }
    class Player implements Runnable {

        @Override
        public void run() {
            System.out.println(s);
        }
    }
}
```
