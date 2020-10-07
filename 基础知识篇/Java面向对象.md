## 一、面向对象

###### EG:举个例子，造一辆小汽车

# 1.画图纸

###### （1）定义车的属性：颜色，速度，几座，牌子。

###### （2）定义车的行为：跑。

# 2.拿着图纸生产汽车

###### 1.面向对象

###### 2.类：图纸

###### （1）面向对象的属性：这一类事物具有相同的属性。

###### （2）面向对象的动作：这一类事物具有相同的行为。

###### 3.对象：类的具体化，具体某一样东西。

###### 4.传参

```
public class Car {
   String color;
   int speed;
   int seat;
public void fly(String color){
    System.out.println(color+"\t颜色的车跑得快");
}
    public static void main(String[] args) {
        Car c=new Car();
        c.speed=100;
        c.color="red";
        c.fly("黑色");

    }
}

```

###### 5.this关键字,指的就是当前类的对象。

```
public class Car {
   String color;
   int speed;
   int seat;
   public void run(){
       System.out.println("车能跑");
       System.out.println(this);
       System.out.println(this.color);
   }
public void fly(String color){
    System.out.println(color+"\t颜色的车跑得快");
}
    public static void main(String[] args) {
        Car c=new Car();
        c.speed=100;
        c.color="red";
        System.out.println(c.color);
        c.run();
        c.fly("黑色");

    }
}

```

# 3.构造方法

###### 1.创建对象时自动调用的无参构造方法。

###### 2.形式：public xxx（）{}    作用：初始化对象

###### 3.与类名一致

```
public class Car {
    String color;
    int speed;
    int seat;
    public  void  run(){
        System.out.println(this.color+"颜色的车在跑");
        System.out.println(this.speed+"速度的车在跑");
        System.out.println(this.seat+"座位的车在跑");
    }
    public Car(String color,int speed,int seat){  //构造方法。
      this.color=color;
      this.speed=speed;
      this.seat=seat;
    }
    public static void main(String[] args) {
        Car c=new Car("红色",120,10);
        Car c1=new Car("绿色",180,15);
        c.run();
        c1.run();

    }
}
```

###### 4.构造方法也可以进行重载

```
public class sportCar {
    String name;  //这里的name=this.name;
    int speed;
    String color;
    int seat;
    String country;
    public sportCar(String name,int speed,String color,String country){
        this.name=name;
        this.speed=speed;
        this.color=color;
        this.country=country;
    }
    public sportCar(String name,int speed,String country){
        this.name=name;
        this.speed=speed;
        this.country=country;
    }

    public static void main(String[] args) {
        sportCar car1=new sportCar("阿斯顿马丁",110,"黑色","英国");
        sportCar car2=new sportCar("兰博基尼",200,"意大利");

    }
}

```

###### 5.构造方法一样，参数不同，这就叫重载。同名不同参。

###### 6.比如两个方法中有大量重叠的参数，可以简写。

```
public class sportCar {
    String name;
    int speed;
    String color;
    int seat;
    String country;
    public sportCar(String name,int speed,String color,String country){
        this(name,speed,country);//简写，省略大量ctrl c ctrl v。
        this.color=color;
    }
    public sportCar(String name,int speed,String country){
        this.name=name;
        this.speed=speed;
        this.country=country;
    }

    public static void main(String[] args) {
        sportCar car1=new sportCar("阿斯顿马丁",110,"黑色","英国");
        sportCar car2=new sportCar("兰博基尼",200,"意大利");

    }
}

```

###### 7.EG:注意new对象时候，Hero()，构造方法此时不能为空，必须有参，因为上面已经定义，此时状态不是默认状态。

```
public class Hero {
    String name;
    String skill_w;
    String skill_a;
    String skill_d;
    String skill_s;

    //构造方法,两个，同名不同参数
    public Hero(String name){
        this.name=name;
    }
    public Hero(String name,String skill_a,String skill_d,String skill_s,String skill_w){
        this(name);
        this.skill_a=skill_a;
        this.skill_d=skill_d;
        this.skill_s=skill_s;
        this.skill_w=skill_w;
    }
//方法
    public void fight(){
        System.out.println(this.name+"英雄的移动技巧");
    }
    public static void main(String[] args) {
        Hero h1=new Hero("亚索","左移","右移","后退","前进");
     h1.fight();
    }
}
```

###### 8.蜘蛛侠和灭霸例子

新建超人类SuperMan.java，对象类为蜘蛛侠

```
public class SuperMan {
    String name;
    int blood;
    int attack;
    //构造方法
 public SuperMan(String name,int blood, int attack){
     this.name=name;
     this.blood=blood;
     this.attack=attack;
 }
    public void fight(Monster ms){
        System.out.println(this.name+"暴揍"+ms.name);
        ms.blood-=this.attack;
        System.out.println("灭霸能量"+ms.blood);
    }

}

```

再建怪兽类Monster.java，对象为灭霸

```
public class Monster {
    String name;
    int blood;
    int attack;
    public Monster(String name,int blood, int attack){
        this.name=name;
        this.blood=blood;
        this.attack=attack;
    }
    public void fighted(SuperMan sp){
        System.out.println(this.name+"在揍"+sp.name);
        sp.blood-=this.attack;
        System.out.println("蜘蛛侠能量"+sp.blood);
    }
}

```

最后新建对战场所Client.java

```
public class Client {
    public static void main(String[] args) {
        SuperMan sp=new SuperMan("蜘蛛侠",1000,20);
        Monster ms=new Monster("灭霸",500,30);
        sp.fight(ms);
        System.out.println("/*************************************分割/");
        ms.fighted(sp);
    }
}

```

# 4.static对象.

###### 1.被static修饰的成员变量叫做静态变量，也叫做类变量，说明这个变量是属于这个类的，而不是属于是对象。

```
public class Student {
    String name;
    String sex;
    int age;
    public Student(String name,String sex,int age){
        this.name=name;
        this.sex=sex;
        this.age=age;

    }

    public static void main(String[] args) {
        Student s1=new Student("张三","男",25);

        Student s2=new Student("李四","女",22);

        s1.age=30;
        s2.age=20;
        System.out.println(s1.age);
        System.out.println("/*******************************/");
        System.out.println(s2.age);

    }
}

```

###### 2.特点

1.数据共享。

2.属于类，不属于对象。

3.先于对象产生。

注:在静态方法和静态块里面不能使用this。

在静态方法里可以调用静态东西，不能调用动态。

# 5.包跟导包

###### 1.在idea中，新建com.xxx.xxx然后新建类

![image-20201001131641034](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001131641034.png)

###### 2.两个类，在TestPerson.java中创建Person对象，然后alt+enter导入进来。

###### 3.包的本质就是文件夹，import+包+类。

###### 4.在自己包里面不需要导包。

###### 5.java.lang下所有内容都不需要导包

# 6.访问权限

###### public：所有人都可用。

###### default：包访问权限，只有自己包内可用。

###### private：私有的。

### 注：变量前面加public表示对外开放，不加则表示默认protected，则只对同包开放。

```
package com.itppf.entity;//包的声明

public class Person {
    public String pub="public";
    protected String pro="protected";
    private String pri="private";
        public static void main(String[] args) {
          Person p1=new Person();
            System.out.println(p1.pub);
            System.out.println(p1.pro);
            System.out.println(p1.pri);

    }
}

```

![image-20201001134249194](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001134249194.png)

###### 1.同一个类下面都可以访问。

######   新建类Person1.java，所以就有。

![image-20201001134459689](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001134459689.png)

私有方法private就会报错。

其余三个都可以打印出来default，public，protected。

##### 新建包com.itppf.dao。

![image-20201001135122348](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001135122348.png)

只有公共方法public可以，其余的都报错。

# 7.get/set方法

###### 1.由于某些情况下，我们需要保护个人信息，需要使用到private访问权限，而必要的参数拿不过去，因此需要将它赋值给set（）方法。

具体

this.xxx=xxx;

###### 2.然后使用get方法返回值进行拿取。

举个例子.

新建一个学生类，Student.java

```
package com.itppf.entity;

public class Student {
     int id;
     String name;
     String sex;
     String address;
    //成员方法
    public void base(){
        System.out.println(this.name+"的基本信息");
    }
    }
```

在这个方法中定义了学生的基本信息。

然后在新建主函数窗口，StudentTest.java

```
package com.itppf.entity;
public class StudentTest {
    public static void main(String[] args) {
        Student s1=new Student();
        s1.name="张三";
        s1.base();
    }
}

```

然后输出“张三的基本信息”。

当我们使用private修饰时，会不识别id，name等属性。

```
package com.itppf.entity;

public class Student {
    private int id;
    private String name;
    private String sex;
    private String address;
    //成员方法
    public void base(){
        System.out.println(this.name+"的基本信息");
    }
    }
```

![image-20201001163304025](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001163304025.png)

因此这个时候我们就需要方法。

![image-20201001164257749](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001164257749.png)

private后的name根本拿不到，必须要set传入参数后，根据get方法返回值去拿取。

#### 完整的get/set方法学生例子。



```
package com.itppf.entity;

public class Student {
    private int id;
    private String name;
    private String sex;
    private String address;
    //set方法，由于上面定义的方法全是私有的，不能够在其他类使用，而我们在某些情况下要保护这些信息，因此使用set/get方法去拿取。
    public void setId(int id){
        this.id=id;  //id是传递进来的值，而this.id则是成员变量（int id）。
    }
    public int getId(){
       return this.id;
    }

    public void setName(String name){
        this.name=name;
    }

    public String getName(){
        return this.name;
    }


    public void setSex(String sex){
        this.sex=sex;
    }
    public String getSex(){
        return this.sex;

    }


    public void setAddress(String address) {
        this.address=address;
    }

    public  String getAddress(){
        return this.address;
    }
}

```

```
package com.itppf.entity;
public class StudentTest {
    public static void main(String[] args) {
        Student s1=new Student();
        s1.setId(1);
        s1.setName("李四");
        s1.setSex("男");
        s1.setAddress("中国甘肃");
        System.out.println(s1.getId());
        System.out.println(s1.getName());
        System.out.println(s1.getSex());
        System.out.println(s1.getAddress());
        System.out.println("该生学号为:"+s1.getId()+";\n姓名为:"+s1.getName()+";\n性别为:"+s1.getSex()+";\n籍贯为:"+s1.getAddress());

    }
}

```

输出：

![image-20201001165501594](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001165501594.png)

# 8.继承

###### 1.子类可以继承父类中除了private以外的其他内容。

###### 2.形式：public class 类 extends 父类。

###### 3.作用：简化代码的开发。

Father.java

```
package com.itppf.dao;

public class Father {
    private void hobby(){
        System.out.println("父亲喜欢搓麻将");
    }
    public void temper(){
        System.out.println("父亲的脾气好");
    }
}

```

Son.java

```
package com.itppf.dao;

public class Son extends Father{
}
```

```
package com.itppf.dao;

public class ExtendsTest {
    public static void main(String[] args) {
        Son s1=new Son();
        s1.temper();
    }
}

```

但是，private修饰的方法不能够被调用。比如上面的hobby()方法。



![](C:\Users\18522\Desktop\IDEAworkplace – ExtendsTest.java IntelliJ IDEA 2020_10_1 17_52_48_wps图片.jpg)

在实战中，比如登录的实现，有member.java、admin.java、然后再新建user.java。member和admin继承user共有的方法。

#### 继承：子类对父类进行了扩展。

举个例子

```
package com.itppf.dao;

public class Father {
    public void temper(){
        System.out.println("父亲的脾气好");
    }
}

```

在子类继承父类的基础上进行了扩展，hobby（）方法。

```
package com.itppf.dao;

public class Son extends Father{
    public void hobby(){
        System.out.println("我喜欢打篮球");
    }
}
```

```
package com.itppf.dao;

public class ExtendsTest {
    public static void main(String[] args) {
        Son s1=new Son();
        s1.temper();
        s1.hobby();
    }
}
```

# 9.super关键字

###### 1.super表示父类中的内容。

###### 2.举个例子

###### 3.新建类Animal作为父类。

```
public String name="动物";package com.itppf.dao;

public class Animal {
    public String name="动物";
}
```

然后实例化对象Tiger

```
package com.itppf.dao;

public class Tiger extends Animal{
    public void eat(){
        System.out.println(this.name+"吃草");
    }
    public static void main(String[] args) {
        Tiger tiger1=new Tiger();
        tiger1.eat();
    }
}
```

打印也没有问题

但是。。。。

如果在Tiger（子类）中添加变量String name=“奶牛”

```
package com.itppf.dao;

public class Tiger extends Animal{
public String name="奶牛";
    public void eat(){
        System.out.println(this.name+"吃草");
    }
    public static void main(String[] args) {
        Tiger tiger1=new Tiger();
        tiger1.eat();
    }
}
```



则运行

![image-20201001183955552](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001183955552.png)

说明这个是有顺序的，类似于就近原则，先找自己类，再找父类。

因此我们要用到super关键字，super表示父类。

![image-20201001185320546](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201001185320546.png)

看上面的这个例子。

```
package com.itppf.dao;


public class Animal {
    public String name="动物";
    public Animal(){
        System.out.println("父类的构造方法");

    }
}





package com.itppf.dao;

public class Tiger extends Animal{
    public  String name="奶牛";
    public Tiger(){
        System.out.println("子类的构造方法");
    }
    public void eat(){
        System.out.println(this.name+"吃草");
        System.out.println(super.name+"吃草");
    }
    public static void main(String[] args) {
        Tiger tiger1=new Tiger();
        tiger1.eat();
    }
}
```

你会发现，先调用父类的构造方法，然后调用子类的构造方法。

![image-20201002225109362](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201002225109362.png)

其实这里默认了super(),如果添加上，super（），结果依然一样。

```
package com.itppf.dao;

public class Tiger extends Animal{
    public  String name="奶牛";
    public Tiger(){
        super();                                       //调用父类的构造方法
        System.out.println("子类的构造方法");
    }
    public void eat(){
        System.out.println(this.name+"吃草");
        System.out.println(super.name+"吃草");
    }
    public static void main(String[] args) {
        Tiger tiger1=new Tiger();
        tiger1.eat();
    }
}
```

但是注意super(),必须放在第一行，否则会报错。

![image-20201002225525063](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201002225525063.png)

###### 参数的传递

1.super可以获取到父类中的内容。

2.如果父类中无参，可以不写。如果有参数，必须要写上。

```
package com.itppf.dao;


public class Animal {
    public String name="动物";
    public Animal(String name){
        System.out.println("父类的构造方法");
        this.name=name;
    }
}

```

```
package com.itppf.dao;

public class Tiger extends Animal{
    public  String name="奶牛";
    public Tiger(){
        super("老虎");         //name=“老虎”，然后传到this.name,从而修改了动物。
        System.out.println("子类的构造方法");
    }
    public void eat(){
        System.out.println(super.name);
        System.out.println(this.name);

    }
    public static void main(String[] args) {
        Tiger tiger1=new Tiger();
        tiger1.eat();

    }
}

```

super和this区别父类和子类中重名的内容。

# 10.方法的重写

###### 1.重写：子类对父类中的方法进行重新的定义。

###### 2.语法：子类和父类中方法的声明完全一致。

###### 3.重写又称为方法的覆盖。

###### 4.“构造方法不能重写!!!,构造方法也不能被继承!!! 构造方法可以重载!! public Demo(){ } public Demo(int a){ } 这个是构造方法的重载!!!”

举个例子

```
package com.itppf.dao;

public class Phone {
    public void name(){

        System.out.println("我是所有手机的总称！");
    }
}

```

```
package com.itppf.dao;

public class Vivo extends Phone{
    @Override
    public void name() {
        super.name();             //super可以调用父类中被重写了的内容。
        System.out.println("不！重写之后，我是vivo");
    }

    public static void main(String[] args) {
        Vivo v1=new Vivo();
        v1.name();
    }
}

```

# 11.多态

###### 1.多态：同一个对象拥有不同的形态。

###### 2.先引出一个例子。

```
package com.itppf.dao;

public class Noodle {
    public void cook(){
        System.out.println("做一碗面条！");
    }
}

```

```
package com.itppf.dao;

public class Rice {
    public void cook(){
        System.out.println("做一碗米饭！");

    }
    }
```

```
package com.itppf.dao;

public class Cookier {
    public void cook(Noodle n){
        n.cook();
    }
    public void cook(Rice r){
        r.cook();
    }
}
```

然后创建做饭的场景。

```
package com.itppf.dao;

public class Client {
    public static void main(String[] args) {
        Noodle n=new Noodle();
        Rice r=new Rice();

        Cookier c=new Cookier();//new一个厨师
        c.cook(n);//让厨师做面条
        c.cook(r);//让厨师做米饭
    }
}
```

###### 3.由上面的例子可知，无论是做米饭还是做面条都需要创建不同的方法，这样以来就十分繁琐，那么我们有没有方法能简化这一步操作呢？

答案是可以的，我们可以定义一个食物类，面条和米饭同属于食物。

为了更直观体现，再新建一个soup类

```
package com.itppf.dao;

public class Noodle extends  Food{
    public void cook(){
        System.out.println("做一碗面条！");
    }
}
```

```
package com.itppf.dao;

public class Rice extends Food{
    public void cook(){
        System.out.println("做一碗米饭！");
    }
    }
```

```
package com.itppf.dao;

public class Soup extends Food {
    public void cook(){
        System.out.println("做一碗汤！");
    }
}
```

然后创建食物类

```
package com.itppf.dao;

public class Food {
public void cook(){
    System.out.println("烹饪食物");//主要使用cook方法，这里写不写都行
}
}
```

创建厨师类

```
package com.itppf.dao;

public class Cookier{
//    public void cook(Noodle n){
//        n.cook();
//    }
//    public void cook(Rice r){
//        r.cook();
//    }
public void cook(Food food){     //接收传进来的食物类型，也就是接收实例化的食物值，然后让不同的食物去实现各自的方法。
    food.cook();
}
}

```

创建做饭的场景

```
package com.itppf.dao;

public class Client {
    public static void main(String[] args) {
//        Noodle n=new Noodle();
//        Rice r=new Rice();
//
//        Cookier c=new Cookier();//new一个厨师
//        c.cook(n);//让厨师做面条
//        c.cook(r);//让厨师做米饭
        Food food1=new Noodle();   //把面条、米饭、汤当做食物来看，把子类的对象赋值给父类的引用，向上转型。向下转型
                                     //Noodle noodle=(Noodle)food1 强制转型、
        Food food2=new Rice();
        Food food3=new Soup();

        Cookier cookier=new Cookier();     
        cookier.cook(food1);
        cookier.cook(food2);
        cookier.cook(food3);

    }
}
```

练习：

![image-20201003153902950](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201003153902950.png)

###### 4.根据类图，写游戏代练，其实和上面的例子一样，就是看你方法里面写什么。

```
//先根据UML图写出Game类
package com.itppf.entity;

public class Game {
    public void start(){
        System.out.println("开始游戏");
    }
    public void play(){
        System.out.println("开始进入游戏");
    }
    public void end(){
        System.out.println("结束游戏");
    }
}


//LOL
package com.itppf.entity;

public class LOL extends Game {
    public void play(){
        System.out.println("开始玩LOL！");
    }
}


//DNF
package com.itppf.entity;

public class DNF extends Game {
    public void play(){
        System.out.println("开始玩DNF！");

    }
}


//CS
package com.itppf.entity;

public class CS extends Game {
    public void play(){
        System.out.println("开始玩CS！");

    }
}



//玩家
package com.itppf.entity;

public class Player{
    public void happy(Game game){
        game.play();
    }
}


//游戏场景
package com.itppf.entity;

public class GameClient {
    public static void main(String[] args) {
        Game game1=new DNF();
        Game game2=new LOL();
        Game game3=new CS();


        Player player=new Player();
        player.happy(game1);
        player.happy(game2);
        player.happy(game3);

    }
}

```

# 12.final关键字

###### 1.final：被final修饰的变量不可以被改变（无论是成员变量还是局部变量都不可改变），最终的，最后的，不可以被改变的。

###### 2.被final修饰的方法不能够重写。

###### 3.被final修饰的类不可以被继承。

举个例子

```
package com.itppf.entity;

public class Car {
    
    public final void type(){

        System.out.println("你的车是什么类型啊！");
    }
    
}
```

![image-20201004132653326](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201004132653326.png)

# 13.抽象

###### 1.在java中：只声明，不实现。

###### 2.abstract修饰方法，这个方法就是一个抽象方法，抽象方法没有方法体。

###### 3.类中如果有个抽象方法，这个类必须是一个抽象类，否则会报错。

![image-20201004145202683](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201004145202683.png)

![image-20201004145235286](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201004145235286.png)

###### 4.抽象类的特点：

###### 5.不可以创建对象，没有实例，不存在的东西。

##### 6.抽象类的子类，必须重写父类中的抽象方法。

###### 7.简单说明一下，抽象类继承父类的时候，由于父类中的方法是抽象方法，所以子类中的方法也是抽象方法，这时要求子类重写父类的方法才能够实现实例化。

###### 注：父类是抽象类，子类不一定是抽象类。

如何让它不报错？

必须重写父类的方法。

![IDEAworkplace – Apple.java IntelliJ IDEA 2020_10_4 15_01_05](C:\Users\18522\Videos\Captures\IDEAworkplace – Apple.java IntelliJ IDEA 2020_10_4 15_01_05.png)

重写之后不报错。

![image-20201004150202451](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201004150202451.png)

##### 8.作用:通过抽象类可以强制要求子类中必须有哪些方法。

添加一个抽象方法shape()后，子类必须重写这个方法，否则会报错。

![image-20201004150842477](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201004150842477.png)

![image-20201004150954808](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201004150954808.png)

重写之后。

![image-20201004151026058](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201004151026058.png)

抽象类更多的是规范化的作用，在父类中定义抽象方法，然后在子类中必须去重写这些方法，然后利用多态性进行操作。

###### EG:1.抽象化的父类

```
package com.itppf.entity;

public abstract class Fruit {
    public abstract void type();
    public abstract  void color();
}
```

###### 2.两个子类继承父类并且重写方法。

```
package com.itppf.entity;

public class Peach extends Fruit{
    public void type(){
        System.out.println("这个水果的名字叫桃子！");
    }
    public void color(){
        System.out.println("这个苹果的颜色是红色的！");
    }
}
```

```
package com.itppf.entity;

public class Apple extends Fruit{
    public void type(){
        System.out.println("这个水果的名字叫苹果！");
    }
    public void color(){
        System.out.println("这个苹果的颜色是红色的！");
    }
}
```

###### 3.售卖者

```
package com.itppf.entity;

public class Saler {
    public void sale(Fruit fruit){          //这里接收参数，并且调用各自类中的方法。
       fruit.type();          
       fruit.color();
    }
}
```

###### 4.售卖场景

```
package com.itppf.entity;

public class FruitClient {
    public static void main(String[] args) {
        Fruit fruit1=new Apple();
        Fruit fruit2=new Peach();

        Saler saler1=new Saler();
        saler1.sale(fruit1);        //这里将苹果的参数传到售卖者那里。
        System.out.println("*******************");
        saler1.sale(fruit2);               //这里将桃子的参数传到售卖者那里。
    }
}

```

###### 8.注意：抽象类中可以添加别的方法,类似于

```
package com.itppf.entity;

public abstract class Fruit {
    public abstract void type();
    public abstract  void color();
    public void weight(){
        System.out.println("这个水果很重！");
    }
}

```

# 14.接口

###### 1.接口是一种特殊的抽象类。

###### 2.接口中所有的方法都是抽象方法，省略掉abstract。

###### 3.接口使用interface来声明。

###### 4.接口中的方法都是公开的，公共的。

###### 5.能继承接口的只能是接口。

###### 6.接口和类只能是实现关系。

笔记记到这里，学了抽象类之后突然明白了接口存在的意义。总结一下，就是标准化、规范化地定义一个东西，人人都能拿到接口去做自己的东西。

```
package com.itppf.dao;

public interface place {
    public abstract void point();
}
```

```
package com.itppf.dao;

public class home implements place {
    public void point(){                 //必须要实现接口方法，其实就是重写。

    }
}
```

继承和接口用法几乎差不多，接口也具有多态性。

接口可以把不相关的东西进行整合。

###### 注：类只能单继承，但接口可以多实现。

###### 注：接口里面的变量都是全局静态变量。

###### 在接口里面定义了面积，然后去调用会报错。

![image-20201005161911062](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201005161911062.png)

在HomeTest中调用会报错。

![image-20201005162046508](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201005162046508.png)

因为被隐藏到的是

```
    public static final int area=100;
```

这样可以打印出来

```
   System.out.println(home1.area);
```

###### 这个例子可以比较形象地展现接口。

```
package com.itppf.dao;

public interface Country {
    public abstract void specificcountry();
}
```

```
package com.itppf.dao;

public  interface Province {
    public abstract void specificprovince();
}
```

```
package com.itppf.dao;

public interface Area {

    public abstract void specificsize();
}
```

```
package com.itppf.dao;

public interface Type {
    public abstract void specifictype();
}
```

```
package com.itppf.dao;

public class Place {
    public  void specificplace(){
        System.out.println("你家具体在哪个地方？");
    }
}
```

```
package com.itppf.dao;
//单继承，多实现。
public class Home extends Place implements Country,Province,Area,Type{  
//类可以实现多个接口，而接口也可以被多个接口继承。
//这里要讲，你的家不仅仅在这个国家里面，而且在这个城市里面，或者定义大小，你家有多大？多态性的体现。
//重写了一个继承的父类和三个接口，一个是展示你居住地的省份，一个是国家，还有一个是居住面积。
    @Override        //表示这个方法是重写的
    public void specificplace() {
//        super.specificplace(); //super调用的是父类的方法。
        System.out.println("你家居住的具体位置在哪里？");
    }

    @Override
    public void specificsize() {
        System.out.println("你家的居住面积多大？");
    }

    @Override
    public void specificprovince() {
        System.out.println("你家居住在哪个省份？");
    }

    @Override
    public void specificcountry() {
        System.out.println("你家居住在哪个国家？");
    }
    @Override
    public void specifictype() {
        System.out.println("你家是什么建筑风格？");
    }

}
```

```
package com.itppf.dao;

public class HomeTest {
    public static void main(String[] args) {
//        Home home1=new Home();
//        home1.specificpoint();

         Home home1=new Home(); //从家的方面去看我家，创建对象“hom1”；
         Type home2=new Home(); //从件筑风格的方面去看我家，创建对象“hom2”；（向上转型）
         Area home3=new Home();  //从建筑面积的方面去看我家，创建对象“hom3”； （向上转型）
        Province home4=new Home();  //从哪个省的方面去看我家，创建对象“hom4”； （向上转型）
        Country home5=new Home(); //从哪个国家的方面去看我家，创建对象“hom1”；（向上转型）

        //以上很好地展现出了java的多态性。

        System.out.println("-----从家的方面去调用home1具体实例-----");
        home1.specificplace();
        home1.specifictype();
        home1.specificsize();
        home1.specificprovince();
        home1.specificcountry();
        System.out.println("*******");

        System.out.println("-----从建筑风格的方面去调用home2具体实例-----");
//        home2.specificplace();
        home2.specifictype();
//        home2.specificsize();
//        home2.specificprovince();
//        home2.specificcountry();
//    由上可知，在建筑风格的角度去调用，只能看到家里建筑风格，大小，国家，省份看不到
        System.out.println("*******");


        System.out.println("-----从建筑大小的方面去调用home3具体实例-----");
//        home3.specificplace();
//        home3.specifictype();
        home3.specificsize();
//        home3.specificprovince();
//        home3.specificcountry();
//    由上可知，在建筑大小的角度去调用，只能看到家里建筑大小，风格，国家，省份看不到
        System.out.println("*******");


        System.out.println("-----从居住省份的方面去调用home4具体实例-----");
//        home4.specificplace();
//        home4.specifictype();
//        home4.specificsize();
       home4.specificprovince();
//        home4.specificcountry();
//    由上可知，在居住省份的角度去调用，只能看到家里居住的省份，大小，国家，建筑风格看不到
        System.out.println("*******");
        System.out.println("*     *");
        System.out.println("*     *");
        System.out.println("*******");


        System.out.println("-----从居住国家的方面去调用home5具体实例-----");
//        home5.specificplace();
//        home5.specifictype();
//        home5.specificsize();
//        home5.specificprovince();
        home5.specificcountry();
//    由上可知，在居住国家的角度去调用，只能看到家里居住的国家，大小，风格，省份看不到
        System.out.println("*******");




    }
}

```



![image-20201005155648466](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201005155648466.png)

###### 接口练习

![image-20201005163549344](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201005163549344.png)

综合以上，方案二比较好，类如果都实现了接口方法，则是实现类，否则都是抽象类。

###### 方案一：

```
package com.itppf.dao;

public interface IDAO {
    public abstract void connect();
    public abstract void add();
    public abstract void del();
    public abstract  void upd();
    public abstract void sel();

}
```

```
package com.itppf.dao;

public class MysqlDAO implements IDAO{

    @Override
    public void connect() {
        System.out.println("连接mysql");
    }

    @Override
    public void add() {
        System.out.println("增加数据");
    }

    @Override
    public void del() {
        System.out.println("删除数据");
    }

    @Override
    public void upd() {
        System.out.println("更新数据");
    }

    @Override
    public void sel() {
        System.out.println("查询数据");
    }
}

```

```
package com.itppf.dao;

public class OrcaleDAO implements IDAO{
    @Override
    public void connect() {
        System.out.println("连接Orcale");
    }

    @Override
    public void add() {
        System.out.println("增加数据");
    }

    @Override
    public void del() {
        System.out.println("删除数据");
    }

    @Override
    public void upd() {
        System.out.println("更新数据");
    }

    @Override
    public void sel() {
        System.out.println("查询数据");
    }
}
```

```
package com.itppf.dao;

import com.sun.org.apache.xpath.internal.operations.Or;

import java.util.Scanner;

public class FirstClient {
    public static void main(String[] args) {
        System.out.println("你想要连接哪一个数据库");
        Scanner scanner=new Scanner(System.in);
        int n=scanner.nextInt();
        if(n==1){
           IDAO idao=new MysqlDAO();
           idao.connect();
           idao.add();
           idao.del();
           idao.upd();
           idao.sel();
        }else if(n==2){
            IDAO idao=new OrcaleDAO();
            idao.connect();
            idao.add();
            idao.del();
            idao.upd();
            idao.sel();
        }


    }
}
```

以上方案一可以看得出程序代码的复用性很差。

###### 方案二：

```
package com.itppf.entity;

public interface IDAO {
    public abstract void connect();
    public abstract void  add();
    public  abstract  void  del();
    public  abstract  void upd();
    public  abstract  void sel();
}
```

```
package com.itppf.entity;

public  abstract class AbstractDAO implements IDAO {
    @Override
    public void add() {
        System.out.println("增加数据");
    }

    @Override
    public void del() {
        System.out.println("删除数据");
    }

    @Override
    public void upd() {
        System.out.println("更新数据");
    }

    @Override
    public void sel() {
        System.out.println("查询数据");
    }
}
```

```
package com.itppf.entity;

public class MysqlDAO extends AbstractDAO {
    @Override
    public void connect(){
        System.out.println("连接mysql数据库！");
    }
}
```

```
package com.itppf.entity;

public class OrcaleDAO extends AbstractDAO{
    @Override
    public void connect() {
        System.out.println("连接orcale数据库！");
    }
}
```

```
package com.itppf.entity;

import com.sun.xml.internal.bind.v2.model.core.ID;

import java.util.Scanner;

public class ScondClient  {
    public static void main(String[] args) {
        System.out.println("你想连接哪个数据库？1-mysql 2-orcale");
        Scanner scanner=new Scanner(System.in);
        int n=scanner.nextInt();
        //全局声明
        IDAO idao=null;
        if(n==1){
             idao=new MysqlDAO();
        }else if(n==2){
              idao=new OrcaleDAO();
        }
        idao.connect();
        idao.add();
        idao.del();
        idao.upd();
        idao.sel();
    }
}
```

方案二则是将公有的方法从接口里面抽出来，形成一个抽象类，然后子类继承父类并且将不同的部分进行重写。

###### 注：java接口可以被继承,而且是多继承,但是只能是接口继承接口,类只能实现接口。一个接口可以继承另一个接口或多个,一个普通类可以实现多个接口。

# 15.成员变量初始值

###### 1.java中的变量必须先声明，再赋值，最后才能使用。

###### 2.java中的成员变量，在创建对象的时候，都会执行一次初始化的操作，默认一个初始值。

###### 3.基本数据类型默认值都是0，引用数据类型默认值都是null，null表示的是占位符。

```
public class InitialValue {
    byte b;
    float f;
    double d;
    int i;
    char c;
    boolean bool;
    short s;
    long l;

    String str;
    InitialValue inital;
}
```

```
public class InitialTest {
    public static void main(String[] args) {
        InitialValue i=new InitialValue();
        System.out.println("byte="+i.b);
        System.out.println("float="+i.f);
        System.out.println("double="+i.d);
        System.out.println("int="+i.i);
        System.out.println("char="+i.c);
        System.out.println("boolean="+i.bool);
        System.out.println("short="+i.s);
        System.out.println("long="+i.l);
        System.out.println("String="+i.str);
        System.out.println("InitialValue="+i.inital);
    }
}
```

# 16.object

###### 1.object是基类，任何类都要继承自它。

###### 2.我们写的类，即使不继承自父类，也会继承自它。继承的父类也是object的子类。

# 17.equals和==

###### 1.==判断左右的数据是否相等。

###### 2.object类提供的一种方法，判断两个对象是否相等。

```
public class Cow {
    String name;
    String color;
    int age;
    public Cow(String name,String color,int age){
        this.name=name;
        this.color=color;
        this.age=age;
    }

    public static void main(String[] args) {
        Cow cow1=new Cow("小黄","黄色",12);
        Cow cow2=new Cow("小黄","黄色",12);


        System.out.println(cow1==cow2);
        System.out.println(cow1.equals(cow2));
    }
}

输出：
false
false
```

###### 3."=="一般默认基本数据类型是否相等，判断两个内存的地址是否一致，这里new开辟了新空间，所以肯定不一致。

###### 4."equals"默认是object提供的方法。

```
public class Cow {
    String name;
    String color;
    int age;
    public Cow(String name,String color,int age){
        this.name=name;
        this.color=color;
        this.age=age;
    }
     public boolean equals(Cow cow){
     if(this.name==cow.name && this.color==cow.color){
         return true;
     }else{
         return false;
     }
}
    public static void main(String[] args) {
        Cow cow1=new Cow("小黄","黄色",12);
        Cow cow2=new Cow("小黄","黄色",12);


//        System.out.println(cow1==cow2);
        System.out.println(cow1.equals(cow2));
    }
}

输出:
true
```

###### 5.上面代码中的"equals"是子类对于父类object方法的不满，然后行的扩展，然后进行重写。

```
  if(this.name==cow.name && this.color==cow.color){   //这句中的条件可以写一个两个或者全部。
```

> ######  EG：举个例子，cow1和cow2只有名字一样其余都不一样，然后根据name判断是否相等？

```
public class Cow {
    String name;
    String color;
    int age;
    public Cow(String name,String color,int age){
        this.name=name;
        this.color=color;
        this.age=age;
    }
     public boolean equals(Cow cow){
     if(this.name==cow.name){
         return true;
     }else{
         return false;
     }
}
    public static void main(String[] args) {
        Cow cow1=new Cow("小黄","黑色",11);
        Cow cow2=new Cow("小黄","黄色",12);


//        System.out.println(cow1==cow2);
        System.out.println(cow1.equals(cow2));
    }
}

输出：
true
```

###### 6.说明equals很灵活，纵使颜色和年龄都不同，然后根据name相等依然可以得出两者相同。

###### 7.同理，只有年龄不同，依然可根据name&&color得出相同。

###### 经典案例一：

```
package com.itppf;

public class Tiger {
    public static void main(String[] args) {
        String str1="老虎";
        String str2="老虎";
        System.out.println(str1==str2);
        System.out.println(str1.equals(str2));

    }
}

输出：
true;
true;
```

这里str1开辟了内存地址，str2发现一样后也指向了“老虎”。

###### 经典案例二：

```
package com.itppf;

public class Tiger {
    public static void main(String[] args) {
       String str3=new String("老虎");
        String str4=new String("老虎");

        System.out.println(str3==str4);
        System.out.println(str3.equals(str4));
    }
}

输出：
false；//new String来引入（”老虎“），是不同的对象。
true；//两个字符串的内容是一致的。
```

###### 练习模拟登陆。

```
import java.util.Scanner;

public class Login {

    public static void main(String[] args) {
        String username="admin";
        String userpassword="admin";
        Scanner scanner=new Scanner(System.in);
        System.out.println("请输入用户名：");

        String uname=scanner.nextLine();
        System.out.println("请输入密码：");

        String upassword=scanner.nextLine();

        if (uname.equals(username) && userpassword.equals(upassword) ){
            System.out.println("登陆成功");
        }else{
            System.out.println("登录失败");
        }

    }
}

```

这里涉及到一个问题，扫描仪调用的next()、nextInt()、nextLine()到底有什么区别？

1.他们的区别在于对于空格的处理方式不同，以及返回值不同。

2.使用nextLine()方法时，不将空格看做是两个字符串的间隔，而是看作字符串的一部分，返回时，它作为String类型一并返回。

3.使用next()方法时，将空格看作是两个字符串的间隔。

4.使用nextInt()方法时，与next()方法类似，只是它的返回值是int类型的，依旧将空格看作是两个输入的数据的间隔。

# 18.toString

###### 1.toString()对一个对象字符串的表现形式。

###### 2.java中建议对toString()方法进行重写，原本默认是方法是包名+类名+内存地址。

###### 直接赋值：

```
package com.itppf.entity;

public class Dog {
    String name="小黄";        
    String color="绿色";
    int age=13;

    public static void main(String[] args) {
        Dog dog1=new Dog();
        System.out.println(dog1);
        System.out.println(dog1.toString());
    }
}
```

###### 突然我在这里意识到了一个问题，那就是：

###### 直接赋值和使用构造方法有什么区别？

###### 直接赋值内存地址和值都相同，构造方法赋值，内存地址不同，值同。直接赋值比较耗费内存，而使用构造方法可以起到懒加载的作用，创建对象后开始赋值。

###### 使用构造方法：

```
package com.itppf.entity;

public class Dog {
 String name;
    String cllor;
    int age;

    public Dog(String name,String color,int age){
        this.name=name;
        this.cllor=color;
        this.age=age;
    }

    @Override
    public String toString() {                      //这是idea提供的自动重写方法。
        return "Dog{" +
                "name='" + name + '\'' +
                ", cllor='" + color + '\'' +
                ", age=" + age +
                '}';
    }

  //public String toString(){                       这是我重写的构造方法。
   //    return "我的狗的名字叫："+this.name+"我的狗的颜色是："+this.color+"年龄:"+this.age;
    //}

    public static void main(String[] args) {
        Dog dog2=new Dog("小黄","黄色",13);
        System.out.println(dog2.toString());
    }
            }
```

###### 这是idea提供的自动重写方法。

![image-20201006192415010](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006192415010.png)

![image-20201006192432605](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006192432605.png)

######   这是我重写的构造方法。

![image-20201006192517475](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006192517475.png)

![image-20201006192541393](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006192541393.png)

# 19.instanceof关键字

###### 1.主要判断对象属于哪种类型的。

```
package com.itppf.entity;

public class Mouse extends Animal {
    public static void main(String[] args) {
 Animal animal=new Mouse();
//Animal animal=new Animal();这不是老鼠。
 if(animal instanceof Mouse){
     System.out.println("这是一只老鼠");
        }else{
     System.out.println("这不是老鼠");
 }

    }
}
```

# 20.参数传递的问题

###### 1.值传递（java中就是值传递）。

###### 2.引用传递。

```
package com.itppf.entity;

public class ChairTest {
    public static void chang(Chair chair){
       chair=new Chair("长椅子");
    }

    public static void main(String[] args) {
        Chair chair=new Chair("短椅子");
        chang(chair);
        System.out.println(chair.name);
    }
}
输出：
短椅子

package com.itppf.entity;

public class ChairTest {
    public static void chang(Chair chair){
        chair.name="长椅子";
    }

    public static void main(String[] args) {
        Chair chair=new Chair("短椅子");
        chang(chair);
        System.out.println(chair.name);
    }
}
输出：
短椅子
```

###### 这里使用到了内存分析，需要画图分析。

#### 总结：面向对象，上帝视角，把控全局。

###### 1.类与对象：对象操作程序，类创建对象，类与对象就是对数据的封装。

###### 2.构造：给对象设置属性值，出厂化的设置、（this表示当前类的对象，拿到这个对象内容、访问构造方法。super 调用自己类中父类的内容，子类和父类中重名的内容可以区分，调用父类的构造方法）。

###### 3.访问权限：

###### 4.继承：父类有的功能，子类可以进行扩展，简化开发。

###### 5.多态：同一个对象有不同的形态，你可以是儿子，可以是爸爸，可以是弟弟。

###### 6.抽象：abstract，抽象方法可以不写方法体，抽象类可以写抽象方法也可以写正常的方法，对子类的约束，必须重写抽象类中的抽象方法。

###### 7.接口：特殊的抽象类，interface。能继承接口的必须是接口。类可实现接口，一个类可以实现多个接口，为了弥补java不能多继承，java可以多实现。

###### 8.内存分析：

# 21.异常处理

###### 编译异常：语法错误，编码错误。

###### 1.运行异常：编译的时候是没有错误的，语法方面是绝对正确的，找的就是运行时候的错误。

###### 2.抛异常：发现错误的时候，会创建一个错误的对象对错误进行收集，丢出错误对象的过程叫抛异常。

###### 3.捕获异常：默认由JVM来捕获异常，对错误信息进行打印，JVM会终止程序的进行。

##### 1.异常的分类：

![image-20201006210100262](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006210100262.png)

###### Throwable是所有异常的根，所有的异常都继承自Throwable，类似于Object。

###### Error：系统级的错误。

###### RuntimeExpection：运行异常，不手动处理，出问题了处理，例子（车爆胎）。

###### 其他Exception：必须要经过手动处理，例子（路障）。

##### 2.异常处理try...catch

###### 语法：

```
try{
尝试执行的代码;
}catch(Exception e){                      //catch抓住,Exception类型的e来接收异常。
处理异常的代码;
}finally                                 //无论是否出错，都要finally  
```

###### 举个例子

```
package com.itppf.entity;

public class YcTest {
    public static void main(String[] args) {
     try{
         System.out.println(1/0);
     }catch (Exception e){
         e.printStackTrace();   //打印出错误，面向程序员。
         System.out.println("程序出错了！"); //面向用户
     }finally{
         System.out.println("执行finally");
     }
    }
}
```

![image-20201006212153191](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006212153191.png)

如果程序是对的呢？

![image-20201006212233789](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006212233789.png)

###### finally：很有用，代码没有错，可以使用finally看到。

###### 使用finally关闭文件，否则文件始终处于打开状态。

##### 3.异常处理throws和throw

```
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

public class FileTest {
   public static void read(){
       InputStream inputStream=new FileInputStream(new File("hello,world!"));
   }
}
```

###### ![image-20201006214006801](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006214006801.png)第一第一种：try...catch

```
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

public class FileTest {
   public static void read(){
       try{
           InputStream inputStream=new FileInputStream(new File("hello,world!"));
       }catch (Exception e){
           System.out.println("出错");
       }finally{
           System.out.println("结束");
       }
   }
}
```

![image-20201006214136873](C:\Users\18522\AppData\Roaming\Typora\typora-user-images\image-20201006214136873.png)

###### 第二种方法：代表当前异常不处理这个错误，扔出去，有人调用这个方法，谁调用谁处理。

```
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

public class FileTest {
   public static void read() throws Exception{    //代表当前异常不处理这个错误，扔出去，有人调用这个方法，谁调用谁处理。。
       InputStream inputStream=new FileInputStream(new File("hello,world!"));

   }

    public static void main(String[] args) {
        try {
            read();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

或者继续抛出。

```
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStream;

public class FileTest {
   public static void read() throws Exception{    //代表当前异常不处理这个错误，扔出去，有人调用这个方法，谁调用谁处理。。
       InputStream inputStream=new FileInputStream(new File("hello,world!"));


   }

    public static void main(String[] args) throws Exception{
        read();
        }
    }
```

###### 这样一直抛，等于会抛给用户。

###### 尽量能处理的问题不要抛给用户

##### 4.自定义异常

直接继承Exception或者RuntimeException来实现自定义异常。

```
public class Person {
    String name;
    String gender;
    public  Person(String name,String gender){
        this.name=name;
        this.gender=gender;

    }
}
```

```
public class Bathhouse {
    public void  manBathhouse(Person person) throws GenderException{
        if(person.gender.equals("男")){
            System.out.println("欢迎来到男浴室");  //如果是男，欢迎来到男浴室。
        }else {       //否则抛出异常
            throw new GenderException("走错了");
        }
    }
}
```

```
//自己定义的必须继承Exception或者RuntimeException
public class GenderException extends Exception {
    public GenderException(String msg){
        super(msg);        //调用父类的构造方法

    }
}
```

```
public class GenderTest {
    public static void main(String[] args) throws GenderException{
        Person person1=new Person("张三","男");
        Person person2=new Person("李四","女");

        Bathhouse bathhouse=new Bathhouse();
//        bathhouse. manBathhouse(person1);
        bathhouse.manBathhouse(person2);
    }
}

```

###### 以上就是我跟这IT老男孩学习的面向对象的笔记，大多是我自己感悟，我觉得经过学习后基本了解了面向对象，以后需要学习的还有很多，数据结构以及数组，对接口，继承，封装，多态的深入了解，以及java的二十三种设计模式，加油吧。