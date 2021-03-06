# 访问修饰符

| 修饰符                                   | 作用                                                         |
| ---------------------------------------- | ------------------------------------------------------------ |
| public                                   | 公开的公共的，任何地方都可以访问                             |
| private                                  | 私有的，只能在当前类的内部访问                               |
| protected                                | 受保护的，只能在当前类的内部以及该类的子类中访问。           |
| internal                                 | 内部，只能在当前项目中访问。在同一个项目中，internal和public的权限是一样。 |
| protected internal（protected+internal） | 受保护的+内部；只能在当前类的内部以及该类的子类中访问+只能在当前项目中访问 |

> **注意；**
>
> 1. 能够**修饰类**的访问修饰符只有两个：public、internal。类不加修饰符默认是internal
> 2. 可访问性不一致。子类的访问权限不能**高于**父类的访问权限，会暴漏父类的成员。



