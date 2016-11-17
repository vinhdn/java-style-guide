# Java Style follow raywenderlich.com

Cách viết code và hiển thị chuẩn cho Java sử dụng nguồn từ trang raywenderlich.

## Mở đầu

Hiện tại có rất nhiều các nguồn khác nhau đưa ra các style để viết code cho java cũng như Android, mình có thể thì đang tham khảo 2 nguồn chính tại
[Android contributors style guide](https://source.android.com/source/code-style.html)
và
[Google Java Style Guide](https://google.github.io/styleguide/javaguide.html).

## Table of Contents

- [Nomenclature - Cách đặt tên](#nomenclature)
  + [Packages](#packages)
  + [Classes & Interfaces](#classes--interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Variables & Parameters](#variables--parameters)
  + [Misc - Viết tắt](#misc)
- [Declarations - Khai báo](#declarations)
  + [Access Level Modifiers](#access-level-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Enum Classes](#enum-classes)
- [Getters & Setters](#getters--setters)
- [Brace Style - Ngoặc nhọn](#brace-style)
- [Switch Statements](#switch-statements)
- [Annotations](#annotations)
- [XML Guidance](#xml-guidance)
  + [XML File Names](#xml-file-names)
  + [Use Context-Specific XML Files](#use-context-specific-xml-files)
- [Language](#language)


## Nomenclature - Cách đặt tên

Cách đặt tên cơ bản phải theo quy định của java và xml

### Packages

Tất cả text đều phải là chữ thường (lower-case), nếu mà có nhiều từ khác trong một package thì viết liền không luôn các từ đó lại với nhau:

__BAD__:

```java
com.omiNext.packages_name
```

__GOOD__:

```java
com.ominext.packagesname
```

### Classes & Interfaces

Viết bằng __UpperCamelCase__ (Viết hoa chữ cái đầu của từng từ). For example `OldDog`.

### Methods

Viết bằng __lowerCamelCase__ (Viết hoa chứ cái đầu của từng từ trừ chữ đầu). For example `setColor`.

### Fields

Viết bằng __lowerCamelCase__.

Riêng các biến static final thì viết bằng __uppercase__, và phân biệt các từ bằng dấu gạch dưới:

```java
public static final int THE_AGE = 25;
```
- Các biến Non-public, non-static thêm `m` vào trước.
- Các biến static thì thêm `s` vào trước.

For example:

```java
public class MyClass {
  public static final int SOME_CONSTANT = 42;
  public int publicField;
  private static MyClass sInstance;
  int mPackagePrivate;
  private int mPrivate;
  protected int mProtected;
}
```

### Variables & Parameters

Viết bằng __lowerCamelCase__.

### Misc

Những từ viết tắt thì mình chỉ viết hoa chữ cái đầu, các chữ cái viết tắt sau thì mình viết thường. For example:

__BAD:__

```java
XMLHTTPRequest
String URL
findPostByID
```
__GOOD:__

```java
XmlHttpRequest
String url
findPostById
```

## Declarations - Khai báo

### Access Level Modifiers

Cần phân quyền rõ ràng cho các lớp, biến, hàm. (public, private, protected...)

### Fields & Variables

Hãy khai báo mỗi biến một dòng để dễ nhìn và dễ quản lý.

__BAD:__

```java
String username, twitterHandle;
```

__GOOD:__

```java
String username;
String twitterHandle;
```

### Classes

Nên viết mỗi class trong một file.


### Enum Classes

Nếu khai báo một enum class mà không tồn tại hàm trong đó thì các enum viết trên một dòng.

```java
private enum CompassDirection { EAST, NORTH, WEST, SOUTH }
```

## Getters & Setters

Để truy vấn các biến private hoặc protected cần tạo get và set cho các biến đó

Tham khảo của Google: http://developer.android.com/training/articles/perf-tips.html#GettersSetters

## Brace Style

Mình nên để dấu mở ngoặc nhọn trên cùng dòng với dòng định nghĩa tên hàm

__BAD:__

```java
class MyClass
{
  void doSomething()
  {
    if (someTest)
    {
      // ...
    }
    else
    {
      // ...
    }
  }
}
```

__GOOD:__

```java
class MyClass {
  void doSomething() {
    if (someTest) {
      // ...
    } else {
      // ...
    }
  }
}
```

Trong các function điều kiện thì phải đưa các câu lệnh vào trong dấu {} dù có chỉ có 1 lênh.

__BAD:__

```java
if (someTest)
  doSomething();
if (someTest) doSomethingElse();
```

__GOOD:__

```java
if (someTest) {
  doSomething();
}
if (someTest) { doSomethingElse(); }
```


## Switch Statements

Sử dụng switch, bắt buộc phải có default cuối switch

__BAD:__

```java
switch (anInput) {
  case 1:
    doSomethingForCaseOne();
  case 2:
    doSomethingForCaseOneOrTwo();
    break;
  case 3:
    doSomethingForCaseOneOrThree();
    break;
}
```

__GOOD:__

```java
switch (anInput) {
  case 1:
    doSomethingForCaseOne();
    // fall through
  case 2:
    doSomethingForCaseOneOrTwo();
    break;
  case 3:
    doSomethingForCaseOneOrThree();
    break;
  default:
    break;
}
```

## Annotations - Chú thích

Chú thích cho phần Override Interfaces `@Override` cần được viết trên function một dòng. (Không nên bỏ đi)

__BAD:__

```java
protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
}
```

__GOOD:__

```java
@Override
protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
}
```


## XML Guidance

Các rules cho file XML view android

### XML File Names

Phải viết loại view của file trước rồi viết tên của các file sau.
Tất cả các chữ viết thường, các từ cách nhau bằng dấu gạch dưới.

__BAD:__

- `login.xml`
- `main_screen.xml`
- `rounded_edges_button.xml`

__GOOD:__

- `activity_login.xml`
- `fragment_main_screen.xml`
- `button_rounded_edges.xml`

### Use Context-Specific XML Files

XML resources phân chia theo cấu trúc của Android bên dưới:

- Strings => `res/values/strings.xml`, `res/values-vi/strings.xml`
- Styles => `res/values/styles.xml`, `res/values-sw620dp/styles`
- Colors => `res/color/colors.xml`
- Animations => `res/anim/`
- Drawable => `res/drawable`, `res/drawable-xhdpi`
- Layout => `res/layout`, `res/layout-xlarge`



## Language

Use US English spelling.

__BAD:__

```java
String colour = "red";
```

__GOOD:__

```java
String color = "red";
```

## Copyright Statement

The following copyright statement should be included at the top of every source
file:

    /*
     * Copyright (c) 2016 Razeware LLC
     *
     * Permission is hereby granted, free of charge, to any person obtaining a copy
     * of this software and associated documentation files (the "Software"), to deal
     * in the Software without restriction, including without limitation the rights
     * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
     * copies of the Software, and to permit persons to whom the Software is
     * furnished to do so, subject to the following conditions:
     *
     * The above copyright notice and this permission notice shall be included in
     * all copies or substantial portions of the Software.
     *
     * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
     * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
     * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
     * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
     * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
     * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
     * THE SOFTWARE.
     */
