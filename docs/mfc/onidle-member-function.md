---
title: OnIdle 成員函式
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: 7b3f2fbeac6ae356003abf12b5df4c54c8bb327a
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175129"
---
# <a name="onidle-member-function"></a>OnIdle 成員函式

當正在不處理任何 Windows 訊息時，架構會呼叫[CWinApp](../mfc/reference/cwinapp-class.md)成員函式[OnIdle](../mfc/reference/cwinapp-class.md#onidle) （MFC 程式庫參考中所述）。

覆寫 `OnIdle` 以執行背景工作。 預設版本會更新使用者介面物件 (例如工具列按鈕) 的狀態，以及執行清除架構在其作業期間建立的暫存物件。 下圖說明沒有訊息在佇列中時，訊息迴圈如何呼叫 `OnIdle`。

![訊息迴圈處理序](../mfc/media/vc387c1.gif "訊息迴圈處理序") <br/>
訊息迴圈

如需您可以在閒置迴圈中執行的詳細資訊，請參閱[閒置迴圈處理](../mfc/idle-loop-processing.md)。

## <a name="see-also"></a>另請參閱

[CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)
