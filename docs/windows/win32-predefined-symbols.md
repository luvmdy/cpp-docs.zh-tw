---
title: Win32 預先定義的符號
ms.date: 11/04/2016
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
ms.openlocfilehash: 703e00ebcf50c987fe3a0a9399cd7497bb9c95f8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434693"
---
# <a name="win32-predefined-symbols"></a>Win32 預先定義的符號

這些符號定義在 Win32 的標頭檔，並支援標準的 Windows 應用程式函數和動作。 常見的 UI 項目主要用於這些符號。 當您使用資源編輯器中的控制項時，這些符號會出現在[屬性 視窗](/visualstudio/ide/reference/properties-window)通用控制項相關聯。 比方說，如果您的工具列應該會顯示應用程式圖示，圖示會與相關聯的符號 IDI_SMALL 中**屬性視窗**。

|||
|-|-|
|IDABORT|控制： 對話方塊的 [中止] 按鈕|
|IDC_STATIC|在對話方塊中的控制項： 靜態文字|
|IDCANCEL|控制： 對話方塊的 [取消] 按鈕|
|IDD_ABOUTBOX，而|關於對話方塊 對話方塊中： 產品|
|IDI_PROJECTNAME|圖示： 目前的專案圖示|
|IDI_SMALL|圖示︰ 目前專案小圖示|
|IDIGNORE|使用對話方塊上的 [忽略] 按鈕所使用的控制項：|
|IDM_ABOUT|功能表項目： 搭配說明...關於...|
|IDM_EXIT|功能表項目： 搭配檔案...結束...|
|IDNO|控制： 對話方塊的 [無] 按鈕|
|IDOK|控制項： 對話方塊 [確定] 按鈕|
|IDRETRY|控制： 對話方塊的 [重試] 按鈕|
|IDS_APP_TITLE|字串： 目前的應用程式名稱|
|IDYES|控制： 對話方塊 [是] 按鈕|

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)<br/>
[符號：資源識別項](../windows/symbols-resource-identifiers.md)