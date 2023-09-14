# acm_leetcode

## 环境配置

reference:

- https://blog.csdn.net/m0_70885101/article/details/131154332
- https://zhuanlan.zhihu.com/p/147366852?tdsourcetag=s_pctim_aiomsg
- 控制面板，卸载“LLVM”(之前学opengl下的，但是编译很慢)
- 之前装了mingw64，不用再装
- vscode配置文件

  - tasks.json，task是任务的意思，我们的编译和运行就是我们想要vscode执行的任务，为此我们要在tasks.json里写两个task：`Build`和 `Run`(这里为什么不是 `Compile`呢？是因为从源码到可执行的过程中不仅是 **编译(Compile)** ,还有预编译、链接等过程，用 **构建(Build)** 来表述更合适)。除了编译和运行，我们还需要进行 **调试(Debug)** ，这个就不是通过task来实现的了，而是通过 `launch.json`文件来实现。
  - cpp文件同目录下建了一个build文件夹存在exe文件
