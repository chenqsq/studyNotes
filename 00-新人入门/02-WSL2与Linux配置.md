# 一、先确认你的系统版本

按：

```bash
win + r
```

输入：

```bash
winver
```

如果是：

* Windows 10 2004 及以上
* Windows 11

基本都能直接装。

---

# 二、最快安装方法（推荐）

## 1. 用管理员打开 PowerShell

开始菜单搜索：

```bash
PowerShell
```

右键：

```text
以管理员身份运行
```

---

## 2. 输入安装命令

直接执行：

```powershell
wsl --install
```

它会自动：

* 开启 WSL 功能
* 开启虚拟机平台
* 下载 Linux 内核
* 安装 Ubuntu
* 默认安装 WSL2

---

## 3. 重启电脑

执行完后重启。

---

## 4. 首次启动 Ubuntu

重启后会自动弹出 Ubuntu 终端。

设置：

```text
用户名
密码
```

密码输入时不会显示，这是正常的。

---

# 三、查看是否安装成功

输入：

```powershell
wsl -l -v
```

正常会看到：

```text
NAME      STATE           VERSION
Ubuntu    Running         2
```

说明已经是 WSL2。

---

# 四、如果 `wsl --install` 报错

有些精简版系统会缺组件。

可以手动开启：

## 1. 开启功能

管理员 PowerShell：

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

---

## 2. 重启

---

## 3. 设置 WSL2 为默认

```powershell
wsl --set-default-version 2
```

---

# 五、安装指定 Linux 发行版

查看可安装系统：

```powershell
wsl --list --online
```

比如：

```text
Ubuntu
Debian
kali-linux
openSUSE
```

安装：

```powershell
wsl --install -d Ubuntu
```

或者：

```powershell
wsl --install -d Debian
```

---

# 六、你后续开发会常用的命令

## 启动 Linux

```powershell
wsl
```

---

## 退出 Linux

```bash
exit
```

---

## 查看发行版

```powershell
wsl -l -v
```

---

## 关闭 WSL

```powershell
wsl --shutdown
```
