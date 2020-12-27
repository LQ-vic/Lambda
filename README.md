# Lambda
public interface MyInterface {
    void show1();

    void show2();

//    void show3();

//    public default void show3() {
//        System.out.println("show3");
//    }

    default void show3() {
        System.out.println("show3");
    }
}





/*
    需求：
        1:定义一个接口MyInterface，里面有两个抽象方法：
            void show1();
            void show2();
        2:定义接口的两个实现类：
            MyInterfaceImplOne
            MyInterfaceImplTwo
        3:定义测试类：
            MyInterfaceDemo
            在主方法中，按照多态的方式创建对象并使用
 */
public class MyInterfaceDemo {
    public static void main(String[] args) {
        //按照多态的方式创建对象并使用
        MyInterface my = new MyInterfaceImplOne();
        my.show1();
        my.show2();
        my.show3();
    }
}






public class MyInterfaceImplOne implements MyInterface {
    @Override
    public void show1() {
        System.out.println("One show1");
    }

    @Override
    public void show2() {
        System.out.println("One show2");
    }

    @Override
    public void show3() {
        System.out.println("One show3");
    }
}






public class MyInterfaceImplTwo implements MyInterface {
    @Override
    public void show1() {
        System.out.println("Two show1");
    }

    @Override
    public void show2() {
        System.out.println("Two show2");
    }
}






public interface MyInterfaceSon extends MyInterface {
    void show3();
}






public interface Flyable {
    public static void test() {
        System.out.println("Flyable 中的静态方法执行了");
    }
}





public interface Inter {
    void show();

    default void method(){
        System.out.println("Inter 中的默认方法执行了");
    }

//    public static void test(){
//        System.out.println("Inter 中的静态方法执行了");
//    }

    static void test(){
        System.out.println("Inter 中的静态方法执行了");
    }
}




/*
    需求：
        1:定义一个接口Inter，里面有三个方法：一个是抽象方法，一个是默认方法，一个是静态方法
            void show();
            default void method(){ }
            public static void test(){ }
        2:定义接口的一个实现类：
            InterImpl
        3:定义测试类：
            InterDemo
            在主方法中，按照多态的方式创建对象并使用
 */
public class InterDemo {
    public static void main(String[] args) {
        //按照多态的方式创建对象并使用
        Inter i = new InterImpl();
        i.show();
        i.method();
//        i.test();

        Inter.test();
//        InterImpl.test();

        Flyable.test();

    }
}






public class InterImpl implements Inter,Flyable {
    @Override
    public void show() {
        System.out.println("show方法执行了");
    }
}





public interface Inter {
    default void show1() {
        System.out.println("show1开始执行");
//        System.out.println("初级工程师");
//        System.out.println("中级工程师");
//        System.out.println("高级工程师");
//        show();
        method();
        System.out.println("show1结束执行");
    }

    default void show2() {
        System.out.println("show2开始执行");
//        System.out.println("初级工程师");
//        System.out.println("中级工程师");
//        System.out.println("高级工程师");
//        show();
        method();
        System.out.println("show2结束执行");
    }

    private void show() {
        System.out.println("初级工程师");
        System.out.println("中级工程师");
        System.out.println("高级工程师");
    }

    static void method1() {
        System.out.println("method1开始执行");
//        System.out.println("初级工程师");
//        System.out.println("中级工程师");
//        System.out.println("高级工程师");
//        show();
        method();
        System.out.println("method1结束执行");
    }

    static void method2() {
        System.out.println("method2开始执行");
//        System.out.println("初级工程师");
//        System.out.println("中级工程师");
//        System.out.println("高级工程师");
        method();
        System.out.println("method2结束执行");
    }

    private static void method() {
        System.out.println("初级工程师");
        System.out.println("中级工程师");
        System.out.println("高级工程师");
    }
}



/*
    需求：
        1:定义一个接口Inter，里面有四个方法：二个默认方法，二个静态方法
            default void show1(){   }
            default void show2(){   }
            static void method1(){   }
            static void method2(){   }
        2:定义接口的一个实现类：
            InterImpl
        3:定义测试类：
            InterDemo
            在主方法中，按照多态的方式创建对象并使用
 */
public class InterDemo {
    public static void main(String[] args) {
        //按照多态的方式创建对象并使用
        Inter i = new InterImpl();
        i.show1();
        System.out.println("--------");
        i.show2();
        System.out.println("--------");

        Inter.method1();
        System.out.println("--------");
        Inter.method2();

    }
}






public class InterImpl implements Inter {

}




/*
    需求：启动一个线程，在控制台输出一句话：多线程程序启动了
 */
public class LambdaDemo {
    public static void main(String[] args) {
        //实现类的方式实现需求
//        MyRunnable my = new MyRunnable();
//        Thread t = new Thread(my);
//        t.start();

        //匿名内部类的方式改进
//        new Thread(new Runnable() {
//            @Override
//            public void run() {
//                System.out.println("多线程程序启动了");
//            }
//        }).start();

        //Lambda表达式的方式改进
        new Thread( () -> {
            System.out.println("多线程程序启动了");
        } ).start();
    }
}





public class MyRunnable implements Runnable {

    @Override
    public void run() {
        System.out.println("多线程程序启动了");
    }
}





public interface Eatable {
    void eat();
}




/*
    Lambda表达式的格式：(形式参数) -> {代码块}

    练习1：
        1:定义一个接口(Eatable)，里面定义一个抽象方法：void eat();
        2:定义一个测试类(EatableDemo)，在测试类中提供两个方法
            一个方法是：useEatable(Eatable e)
            一个方法是主方法，在主方法中调用useEatable方法
 */
public class EatableDemo {
    public static void main(String[] args) {
        //在主方法中调用useEatable方法
        Eatable e = new EatableImpl();
        useEatable(e);

        //匿名内部类
        useEatable(new Eatable() {
            @Override
            public void eat() {
                System.out.println("一天一苹果，医生远离我");
            }
        });

        //Lambda表达式
        useEatable(() -> {
            System.out.println("一天一苹果，医生远离我");
        });
    }

    private static void useEatable(Eatable e) {
        e.eat();
    }
}






public class EatableImpl implements Eatable {

    @Override
    public void eat() {
        System.out.println("一天一苹果，医生远离我");
    }
}






public interface Flyable {
    void fly(String s);
}





/*
    Lambda表达式的格式：(形式参数) -> {代码块}

    练习2：
        1:定义一个接口(Flyable)，里面定义一个抽象方法：void fly(String s);
        2:定义一个测试类(FlyableDemo)，在测试类中提供两个方法
            一个方法是：useFlyable(Flyable f)
            一个方法是主方法，在主方法中调用useFlyable方法
 */
public class FlyableDemo {
    public static void main(String[] args) {
        //在主方法中调用useFlyable方法
        //匿名内部类
        useFlyable(new Flyable() {
            @Override
            public void fly(String s) {
                System.out.println(s);
                System.out.println("飞机自驾游");
            }
        });
        System.out.println("--------");

        //Lambda
        useFlyable((String s) -> {
            System.out.println(s);
            System.out.println("飞机自驾游");
        });

    }

    private static void useFlyable(Flyable f) {
        f.fly("风和日丽，晴空万里");
    }
}




public interface Addable {
    int add(int x,int y);
}




/*
    Lambda表达式的格式：(形式参数) -> {代码块}

    练习3：
        1:定义一个接口(Addable)，里面定义一个抽象方法：int add(int x,int y);
        2:定义一个测试类(AddableDemo)，在测试类中提供两个方法
            一个方法是：useAddable(Addable a)
            一个方法是主方法，在主方法中调用useAddable方法
 */
public class AddableDemo {
    public static void main(String[] args) {
        //在主方法中调用useAddable方法
        useAddable((int x,int y) -> {
            return x + y;
//            return  x - y;
        });

    }

    private static void useAddable(Addable a) {
        int sum = a.add(10, 20);
        System.out.println(sum);
    }
}



public interface Addable {
    int add(int x, int y);
}




public interface Flyable {
    void fly(String s);
}



/*
    Lambda表达式的省略模式
 */
public class LambdaDemo {
    public static void main(String[] args) {
//        useAddable((int x,int y) -> {
//            return x + y;
//        });
        //参数的类型可以省略
        useAddable((x, y) -> {
            return x + y;
        });
        //但是有多个参数的情况下，不能只省略一个
//        useAddable((x,int y) -> {
//            return x + y;
//        });

//        useFlyable((String s) -> {
//            System.out.println(s);
//        });
//        useFlyable((s) -> {
//            System.out.println(s);
//        });
        //如果参数有且仅有一个，那么小括号可以省略
//        useFlyable(s -> {
//            System.out.println(s);
//        });

        //如果代码块的语句只有一条，可以省略大括号和分号
        useFlyable(s -> System.out.println(s));

        //如果代码块的语句只有一条，可以省略大括号和分号，如果有return，return也要省略掉
        useAddable((x, y) -> x + y);
    }

    private static void useFlyable(Flyable f) {
        f.fly("风和日丽，晴空万里");
    }

    private static void useAddable(Addable a) {
        int sum = a.add(10, 20);
        System.out.println(sum);
    }
}




public interface Inter {
    void show();

//    void method();
}





/*
    Lambda表达式的注意事项
 */
public class LambdaDemo {
    public static void main(String[] args) {
//        useInter(() -> {
//            System.out.println("好好学习天天向上");
//        });

        //使用Lambda必须要有接口，并且要求接口中有且仅有一个抽象方法
        useInter(() -> System.out.println("好好学习天天向上"));

        //必须有上下文环境，才能推导出Lambda对应的接口
//        new Thread(new Runnable() {
//            @Override
//            public void run() {
//                System.out.println("匿名内部类");
//            }
//        }).start();

//        Runnable r = () -> System.out.println("Lambda表达式");
//        new Thread(r).start();

        new Thread(() -> System.out.println("Lambda表达式")).start();
    }

    private static void useInter(Inter i) {
        i.show();
    }
}





public abstract class Animal {
    public abstract void method();
}





public interface Inter {
    void show();
//    void show2();
}






/*
    Lambda表达式和匿名内部类的区别
 */
public class LambdaDemo {
    public static void main(String[] args) {
        //匿名内部类
        /*
        useInter(new Inter() {
            @Override
            public void show() {
                System.out.println("接口");
            }
        });

        useAnimal(new Animal() {
            @Override
            public void method() {
                System.out.println("抽象类");
            }
        });

        useStudent(new Student(){
            @Override
            public void study() {
                System.out.println("具体类");
            }
        });
        */

        useInter(new Inter() {
            @Override
            public void show() {
                System.out.println("接口");
            }
        });

        //Lambda
//        useInter(() -> System.out.println("接口"));
//        useAnimal(() -> System.out.println("抽象类"));
//        useStudent(() -> System.out.println("具体类"));

//        useInter(() -> System.out.println("接口"));

//        useInter(new Inter() {
//            @Override
//            public void show() {
//                System.out.println("show");
//            }
//
//            @Override
//            public void show2() {
//                System.out.println("show2");
//            }
//        });

    }

    private static void useStudent(Student s) {
        s.study();
    }

    private static void useAnimal(Animal a) {
        a.method();
    }

    private static void useInter(Inter i) {
        i.show();
    }
}






public class Student {
    public void study() {
        System.out.println("爱生活，爱Java");
    }
}
