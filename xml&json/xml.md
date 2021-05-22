# XML

XmlDocument类

> https://docs.microsoft.com/zh-cn/dotnet/api/system.xml.xmldocument?redirectedfrom=MSDN&view=netframework-4.8
>
> 以下代码示例都以books.xml为例

**books.xml;**

```xml
<?xml version="1.0" encoding="utf-8"?>
<books>
  <book>
    <name id="233">andorid</name>
    <author>明日科技</author>
    <price>65.5</price>
  </book>
  <book>
    <name id="002">PHP从入门到精通</name>
    <author>明日科技</author>
    <price>66.5</price>
  </book>
  <book>
    <name id="003">新家的书</name>
    <author>追加</author>
    <price>9999</price>
  </book>
</books>
```

## 属性

- `InnerText`往标签内添加内容如所示<h1>往这里添加内容</h1>
- `InnerXml`往标签内添加标签，添加标签格式的会被转换为xml元素，如所示。<div>**<p>此标签会被解析为xml节点</p>**</div>
- `DocumentElement` 获取文档的根 XmlElement。 返回XmlElement
- `LastChild` 获取节点的最后一个子级。
- `ChildNodes` 获取节点的所有子节点。 返回子节点集合XmlNodeList
- `Value` 获取或设置节点的值。 配合`Attributes`属性使用
- `Attributes` 获取节点指定属性值。
  - Attributes[“属性名”].Value

## 方法

- `CreateXmlDeclaration(xml版本，编码，是否独立【可以直接填写null】)` 创建一个具有指定值的 xml头部描述的节点。 返回XmlDeclaration

- `CreateElement(String)` 创建具有指定名称的元素。 返回XmlElement

- `SetAttribute(属性名，属性值)`给元素添加属性。

- `AppendChild(node)` 将指定的节点添加到该节点的子节点列表的末尾。 添加创建的元素。

- `Save(path)` 将 XML 文档保存到指定的文件。 如果存在指定文件，则此方法会覆盖它。

- `Load(String)` 从指定的 URL 加载 XML 文档。

- `Load(Stream)` 从指定的流加载 XML 文档。

- `SelectNodes(String)` 选择匹配 XPath 表达式的节点列表 返回

  - XPath 表达式

    “节点1/节点2/节点3”

    “/books/book/name” 如同css中的直接自带选择器，一级一级找.

- `SelectSingleNode(String)` 选择匹配 XPath 表达式的第一个 XmlNode。返回XmlNode

- `RemoveAll()` 移除当前节点的所有子节点和/或属性。



## 修改xml内容；

```csharp
//改变属性的值
            XmlDocument doc = new XmlDocument();
            doc.Load("books.xml");
            XmlNode xn = doc.SelectSingleNode("/books/book/name"); //获取匹配项【只返回第一个匹配项】
            xn.Attributes["id"].Value = "233";//修改属性值
            xn.InnerText = "andorid";//修改标签内容
            doc.Save("books.xml");
            Console.WriteLine("修改成功");
```

## 创建xml节点

```csharp
//创建xmlDoc对象。
            XmlDocument doc = new XmlDocument();

            //加载xml文档
            doc.Load("books.xml");
            //获得根节点
            XmlElement books = doc.DocumentElement;

            ////////////////////////////////////
            //开始追加
            //创建book标签
            XmlElement book = doc.CreateElement("book");
            //添加到books
            books.AppendChild(book);

            //创建namebiaoq
            XmlElement name = doc.CreateElement("name");
            //给name添加属性
            name.SetAttribute("id", "003");
            //给name添加内容
            name.InnerText = "新家的书";
            //把name添加到book上。
            book.AppendChild(name);

            //创建author
            XmlElement author = doc.CreateElement("author");
            author.InnerText = "追加";
            book.AppendChild(author);

            //创建price

            XmlElement price = doc.CreateElement("price");
            price.InnerText = "9999";
            book.AppendChild(price);

            doc.Save("books.xml");//保存



            Console.WriteLine("追加成功");

            Console.ReadKey(true);
```

## XPath表达式

XPath 是一门在 XML 文档中查找信息的语言

在 XPath 中，有七种类型的节点：元素、属性、文本、命名空间、处理指令、注释以及文档节点（或称为根节点）。

### 选取节点

XPath 使用路径表达式在 XML 文档中选取节点。节点是通过沿着路径或者 step 来选的。路径表达式：

| 表达式   | 描述                                                       |
| -------- | ---------------------------------------------------------- |
| nodename | 选取此节点的所有子节点。                                   |
| /        | 从根节点选取。                                             |
| //       | 从匹配选择的当前节点选择文档中的节点，而不考虑它们的位置。 |
| .        | 选取当前节点。                                             |
| ..       | 选取当前节点的父节点。                                     |
| @        | 选取属性。                                                 |

### 谓语（Predicates）

放在方括号[]中，相当于筛选条件，用来查找[]中指定的特定节点或者包含某个指定的值的节点。

| 路径表达式                         | 结果                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| /bookstore/book[1]                 | 选取属于 bookstore 子元素的第一个 book 元素。                |
| /bookstore/book[last()]            | 选取属于 bookstore 子元素的最后一个 book 元素。              |
| /bookstore/book[last()-1]          | 选取属于 bookstore 子元素的倒数第二个 book 元素。            |
| /bookstore/book[position()<3]      | 选取最前面的两个属于 bookstore 元素的子元素的 book 元素。    |
| //title[@lang]                     | 选取所有拥有名为 lang 的属性的 title 元素。                  |
| //title[@lang='eng']               | 选取所有 title 元素，且这些元素拥有值为 eng 的 lang 属性。   |
| /bookstore/book[price>35.00]       | 选取 bookstore 元素的所有 book 元素，且其中的 price 元素的值须大于 35.00。 |
| /bookstore/book[price>35.00]/title | 选取 bookstore 元素中的 book 元素的所有 title 元素，且其中的 price 元素的值须大于 35.00。 |

### 选取未知节点

XPath 通配符可用来选取未知的 XML 元素。

| 通配符 | 描述                 |
| ------ | -------------------- |
| *      | 匹配任何元素节点。   |
| @*     | 匹配任何属性节点。   |
| node() | 匹配任何类型的节点。 |

**例子**

| /bookstore/* | 选取 bookstore 元素的所有子元素。 |
| ------------ | --------------------------------- |
| //*          | 选取文档中的所有元素。            |
| //title[@*]  | 选取所有带有属性的 title 元素。   |

### 选取若干路径

在路径表达式中使用“|”运算符可以选取若干个路径。

| 路径表达式                       | 结果                                                         |
| -------------------------------- | ------------------------------------------------------------ |
| //book/title \| //book/price     | 选取 book 元素的所有 title 和 price 元素。                   |
| //title \| //price               | 选取文档中的所有 title 和 price 元素。                       |
| /bookstore/book/title \| //price | 选取属于 bookstore 元素的 book 元素的所有 title 元素，以及文档中所有的 price 元素。 |

### 亲属关系匹配

| 例子                   | 结果                                                         |
| ---------------------- | ------------------------------------------------------------ |
| child::book            | 选取所有属于当前节点的子元素的 book 节点。                   |
| attribute::lang        | 选取当前节点的 lang 属性。                                   |
| child::*               | 选取当前节点的所有子元素。                                   |
| attribute::*           | 选取当前节点的所有属性。                                     |
| child::text()          | 选取当前节点的所有文本子节点。                               |
| child::node()          | 选取当前节点的所有子节点。                                   |
| descendant::book       | 选取当前节点的所有 book 后代。                               |
| ancestor::book         | 选择当前节点的所有 book 先辈。                               |
| ancestor-or-self::book | 选取当前节点的所有 book 先辈以及当前节点（如果此节点是 book 节点） |
| child::*/child::price  | 选取当前节点的所有 price 孙节点。                            |
| parent::*              | 找到父级元素                                                 |
| following::*           | 选取文档中当前节点的结束标签之后的所有节点                   |
| preceding::*           | 选取文档中当前节点的开始标签之前的所有节点。                 |
| preceding-sibling::*   | 选取当前节点之前的所有同级节点                               |
| following-sibling::*   | 选取当前节点之后的所有同级节点                               |
| descendant::*          | 选取当前节点的所有后代元素（子、孙等）                       |

## 创建XML

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Xml;

namespace lesson16
{
    class Program
    {
        static void Main(string[] args)
        {
            //创建xmlDoc对象。
            XmlDocument doc = new XmlDocument();
            //创建文档头声明
            XmlDeclaration docStatement = doc.CreateXmlDeclaration("1.0", "utf-8", null);
            //添加到文档流
            doc.AppendChild(docStatement);
            //创建根元素
            XmlElement books = doc.CreateElement("books");
            //文档流添加根元素
            doc.AppendChild(books);

            //创建book标签
            XmlElement book = doc.CreateElement("book");
            //添加到books
            books.AppendChild(book);

            //创建namebiaoq
            XmlElement name = doc.CreateElement("name");
            //给name添加属性
            name.SetAttribute("id","001");
            //给name添加内容
            name.InnerText = "c#从入门到精通";
            //把name添加到book上。
            book.AppendChild(name);

            //创建author
            XmlElement author = doc.CreateElement("author");
            author.InnerText = "明日科技";
            book.AppendChild(author);

            //创建price

            XmlElement price = doc.CreateElement("price");
            price.InnerText = "65.5";
            book.AppendChild(price);

            ////////////////////////////////////////////////////////////
            //创建book1标签
            XmlElement book1 = doc.CreateElement("book");
            books.AppendChild(book1);
            XmlElement name1 = doc.CreateElement("name");
            name1.SetAttribute("id", "002");
            name1.InnerText = "PHP从入门到精通";
            book1.AppendChild(name1);

            //创建author
            XmlElement author1 = doc.CreateElement("author");
            author1.InnerText = "明日科技";
            book1.AppendChild(author1);

            //创建price

            XmlElement price1 = doc.CreateElement("price");
            price1.InnerText = "66.5";
            book1.AppendChild(price1);


            doc.Save("books.xml");

            Console.WriteLine("保存成功");

            Console.ReadKey(true);
        }
    }
}
```

**结果；**

```xml
<?xml version="1.0" encoding="utf-8"?>
<books>
  <book>
    <name id="001">c#从入门到精通</name>
    <author>明日科技</author>
    <price>65.5</price>
  </book>
  <book>
    <name id="002">PHP从入门到精通</name>
    <author>明日科技</author>
    <price>66.5</price>
  </book>
</books>
```



## 追加XML

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Xml;

namespace lesson17
{
    class Program
    {
        static void Main(string[] args)
        {
            //创建xmlDoc对象。
            XmlDocument doc = new XmlDocument();

            //加载xml文档
            doc.Load("books.xml");
            //获得根节点
            XmlElement books = doc.DocumentElement;

            ////////////////////////////////////
            //开始追加
            //创建book标签
            XmlElement book = doc.CreateElement("book");
            //添加到books
            books.AppendChild(book);

            //创建namebiaoq
            XmlElement name = doc.CreateElement("name");
            //给name添加属性
            name.SetAttribute("id", "003");
            //给name添加内容
            name.InnerText = "新家的书";
            //把name添加到book上。
            book.AppendChild(name);

            //创建author
            XmlElement author = doc.CreateElement("author");
            author.InnerText = "追加";
            book.AppendChild(author);

            //创建price

            XmlElement price = doc.CreateElement("price");
            price.InnerText = "9999";
            book.AppendChild(price);

            doc.Save("books.xml");//保存



            Console.WriteLine("追加成功");

            Console.ReadKey(true);

        }
    }
}
```

结果；

```xml
<?xml version="1.0" encoding="utf-8"?>
<books>
  <book>
    <name id="001">c#从入门到精通</name>
    <author>明日科技</author>
    <price>65.5</price>
  </book>
  <book>
    <name id="002">PHP从入门到精通</name>
    <author>明日科技</author>
    <price>66.5</price>
  </book>
  <book> //追加的xml
    <name id="003">新家的书</name> 
    <author>追加</author>
    <price>9999</price>
  </book>
</books>
```

## 读取

### 普通

读取xml标签内的所有内容

```csharp
//创建XmlDocument对象
            XmlDocument doc = new XmlDocument();
            //加载要读取的XML
            doc.Load("Books.xml");

            //获得根节点
            XmlElement books = doc.DocumentElement;

            //获得子节点 返回节点的集合
            XmlNodeList xnl = books.ChildNodes;

            foreach (XmlNode item in xnl)
            {
                Console.WriteLine(item.InnerText);//打印节点内容
            }
```

### 指定节点内容和属性值

```csharp
            XmlDocument doc = new XmlDocument();//创建xml对象
            doc.Load("books.xml");//加载xml
            XmlNodeList xnl = doc.SelectNodes("/books/book/name");//指定要获取的节点

            foreach (XmlNode node in xnl)
            {
                Console.WriteLine(node.InnerText);//打印节点内容
                Console.WriteLine(node.Attributes["id"].Value);//打印id属性
            }
            Console.ReadKey();
```

## 修改

### 修改属性值和标签内容

```c
//改变属性的值
            XmlDocument doc = new XmlDocument();
            doc.Load("books.xml");
            XmlNode xn = doc.SelectSingleNode("/books/book/name"); //获取匹配项【只返回第一个匹配项】
            xn.Attributes["id"].Value = "233";//修改属性值
            xn.InnerText = "andorid";//修改标签内容
            doc.Save("books.xml");
            Console.WriteLine("修改成功");
```

