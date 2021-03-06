### 2.3 – 错误处理  
Lua代码活动可以抛出错误。错误将会中断Lua程序的运行，捕获错误可以使出错程序继续运行。  

Lua代码可以调用error函数显式的抛出错误。（error函数没有返回值。）  

想要捕获错误，你可以使用“受保护的调用”*pcall*(或*xpcall*).*pcall*函数可以使用保护模式调用指定的函数。函数运行中产生的错误会中断函数的运行，立即返回到*pcall*，*pcall*将会返回一个状态码。  

因为Lua是一门嵌入式扩展语言，所以Lua代码会从主程序中的C函数调用运行。（当你独立使用Lua时，*lua*程序即为主程序）通常情况下，此类调用是受保护的；所以，当编译或运行未受保护的代码块产生错误时，将立即返回主程序，进而对此采取一些适当的措施，比如输出错误信息。  

当错误产生时，一个带有错误信息的错误对象将会被传播。Lua本身只会生成错误信息为字符串的错误，但是程序可能会产生以任意类型的值作为错误对象的错误。处理此类错误就是Lua程序或主程序的任务。因为历史原因，错误对象常被称为错误信息，即便它不一定是一个字符串。  

当你使用*xpcall*（或C中的*lua_pcall*）时你需要定义一个出错时调用的信息处理器。这个函数在调用时接受源错误对象并返回一个新的错误对象。出错时它在释放栈之前被调用，所以它可以获得更多的与错误相关的信息，例如检查栈或回溯栈数据。信息处理器也会在保护模式下调用；所以，信息处理器中产生的错误将会再次调用信息处理器。如果多次发生这种循环，Lua将会终止它并返回一个适当的信息。信息处理器只会在产生常规运行时错误时被调用。他不会在产生内存分配错误时或产生析构错误以及其它信息处理器出错时被调用。  

Lua还提供了警告系统(详见warn节)，与错误不同，警告不会对程序运行产生任何干扰。他们通常只会生成一个消息给用户，这种行为可以在C中更改（详见lua_setwarnf节）。  