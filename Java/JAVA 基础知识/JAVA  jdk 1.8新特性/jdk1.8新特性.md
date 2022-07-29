# JDK1.8新特性


----

## 接口默认方法和静态方法

 ```
      public ininterface  MyDemeService{
        //抽象方法
        String  getName();
        //默认抽象方法  可扩展 调用方式 可通过实现类进行 .方法名
        default getName(){
              return "MyDemeService_name";
        };
        //静态方法  类方法  可通过 MyDemeService.getName() 进行调用
        static getName() {
            return "static-MyDemeService_name"
        }
        
      }
      
      public class MyDemeServiceImpl  implements MyDemeService{
            //抽象方法
           public String getName(){
              return "MyDemeService_name";
           }
      }
      
      
      public  class MyDeme(){
      
            public void  main(String[] args){
                MyDemeServiceImpl myService = new MyDemeServiceImpl();
                //调用默认方法
                System.out.println(myService.defaultGetName());
                //调用静态方法
                System.out.println(MyDemeService.getName());
            }
      
      }
 ```

### 使用心得  
1. 一般用于业务查询返回默认值时可使用默认方法
2. 默认方法遵循类优先法则
### 面试问题
接口中定义的方法是否支持方法体




## Lambda 表达式运用

### 使用规范

``` 
(参数列表) ->{
    方法体

}
```

1) 没有参数的Lambda表达式
```
()->new [具体类] ;

```
2) 只有一个参数的Lambda表达式
```
x->{
  //具体方法体
  System.out.println("hello world")
}
```
3) 多个参数的Lambda表达式
```
(x,y)->{
 //具体方法体
 System.out.println(x);
 System.out.println(y);
 return  x*y;
}
```
4) 一个参数和仅一条语句的Lambda表达式
```
x->3+x;
```
5) 多个参数和仅一条语句的Lambda表达式
```
 (x,y)-> x+y;
```

1) **Lambda 集合使用方法**

    forEch
    filter
    map
    


## 函数式接口定义及使用
自定义函数式编程 在抽象接口类上添加注解 @FunctionalInterface
```
    @FunctionalInterface
    public interface MyFunctionalInterface {
        void execute();
    
    }
    
    public  class MyTest{
    
        public void deme(MyFunctionalInterface FunctionalInterface){
            FunctionalInterface.execute();
        }
        
        @Test
        public void exec(){
        
            //JDK8 以前
            demo(new MyFunctionalInterface(){
            
                @Override
                public void exec() {
                       System.out.println("jdk8 before");
                }
            });
            
            //jdk8 after
            demo(()-> System.out.println("jdk8 after"))
        }
    }
```





