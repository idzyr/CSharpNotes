# Object

object是所有类的超类，所以任何类都有ToString方法

## 方法

- `ToString();`

### ToString 格式

- 取中文日期显示

  1. 年月日时分currentTime.ToString("f");//不显示秒
  2. 年月currentTime.ToString("y");
  3. 月日currentTime.ToString("m");
  4. 格式为：2003-9-23 currentTime.ToString("d");
  5. 格式为：14:24 currentTime.ToString("t");

- 字符型转换转为字符串

  1. 12345.ToString("n");//结果：12,345.00
  2. 12345.ToString("C");//结果：￥12,345.00
  3. 12345.ToString("e");//结果：1.234500e+004
  4. 12345.ToString("f4");//结果：12345.0000
  5. 12345.ToString("x");//结果：3039(16进制)
  6. 12345.ToString("p");//结果：1,234,500.00%

- 日期

  1. DateTime.Now为2007-7-1722:07:24
  2. DateTime.Now.ToString("yy－MM－dd")处理后：07-07-172、DateTime.Now.ToString("yy年MM月dd日")处理后：07年07月17日（中文样式）

- ToString("x2") 1).转化为16进制。

  2).大写X:ToString("X2")即转化为大写的16进制。

  3).小写x:ToString("x2")即转化为小写的16进制。

  4).2表示输出两位，不足的2位的前面补0,如 0x0A 如果没有2,就只会输出0xA

