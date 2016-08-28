#vlfeat-0.9.20 vs2013平台下将vlfeat库编译成lib和dll库

  1. 新建vlfeat控制台应用程序，将vlfeat-0.9.20目录下的vl文件夹拷贝到~\vlfeat\vlfeat文件夹下；添加.c 和 .h 文件到工程中。
  2. 配置属性中的配置类型由“应用程序(.exe)” 改为 “动态库(.dll)”；字符集由“Unicode字符集” 改为“多字节字符集”
  3. 预处理器定义中添加
      ```
      VL_BUILD_DLL 、
      _CRT_SECURE_NO_WARNINGS 、
      __SSE2__ 、
      _SSE2_ 、
      __AVX__ 、
      ```
  4. error C4146 一元负运算符应用于无符号类型，结果仍为无符号类型：将C/C++--> 常规--> SDL检查改为否(/sdl-)
  5. 重新编译生成vlfeat.dll文件，将配置类型改为“静态库(.lib)” 生成 vlfeat.lib 文件
  6. 测试
      * 新建控制台应用程序
      * 添加vlfeat-0.9.20中vl文件夹路径；添加vlfeat.lib库
      * 测试代码

```cpp
    #include <iostream>
    #include "vl/generic.h"
    
    int _tmain(int argc, _TCHAR* argv[])
    {
	    VL_PRINT("Hello world!\n");
    
	    std::cout << "ok!" << std::endl;
	    return 0;
    }
```
    //输出
    Hello world!
    ok
