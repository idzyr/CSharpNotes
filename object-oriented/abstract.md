# 抽象类

当父类中的方法不知道如何去实现的时候，可以考虑将父类写成抽象类，将方法写成抽象方法。

**特点；**

1. 抽象类被`abstract,`修饰。
2. 抽象成员必须标记为`abstract`并且不能有任何实现。
3. 抽象成员必须在抽象类中。抽象类中不一定都是抽象方法。
4. 抽象类不能被实例化,只能被继承。
5. 继承抽象类的类必须重写抽象类中的所有抽象方法。
6. 抽象成员的访问修饰符不能是private
7. 抽象类是有构造函数的。虽然不能被实例化
8. 如果父类的抽象方法中有参数，那么。继承这个抽象父类的子类在重写父类的方法的时候必须传入对应的参数。如果抽象父类的抽象方法中有返回值，那么子类在重写这个抽象方法的时候 也必须要传入返回值。

- 抽象类和抽象方法

  ```csharp
  using System;
  using System.Collections.Generic;
  using System.Linq;
  using System.Text;
  using System.Threading.Tasks;
  
  namespace 抽象类
  {
      public abstract class Animal
      {
          //写一个吃的抽象类
          public abstract void eat();
      }
  }
  ```

- 继承抽象类，并重写抽象方法

  ```csharp
  using System;
  using System.Collections.Generic;
  using System.Linq;
  using System.Text;
  using System.Threading.Tasks;
  
  namespace 抽象类
  {
      public class Dog :Animal
      {
          //重写抽象类中的抽象方法。
          public override void Eat()
          {
              Console.Write("狗吃骨头");
          }
      }
  }
  ```

- 测试类

  ```csharp
  using System;
  using System.Collections.Generic;
  using System.Linq;
  using System.Text;
  using System.Threading.Tasks;
  
  namespace 抽象类
  {
      class Program
      {
          static void Main(string[] args)
          {
              Dog dog = new Dog();
              dog.Eat();
              Console.ReadKey();
  
          }
      }
  }
  ```

