
tags: #分析/关系 
#内容/编程/C语言


gcc 和 g++ 的区别无非就是调用的编译器不同, 并且传递给链接器的参数不同.

具体而言

**g++** 会把 `.c` 文件当做是 C++ 语言 (在 `.c` 文件前后分别加上 `-xc++` 和 `-xnone`, 强行变成 C++), 从而调用 `cc1plus`进行编译.

**g++** 遇到 `.cpp` 文件也会当做是 C++, 调用 `cc1plus` 进行编译. 

**g++** 还会默认告诉链接器, 让它链接上 C++ 标准库.

  

**gcc** 会把 `.c` 文件当做是 C 语言. 从而调用 `cc1` 进行编译.

**gcc** 遇到 `.cpp` 文件, 会处理成 C++ 语言. 调用 `cc1plus` 进行编译. 

**gcc** 默认不会链接上 C++ 标准库.

  

这些区别都可以在 

[@d41d8c](//www.zhihu.com/people/a05aa7fb2674d758661f495cb5ffd906)

回答中的那两个源代码中看到.

  
  
作者：孙孟越  
链接：https://www.zhihu.com/question/20940822/answer/1942335273  
来源：知乎  
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。