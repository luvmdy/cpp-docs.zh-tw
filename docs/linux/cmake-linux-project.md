---
title: "在 Visual Studio 中設定 Linux CMake 專案 | Microsoft Docs"
ms.custom: 
ms.date: 10/25/2107
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8707b32-f90d-494d-ae0b-1d44425fdc25
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e3baa9b6e362f93e7b2cda59d34cabf87324292
ms.sourcegitcommit: 1b480aa74886930b3bd0435d71cfcc3ccda36424
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="configure-a-linux-cmake-project"></a>設定 Linux CMake 專案
  
**Visual Studio 2017 15.4 版**：當您安裝 Linux C++ 工作負載時，預設會選取適用於 Linux 的 CMake 支援。 您現在可以使用採用 CMake 的現有程式碼基底，而不必將它轉換成 Visual Studio 專案。 如果程式碼基底為跨平台，您可以從 Visual Studio 內將 Windows 和 Linux 鎖定為目標。 

本主題假設您對 Visual Studio 中的 CMake 支援有基本認識。 如需詳細資訊，請參閱 [Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)。 如需 CMake 本身的詳細資訊，請參閱 [Build, Test and Package Your Software With CMake](https://cmake.org/) (使用 CMake 建置、測試及封裝您的軟體)。

> [!NOTE] 
> Visual Studio 中的 CMake 支援需要 CMake 3.8 中所引進的伺服器模式支援。 如果您的套件管理員提供舊版的 CMake，您可以從來源建置 CMake 3.8 來解決此問題。



## <a name="open-a-folder"></a>開啟資料夾
若要開始使用，請從主功能表選擇 [檔案] | [開啟] | [資料夾]，或在命令列上鍵入 `devenv.exe <foldername>`。 您開啟的資料夾內應該有 CMakeLists.txt 檔案，以及您的原始程式碼。
下列範例顯示簡單的 CMakeLists.txt 檔案和 .cpp 檔案：

```cpp
// Hello.cpp

#include <iostream>;
 
int main(int argc, char* argv[])
{
    std::cout << "Hello" << std::endl;
}
```

CMakeLists.txt： 
```cmd
project (hello-cmake)
add_executable(hello-cmake hello.cpp)
```

## <a name="choose-a-linux-target"></a>選擇 Linux 目標
只要您開啟資料夾，Visual Studio 就會剖析 CMakeLists.txt 檔案，並指定 x86-Debug 的 Windows 目標。 若要以 Linux 為目標，請將專案設定變更為 Linux-Debug 或 Linux-Release。

根據預設，Visual Studio 會選擇清單中的第一部遠端系統 (在 [工具] | [選項] | [跨平台] | [連線管理員] 下)。 如果找不到遠端連線，系統會提示您建立一個連線。

指定 Linux 目標之後，您的來源會複製到 Linux 電腦。 然後會在 Linux 電腦上執行 CMake，以產生您專案的 CMake 快取。  

![在 Linux 上產生 CMake 快取](media/cmake-linux-1.png "在 Linux 上產生 CMake 快取")  

## <a name="debug-the-project"></a>偵錯專案  
若要在遠端系統上偵錯您的程式碼，請設定中斷點，在 [專案設定] 旁的工具列功能表中選取 CMake 目標作為啟動項目，然後按一下 [執行] (或按 F5)。

## <a name="configure-cmake-settings-for-linux"></a>設定適用於 Linux 的 CMake 設定
若要變更預設 CMake 設定，請從主功能表選擇 [CMake] | [變更 CMake 設定] | [CMakeLists.txt]，或在**方案總管**中以滑鼠右鍵按一下 CMakeSettings.txt，然後選擇 [變更 CMake 設定]。 Visual Studio 接著會在您的資料夾中建立新的檔案 `CMakeSettings.json`，並填入 [專案設定] 功能表項目中列出的預設組態。 下列範例顯示根據上一個程式碼範例之 Linux-Debug 的預設組態：

```json
{
      "name": "Linux-Debug",
      "generator": "Unix Makefiles",
      "remoteMachineName": "${defaultRemoteMachineName}",
      "configurationType": "Debug",
      "remoteCMakeListsRoot": "/var/tmp/src/${workspaceHash}/${name}",
      "cmakeExecutable": "/usr/local/bin/cmake",
      "buildRoot": "${env.LOCALAPPDATA}\\CMakeBuilds\\${workspaceHash}\\build\\${name}",
      "remoteBuildRoot": "/var/tmp/build/${workspaceHash}/build/${name}",
      "remoteCopySources": true,
      "remoteCopySourcesOutputVerbosity": "Normal",
      "remoteCopySourcesConcurrentCopies": "10",
      "cmakeCommandArgs": "",
      "buildCommandArgs": "",
      "ctestCommandArgs": "",
      "inheritEnvironments": [ "linux-x64" ]
}
```
`name` 值可以是您喜歡的任何值。 `remoteMachineName` 值指定以哪部遠端系統為目標 (如果有多部遠端系統)。 此欄位已啟用 IntelliSense 來協助您選取正確的系統。 `remoteCMakeListsRoot` 欄位指定專案來源將要複製到的遠端系統。 `remoteBuildRoot` 欄位是遠端系統上將產生組建輸出的位置。 該輸出也會在本機複製到 `buildRoot` 所指定的位置。

## <a name="building-a-supported-cmake-release-from-source"></a>從來源建置支援的 CMake 版本
您 Linux 電腦上所需的 CMake 最低版本為 3.8，而且該版本必須同時支援伺服器模式。 若要確認這會執行此命令：

```cmd
cmake --version
```

若要確認已啟用伺服器模式，請執行：

```cmd
cmake -E capabilities
```

在輸出中，尋找 “serverMode”:true。 請注意，即使您如下所述從來源編譯 CMake，還是必須在完成時檢查功能。 您的 Linux 系統可能具有防止伺服器模式啟用的限制。

若要在 Linux 系統殼層中開始從來源建置，請確定您的套件管理員是最新版本，而且您有 git 和 cmake 可用。 首先，複製 CMake 來源：

```cmd
sudo apt-get update
sudo apt-get install -y git cmake
git clone https://github.com/Kitware/CMake.git
cd CMake
```

接下來，確定您使用的是 Visual Studio 支援的 CMake 版本。 我們將積極追蹤 CMake 開發，但無法保證支援最新版本。 若要建置 3.9.0 (舉例來說)，請先執行：

```cmd
git checkout tags/v3.9.0
```

接下來，執行下列命令：

```cmd
mkdir out
cd out
cmake ../
make
sudo make install
```

上述命令會建置最新版的 CMake 並安裝到 /usr/local/bin。 執行此命令可確認版本為 >= 3.8，而且已啟用伺服器模式：

```cmd
/usr/local/bin/cmake –version
cmake -E capabilities
```

## <a name="see-also"></a>另請參閱
[使用專案屬性](../ide/working-with-project-properties.md)  
[Visual C++ 的 CMake 工具](../ide/cmake-tools-for-visual-cpp.md)