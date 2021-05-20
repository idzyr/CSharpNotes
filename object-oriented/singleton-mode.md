# 单例模式

类只能实例化一个对象 【此功能同样适用于winForm程序】

1. 构造函数私有化

2. 提供一个静态方法给外界，使用此方法返回一个对象。

3. 创建一个单例，

   ```c
    public class Form2
       {
           //构造函数私有化
           private Form2()
           {
   
           }
   
           public static Form2 OnlyObject = null;//存放创建的唯一对象【单列对象】。
   
           /// <summary>
           /// 对外提供创建对象方法
           /// </summary>
           /// <returns></returns>
           public static Form2 GetForm2()
           {
               //正式限制创建对象
               if (OnlyObject == null)//只有OnlyObject是null时才创建对象
               {
                   OnlyObject = new Form2(); //创建这个类的对象。
               }
               return OnlyObject;//返回创建的对象。
           }
   
       }
   
   //外部使用
    Form2 form2 = Form2.GetForm2();//获得对象。
               form2.Show();
   ```

