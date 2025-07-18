# librime 补丁

## 简介

rime漏字现象以及 Caps_Lock 导致无法返回中文输入的临时解决方案

## 使用方法

```
# 第一次执行 克隆 librime 仓库
git clone https://github.com/rime/librime.git
cd librime

# 切换到特定提交（patch基于该提交制作
git checkout 1a1fbbe

# 首次执行 引入插件
cd plugins
git clone https://github.com/hchunhui/librime-lua
git clone https://github.com/lotem/librime-proto
git clone https://github.com/rime/librime-predict
git clone https://github.com/lotem/librime-octagram
cd ..

# 首次不执行（按需执行） 用于重置代码
git reset --hard 1a1fbbe

# 应用补丁
git apply path/to/fix_input.patch

# 编译安装
rm -rf ./build && make -j$(nproc) && sudo make install
```

## 演示

### 漏字
![](./res/input_fix.gif)

### 大写锁定
![](./res/caps_fix.gif)
