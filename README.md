# librime 补丁

## 简介

修复 rime 漏字现象 

## 使用方法

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
rm -rf ./build && make -j$(nproc) && sudo make install
```

## 演示

### 漏字
![](./res/input_fix.gif)

### 大写锁定
![](./res/caps_fix.gif)
