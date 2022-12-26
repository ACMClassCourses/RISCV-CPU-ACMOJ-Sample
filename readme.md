# RISCV-CPU-ACMOJ-Sample

This is a sample repo for RISC-V CPU simulation on ACMOJ.

1. OJ 仅需要两个文件夹：`sim` 和 `src` 即可完成模拟：``sim``  中存放 ``testbench.v``， ``src`` 中存放你的 CPU 设计以及 uart、内存等辅助模块。本 repo 中给出的这两个文件夹与 [ACMClassCourses/RISCV-CPU: MS108 Course Project, SJTU ACM Class. (github.com)](https://github.com/ACMClassCourses/RISCV-CPU/tree/main/riscv) 中给出的几乎完全一致，唯一区别在于 OJ 的 ``testbench.v`` 里不会执行波形输出（即上述 repo 中 ``testbench.v`` 里的 29 行、30 行的 ）``dumpfile("test.vcd"); dumpvars(0, testbench);`` 是没有的。同时，31 行的在 300000000 步后停止的限制也被移除了。理论上，您只要使用本 repo 作为模版，将你自己写的文件放入 src 文件夹即可提交 OJ，无需任何改动。
2. 请手动选择评测语言为 ``Git (Verilog)``。
3. 如果你持续遭遇 WA 或 RE，请考虑检查如下几点：
   - 您是否修改过上述 ``testbench.v`` （如果打开波形输出 stdout 会有额外信息，自然会 WA）
   - 您是否修改过 ``src\common\block_ram\block_ram.v`` （OJ 是从当前目录的 ``test.data`` 读取内存信息的）
   - 您的 repo 中是否有多余文件：OJ 在模拟的时候是会用上 src 里的所有 .v 文件的，repo 里最好只放需要的模块，以免造成模块名重复之类的问题；
   - 您的 include: 很多同学会包含 ``define.v`` 这个文件来定义所有模块共用的设计，比如寄存器位宽等。OJ 将 include 路径定义为整个 ``src`` 文件夹，所以你的  ``define.v`` 必须平铺在 ``src`` 文件夹下，不能在别的地方，也不能在 ``src`` 的子文件夹的什么位置。（如果你知道我在说什么，你当然也可以 ``include 'def/define.v' ``）
   - 您的 iverilog 版本 与 您遵守了哪个版本的 IEEE 标准 Verilog 硬件描述语言（参考主页参数，本 Readme 发布时我们采用的是 iverilog 10.3, IEEE 1364-2005）。

