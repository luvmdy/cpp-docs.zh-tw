---
title: 格式化自訂建置步驟或建置事件的輸出
ms.date: 08/27/2018
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
ms.openlocfilehash: 333d3af92da2388b42f51f197dee5da82900022d
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330407"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>格式化自訂建置步驟或建置事件的輸出

如果已正確格式化自訂建置步驟或建置事件的輸出，使用者會獲得下列好處：

- 會在 [輸出] 視窗計算警告和錯誤。

- 輸出會出現在 [工作清單] 視窗。

- 按一下 [輸出] 視窗中的輸出會顯示適當的主題。

- [工作清單] 視窗或 [輸出] 視窗中已啟用 F1 作業。

輸出的格式應該是：

> {<em>filename</em>**(**<em>line#</em> \[**,** <em>column#</em>]**)** &#124; *toolname*} **:** \[ <em>any text</em> ] {**error** &#124; **warning**} <em>code+number</em>**:**<em>localizable string</em> \[ <em>any text</em> ]

其中：

- {*a* &#124; *b*} 是 *a* 或 *b* 的選擇。

- \[<em>item</em>] 是選擇性字串或參數。

- **粗體**表示常值。

例如: 

> C:\\*sourcefile.cpp*(134) : 錯誤 C2143: 語法錯誤 : 在 '}' 之前遺漏 ';'
>
> LINK : 嚴重錯誤 LNK1104: 無法開啟檔案 '*'somelib.lib*'

## <a name="see-also"></a>另請參閱

[了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)