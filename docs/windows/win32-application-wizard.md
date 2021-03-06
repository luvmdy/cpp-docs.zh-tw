---
title: Win32 應用程式精靈
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.win32.overview
helpviewer_keywords:
- Win32 Application Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 1b89ae1c91536956924090f4a5eafa883053ed7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526150"
---
# <a name="win32-application-wizard"></a>Win32 應用程式精靈

Visual C++ Win32 應用程式精靈可讓您建立四種類型的專案 (請見下表標題列)。 在每個案例中，您都可以為開啟的專案類型指定適合的其他選項。 下表指出每種應用程式類型可使用的選項。

|支援類型|主控台應用程式|可執行檔 (Windows) 應用程式|動態連結程式庫|靜態程式庫|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**空專案**|是|是|是|否|
|**匯出符號**|否|否|是|否|
|**先行編譯標頭**|否|否|否|是|
|**ATL 支援**|是|否|否|否|
|**MFC 支援**|是|否|否|是|

## <a name="overview"></a>總覽

這個精靈頁面說明目前適用於您建立之 Win32 應用程式的專案設定。 根據預設，設定下列選項：

- 專案是 Windows 應用程式。

- 專案不是空的。

- 專案不包含匯出符號。

- 專案不使用先行編譯的標頭檔 (這個選項僅適用於靜態程式庫專案)。

- 專案對 MFC 或 ATL 都不支援。

若要變更這些預設值，請按一下精靈左欄的 [[應用程式設定]](../windows/application-settings-win-32-project-wizard.md) 索引標籤，進行必要的變更。

一旦建立了 Windows 桌面應用程式，就可以使用 [泛型](../ide/generic-cpp-class-wizard.md) 程式碼精靈加入泛型 C++ 類別。 您可以加入其他項目，例如 HTML 檔案、標頭檔、資源或文字檔案。

> [!NOTE]
> 您不能加入 ATL 類別，而 MFC 類別只能加入支援 MFC 的那些 Windows 桌面應用程式類型 (請見上表)。

您可以在 **方案總管**中檢視精靈為專案建立的檔案。 更多精靈為您的專案所建立之檔案的相關資訊，請參閱專案所產生的檔案， `ReadMe.txt`。 如需檔案類型的詳細資訊，請參閱 [為 Visual C++ 專案建立的檔案類型](../ide/file-types-created-for-visual-cpp-projects.md)。

## <a name="see-also"></a>另請參閱

[建立空的 Windows 傳統型應用程式](../windows/creating-an-empty-windows-desktop-application.md)<br/>
[Visual C++ 專案類型](../ide/visual-cpp-project-types.md)