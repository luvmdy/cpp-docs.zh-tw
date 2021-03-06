---
title: -可覆寫註解
ms.date: 11/04/2016
helpviewer_keywords:
- Overridables comment in MFC source files
- MFC source files, Overridables comment
- overriding, Overridables comment in MFC source files
- comments, MFC
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
ms.openlocfilehash: 9efba74676ba118659601522fc915bf25f607116
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554151"
---
# <a name="-overridables-comment"></a>// 可覆寫函式註解

MFC 類別宣告的 `// Overridables` 區段含有當您需要修改基底類別行為時，您可以在衍生類別中覆寫的虛擬函式。 這些虛擬函式的名稱通常是以「On」為開頭，不過並非絕對必要。 此處的函式是專門用來覆寫，經常會實作或提供某種「回呼」或「攔截」。 一般來說，這些成員是受到保護的。

在 MFC 中，純虛擬函式一定會放置在此區段。 C++ 中的純虛擬函式是以下一種形式：

`virtual void OnDraw( ) = 0;`

中的範例清單自類別`CStdioFile`，請在[註解的範例](../mfc/an-example-of-the-comments.md)，此清單包含沒有可覆寫區段。 類別`CDocument`，相反地，會列出大約 10 個可覆寫成員函式。

在一些類別中，您也可能會看到 `// Advanced Overridables` 註解。 這些是只有進階程式設計人員才應該嘗試覆寫的函式。 您可能永遠不需要覆寫這些函式。

> [!NOTE]
>  本文所述的慣例一般而言，也適合用於 Automation (先前稱為 OLE Automation) 方法和屬性。 Automation 方法與 MFC 作業類似。 Automation 屬性類似於 MFC 屬性。 Automation 事件 (支援 ActiveX 控制項，先前稱為 OLE 控制項) 與 MFC 可覆寫成員函式類似。

## <a name="see-also"></a>另請參閱

[使用 MFC 原始程式檔](../mfc/using-the-mfc-source-files.md)<br/>
[註解的範例](../mfc/an-example-of-the-comments.md)<br/>
[實作註解](../mfc/decrement-implementation-comment.md)<br/>
[建構函式註解](../mfc/decrement-constructors-comment.md)<br/>
[屬性註解](../mfc/decrement-attributes-comment.md)<br/>
[作業註解](../mfc/decrement-operations-comment.md)

