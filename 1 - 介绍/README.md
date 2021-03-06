## 1 – 介绍
Lua是一个强大的、高效的、轻量级的嵌入式脚本语言，它支持面向过程编程、面向对象编程、函数式编程、数据驱动式编程以及数据描述。  

Lua将简单的过程语法与基于联合数组和可扩展语义的强大数据结构相结合。Lua是动态类型语言，通过基于寄存器的虚拟机直接执行字节码，并且带有GC内存管理机制，这使其成为编写配置文件、编写脚本和编写程序原型的最佳选择。  

Lua以由clean C（标准C语言和C++语言的交集）编写成的库的形式实现。Lua分发版本中包含一个名为lua的主程序，它使用Lua库来提供完整的Lua解释器功能，可以通过交互式编程或执行现有脚本文件的形式使用。Lua可以被用于嵌入到任意的程序中作为脚本运行或在解释器中独立的运行。  

作为一个扩展语言，Lua没有主函数的概念：它被嵌入到其他语言编写的程序或在Lua解释器中运行，其他语言编写的程序可以通过接口调用Lua函数来执行Lua代码，也可以读写Lua变量，甚至可以将C函数注册到Lua虚拟机并在Lua代码中调用。通过调用C函数，可以扩展Lua语言的功能并用于不同领域，从而建立共用Lua语法的不同的编程语言。  

Lua是免费软件，按照许可证中的规定，它不提供任何担保。Lua 5.4版本可以在[Lua官网](http://www.lua.org "Lua官网")获取。  

和其它文档一样，这篇文档也都是干货。如果想要了解Lua某些内容的设计原因，可以在Lua官网上查阅技术论文。如果想要系统的学习Lua编程，可以阅读由Roberto Ierusalimschy编著的《*Programming in Lua*》。  