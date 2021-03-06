---
title: 變更符號標頭檔的名稱
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.header
helpviewer_keywords:
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
ms.openlocfilehash: 4d9aa350d0f680e975c68bf46ac066072df044cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432328"
---
# <a name="changing-the-names-of-symbol-header-files"></a>變更符號標頭檔的名稱

通常所有符號定義會儲存在`Resource.h`。 不過，您可能需要變更這 Include 檔案名稱，好讓您可以，比方說在相同目錄中處理多個資源檔。

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>變更資源符號標頭檔名稱

1. 在 [資源檢視](../windows/resource-view-window.md)，以滑鼠右鍵按一下.rc 檔，然後選擇[Resource Includes](../windows/resource-includes-dialog-box.md)從捷徑功能表。

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 在 **符號標頭檔**方塊中，輸入 include 檔案的新名稱。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[檢視資源符號](../windows/viewing-resource-symbols.md)<br/>
[預先定義的符號識別碼](../windows/predefined-symbol-ids.md)