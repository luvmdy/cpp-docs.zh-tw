---
title: 將 RichEdit 1.0 控制項與 MFC 一起使用
ms.date: 11/04/2016
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
ms.openlocfilehash: 080ad995b9c7a041337d9b296d6ef8906e7f20ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468311"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>將 RichEdit 1.0 控制項與 MFC 一起使用

若要使用 RichEdit 控制項，您必須先呼叫[AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2)載入 RichEdit 2.0 控制項 (RICHED20。DLL)，或呼叫[AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit)載入較舊的 RichEdit 1.0 控制項 (RICHED32。DLL)。

您可以使用目前[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)類別與較舊的 RichEdit 1.0 控制項，但`CRichEditCtrl`只設計來支援 RichEdit 2.0 控制項。 RichEdit 1.0 和 RichEdit 2.0 都非常類似，因為大部分的方法就會運作;不過請注意有一些差異，因此有些方法可能會無法正確運作，或完全無法運作的 1.0 和 2.0 控制項之間。

## <a name="requirements"></a>需求

MFC

## <a name="see-also"></a>另請參閱

[對話方塊編輯器的疑難排解](../windows/troubleshooting-the-dialog-editor.md)<br/>
[對話方塊編輯器](../windows/dialog-editor.md)