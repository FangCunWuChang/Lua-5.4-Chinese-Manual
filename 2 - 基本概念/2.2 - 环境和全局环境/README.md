### 2.2 – 环境和全局环境  
如不久后我们将在3.2节和3.3.3节中提到的那样，任何可用名称（目前未与任何声明绑定的名称）的声明`var`都会在语法层面上被转换为`_ENV.var`。此外，每块代码都会在一个全局的local变量`_ENV`的范围内编译（详见3.3.2节），所以`_ENV`在任何一个代码块中都不能作为可用名称使用。  

尽管`_ENV`全局变量和可用名称转换是真实存在的，`_ENV`是一个完全合法的名称。你也可以使用该名称定义新的变量和参数。每个可用名称的引用都会使用当前位置可用的`_ENV`，每个`_ENV`的作用范围遵循Lua变量作用范围规则（详见3.5节）。  

`_ENV`变量所引用的表被称为环境。  

Lua维护了一个被称为全局环境的重要的环境。这个值在C注册表中与一个特殊的索引相关联（详见4.3节）。在Lua中，全局变量`_G`被初始化为全局环境。(`_G`从来不会被Lua虚拟机内部使用，所以更改它的值只会影响你自己的代码的运行)  

当Lua载入一个代码块时，它的`_ENV`变量的默认值会被初始化为全局环境（详见load节）。因此，在默认情况下，Lua代码中的可用名称在定义时会被加入全局环境，所以他们也被称为全局变量。此外，所用的标准库都会被加载进全局环境并且一些函数也会在其中执行。你可以使用`load`（或`loadfile`）来加载一个具有独立环境的代码块。（在C中，在载入代码块后需要修改首个upvalue的值；详见*lua_setupvalue*节）  