一、keyof typeof
```
enum Test {
  Get = 1;
  Post= 2;
}
keyof typeof Test;
```
 解释：typeof返回Test对应类型{Get: number, Post: number}, keyof获取集合{Get | Post}
