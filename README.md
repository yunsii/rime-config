# Rime 定制

## 功能特性

- [rime-ice](https://github.com/iDvel/rime-ice)
- [小鹤双拼](https://flypy.cc/#/up)
- 只显示双拼编码
- 仿微信输入皮肤

## 如何使用？

### Windows

使用[小狼毫 Weasel](https://github.com/rime/weasel) 输入法，用户文件夹可通过右键直接打开。

- 通过 `git clone git@github.com:iDvel/rime-ice.git --depth 1` 将 [rime-ice](https://github.com/iDvel/rime-ice) 仓库同步到本地
- 将 rime-ice 文件夹中除了 .git 文件夹的内容通过同步到用户文件夹中，冲突文件直接覆盖即可
- 通过 `git clone git@github.com:yunsii/rime-config.git --depth 1` 将本仓库同步到本地
- 将该仓库中的 `/config` 文件夹下的所有文件直接粘贴到用户文件夹下，遇到同名文件直接覆盖即可

### Linux

经测试，最后选择了 [fcitx5-rime](https://github.com/fcitx/fcitx5-rime) 做为 Linux 下的 RIME 输入法。值得注意的是[该版本输入法 UI 由 Fcitx 控制](https://github.com/fcitx/fcitx5-rime/issues/119)。由于默认的主题实在是太复古了，现在暂时先使用 [fcitx5-nord](https://github.com/tonyfettes/fcitx5-nord) 主题，之后会尝试定制一个主题。

该输入法在 Linux 下默认配置文件夹为 [`~/.local/share/fcitx5/rime`](https://github.com/fcitx/fcitx5-rime/issues/61#issuecomment-1649779614)，安装方式同 Windows 下的操作。此外，如果碰到了以下情况：

- 按键预上屏但是光标不跟着移动（可能是缺陷？）
- 只想使用内联的输入方式

可通过[禁用 Preedit Mode 解决](https://github.com/fcitx/fcitx5-rime/issues/81)，方式如下：

![preedit-mode](./resources/preedit-mode.png)

### Android

此前使用过 fcitx5-rime 的经验，让我最后选择了 [fcitx5-android](https://github.com/fcitx5-android/fcitx5-android)，也测试了一下 [trime](https://github.com/osfans/trime)，好像没有 fcitx5-android 好用，而且目前还不支持 Google Play 直接安装。

值得注意的是以为安装 fcitx5-android 后选择双拼就能用了，后来从[怎么在fcitx-android上安装？](https://github.com/iDvel/rime-ice/issues/978)找到文章[最后一块拼图：在Android手机上使用Rime输入法](https://1900.live/last-puzzle-android-rime-input/)才完全弄明白怎么个用法。

踩完坑现在着重提几点注意事项：

- 如果主程序找到 Rime 插件[可能是主程序没有查看程序列表](https://github.com/fcitx5-android/fcitx5-android/issues/410)
- 手动同步时只需要同步 rime-ice 相关的配置即可，实测发现如果也复制了 rime-config 的配置会导致程序异常，可能是部分配置不兼容
- 输入法主程序要让词库生效一定要主动同步一下

## 用户词典同步

参考官方指南中关于[同步用戶資料](https://github.com/rime/home/wiki/UserGuide#%E5%90%8C%E6%AD%A5%E7%94%A8%E6%88%B6%E8%B3%87%E6%96%99)说明，先自定义一个有意义的 ID，目前使用的格式是`<地点>-<设备>-<系统>`。

然后通过**用户资料同步**将当前输入法配置导出到 sync 文件中，我最后选择的网盘是坚果云，直接通过坚果云的**同步该文件夹**功能将 sync 文件夹云同步即可。

根据官方说法，资料同步后会将各子文件的用户词典合并，这样就达到了预期的效果。

## TODO

- 定制 fcitx5 主题
- 支持双拼编码 + 全拼编码显示
- 支持 Node.js 脚本自动化
- 词库手动同步到自动同步
