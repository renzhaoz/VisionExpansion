# Document 文档信息

## 简介

- URL包含当前页面完整的URL(对应url中的URL)

- domain包含页面的域名

- referrer 包含链接到当前页面的那个页面的URL，若当前页面没有来源，referrer值为空字符串

## 特性

- URL domain referrer 都可以在HTTP头部信息中获取 可以通过以下属性访问

  ```
    URL - document.URL
    domain - document.domain
    referrer - document.referrer
  ```

- domain 可写其余只读, domain值的设置必须包含在在域名内

  ```
    // 页面来自 p2p.wrox.com
    document.domain = "wrox.com";
    // 成功
    2
    document.domain = "nczonline.net"; // 出错!
  ```

- domain 值的值从详细到放松改后 就不能改回去了 只能再往送放

  ```
    // 页面来自 p2p.wrox.com
    document.domain = "wrox.com";
    // 放松,成功
    document.domain = "p2p.wrox.com"; // 收紧,错误!
  ```

## 使用场景

- 设置相同的domain值实现在iframe和主界面之间的值的访问(同域名下的子域)
  当页面中有iframe时,在每个页面设置document.domain为相同的值，这些页面就可以访问对方的javascript对象

- referrer 常用与验证当前域名是否被劫持,伪造授权等,但是都会有办法被绕过

```
  <a  href="/exit.php?url=http%3A%2F%2Fexample.com">Example.com</a>
  上面网址中，先跳转到/exit.php，然后再跳转到目标网址。这时，Referer字段就不会包含原始网址。
```