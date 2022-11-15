# tg

## 结构

项目总体称为“应用”（app），分立的功能称为“模块”（module）。

# Git

模块通过`git submodule`子模块功能维护。

## 克隆项目

在克隆项目时需要添加`--recurse-submodules`选项：

```shell
git clone --recurse-submodules https://github.com/mlanfe/tg
```

## 添加模块

```shell
git submodule add <url> <path>
```

其中`url`是模块的 Git 地址，`path`是模块存放在应用中的路径。

目前规范将模块放在`lib/modules`下。示例：

```shell
git submodule https://github.com/mlanfe/tstModule lib/modules/tstModule
```

然后进入子模块目录，初始化当前分支：

```shell
git checkout master
```

## 更新模块

使用`update`获取信息：

```shell
git submodule update
```

拉取每一个子模块的变更：

```shell
git submodule foreach 'git pull'
```

# 开发

## 模块

模块需要在其目录下提供一个`module`变量，然后在`lib/modules/index.dart`中添加到`modules`数组。

可以通过添加启动参数的方式设置初始化路由。示例：

```shell
flutter run --dart-define="route=/tst"
```



