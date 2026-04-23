---
title: WSL学习
markmap:
  colorFreezeLevel: 24
---

# wsl -- Windows Subsystem Linux

## Overview

## commands

+ `dism.exe`  
  + 部署映像服务和管理工具，用于管理Windows映像和服务

  + `/online`
    + 指定要操作的是当前正在运行的操作系统
  + `/enable-feature`
    + 启用一个特定的Windows功能
  + `/featurename:Microsoft-Windows-Subsystem-Linux`
    + 启用 WSL 功能
  + `/all`
    + 启用所有相关的子功能
  + `/norestart`
    + 不用重启计算机，即使某些操作需要重启

+ `dism.exe`
  + `/online`
  + `/enable-feature`
  + `/featurename:VirtualMachinePlatform`
    + 启用虚拟机平台，WSL2依赖该功能
  + `/all`
  + `/norestart`

+ `dism.exe`
  + `/online`
  + `/enable-feature`
  + `/featurename:HypervisorPlatform`
    + 启用Hyper-V功能
  + `/all`
  + `/norestart`

+ `dism.exe`
  + `/online`
  + `/Get-Features`

+ `wsl`
  + `--install`

+ `wsl`
  + `--set-default-version 2`

+ `wsl`
  + `--update`


+ `wsl`
  + `--list`
  + `--online`
  + 罗列所有的在线的可安装操作系统
    + 2026-Apr-22
      
      ```batch
      C:\Workspace>wsl --list --online
      The following is a list of valid distributions that can be installed.
      Install using 'wsl.exe --install <Distro>'.
      
      NAME                            FRIENDLY NAME
      AlmaLinux-8                     AlmaLinux OS 8
      AlmaLinux-9                     AlmaLinux OS 9
      AlmaLinux-Kitten-10             AlmaLinux OS Kitten 10
      AlmaLinux-10                    AlmaLinux OS 10
      Debian                          Debian GNU/Linux
      FedoraLinux-43                  Fedora Linux 43
      FedoraLinux-42                  Fedora Linux 42
      SUSE-Linux-Enterprise-15-SP7    SUSE Linux Enterprise 15 SP7
      SUSE-Linux-Enterprise-16.0      SUSE Linux Enterprise 16.0
      Ubuntu                          Ubuntu
      Ubuntu-24.04                    Ubuntu 24.04 LTS
      Ubuntu-22.04                    Ubuntu 22.04 LTS
      Ubuntu-20.04                    Ubuntu 20.04 LTS
      archlinux                       Arch Linux
      eLxr                            eLxr 12.12.0.0 GNU/Linux
      kali-linux                      Kali Linux Rolling
      openSUSE-Tumbleweed             openSUSE Tumbleweed
      openSUSE-Leap-16.0              openSUSE Leap 16.0
      OracleLinux_7_9                 Oracle Linux 7.9
      OracleLinux_8_10                Oracle Linux 8.10
      OracleLinux_9_5                 Oracle Linux 9.5
      openSUSE-Leap-15.6              openSUSE Leap 15.6
      SUSE-Linux-Enterprise-15-SP6    SUSE Linux Enterprise 15 SP6
      ```

+ `wsl`
  + `--list` / `-l`
  + `--verbose` / `-v`
  + 罗列已安装的子系统
    + 2026-Apr-22

      ```batch
      C:\Workspace>wsl  -l -v
        NAME              STATE           VERSION
      * AlmaLinux9        Stopped         2
        KaliLinuxAll25    Stopped         2
      
      C:\Workspace>
      ```

+ `wsl`
  + `--export` 子系统名 导出文件.tar
  + 导出/备份子系统

    ```batch
    C:\Workspace>wsl --export KaliLinuxAll25     C:\Workspace\VirtualMachine\KaliLinuxAll_250422_01.tar
    Export in progress, this may take a few minutes. (809 MB): ./tmp/    qtsingleapplication-59e7-0: pax format cannot archive sockets: ./tmp/    qtsingleapplication-b8a4-0: pax format cannot archiv (39802 MB)
    
    The operation completed successfully.
    ```

+ `wsl`
  + `--unregister` 子系统名
  + 注销子系统
  
    ```batch
    C:\Workspace>wsl --unregister KaliLinuxAll25
    Unregistering.
    The operation completed successfully.
    ```

+ `wsl`
  + `--import` 子系统名 安装目录 导出文件.tar
  + 导入/恢复子系统

    ```batch
    wsl --import KaliLinuxAll25 C:\Workspace\VirtualMachine\Kali\Kali C:\Workspace\VirtualMachine\KaliLinuxAll_251220.tar
    ```

+ `wsl`
  + `--distribution` / `-d` 子系统名
  + `--user` / `-u` 登录用户名
  + 启动系统
    ```batch
    wsl --distribution KaliLinuxAll25 --user edgar
    ```