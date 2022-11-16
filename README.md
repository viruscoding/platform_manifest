# platform_manifest

精简aosp源码树,提供一个最小的编译环境,用于编译aapt、dexdump、fastboot等工具.

manifest来自：`https://android.googlesource.com/platform/manifest/+/refs/heads/platform-tools-33.0.3/default.xml`

已完成aapt、aapt2、dexdump编译

## mac环境准备

创建大小写敏感磁盘

```
# 创建大小写敏感磁盘
hdiutil create -volname "android" -type SPARSE -fs 'Case-sensitive Journaled HFS+' -size 50g android.dmg
# 挂载
hdiutil attach android.dmg.sparseimage -mountpoint /Volumes/android
# 卸载
hdiutil detach /Volumes/android

```

## 开始构建

### 安装repo

```
mkdir ~/bin
PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

### 初始化repo项目

```
# 进入工作目录
cd /Volumes/android && mkdir platform-tools && cd platform-tools
# 初始化并同步源码树
repo init -u https://github.com/viruscoding/platform_manifest.git -b platform-tools-33.0.3 --depth 1
repo sync
```
