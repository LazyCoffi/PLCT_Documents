# 构建情况汇总

该文档用于记录已进行的构建情况记录

## 构建成功
### libipt
- 原构建情况：excluded
- 原构建失败原因：Exclusive arch不包括riscv64
- 解决方案：添加riscv64支持
- 使用osc构建
- 已提交PR

### openblas
- 原构建情况：failed
- 原构建失败原因：spec文件未添加构建目标riscv64
- 解决方案：判断当环境为riscv64时，设置构建目标为riscv general
- 使用rpmbuild本地构建
- 已提交PR

## 构建失败（failed）
### kmod-kvdo
- 原构建情况：excluded
- 原构建失败原因：Exclusive arch不包括riscv64
- 操作流程：添加riscv64支持，构建成功。但由于环境变动导致构建失败
- 错误：error: Couldn't exec /usr/lib/rpm/openEuler/brp-digest-list: No such file or directory
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/kmod-kvdo/standard_riscv64/riscv64)

### dietlibc
- 原构建情况：excluded
- 原构建失败原因：Exclusive arch不包括riscv64
- 操作流程：添加riscv64支持，构建后构建失败
- 错误：*** unknown architecture, please fix Makefile.  Stop.
- 错误原因：可能是包暂时不支持riscv64环境
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/dietlibc/standard_riscv64/riscv64)

### latrace
- 原构建情况：excluded
- 构建失败原因：Exclusive arch不包括riscv64
- 操作流程：添加riscv64支持，构建后构建失败
- 错误：src/config.h:365:53: error: unknown type name 'La_regs'
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/latrace/standard_riscv64/riscv64)

### libqmi
- 原构建情况：broken
- 构建失败原因：obs配置文件_service未正确指向源码库对应提交
- 操作流程：修改_service文件，构建后状况为excluded，添加riscv64后构建失败
- 错误：error: Couldn't find `libmbim-glib` >= 1.18.0. Install it, or otherwise configure using --disable-mbim-qmux to disable the QMI over MBIM QMUX service
- 错误原因：依赖包libmbim缺失，追踪包libmbim构建状态为excluded,其依赖包为python3-unversioned-command,python包暂时处于循环依赖问题未能解决
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/libqmi/standard_riscv64/riscv64)

### libunwind
- 原构建情况：excluded
- 构建失败原因：Exclusive arch缺少riscv64
- 操作流程：添加riscv64后构建失败
- 错误：checking for ELF helper width... configure: error: Unknown ELF target: riscv64
- 错误原因：可能是ELF暂时缺少riscv64构建目标
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/libunwind/standard_riscv64/riscv64)

### libwd
- 原构建情况：excluded
- 构建失败原因：Exclusive arch缺少riscv64
- 操作流程：添加riscv64后构建失败
- 错误：no compliant workers (constraints mismatch hint: linux:version)
- 错误原因：系统环境不匹配
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/libwd/standard_riscv64/riscv64)

### linux-sgx-driver
- 原构建情况：excluded
- 构建失败原因：Exclusive arch缺少riscv64
- 操作流程：添加riscv64后构建失败
- 错误： fatal error: asm/msr-index.h: No such file or directory
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/linux-sgx-driver/standard_riscv64/riscv64)

### luajit
- 原构建情况：excluded
- 构建失败原因：Exclusive arch缺少riscv64
- 操作流程：添加riscv64后构建失败
- 错误： #error "No support for this architecture (yet)"
- 错误原因：包暂时不支持该系统加购
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/luajit/standard_riscv64/riscv64)

### lxc
- 原构建情况：excluded
- 构建失败原因：Exclusive arch缺少riscv64
- 操作流程：添加riscv64后构建失败
- [错误日志](https://build.openeuler.org/package/live_build_log/home:ChengZou:branches:openEuler:Mainline:RISC-V/lxc/standard_riscv64/riscv64)

## 构建失败（unresolvable）
### linux-sgx
- 缺失依赖包：ocami, python,createrepo_c

### libxsmm
- 缺失依赖包：openblas

### libsmbios
- 缺失依赖包：valgrind

### libkae
- 缺失依赖包libwd

### lcr
- 缺失依赖包lxc