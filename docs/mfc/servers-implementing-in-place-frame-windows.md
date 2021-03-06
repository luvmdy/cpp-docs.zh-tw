---
title: 伺服器：實作就地編輯框架視窗
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
ms.openlocfilehash: 4973db6274ce800e8e1fc413ffbfd44a107a64b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637628"
---
# <a name="servers-implementing-in-place-frame-windows"></a>伺服器：實作就地編輯框架視窗

本文說明如果不使用應用程式精靈來建立您的伺服器應用程式，則必須實作自己的視覺化編輯伺服器應用程式的就地框架視窗。 除了遵循本文中所述的程序，您可以使用現有的就地框架視窗類別，從應用程式精靈產生應用程式或 Visual c + + 提供的範例。

#### <a name="to-declare-an-in-place-frame-window-class"></a>宣告就地框架視窗類別

1. 從 `COleIPFrameWnd` 衍生就地框架視窗類別。

   - 在類別標頭檔中使用 DECLARE_DYNCREATE 巨集。

   - 在您的類別實作 (.cpp) 檔案中使用 IMPLEMENT_DYNCREATE 巨集。 如此可讓架構建立此類別物件。

1. 宣告框架視窗類別中的 `COleResizeBar` 成員。 如果您要支援在伺服器應用程式中就地調整大小，就必須如此。

   宣告`OnCreate`訊息處理常式 (使用**屬性**視窗)，然後呼叫`Create`針對您`COleResizeBar`成員，如果您已定義它。

1. 如果您有工具列，請在框架視窗類別中宣告 `CToolBar` 成員。

   當伺服器作用中時，請覆寫 `OnCreateControlBars` 成員函式來建立工具列。 例如: 

   [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

   請參閱步驟 5 之後關於此程式碼的討論。

1. 這包括主要 .cpp 檔案中的就地框架視窗類別標頭檔。

1. 在您的應用程式類別的 `InitInstance` 中，呼叫文件樣板物件的 `SetServerInfo` 函式以指定用來開啟和就地編輯的資源與就地框架視窗。

中的一系列的函式呼叫**如果**陳述式會建立工具列資源從提供的伺服器。 此時，工具列是容器的視窗階層架構的一部分。 由於這個工具列是衍生自 `CToolBar`，除非您變更擁有者，否則會將其訊息傳遞給至擁有者、容器應用程式的框架視窗。 因此對 `SetOwner` 的呼叫是必要的。 此呼叫會將傳送命令的視窗變更為伺服器的就地框架視窗，使訊息傳遞至伺服器。 如此可讓伺服器回應所提供之工具列的作業。

工具列點陣圖的 ID 應該與在您的伺服器應用程式中所定義的其他就地資源相同。 請參閱[功能表和資源： 伺服器加入](../mfc/menus-and-resources-server-additions.md)如需詳細資訊。

如需詳細資訊，請參閱 < [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)， [COleResizeBar](../mfc/reference/coleresizebar-class.md)，並[Coleresizebar](../mfc/reference/cdoctemplate-class.md#setserverinfo)中*類別庫參考*.

## <a name="see-also"></a>另請參閱

[伺服器](../mfc/servers.md)<br/>
[伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)<br/>
[伺服器：實作伺服器文件](../mfc/servers-implementing-server-documents.md)<br/>
[伺服器：伺服器項目](../mfc/servers-server-items.md)

