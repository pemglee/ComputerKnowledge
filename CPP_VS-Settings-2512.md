# Microsoft Visual Studio Setup

## Overview

## Microsoft Visual Studio Community 2026

项目演示

+ Project_Name: "VSSetup"

+ Location: "C:\Workspace\workspaces\CppWrkspces\lessons\src\ProjFromI8\ChernoCpp"

+ Solution_Name: "VSSetup"

  [ ] Place solution and project in the same directory.

+ Solution Property Pages展示

  ![Solution Property Pages展示](./images/MSVisualStudio-SolutionProperties-2025-12-25%20204316.png)

+ Project Property Pages展示
  
  ![Project Property Pages展示](./images/MSVisualStudio-ProjPropertiesDflt-2025-12-25%20203840.png)

  "Configuration":"All Configurations", "Platform":"All Platforms"

  + "Configuration Properties"

    + General

      ~~"Target Platform":"Windows 10"~~
      ~~"Windows SDK Version":"10.0.15063.0"~~
      "Output Directory":"$(SolutionDir)bin\$(platform)\$(Configuration)" 
      ![](./images/MSVisualStudio-ProjProperties-OutDir-2025-12-25%20203840.png)
      
      "Intermediate Directory":"$(SolutionDir)bin\intermediates\$(platform)\$(Configuration)"


### 目录结构

+ [D] "VSSetup", 解决方案目录

  + [D] ".vs"

  + [D] "VSSetup", 项目目录

    + 

  + [F] "VSSetup.slnx", 解决方案文件

    ```xml
    <Solution>
      <Configurations>
        <Platform Name="x64" />
        <Platform Name="x86" />
      </Configurations>
      <Project Path="VSSetup/VSSetup.vcxproj" />
    </Solution>
    ```