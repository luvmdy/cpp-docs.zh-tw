---
title: "強制回應和非強制回應對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 982bb8f195c3744246addc18d66bee953914dde4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="modal-and-modeless-dialog-boxes"></a>強制回應和非強制回應對話方塊
您可以使用類別[CDialog](../mfc/reference/cdialog-class.md)來管理兩種類型的對話方塊：  
  
-   *強制回應對話方塊*，而這需要使用者回應之前繼續執行程式  
  
-   *非強制回應對話方塊*，其放置在螢幕和都可供使用，在任何時間，但允許其他使用者的活動  
  
 資源編輯和建立對話方塊範本的程序是相同的強制回應和非強制回應對話方塊。  
  
 建立一個對話方塊，為您的程式需要下列步驟：  
  
1.  使用[對話方塊編輯器](../windows/dialog-editor.md)設計對話方塊和建立其對話方塊範本資源。  
  
2.  建立對話方塊類別。  
  
3.  連接[對話方塊資源的控制訊息處理常式來](../windows/adding-event-handlers-for-dialog-box-controls.md)對話方塊類別中。  
  
4.  加入使用對話方塊的控制項，並指定相關聯的資料成員[對話方塊資料交換](../mfc/dialog-data-exchange.md)和[對話方塊資料驗證](../mfc/dialog-data-validation.md)的控制項。  
  
## <a name="see-also"></a>請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)
