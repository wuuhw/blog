---
title: "理解dart中的Number"
date: "2020-01-15T22:40:32.169Z"
template: "post"
draft: false
slug: "/posts/理解dart中的Number/"
category: "dart"
tags:
  - "flutter"
  - "dart"
description: "了解dart中的int 和 double类型， 以及api的操作"
---

# Number

### Base
1. 在dart中的数值类型有2种， 分别是`int` 和 `double`, 都继承与 [`num`](https://api.dart.dev/stable/2.7.0/dart-core/num-class.html);
2. dart 中的int取值范围在` -263 ~ 263 - 1`， 当转换为`javaScript`在浏览器下运行时遵循Js的规则取 ` -253 到 253 - 1`
3. `double` 是64位（双精度）浮点数，采用的是[IEEE 754标准](https://zh.wikipedia.org/wiki/IEEE_754)
4. dart在2.1版本之后在必要的的情况下会自动将int转换为double
    ```
    double d =1;
    print(d); // 1.0
    int i = 1.0; //编译时错误：  A value of type 'double' can't be assigned to a variable of type 'int'.
    print(i);
    ```


### 静态方法
1. parse 将数字字符串转换为num, 有问题则抛出异常[`FormatException`](https://api.dart.dev/stable/2.1.1/dart-core/FormatException-class.html)
    ```dart
    // int.parse(String input): int ｜Error
    // double.parse(String input): double ｜Error
    
    print(int.parse('1000')); // 1000
    print(double.parse('1000.0')); // 1000.0
    
    print(int.parse('1000.0')); // FormatException
    print(int.parse('text1000')); // FormatException
    ```
2. tryParse 将数字字符串转换为num, 有问题则返回 `null`。 在处理用户输入的时候tryParse 会比 parse 更合理一点
    ```
    // int.tryParse(String input): int | null
    // double.tryParse(String input): double | null
        
    print(int.tryParse('1000')); // 1000
    print(double.tryParse('1000.0')); // 1000.0
    
    print(int.tryParse('1000.0')); // null
    print(int.tryParse('text1000')); // null
    ```
    
### 方法
1. abs 取绝对值
    ```
    var num = -10;
    print(num.abs());  // 10
    print((-10.11).abs()); // 10.11
    
    print(-10.abs());  // -10
    print(-10.11.abs()); // -10.11
    ```
2. ceil 向上取整
    ```
    print(10.11.ceil()); // 11
    print(-10.11.ceil()); // -11
    print((-10.11).ceil()); // -10
    ```
3. ceilToDouble 向上取整,返回是一个double类型的整数` 1.0、 2.0`
    ```
    print(10.11.ceilToDouble()); // 11.0
    print(-10.11.ceilToDouble()); // -11.0
    print((-10.11).ceilToDouble()); // -10.0
    ```
4. clamp(lowerLimit, upperLimit) 限制边界，使取值范围在lowerLimit ～ upperLimit 之间，
    ```
    print(10.clamp(1, 100)); // 10  如果num < lowerLimit，返回 lowerLimit
    print(0.clamp(1, 100)); // 1   如果 lowerLimit < num > upperLimit，返回 num
    print(101.clamp(1, 100)); // 100 如果num > upperLimit，返回 upperLimit
    ```
5. compareTo(num other) 与 `other` 进行比较
    ```
    print(10.compareTo(9)); // 1 如果 num > other， 返回 正整数 1
    print(10.compareTo(10.0)); // 0 如果 num == other， 返回 0
    print(10.compareTo(100)); // -1 如果 num < other， 返回 负整数 -1
    print((-0.0).compareTo(0.0)); // -1 NOTE: 使用compareTo的时候 -0.0 小于 0.0. 这一点需要特殊注意，和 == 操作符不一致
    print((-0.0) == 0.0); // true 
    ```
6. floor 向下取整
    ```
    print(10.11.floor()); // 10
    print(-10.11.floor()); // -10
    print((-10.11).floor()); // -11
    ```
6. floorToDouble 向下取整，返回是一个double类型的整数` 1.0、 2.0`
    ```
    print(10.11.floor()); // 10.0
    print(-10.11.floor()); // -10.0
    print((-10.11).floor()); // -11.0
    ```
7. floorToDouble 向下取整，返回是一个double类型的整数` 1.0、 2.0`
    ```dart
    main() {
      var list = [
        [15, 3],
        [10, 3],
        [2, 10],
        [9, 8],
        [9, 2],
        [7, 5]
      ];
      list.forEach((item) {
        var i1 = item[0];
        var i2 = item[1];
        print(
            '${i1}.remainder(${i2}) == ${i1} / ${i2}: ${i1.remainder(i2) == i1 % i2} ');
      });
      // 15.remainder(3) == 15 / 3: true 
      // 10.remainder(3) == 10 / 3: true 
      // 2.remainder(10) == 2 / 10: true 
      // 9.remainder(8) == 9 / 8: true 
      // 9.remainder(2) == 9 / 2: true 
      // 7.remainder(5) == 7 / 5: true 
    }
    ```

   
   
   
   

