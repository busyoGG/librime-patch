# librime 补丁

## 简介

librime: 修复 rime 漏字现象 

fcitx5: 修复英文锁定 bug 以及 Electron Wayland 无法删除第一个预编辑字母的 bug (niri环境测试)

## 使用方法

### rime 漏字
[fix_input.patch](fix_input.patch)

```
# 首次执行 克隆 librime 仓库
git clone https://github.com/rime/librime.git
cd librime

# 切换到特定提交（patch基于该提交制作
git checkout 0ecfc9c

# 首次执行 引入插件
cd plugins
git clone https://github.com/hchunhui/librime-lua
git clone https://github.com/lotem/librime-proto
git clone https://github.com/rime/librime-predict
git clone https://github.com/lotem/librime-octagram
cd ..

# 首次不执行（按需执行） 用于重置代码
git reset --hard 0ecfc9c

# 应用补丁
git apply path/to/fix_input.patch

# 编译安装
make -j$(nproc) && sudo make install
```

### 英文锁定
[fix_waylandimserverv2_bug.patch](fix_waylandimserverv2_bug.patch)

```
# 首次执行 克隆 fcitx5 仓库
git clone https://github.com/fcitx/fcitx5.git
cd fcitx5
# 应用补丁
git apply path/to/fix_waylandimserverv2_bug.patch

# 编译安装
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=/usr
make -j$(nproc)
sudo make install
```

## 演示

### 漏字
![](./res/input_fix.gif)

### 英文锁定
![](./res/caps_fix.gif)
