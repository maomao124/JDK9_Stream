

## Stream流新增的方法

### 新增方法

* **takeWhile()** ：从Stream中依次获取满足条件的元素，直到不满足条件为止结束获取，只要遇到第一个不满足的条件元素马上停止获取
* **dropWhile()**：从Stream中依次删除满足条件的元素，直到不满足条件为止结束删除
* **ofNullable()**：Java 8中Stream不能完全为 null（一个元素不能为 null 多个元素是可以存在 null ），否则会报空指针异常。而 Java 9 中的 ofNullable 方法允许我们创建一个单元素 Stream，可以包含一个非空元素，也可以创建一个空 Stream





### 使用



```java
package mao;

import java.util.ArrayList;
import java.util.List;
import java.util.function.Predicate;
import java.util.stream.Collectors;

/**
 * Project name(项目名称)：JDK9_Stream
 * Package(包名): mao
 * Class(类名): Test1
 * Author(作者）: mao
 * Author QQ：1296193245
 * GitHub：https://github.com/maomao124/
 * Date(创建日期)： 2023/10/31
 * Time(创建时间)： 16:45
 * Version(版本): 1.0
 * Description(描述)： 无
 */

public class Test1
{
    public static void main(String[] args)
    {
        List<Integer> list = new ArrayList<>();
        for (int i = 0; i < 20; i++)
        {
            list.add(i);
        }
        List<Integer> list1 = list.stream().takeWhile(new Predicate<Integer>()
        {
            @Override
            public boolean test(Integer integer)
            {
                return integer < 10;
            }
        }).collect(Collectors.toList());
        System.out.println(list1);
        List<Integer> list2 = list.stream().takeWhile(integer -> integer % 4 != 3).collect(Collectors.toList());
        System.out.println(list2);
    }
}
```



```sh
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
[0, 1, 2]
```





```java
package mao;

import java.util.ArrayList;
import java.util.List;
import java.util.function.Predicate;
import java.util.stream.Collectors;

/**
 * Project name(项目名称)：JDK9_Stream
 * Package(包名): mao
 * Class(类名): Test2
 * Author(作者）: mao
 * Author QQ：1296193245
 * GitHub：https://github.com/maomao124/
 * Date(创建日期)： 2023/10/31
 * Time(创建时间)： 16:54
 * Version(版本): 1.0
 * Description(描述)： 无
 */

public class Test2
{
    public static void main(String[] args)
    {
        List<Integer> list = new ArrayList<>();
        for (int i = 0; i < 20; i++)
        {
            list.add(i);
        }
        List<Integer> list1 = list.stream().dropWhile(new Predicate<Integer>()
        {
            @Override
            public boolean test(Integer integer)
            {
                return integer < 10;
            }
        }).collect(Collectors.toList());
        System.out.println(list1);
        List<Integer> list2 = list.stream().dropWhile(integer -> integer > 10).collect(Collectors.toList());
        System.out.println(list2);
        List<Integer> list3 = list.stream().dropWhile(integer -> integer % 5 != 3).collect(Collectors.toList());
        System.out.println(list3);
    }
}
```



```sh
[10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
[3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
```





```java
package mao;

import java.util.stream.Stream;

/**
 * Project name(项目名称)：JDK9_Stream
 * Package(包名): mao
 * Class(类名): Test3
 * Author(作者）: mao
 * Author QQ：1296193245
 * GitHub：https://github.com/maomao124/
 * Date(创建日期)： 2023/10/31
 * Time(创建时间)： 16:57
 * Version(版本): 1.0
 * Description(描述)： 无
 */

public class Test3
{
    public static void main(String[] args)
    {
        Stream<Object> stream = Stream.ofNullable(null);
        System.out.println(stream.count());
        System.out.println(stream);
    }
}
```



```sh
0
java.util.stream.ReferencePipeline$Head@4eec7777
```





