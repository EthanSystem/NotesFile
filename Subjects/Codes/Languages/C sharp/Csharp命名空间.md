# Csharp命名空间

tags: #日期/2022-12-20 #类型/笔记 #内容/csharp 





在c#中，namespace A;和namespace A {}有什么区别？





在 C# 中，命名空间是用于组织类型的逻辑结构。命名空间可以包含类、接口、结构、枚举、委托等类型。

在 C# 中，命名空间的声明有两种形式：

1. namespace A;

这种声明方式只是声明了命名空间 A，但没有包含任何类型。这种方式常用于在一个文件中声明多个命名空间，然后在另一个文件中引用这些命名空间。

例如：

```c#
Copy codenamespace A;
namespace B;
namespace C;
```

2. namespace A {}

这种声明方式包含了命名空间 A，并在花括号内声明了命名空间 A 中的类型。

例如：

```C#
Copy codenamespace A
{
    public class MyClass
    {
        // class members go here
    }
}
```

 